<h2 align="center">
  🚀 Coffee Shop
</h2>

<p align="center">
  
  <a href="https://github.com/Silve1ra/coffee-shop/commits/main">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/Silve1ra/coffee-shop">
  </a>

  <a href="https://github.com/Silve1ra/coffee-shop/issues">
    <img alt="Repository issues" src="https://img.shields.io/github/issues/Silve1ra/coffee-shop">
  </a>

  <img alt="License" src="https://img.shields.io/badge/license-MIT-brightgreen">
</p>

This project is a Coffee Shop. 
All backend code follows [PEP8 style guidelines](https://www.python.org/dev/peps/pep-0008/).

## Getting Started

### Pre-requisites and Local Development 
Developers using this project should already have Python3, pip and node installed on their local machines.

#### Backend

To run the application run the following commands: 
```
pip install -r requirements.txt
```
```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```
or (Windows 10 PowerShell):
```
$env:FLASK_APP='flaskr'
$env:FLASK_ENV='development'
flask run
```

The api run on `http://127.0.0.1:5000/` and the app on `http://127.0.0.1:4200`. 

#### Frontend

From the frontend folder, run the following commands to start the client: 
```
npm install // only once to install dependencies
npm start 
```

## API Reference

### Getting Started
- Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, `http://127.0.0.1:5000/`, which is set as a proxy in the frontend configuration. 
- Authentication: This application has specific functionalities where it requires authentication. 

### Error Handling
Errors are returned as JSON objects in the following format:
```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:
- 400: Bad Request
- 401: Unauthorized
- 404: Resource Not Found
- 405: Method Not Allowed
- 422: Not Processable
- 500: Internal Server Error

### Endpoints 
#### GET /categories
- General:
    - Returns a list of drinks and a message with success status.
    - This functionality is public for any user.
- Sample: `http://127.0.0.1:5000/drinks`
```
{
  "drinks": [
    {
      "id": 1,
      "recipe": [
        {
          "color": "blue",
          "parts": 1
        }
      ],
      "title": "water"
    }
  ],
  "success": true
}
```

#### GET /drinks-detail
- General:
    - Returns a list of the drinks details and a message with success status.
    - This functionality is restritected to specific logged in user roles.
- Sample: `http://127.0.0.1:5000/drinks-detail`
```{
  "drinks": [
    {
      "id": 1,
      "recipe": [
        {
          "color": "blue",
          "name": "water",
          "parts": 1
        }
      ],
      "title": "water"
    }
]
```

#### POST /drinks
- General:
    - Creates a new drink using the submitted title and recipe, with name, color and parts. Returns the created drink and a message with success status.
    - This functionality is restritected to specific logged in user roles.
- `http://127.0.0.1:5000/drinks`
```
body example
{
    "title": "Water2",
    "recipe": {
        "name": "Water",
        "color": "blue",
        "parts": 1
    }
}
```
```
response:
{
  "drinks": [
    {
      "id": 2,
      "recipe": [
        {
          "color": "blue",
          "name": "Water",
          "parts": 1
        }
      ],
      "title": "Water2"
    }
  ],
  "success": true
}
```

#### PATCH /drinks/{drink_id}
- General:
    - Updates the drink of the given ID and the submitted title and recipe information. Returns updated drink and a message with success status.
    - This functionality is restritected to specific logged in user roles.
- `http://127.0.0.1:5000/drinks/1`
```
body example
{
	"title": "water 2 new",
	"recipe": [
		{
			"color": "pink",
			"name": "Water",
			"parts": 1
		}
	]
}
```
```
response
{
  "drinks": [
    {
      "id": 2,
      "recipe": [
        {
          "color": "pink",
          "name": "Water",
          "parts": 1
        }
      ],
      "title": "water 2 new"
    }
  ],
  "success": true
}
```

#### DELETE /drinks/{drink_id}
- General:
    - Deletes the drink of the given ID if it exists. Returns the id of the deleted drink and a message with success status.
    - This functionality is restritected to specific logged in user roles.
- `http://127.0.0.1:5000/drinks/1`
```
{
  "deleted": 1,
  "success": true
}
```

## Authors
Yours truly, <a href="https://github.com/Silve1ra"><b>Felipe Silveira</b> 

## Acknowledgements 
The awesome Udacity Nanodegree helping me to be an extraordinary full stack developer! 
