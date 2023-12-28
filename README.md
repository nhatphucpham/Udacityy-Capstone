# Casting Agency Project

Udacity Full-Stack Web Developer Nanodegree Program Capstone Project

-   [Heroku](https://capstone-casting-a15b45204462.herokuapp.com/): Link Heroku

## Project Motivation

The Casting Agency Project models a company that is responsible for creating movies and managing and assigning actors to those movies. You are an Executive Producer within the company and are creating a system to simplify and streamline your process.

This project is simply a workspace for practicing and showcasing different set of skills related with web development. These include data modelling, API design, authentication and authorization and cloud deployment.

## Getting Started

The project adheres to the PEP 8 style guide and follows common best practices, including:

-   Variable and function names are clear.
-   Endpoints are logically named.
-   Code is commented appropriately.
-   Secrets are stored as environment variables.

### Key Dependencies & Platforms

-   [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

-   [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

-   [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

-   [Auth0](https://auth0.com/docs/) is the authentication and authorization system we'll use to handle users with different roles with more secure and easy ways

-   [PostgreSQL](https://www.postgresql.org/) this project is integrated with a popular relational database PostgreSQL, though other relational databases can be used with a little effort.

-   [Heroku](https://www.heroku.com/what) is the cloud platform used for deployment

### Running Locally

#### Installing Dependencies

##### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

##### Virtual Environment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organized. Instructions for setting up a virtual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

Once you have your virtual environment setup and running, install dependencies by running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

#### Database Setup

With Postgres running, restore a database using the `capstone.psql` file provided. In terminal run:

```bash
createdb capstone
psql capstone < capstone.psql
```

#### Running Tests

To run the tests, run

```bash
dropdb capstone_test
createdb capstone_test
psql capstone_test < capstone.psql
python test_app.py
```

#### Auth0 Setup

You need to setup an Auth0 account.

Environment variables needed: (setup.sh)

```bash
export AUTH0_DOMAIN="dev-sif3oiav3j1s6ypx.us.auth0.com" # Choose your tenant domain # Example : dev-fsnd-capstone.us.auth0.com
export ALGORITHMS="RS256"
export API_AUDIENCE="capstone" # Create an API in Auth0
```

##### Roles

-   Casting Assistant

    -   GET /actors and /movies

-   Casting Director

    -   GET /actors and /movies
    -   ADD /actors and DELETE /actors
    -   PATCH /actors and /movies

-   Executive Producer

    -   GET /actors and /movies
    -   ADD /actors and DELETE /actors
    -   PATCH /actors and /movies
    -   ADD /movies and DELETE /movies

##### Permissions

Following permissions should be created under created API settings.

-   Movies Permissions

    -   `get:movies`
    -   `create:movies`
    -   `update:movies`
    -   `delete:movies`

-   Actors Permissions

    -   `get:actors`
    -   `create:actors`
    -   `update:actors`
    -   `delete:actors`

##### JWT Tokens for each role:

-   Casting Assistant - `eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkFnTGRtdDJSYk5rODRVX1p6bk5HSiJ9.eyJpc3MiOiJodHRwczovL2Rldi1zaWYzb2lhdjNqMXM2eXB4LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJhdXRoMHw2NThkMGIzMzdkYWFkNDI4MDEwOGVlMWUiLCJhdWQiOiJjYXBzdG9uZSIsImlhdCI6MTcwMzc0MjM4MCwiZXhwIjoxNzAzNzQ5NTgwLCJhenAiOiJQRmFieW1OVnQyYXBPZzBGZnpIWFpjelVxbWZtVjBuUiIsInNjb3BlIjoiIiwicGVybWlzc2lvbnMiOlsiZ2V0OmFjdG9ycyIsImdldDptb3ZpZXMiXX0.XNkwFnFiLngWrahcaTsANw2gl-CfdghwB6xCnJDd5mD54jtdJvbfbExjV7iyu9HsGjcigni_hLXBVSUqHEbW5FJBYiXPG1Ptq7exMYzk0S442bALO7rYNdaUm9X57cd0k8P7wrd_5mYUll5RXCQ3D-0HgzSaAMu2J5C1CO5xLXR-FLM8jKOhTiIpmbWgUbowi-HQOM7rTGi4ypreqdxHX9AL1h7yGRBn6h9Vn9DikNWUKzeiFhCaXe3G3dj4QXF43TzUPK6b024VDKmUCr6_PrpiuRVBsmEXnuVJN_iQE2dGzeeRrrmCSN_ljaeiV1tJYnA28kkYAAnU2tddH3qd-A`

-   Casting Director : `eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkFnTGRtdDJSYk5rODRVX1p6bk5HSiJ9.eyJpc3MiOiJodHRwczovL2Rldi1zaWYzb2lhdjNqMXM2eXB4LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJhdXRoMHw2NThkMGJmMGNjMDIyNmQ0YWY5MmZkNzAiLCJhdWQiOiJjYXBzdG9uZSIsImlhdCI6MTcwMzc0MjQ4NSwiZXhwIjoxNzAzNzQ5Njg1LCJhenAiOiJQRmFieW1OVnQyYXBPZzBGZnpIWFpjelVxbWZtVjBuUiIsInNjb3BlIjoiIiwicGVybWlzc2lvbnMiOlsiY3JlYXRlOmFjdG9ycyIsImRlbGV0ZTphY3RvcnMiLCJnZXQ6YWN0b3JzIiwiZ2V0Om1vdmllcyIsInVwZGF0ZTphY3RvcnMiLCJ1cGRhdGU6bW92aWVzIl19.sKjozPaNyyNbyW_zMqxglR0-ZVSXBMQryPh-Qia_ZxXF8wyioJh5KsIuX35aKj--5iL6IvyitszdbvpAscRyLc3CSUpFHxquEIQbzRIVxp0iiUF4_wGVuubCNoBP0zaoXJ3HPDdy0W5qSf4kJsvvsmMHPzNe8N5PBUL1OMoMkFDK53W-LbgsM1PBVGwbCNKQuMT-UiY9gLMyawvgdKitRKzFKVNcB_bxW1jNXIcKb0b-5JcuLY5NmkdbaUZF44STGeNapzM_r96PF-D-gZu4vbVXfGBh0mVlDaRDeFCraOe-PymwzW_ytnsh--rZlqS7JBEM0YUtVIOK2E5PtiNrEw`

-   Executive Producer : `eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkFnTGRtdDJSYk5rODRVX1p6bk5HSiJ9.eyJpc3MiOiJodHRwczovL2Rldi1zaWYzb2lhdjNqMXM2eXB4LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJnb29nbGUtb2F1dGgyfDEwMTUwNDk1ODI2MTIyMTc2ODcxMCIsImF1ZCI6ImNhcHN0b25lIiwiaWF0IjoxNzAzNzQyMTQxLCJleHAiOjE3MDM3NDkzNDEsImF6cCI6IlBGYWJ5bU5WdDJhcE9nMEZmekhYWmN6VXFtZm1WMG5SIiwic2NvcGUiOiIiLCJwZXJtaXNzaW9ucyI6WyJjcmVhdGU6YWN0b3JzIiwiY3JlYXRlOm1vdmllcyIsImRlbGV0ZTphY3RvcnMiLCJkZWxldGU6bW92aWVzIiwiZ2V0OmFjdG9ycyIsImdldDptb3ZpZXMiLCJ1cGRhdGU6YWN0b3JzIiwidXBkYXRlOm1vdmllcyJdfQ.DJb5gjPrFnUTRX6BFZbJvxcb7WNfVhUaHvhL6Kn08jNCQcoJ6ODS5CJmhmr5Mtjt7SRyOSvFnl0BOJ9zAozphnhK9FQlL2FdrX2sIO-vrWUH7ZEHvSAzDr97lH1y9Xj6B5pH3Y4oYV809-dFR4egtT0wxM-qzWVpYqmlvqz-a_VTBEXL7z3y1FmrBPnqBHFco6Uj_vZrkY_55IiVd3yYzpA6z7YpnbkUB19ufalw5Aun083Gz1VRfU8rnCEV6nb4bYwaFbHTLAaLhpL2p-CurKFue9fige72CMqVQWWwIYpBi0zmWiB0VObAtN0Kauxlms83YE1ibN1wNDvobmDPtQ`

##### Set JWT Tokens in `auth_config.json`

Use the following link to create users and sign them in. This way, you can generate

```
https://dev-sif3oiav3j1s6ypx.us.auth0.com/authorize?audience=capstone&response_type=token&client_id=PFabymNVt2apOg0FfzHXZczUqmfmV0nR&redirect_uri=https://render-deployment-capstone-xfu3.onrender.com/
```

#### Launching The App

1.  Initialize and activate a virtualenv:

    ```bash
    virtualenv --no-site-packages env_capstone
    source env_capstone/bin/activate
    ```

2.  Install the dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3.  Configure database path to connect local postgres database in `models.py`

        ```python
        database_path = "postgresql://{}/{}".format('localhost:5432', 'capstone_project')
        ```

    **Note:** For default postgres installation, default user name is `postgresql` with no password. But if you need, you can use this template:

        ```python
        database_path = "postgresql://{}:{}@{}/{}".format({{YOUR_USERNAME}}, {{YOUR_PASSWORD}}, 'localhost:5432', 'capstone_project')
        ```

For more details [look at the documentation (31.1.1.2. Connection URIs)](https://www.postgresql.org/docs/9.3/libpq-connect.html)

4. Setup the environment variables for Auth0 under `setup.sh` running:
    ```bash
    source ./setup.sh
    ```
5. To run the server locally, execute:

    ```bash
    export FLASK_APP=main.py
    export FLASK_DEBUG=True
    export FLASK_ENVIRONMENT=debug
    flask run --reload
    ```

    Optionally, you can use `run.sh` script.

## API Documentation

### Models

There are two models:

-   Movie
    -   title
    -   release_date
-   Actor
    -   name
    -   age
    -   gender

### Error Handling

Errors are returned as JSON objects in the following format:

```json
{
    "success": False,
    "error": 400,
    "message": "bad request"
}
```

The API will return three error types when requests fail:

-   400: Bad Request
-   401: Unauthorized
-   403: Forbidden
-   404: Resource Not Found
-   422: Not Processable
-   500: Internal Server Error

## ENPOINTS

### GET Enpoints

#### GET /movies

-   Get all movies

-   Require `get:movies` permission

-   **Example Request:** `curl 'http://localhost:5000/movies'`

-   **Expected Result:**
    ```json
    {
        "movies": [
            {
                "actors": [
                    {
                        "age": 54,
                        "gender": "M",
                        "id": 1,
                        "movie_id": 2,
                        "name": "Tom Hanks"
                    },
                    {
                        "age": 45,
                        "gender": "M",
                        "id": 4,
                        "movie_id": 2,
                        "name": "Robert Downey, Jr."
                    },
                    {
                        "age": 45,
                        "gender": "F",
                        "id": 5,
                        "movie_id": 2,
                        "name": "Julia Roberts"
                    }
                ],
                "id": 2,
                "release_date": "Fri, 04 May 2012 00:00:00 GMT",
                "title": "Yahşi Batı"
            }
        ],
        "success": true
    }
    ```

#### GET /actors

-   Get all actors

-   Requires `get:actors` permission

-   **Example Request:** `curl 'http://localhost:5000/actors'`

-   **Expected Result:**
    ```json
    {
        "actors": [
            {
                "age": 45,
                "gender": "M",
                "id": 6,
                "movie_id": 1,
                "name": "Cem Yılmaz"
            },
            {
                "age": 54,
                "gender": "M",
                "id": 1,
                "movie_id": 2,
                "name": "Tom Hanks"
            },
            {
                "age": 44,
                "gender": "M",
                "id": 2,
                "movie_id": 3,
                "name": "Brad Pitt"
            }
        ],
        "success": true
    }
    ```

### POST Enpoints

#### POST /movies

-   Creates a new movie.

-   Requires `create:movies` permission

-   Requires the title and release date.

-   **Example Request:** (Create)
    ```json
    curl --location --request POST 'http://localhost:5000/movies' \
    	--header 'Content-Type: application/json' \
    	--data-raw '{
    		"title": "Pek Yakında",
    		"release_date": "19-02-2020"
    	}'
    ```
-   **Example Response:**
    ```json
    {
        "success": true,
        "movies": {
            "title": "Pek Yakında",
            "release_date": "19-02-2020"
        }
    }
    ```

#### POST /actors

-   Creates a new actor.

-   Requires `create:actors` permission

-   Requires the name, age and gender of the actor.

-   **Example Request:** (Create)
    ```json
    curl --location --request POST 'http://localhost:5000/actors' \
    	--header 'Content-Type: application/json' \
    	--data-raw '{
    		"name": "Cem Yılmaz",
    		"age": "45",
    		"gender": "M"
        }'
    ```
-   **Example Response:**
    ```json
    {
        "success": true,
        "actors": {
            "name": "Cem Yılmaz",
            "age": "45",
            "gender": "M"
        }
    }
    ```

### PATCH Enpoints

#### PATCH /movies/<movie_id>

-   Updates the movie where <movie_id> is the existing movie id

-   Require `update:movies` permission

-   Responds with a 404 error if <movie_id> is not found

-   Update the corresponding fields for Movie with id <movie_id>

-   **Example Request:**
    ```json
      curl --location --request PATCH 'http://localhost:5000/movies/1' \
    	--header 'Content-Type: application/json' \
    	--data-raw '{
    		"title": "Eyvah eyvah 2"
          }'
    ```
-   **Example Response:**
    ```json
    {
        "success": true,
        "updated": {
            "id": 1,
            "release_date": "Wed, 04 May 2016 00:00:00 GMT",
            "title": "Eyvah eyvah 2"
        }
    }
    ```

#### PATCH /actors/<actor_id>

-   Updates the actor where <actor_id> is the existing actor id

-   Require `update:actors`

-   Responds with a 404 error if <actor_id> is not found

-   **Example Request:**
    ```json
      curl --location --request PATCH 'http://localhost:5000/actors/1' \
    	--header 'Content-Type: application/json' \
    	--data-raw '{
    		"name": "Tom Hanks"
          }'
    ```
-   **Example Response:**
    ```json
    {
        "success": true,
        "actors": {
            "age": 54,
            "gender": "M",
            "id": 1,
            "name": "Tom Hanks"
        }
    }
    ```

### DELETE Enpoints

#### DELETE /movies/<int:movie_id>

-   Deletes the movie with given id

-   Require `delete:movies` permission

-   **Example Request:** `curl --request DELETE 'http://localhost:5000/movies/1'`

-   **Example Response:**
    ```json
    {
        "deleted": 1,
        "success": true
    }
    ```

#### DELETE /actors/<int:actor_id>

-   Deletes the actor with given id

-   Require `delete:actors` permission

-   **Example Request:** `curl --request DELETE 'http://localhost:5000/actors/1'`

-   **Example Response:**
    ```json
    {
        "deleted": 1,
        "success": true
    }
    ```
