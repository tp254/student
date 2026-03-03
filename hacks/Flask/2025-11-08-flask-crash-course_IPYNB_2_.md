---
layout: post
toc: True
breadcrumb: True
title: Crash Course into Python Flask
description: A discussion of key elements in a Python Flask backend project.  This includes preparing a project for deployment and interaction with a frontend.
categories: ['Python Flask']
permalink: /python/flask/crash-course
---

## Time to Review the README


Open the README of the Flask project and work through it. This is how you will get the backend app running on your localhost. Note that some familiarity with tools like Python, GitHub, and code editors (e.g., VSCode) is assumed


### Files and Directories in this Project

> These are some of the key files and directories in this project. Understanding these files will speed up your development 


- `README.md`: This file contains instructions for setting up the necessary tools and cloning the project. A README file is a standard component of all properly set up GitHub projects.


- `main.py`: This Python source file is used to run the project. Running this file starts a Flask web server locally on localhost. During development, this is the file you use to run, test, and debug the project.


- `__init__.py`: This file defines the Flask app, loads environment variables (from `.env`), and sets up security (like CORS) and database connections (SQLite or RDS). It acts as the main configuration and initialization hub for your backend.


- `Dockerfile` and `docker-compose.yml`: These files are used to run and test the project in a Docker container. They allow you to simulate the project's deployment on a server, such as an AWS EC2 instance. Running these files helps ensure that your tools and dependencies work correctly on a clean machine.


- `instances`: This directory is the standard location for storing data files that you want to remain on the server. For example, SQLite database files can be stored in this directory.  Files stored in this location will persist after a web application restart. Everything outside of instances will be recreated at restart.


- `api`: This directory contains code that receives and responds to requests from external servers. It serves as the interface between the external world and the logic and code in the rest of the project.


- `model`: This directory holds class definitions for interacting with the database (like SQLAlchemy models). Models can also connect to third-party APIs or machine learning libraries. By keeping data logic in `model`, you make your code reusable and keep the `api` code simple and clean.


- `requirements.txt`: This file lists the dependencies required to turn this Python project into a Flask/Python project. It may also include other backend dependencies, such as dependencies for working with a database.


- `.gitignore`: This file specifies elements to be excluded from version control. Files are excluded when they are derived and not considered part of the project's original source. In VSCode Explorer, you may notice some files appearing dimmed, indicating that they are intentionally excluded from version control based on the rules defined in .gitignore.

## Flask Server

As a developer, you will create or use a Flask app/server. This lesson will include some interactive steps to help you understand the basic code elements in a Flask server with RESTful endpoints.


> **Note:** This minimal, single-file server is just for learning. In real projects, code is split up for:
> - Routes (API endpoints)
> - Models (data and database)
> - Config (settings)
> - Logic (functions, helpers)
> 
> Later, you'll see how these parts are organized across multiple files.

### Installing dependencies

In a production server, the `requirements.txt` file lists all the packages you need to install, for example:

```
flask
flask_cors
flask_restful
```

Normally, you would run:

```
pip install -r requirements.txt
```

But since we’re working in a `pages` notebook and focusing on Flask usage, we’ll install the needed packages manually below.


```python
# The following lines are required packages for Flask execution
!pip install flask
!pip install flask_cors
!pip install flask_restful

```

    Collecting flask
      Downloading flask-3.1.2-py3-none-any.whl.metadata (3.2 kB)
    Collecting blinker>=1.9.0 (from flask)
      Downloading blinker-1.9.0-py3-none-any.whl.metadata (1.6 kB)
    Collecting click>=8.1.3 (from flask)
      Using cached click-8.3.0-py3-none-any.whl.metadata (2.6 kB)
    Collecting itsdangerous>=2.2.0 (from flask)
      Downloading itsdangerous-2.2.0-py3-none-any.whl.metadata (1.9 kB)
    Collecting jinja2>=3.1.2 (from flask)
      Using cached jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
    Collecting markupsafe>=2.1.1 (from flask)
      Using cached markupsafe-3.0.3-cp313-cp313-macosx_11_0_arm64.whl.metadata (2.7 kB)
    Collecting werkzeug>=3.1.0 (from flask)
      Downloading werkzeug-3.1.3-py3-none-any.whl.metadata (3.7 kB)
    Downloading flask-3.1.2-py3-none-any.whl (103 kB)
    Downloading blinker-1.9.0-py3-none-any.whl (8.5 kB)
    Using cached click-8.3.0-py3-none-any.whl (107 kB)
    Downloading itsdangerous-2.2.0-py3-none-any.whl (16 kB)
    Using cached jinja2-3.1.6-py3-none-any.whl (134 kB)
    Using cached markupsafe-3.0.3-cp313-cp313-macosx_11_0_arm64.whl (12 kB)
    Downloading werkzeug-3.1.3-py3-none-any.whl (224 kB)
    Installing collected packages: markupsafe, itsdangerous, click, blinker, werkzeug, jinja2, flask
    [2K   [38;2;114;156;31m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m7/7[0m [flask]m━━━━━━━━━━━[0m [32m5/7[0m [jinja2]
    [1A[2KSuccessfully installed blinker-1.9.0 click-8.3.0 flask-3.1.2 itsdangerous-2.2.0 jinja2-3.1.6 markupsafe-3.0.3 werkzeug-3.1.3
    
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m A new release of pip is available: [0m[31;49m25.2[0m[39;49m -> [0m[32;49m25.3[0m
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m To update, run: [0m[32;49mpip install --upgrade pip[0m
    Collecting flask_cors
      Downloading flask_cors-6.0.1-py3-none-any.whl.metadata (5.3 kB)
    Requirement already satisfied: flask>=0.9 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask_cors) (3.1.2)
    Requirement already satisfied: Werkzeug>=0.7 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask_cors) (3.1.3)
    Requirement already satisfied: blinker>=1.9.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask>=0.9->flask_cors) (1.9.0)
    Requirement already satisfied: click>=8.1.3 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask>=0.9->flask_cors) (8.3.0)
    Requirement already satisfied: itsdangerous>=2.2.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask>=0.9->flask_cors) (2.2.0)
    Requirement already satisfied: jinja2>=3.1.2 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask>=0.9->flask_cors) (3.1.6)
    Requirement already satisfied: markupsafe>=2.1.1 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask>=0.9->flask_cors) (3.0.3)
    Downloading flask_cors-6.0.1-py3-none-any.whl (13 kB)
    Installing collected packages: flask_cors
    Successfully installed flask_cors-6.0.1
    
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m A new release of pip is available: [0m[31;49m25.2[0m[39;49m -> [0m[32;49m25.3[0m
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m To update, run: [0m[32;49mpip install --upgrade pip[0m
    Collecting flask_restful
      Downloading Flask_RESTful-0.3.10-py2.py3-none-any.whl.metadata (1.0 kB)
    Collecting aniso8601>=0.82 (from flask_restful)
      Downloading aniso8601-10.0.1-py2.py3-none-any.whl.metadata (23 kB)
    Requirement already satisfied: Flask>=0.8 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask_restful) (3.1.2)
    Requirement already satisfied: six>=1.3.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from flask_restful) (1.17.0)
    Collecting pytz (from flask_restful)
      Using cached pytz-2025.2-py2.py3-none-any.whl.metadata (22 kB)
    Requirement already satisfied: blinker>=1.9.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (1.9.0)
    Requirement already satisfied: click>=8.1.3 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (8.3.0)
    Requirement already satisfied: itsdangerous>=2.2.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (2.2.0)
    Requirement already satisfied: jinja2>=3.1.2 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (3.1.6)
    Requirement already satisfied: markupsafe>=2.1.1 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (3.0.3)
    Requirement already satisfied: werkzeug>=3.1.0 in /Users/tanay/opencs/pages/venv/lib/python3.13/site-packages (from Flask>=0.8->flask_restful) (3.1.3)
    Downloading Flask_RESTful-0.3.10-py2.py3-none-any.whl (26 kB)
    Downloading aniso8601-10.0.1-py2.py3-none-any.whl (52 kB)
    Using cached pytz-2025.2-py2.py3-none-any.whl (509 kB)
    Installing collected packages: pytz, aniso8601, flask_restful
    [2K   [38;2;114;156;31m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m3/3[0m [flask_restful]
    [1A[2KSuccessfully installed aniso8601-10.0.1 flask_restful-0.3.10 pytz-2025.2
    
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m A new release of pip is available: [0m[31;49m25.2[0m[39;49m -> [0m[32;49m25.3[0m
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m To update, run: [0m[32;49mpip install --upgrade pip[0m


### Creating a Flask Server

This starts on Port `5001` and supports two endpoints `/` and `/api/data`.

- The `/api/data` endpoint now uses a model class to store and manage data, following best practices for larger systems.
- The API supports both `GET` (read all data) and `POST` (create new data) requests, matching CRUD naming conventions.
- This structure makes it easier to expand with more endpoints and features as your project grows.


```python
%%python --bg 

# Refactored: Use CRUD naming (read, create) in InfoModel
from flask import Flask, jsonify, request
from flask_cors import CORS
from flask_restful import Api, Resource

app = Flask(__name__)
CORS(app, supports_credentials=True, origins='*')

api = Api(app)

# --- Model class for InfoDb with CRUD naming ---
class InfoModel:
    def __init__(self):
        self.data = [
            {
                "FirstName": "John",
                "LastName": "Mortensen",
                "DOB": "October 21",
                "Residence": "San Diego",
                "Email": "jmortensen@powayusd.com",
                "Owns_Cars": ["2015-Fusion", "2011-Ranger", "2003-Excursion", "1997-F350", "1969-Cadillac", "2015-Kuboto-3301"]
            },
            {
                "FirstName": "Shane",
                "LastName": "Lopez",
                "DOB": "February 27",
                "Residence": "San Diego",
                "Email": "slopez@powayusd.com",
                "Owns_Cars": ["2021-Insight"]
            }
        ]

    def read(self):
        return self.data

    def create(self, entry):
        self.data.append(entry)

# Instantiate the model
info_model = InfoModel()

# --- API Resource ---
class DataAPI(Resource):
    def get(self):
        return jsonify(info_model.read())

    def post(self):
        # Add a new entry to InfoDb
        entry = request.get_json()
        if not entry:
            return {"error": "No data provided"}, 400
        info_model.create(entry)
        return {"message": "Entry added successfully", "entry": entry}, 201

api.add_resource(DataAPI, '/api/data')

# Wee can use @app.route for HTML endpoints, this will be style for Admin UI
@app.route('/')
def say_hello():
    html_content = """
    <html>
    <head>
        <title>Hello</title>
    </head>
    <body>
        <h2>Hello, World!</h2>
    </body>
    </html>
    """
    return html_content

if __name__ == '__main__':
    app.run(port=5001)
```

### Explore the Python/Flask app with Linux
This script discovers the running flask process on your machine using Linux commands.

1. lsof - list open files
2. `lsof` and `awk` return the process id, so `ps` can list details, the vericle bar is called a `pipe`.  A pipe flows output from one command to the next.
3. `curl` is a Linux utiltity that is easiest way to test if web server is responding


```python
%%script bash

# After app.run(), see the the Python open files on port 5001
echo "Python open files on port 5001" 
lsof -i :5001
# see the the Python process 
echo
echo "Python process"
lsof -i :5001 | awk '/Python/ {print $2}' | xargs ps
# show ontent of the Python server using curl
echo
echo "Content of the Python root endpoint (aka /), using curl",  
curl http://localhost:5001/
```

    Python open files on port 5001
    
    Python process
    
    Content of the Python root endpoint (aka /), using curl,


      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
      0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
    curl: (7) Failed to connect to localhost port 5001 after 0 ms: Couldn't connect to server



    ---------------------------------------------------------------------------

    CalledProcessError                        Traceback (most recent call last)

    Cell In[3], line 1
    ----> 1 get_ipython().run_cell_magic('script', 'bash', '\n# After app.run(), see the the Python open files on port 5001\necho "Python open files on port 5001" \nlsof -i :5001\n# see the the Python process \necho\necho "Python process"\nlsof -i :5001 | awk \'/Python/ {print $2}\' | xargs ps\n# show ontent of the Python server using curl\necho\necho "Content of the Python root endpoint (aka /), using curl",  \ncurl http://localhost:5001/\n')


    File ~/opencs/pages/venv/lib/python3.13/site-packages/IPython/core/interactiveshell.py:2565, in InteractiveShell.run_cell_magic(self, magic_name, line, cell)
       2563 with self.builtin_trap:
       2564     args = (magic_arg_s, cell)
    -> 2565     result = fn(*args, **kwargs)
       2567 # The code below prevents the output from being displayed
       2568 # when using magics with decorator @output_can_be_silenced
       2569 # when the last Python token in the expression is a ';'.
       2570 if getattr(fn, magic.MAGIC_OUTPUT_CAN_BE_SILENCED, False):


    File ~/opencs/pages/venv/lib/python3.13/site-packages/IPython/core/magics/script.py:348, in ScriptMagics.shebang(self, line, cell)
        343 if args.raise_error and p.returncode != 0:
        344     # If we get here and p.returncode is still None, we must have
        345     # killed it but not yet seen its return code. We don't wait for it,
        346     # in case it's stuck in uninterruptible sleep. -9 = SIGKILL
        347     rc = p.returncode or -9
    --> 348     raise CalledProcessError(rc, cell)


    CalledProcessError: Command 'b'\n# After app.run(), see the the Python open files on port 5001\necho "Python open files on port 5001" \nlsof -i :5001\n# see the the Python process \necho\necho "Python process"\nlsof -i :5001 | awk \'/Python/ {print $2}\' | xargs ps\n# show ontent of the Python server using curl\necho\necho "Content of the Python root endpoint (aka /), using curl",  \ncurl http://localhost:5001/\n'' returned non-zero exit status 7.


### Accessing Flask Server with JavaScript

JavaScript is used to `fetch` data from the backend. After data is received, it is formatted into the HTML DOM.

1. HTML is used to set up the basics of a table.
2. The `<script>` contains JavaScript with a `fetch` that passes the endpoint (URL) and options. The options are critical to communicating request requirements; bad options produce bad results.
3. Data is extracted and written to the `DOM`. Headings are static in the code, but rows are dynamically extracted according to the information contained in the server.


```python
%%html

<h1>Flask app access using JavaScript</h1>

<p>This code extracts data "live" from a local Web Server with JavaScript fetch.  Additionally, it formats the data into a table.</p>

<!-- Head contains information to Support the Document -->


<!-- HTML table fragment for page -->
<table id="demo" class="table">
  <thead>
      <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Residence</th>
      </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
</table>

<script>
{ // Jupyter Notebook container to avoid variable name conflicts

  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");
  
  // prepare URL
  url = "http://localhost:5001/api/data";

  // set options for cross origin header request
  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'include', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json',
    },
  };

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors and display
      if (response.status !== 200) {
          console.error(response.status);
          return;
      }
      // valid response will contain json data
      response.json().then(data => {
          console.log(data);
          for (const row of data) {
            // tr and td build out for each row
            const tr = document.createElement("tr");
            const firstname = document.createElement("td");
            const lastname = document.createElement("td");
            const residence = document.createElement("td");
            // data is specific to the API
            firstname.innerHTML = row.FirstName; 
            lastname.innerHTML = row.LastName; 
            residence.innerHTML = row.Residence; 
            // this builds each td into tr
            tr.appendChild(firstname);
            tr.appendChild(lastname);
            tr.appendChild(residence);
            // add HTML to container
            resultContainer.appendChild(tr);
          }
      })
  })
} 
</script>
```



<h1>Flask app access using JavaScript</h1>

<p>This code extracts data "live" from a local Web Server with JavaScript fetch.  Additionally, it formats the data into a table.</p>

<!-- Head contains information to Support the Document -->


<!-- HTML table fragment for page -->
<table id="demo" class="table">
  <thead>
      <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Residence</th>
      </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
</table>

<script>
{ // Jupyter Notebook container to avoid variable name conflicts

  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare URL
  url = "http://localhost:5001/api/data";

  // set options for cross origin header request
  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'include', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json',
    },
  };

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors and display
      if (response.status !== 200) {
          console.error(response.status);
          return;
      }
      // valid response will contain json data
      response.json().then(data => {
          console.log(data);
          for (const row of data) {
            // tr and td build out for each row
            const tr = document.createElement("tr");
            const firstname = document.createElement("td");
            const lastname = document.createElement("td");
            const residence = document.createElement("td");
            // data is specific to the API
            firstname.innerHTML = row.FirstName; 
            lastname.innerHTML = row.LastName; 
            residence.innerHTML = row.Residence; 
            // this builds each td into tr
            tr.appendChild(firstname);
            tr.appendChild(lastname);
            tr.appendChild(residence);
            // add HTML to container
            resultContainer.appendChild(tr);
          }
      })
  })
} 
</script>



### Add to the InfoDB Array

This example allows you to accept input from the user and add it to the InfoDB.

- Enter a first name, last name, and residence, then click 'Add User' to submit.
- The form sends a POST request to the Flask API and updates the InfoDB in memory.
- Re-run the data table above to see your new entry appear.
- Data is persistent only while the server is running; stopping the server will clear the InfoDB to code defaults.
- For true persistence, a database is needed instead of an in-memory array.


```python
%%html

<h3>Add a New User to InfoDB</h3>
<form id="addUserForm">
  <label for="firstName">First Name:</label>
  <input type="text" id="firstName" name="firstName" required><br>
  <label for="lastName">Last Name:</label>
  <input type="text" id="lastName" name="lastName" required><br>
  <label for="residence">Residence:</label>
  <input type="text" id="residence" name="residence" required><br>
  <button type="submit">Add User</button>
</form>
<div id="addUserResult"></div>

<script>
document.getElementById('addUserForm').addEventListener('submit', async function(event) {
  event.preventDefault();
  const firstName = document.getElementById('firstName').value;
  const lastName = document.getElementById('lastName').value;
  const residence = document.getElementById('residence').value;
  const data = {
    FirstName: firstName,
    LastName: lastName,
    Residence: residence
  };
  try {
    const response = await fetch('http://localhost:5001/api/data', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    });
    const result = await response.json();
    if (response.ok) {
      document.getElementById('addUserResult').innerHTML = '<span style="color:green">User added!</span>';
      document.getElementById('addUserForm').reset();
    } else {
      document.getElementById('addUserResult').innerHTML = '<span style="color:red">' + (result.error || 'Error adding user') + '</span>';
    }
  } catch (err) {
    document.getElementById('addUserResult').innerHTML = '<span style="color:red">Network error</span>';
  }
});
</script>
```



<h3>Add a New User to InfoDB</h3>
<form id="addUserForm">
  <label for="firstName">First Name:</label>
  <input type="text" id="firstName" name="firstName" required><br>
  <label for="lastName">Last Name:</label>
  <input type="text" id="lastName" name="lastName" required><br>
  <label for="residence">Residence:</label>
  <input type="text" id="residence" name="residence" required><br>
  <button type="submit">Add User</button>
</form>
<div id="addUserResult"></div>

<script>
document.getElementById('addUserForm').addEventListener('submit', async function(event) {
  event.preventDefault();
  const firstName = document.getElementById('firstName').value;
  const lastName = document.getElementById('lastName').value;
  const residence = document.getElementById('residence').value;
  const data = {
    FirstName: firstName,
    LastName: lastName,
    Residence: residence
  };
  try {
    const response = await fetch('http://localhost:5001/api/data', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    });
    const result = await response.json();
    if (response.ok) {
      document.getElementById('addUserResult').innerHTML = '<span style="color:green">User added!</span>';
      document.getElementById('addUserForm').reset();
    } else {
      document.getElementById('addUserResult').innerHTML = '<span style="color:red">' + (result.error || 'Error adding user') + '</span>';
    }
  } catch (err) {
    document.getElementById('addUserResult').innerHTML = '<span style="color:red">Network error</span>';
  }
});
</script>



## Stop the Python/Flask process
This script ends the Python/Flask process using pipes to obtain the python process. Then echo the python process to `kill -9`.


```python
%%script bash

python_ps=$(lsof -i :5001 | awk '/Python/ {print $2}')
echo "Killing python process with PID: $python_ps"
echo $python_ps | xargs kill -9
```

    Killing python process with PID: 

