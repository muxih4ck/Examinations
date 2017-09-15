
[Installing Ubuntu inside Windows using VirtualBox](http://www.psychocats.net/ubuntu/virtualbox)

# Flask

> Flask is a microframework for building web applications with Python.

## What do Flask Apps look like

example code of applications written with Flask:

* [flaskr](https://github.com/pallets/flask/tree/master/examples/flaskr/) — a microblog
* [minitwit](https://github.com/pallets/flask/tree/master/examples/minitwit/) — a twitter clone
* [this website](https://github.com/pallets/flask-website) — static pages + mailinglist archives

## Install Flask

### Install easy-install

Easy Install is a python module bundled with
that lets you automatically download, build, install, and manage Python
packages.

```shell
$ sudo apt-get install python-setuptools python-dev build-essential
```

⚠️ Attention: do not include the **$** when copying the code

### Install pip

```shell
$ sudo easy_install pip
```

### Install Flask

```shell
$ pip install flask
```

## A Minimal Application

A minimal Flask application looks something like this:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```

So what did that code do?

* First we imported the Flask class. An instance of this class will be our WSGI application.

* Next we create an instance of this class. The first argument is the name of the application’s module or package. If you are using a single module (as in this example), you should use `__name__` because depending on if it’s started as application or imported as module the name will be different ('__main__' versus the actual import name). This is needed so that Flask knows where to look for templates, static files, and so on.

We then use the route() [decorator](https://www.programiz.com/python-programming/decorator) to tell Flask what URL should trigger our function.
The function is given a name which is also used to generate URLs for that particular function, and returns the message we want to display in the user’s browser.
Just save it as `hello.py`. Make sure to not call your application `flask.py` because this would conflict with Flask itself.

To run the application you can either use the flask command or python’s -m switch with Flask. Before you can do that you need to tell your terminal the application to work with by exporting the FLASK_APP environment variable:

```shell
$ export FLASK_APP=hello.py
$ flask run
 * Running on http://127.0.0.1:5000/
```

If you are on Windows you need to use set instead of export.

Alternatively you can use python -m flask:

```shell
$ export FLASK_APP=hello.py
$ python -m flask run
 * Running on http://127.0.0.1:5000/
```

This launches a very simple builtin server, which is good enough for testing. Now head over to http://127.0.0.1:5000/, and you should see your hello world greeting.

## What to do if the Server does not Start
In case the python -m flask fails or flask does not exist, there are multiple reasons this might be the case. First of all you need to look at the error message.

### Old Version of Flask

Versions of Flask older than 0.11 use to have different ways to start the application. In short, the flask command did not exist, and neither did python -m flask. In that case you have two options: either upgrade to newer Flask versions or have a look at the Development Server docs to see the alternative method for running a server.

### Invalid Import Name

The `FLASK_APP` environment variable is the name of the module to import at flask run. In case that module is incorrectly named you will get an import error upon start (or if debug is enabled when you navigate to the application). It will tell you what it tried to import and why it failed.

The most common reason is a typo or because you did not actually create an app object.

## Debug Mode

The flask script is nice to start a local development server, but you would have to restart it manually after each change to your code. That is not very nice and Flask can do better. If you enable debug support the server will reload itself on code changes, and it will also provide you with a helpful debugger if things go wrong.

To enable debug mode you can export the `FLASK_DEBUG` environment variable before running the server:

```shell
$ export FLASK_DEBUG=1
$ flask run
(On Windows you need to use set instead of export).
```

This does the following things:

* it activates the debugger
* it activates the automatic reloader
* it enables the debug mode on the Flask application.
* There are more parameters that are explained in the Development Server docs.

## Routing

Modern web applications have beautiful URLs. This helps people remember the URLs, which is especially handy for applications that are used from mobile devices with slower network connections.

As you have seen above, the route() decorator is used to bind a function to a URL. Here are some basic examples:

```python
@app.route('/')
def index():
    return 'Index Page'

@app.route('/hello/')
def hello():
    return 'Hello, World'
```

But there is more to it! You can make certain parts of the URL dynamic and attach multiple rules to a function.

### Variable Rules

To add variable parts to a URL you can mark these special sections as <variable_name>. Such a part is then passed as a keyword argument to your function. Optionally a converter can be used by specifying a rule with <converter:variable_name>. Here are some nice examples:

```python
@app.route('/user/<username>/')
def show_user_profile(username):
    # show the user profile for that user
    return 'User %s' % username

@app.route('/post/<int:post_id>/')
def show_post(post_id):
    # show the post with the given id, the id is an integer
    return 'Post %d' % post_id
```

The following **converters** exist:

```
string	accepts any text without a slash (the default)
int	accepts integers
float	like int but for floating point values
path	like the default but also accepts slashes
any	matches one of the items provided
uuid	accepts UUID strings
Unique URLs / Redirection Behavior
```

## URL Building

Flask can also generate URLs. To build a URL to a specific function you can use the `url_for()` function. It accepts the name of the function as first argument and a number of keyword arguments, each corresponding to the variable part of the URL rule. Unknown variable parts are appended to the URL as query parameters. Here are some examples:

run `python` in your terminal to get an python interpreter

```python
>>> from flask import Flask, url_for
>>> app = Flask(__name__)
>>> @app.route('/')
... def index(): pass
...
>>> @app.route('/login/')
... def login(): pass
...
>>> @app.route('/user/<username>/')
... def profile(username): pass
...
>>> with app.test_request_context():
...  print url_for('index')
...  print url_for('login')
...  print url_for('login', next='/')
...  print url_for('profile', username='John Doe')
...
/
/login
/login?next=/
/user/John%20Doe
```

(This uses the `test_request_context()` method. It tells Flask to behave as though it is handling a request, even though we are interacting with it through a Python shell.).

Why would you want to build URLs using the URL reversing function url_for() instead of hard-coding them into your templates?

* Reversing is often more descriptive than hard-coding the URLs. More importantly, it allows you to change URLs in one go, without having to remember to change URLs all over the place.
* URL building will handle escaping of special characters and Unicode data transparently for you, so you don’t have to deal with them.
* If your application is placed outside the URL root - say, in /myapplication instead of / - url_for() will handle that properly for you.

## Rendering Templates

Flask configures the Jinja2 template engine for you automatically.

To render a template you can use the render_template() method. All you have to do is provide the name of the template and the variables you want to pass to the template engine as keyword arguments. Here’s a simple example of how to render a template:

```python
from flask import render_template

@app.route('/hello/')
@app.route('/hello/<name>')
def hello(name=None):
    return render_template('hello.html', name=name)
```

Flask will look for templates in the `templates` folder. So if your application is a module, this folder is next to that module, if it’s a package it’s actually inside your package:

```shell
Case 1: a module:

/application.py
/templates
    /hello.html
-----------------------------
Case 2: a package:

/application
    /__init__.py
    /templates
        /hello.html
```

For templates you can use the full power of Jinja2 templates.

Here is an example template:

```html
<!doctype html>
<title>Hello from Flask</title>
{% if name %}
  <h1>Hello {{ name }}!</h1>
{% else %}
  <h1>Hello, World!</h1>
{% endif %}
```

## HTTP Methods

HTTP (the protocol web applications are speaking) knows different methods for accessing URLs. By default, a route only answers to GET requests, but that can be changed by providing the methods argument to the route() decorator. Here are some examples:

```python
from flask import request

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        do_the_login()
    else:
        show_the_login_form()
```

Here is a quick introduction to HTTP methods and why they matter:

The HTTP method (also often called “the verb”) tells the server what the client wants to do with the requested page. The following methods are very common:

### GET

The browser tells the server to just get the information stored on that page and send it. This is probably the most common method.

### POST

The browser tells the server that it wants to post some new information to that URL.use `request.form.get('<name>')`,**name** is the name of the variable that you want.

### DELETE

Remove the information at the given location.

## Redirects and Errors¶

To redirect a user to another endpoint, use the `redirect()` function; to abort a request early with an error code, use the `abort()` function:

```python
from flask import abort, redirect, url_for

@app.route('/')
def index():
    return redirect(url_for('login'))

@app.route('/login/')
def login():
    abort(401)
    this_is_never_executed()
```

This is a rather pointless example because a user will be redirected from the index to a page they cannot access (401 means access denied) but it shows how that works.

By default a black and white error page is shown for each error code. If you want to customize the error page, you can use the errorhandler() decorator:

```python
from flask import render_template

@app.errorhandler(404)
def page_not_found(error):
    return render_template('page_not_found.html'), 404
```

Note the 404 after the render_template() call. This tells Flask that the status code of that page should be 404 which means not found. By default 200 is assumed which translates to: all went well.