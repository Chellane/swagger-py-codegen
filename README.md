# RESTful Web Framework Generator

[![Build Status][travis-image]][travis-url] [![PyPi Version][pypi-image]][pypi-url]

## Overview


This is a swagger codegen project for Python web framework, which allows generation of RESTful application code automatically given a Swagger Specification doc. Currently, the following languages/frameworks are supported:

* [Flask](http://flask.pocoo.org/) (Python)
* [Tornado](http://www.tornadoweb.org/en/stable/) (Python)
* [Falcon](https://falconframework.org/) (Python)


**Alpha version for now, it can not handle all validation properly.**


## Install

```
pip install swagger-py-codegen
```

## Usage

Create all:

```
swagger_py_codegen --swagger-doc api.yml example-app
```

Command Options:

	-s, --swagger, --swagger-doc    Swagger doc file.  [required]
	-f, --force                     Force overwrite.
	-p, --package                   Package name / application name.
	-t, --template-dir              Path of your custom templates directory.
	--spec, --specification         Generate online specification json response.
	--ui                            Generate swagger ui.
	-j, --jobs INTEGER              Parallel jobs for processing.
	-tlp, --templates               gen flask/tornado/falcon templates, default flask.
	--version                       Show current version.
	--help                          Show this message and exit.

## Examples:

Generate example-app from [api.yml](https://github.com/guokr/swagger-py-codegen/blob/master/api.yml "Title"):

#### Flask Example

    $tree
	.
	|__ api.yml

    $ swagger_py_codegen -s api.yml example-app -p demo
    $ tree (flask-demo)
	.
	|__ api.yml
	|__ example-app
	   |__ demo
	   |  |__ __init__.py
	   |  |__ v1
	   |     |__ api
	   |     |  |__ __init__.py
	   |     |  |__ oauth_auth_approach_approach.py
	   |     |  |__ oauth_auth_approach.py
	   |     |  |__ users_token.py
	   |     |  |__ users_current.py
	   |     |  |__ users.py
	   |     |__ __init__.py
	   |     |__ routes.py
	   |     |__ schemas.py
	   |     |__ validators.py
	   |__ requirements.txt

#### Tornado Example

	$ swagger_py_codegen -s api.yml example-app -p demo -tlp=tornado
    $ tree (tornado-demo)
	.
	|__ api.yml
	|__ example-app
	   |__ demo
	   |  |__ __init__.py
	   |  |__ core
	   |     |__ __init.py
	   |  |__ v1
	   |     |__ api
	   |     |  |__ __init__.py
	   |     |  |__ oauth_auth_approach_approach.py
	   |     |  |__ oauth_auth_approach.py
	   |     |  |__ users_token.py
	   |     |  |__ users_current.py
	   |     |  |__ users.py
	   |     |__ __init__.py
	   |     |__ routes.py
	   |     |__ schemas.py
	   |     |__ validators.py
	   |__ requirements.txt

#### Falcon Example

    $ swagger_py_codegen -s api.yml example-app -p demo -tlp=falcon
    $ tree (falcon-demo)
	.
	|__ api.yml
	|__ example-app
	   |__ demo
	   |  |__ __init__.py
	   |  |__ v1
	   |     |__ api
	   |     |  |__ __init__.py
	   |     |  |__ oauth_auth_approach_approach.py
	   |     |  |__ oauth_auth_approach.py
	   |     |  |__ users_token.py
	   |     |  |__ users_current.py
	   |     |  |__ users.py
	   |     |__ __init__.py
	   |     |__ routes.py
	   |     |__ schemas.py
	   |     |__ validators.py
	   |__ requirements.txt

#### Run Web Server

Install example-app requirements:

    $ cd example-app
    $ pip install -r requirements.txt

Start example-app:

    $ cd demo
    $ python __init__.py

And generate example-app-ui from api.yml with ui:

    $ swagger_py_codegen -s api.yml  example-app-ui -p demo-ui --ui --spec

Then you can visit [http://127.0.0.1:5000/static/swagger-ui/index.html](http://127.0.0.1:5000/static/swagger-ui/index.html) in a browser.


## Compatibility

|component|compatibility|
|-----|-----|
|OpenAPI Spec|2.0|
|Python|2.\*, 3.\*|


## Authors

See the [AUTHORS](https://github.com/guokr/swagger-py-codegen/blob/master/AUTHORS "Title").


## License

MIT

[travis-url]: https://travis-ci.org/guokr/swagger-py-codegen
[travis-image]: https://travis-ci.org/guokr/swagger-py-codegen.svg

[pypi-url]: https://pypi.python.org/pypi/swagger-py-codegen/
[pypi-image]: https://img.shields.io/pypi/v/swagger-py-codegen.svg?style=flat-square
