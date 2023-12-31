# **Introduction**

This application serves as a content management system for a film production company, providing the ability to manage actors and movies. Through the provided endpoints, users can create, read, update, and delete movie and actor records in the database.

# **Motivation Behind The Project**

The primary purpose of building this application is to provide a robust back-end system that manages and keeps track of actors and movies. As film production companies often work with various actors and produce multiple movies, having a reliable system to manage this data becomes crucial.

# **Tech Stack Used In The Project**

**Flask**: A lightweight WSGI web application framework.
**SQLAlchemy**: The Python SQL toolkit and Object-Relational Mapping (ORM) library.
**PostgreSQL**: The open-source relational database.
**Flask-CORS**: A Flask extension for handling Cross-Origin Resource Sharing (CORS).
**Render**: Cloud platform for deploying, managing, and scaling apps.

# **Installation Instructions**

```
pip3 install -r requirements.txt
```

# **Set up the database URL in your environment**
The models.py file contains connection instructions to the Postgres database, which must also be setup and running. Provide a valid username and password, if applicable.

Create a database with name jobportal using Psql CLI:
```
create database capstone;
```

```
export DATABASE_URL="postgresql://postgres:120598@localhost:5432/capstone"
export EXCITED="true"
```

# **Run on local**

```
python manage.py runserver
```

# **RBAC credentials and roles**

Auth0 was set up to manage role-based access control for two users. The API documentation below describes, among others, by which user the endpoints can be accessed. Access credentials and permissions are handled with JWT tockens which must be included in the request header.

# **Testing Instructions**

1. Ensure you have the testing database set up and updated the DATABASE_URL if necessary.
2. Run the tests using the following command:
          python -m unittest test_app.py
Roles and the Permissions Associated With It
* **Casting Assistant**:
  * get:actors
  * get:movies
* **Casting Director** (Has all the permissions of Casting Assistant plus):
  * post:actors
  * delete:actors
  * patch:actors
  * patch:movies
* **Executive Producer** (Has all the permissions of Casting Director plus):
  * post:movies
  * delete:movies
 
# **Documentation of the APIs**

Token auth0 to using Postman:
**ASSISTANT**='eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkRNUTFJWVZiVFhYSFRjaU9iWGMtQiJ9.eyJpc3MiOiJodHRwczovL2Rldi1sOGxmc3MxZGU4eHltaWZ5LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcUBjbGllbnRzIiwiYXVkIjoiQ2Fwc3RvbmVfdWRhY2l0eSIsImlhdCI6MTY5NjA5MjgwNywiZXhwIjoxNjk2MTc5MjA3LCJhenAiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcSIsInNjb3BlIjoiZ2V0OmFjdG9ycyBnZXQ6bW92aWVzIiwiZ3R5IjoiY2xpZW50LWNyZWRlbnRpYWxzIiwicGVybWlzc2lvbnMiOlsiZ2V0OmFjdG9ycyIsImdldDptb3ZpZXMiXX0.dt7eMJMbXIVYKKq16TaUFQdnBCmQj8oTLoZnHn3RFiRPphexgXUR0Qm1GkgRw52QmRbOOGOG_aGofkKZxuCyG_Jse5sdJ0cff50isCLcX7Hq85HW9MQNbOJvjfTTVCgs4D66kTTxsT_bgqLLBpOXfEB1CbvraEtxqnCMZV-83I2FQXVlYYQ8PS6sP_km73CYDQx8gkHEMQlJC3Mdn09s77clSH7pwuMbDfUn5SJLGHM9dwEkN1C1_NaNVQ97aX14Y6OtdKl4S3IueT3Kcws0UjRArmLR3_d6CVQ6kWhgM6U3HGYTKpXf_d__BPph1nbWX22E7jzJSkiGk2qvMDIFbA'
**DIRECTOR**='eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkRNUTFJWVZiVFhYSFRjaU9iWGMtQiJ9.eyJpc3MiOiJodHRwczovL2Rldi1sOGxmc3MxZGU4eHltaWZ5LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcUBjbGllbnRzIiwiYXVkIjoiQ2Fwc3RvbmVfdWRhY2l0eSIsImlhdCI6MTY5NjA5Mjg5MiwiZXhwIjoxNjk2MTc5MjkyLCJhenAiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcSIsInNjb3BlIjoiZ2V0OmFjdG9ycyBnZXQ6bW92aWVzIHBvc3Q6YWN0b3JzIGRlbGV0ZTphY3RvcnMgcGF0Y2g6YWN0b3JzIHBhdGNoOm1vdmllcyIsImd0eSI6ImNsaWVudC1jcmVkZW50aWFscyIsInBlcm1pc3Npb25zIjpbImdldDphY3RvcnMiLCJnZXQ6bW92aWVzIiwicG9zdDphY3RvcnMiLCJkZWxldGU6YWN0b3JzIiwicGF0Y2g6YWN0b3JzIiwicGF0Y2g6bW92aWVzIl19.i2Bno9hH_2B9tM5qzDZfed2yAEEJX6urlOBkYnmzlfr9syd9yU2F0Jq4ZBQNL4ENF1Wpim64AF6GvouEWmXeySYR42gTx3IsZHp1dDQuMj16izigqJZ5uaGAREPrTaM2ZsV8fre7ZQsL8qDME6aU7zKOQg5XTWCGrT3AVFYtnFoq3sqVN7JslZTFZ448WtLix6r6ExwHpwCFFiRxOXYVgLtjPHCIFecEHKFf5OG-V7rTvbL3stlaCgw9OOQv8nBsMQc63E5YwzZFkACbsvK0bv2wXq7jElj9iEDnOP7Uj6HIfoHQgFFlyiPNp07BwREE_lhX0kOYvC2WNEA1azuIzw'
 **PRODUCER**='eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkRNUTFJWVZiVFhYSFRjaU9iWGMtQiJ9.eyJpc3MiOiJodHRwczovL2Rldi1sOGxmc3MxZGU4eHltaWZ5LnVzLmF1dGgwLmNvbS8iLCJzdWIiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcUBjbGllbnRzIiwiYXVkIjoiQ2Fwc3RvbmVfdWRhY2l0eSIsImlhdCI6MTY5NjA2MjE1MiwiZXhwIjoxNjk2MTQ4NTUyLCJhenAiOiJqU3lJUmFKb2Ridm9XWW5DOXpZbmFvaGxqQjBhVE9JcSIsInNjb3BlIjoiZ2V0OmFjdG9ycyBnZXQ6bW92aWVzIHBvc3Q6YWN0b3JzIGRlbGV0ZTphY3RvcnMgcGF0Y2g6YWN0b3JzIHBhdGNoOm1vdmllcyBkZWxldGU6bW92aWVzIHBvc3Q6bW92aWVzIiwiZ3R5IjoiY2xpZW50LWNyZWRlbnRpYWxzIiwicGVybWlzc2lvbnMiOlsiZ2V0OmFjdG9ycyIsImdldDptb3ZpZXMiLCJwb3N0OmFjdG9ycyIsImRlbGV0ZTphY3RvcnMiLCJwYXRjaDphY3RvcnMiLCJwYXRjaDptb3ZpZXMiLCJkZWxldGU6bW92aWVzIiwicG9zdDptb3ZpZXMiXX0.easSkGGr_gGZAq8_WCu3ZPtrohfSlPWSTwpCGQGY76K2PKjA_987YmkJ_UIpLL0y1eAKL9QQd1yR-Qtk5NXrOaoh6DRfM4rbRx1qSCOOGVIgDe9PRJVP7eCULo-vTUORcYWOcfKb_RwbaQ-3_wmLeCTYAa4TDsKaXCUboUP6q_U-KvOMyJtysU7akuwFRTcifZq0VSde-Zl33gNdGVh7V2SNKK9TV5WMyuooa4z4kRmiTyAIA2JGJ-MM2x2JgExWcKD2NyIFYLClmlIjX-fqI8_8TSebLsJFowb9IMHfOt7ucia_1Xx5LsJMhLJP5t4hjBLwXcfZbfFm_ssvismaLg'

Type: Bearer

**get:/actors**

output
```json
{
    "actors": [
        {
            "age": 30,
            "gender": "male",
            "id": 1,
            "name": "Tu"
        },
}
```
**get:movies**

```json
{
    "movies": [
        {
            "id": 1,
            "release_date": "Fri, 11 Dec 1998 17:00:00 GMT",
            "title": "Enjoy my life"
        },
}
```
**post:actors**

in postman, body (raw -> json)
```json
{
  "name": "Tu",
  "age": 30,
  "gender": "male"
}
```

**post:movies**

in postman, body (raw -> json)
```json
{
    "title": "Enjoy life",
    "release_date": "2022-09-09"
}
```

**delete:actors**

delete:/actors/<actor_id>

**Example:**

```
http://127.0.0.1:5000/actors/5
```
**output**

```json
{
    "delete": 5,
    "success": true
}
```

**delete:movies**

delete:/movies/<movie_id>

**Example:**

```
http://127.0.0.1:5000/movies/5
```
**output**

```json
{
    "delete": 5,
    "success": true
}
```

**patch:actors**

delete:/actors/<actor_id>

**Example:**

```
http://127.0.0.1:5000/actors/4/
```
input:
```json
{
    "name": "Updated Name",
    "age": 24,
    "gender": "Male"
}
```

**output**

```json
{
    "actor": {
        "age": 24,
        "gender": "Male",
        "id": 4,
        "name": "Updated Name"
    },
    "success": true
}
```

**patch:movies**

delete:/movies/<movie_id>

**Example:**

```
http://127.0.0.1:5000/movies/4/
```
input:
```json
{
    "release_date": "1-1-2023",
    "title": "Updated Name"
}
```

**output**

```json
{
    "movie": {
        "id": 4,
        "release_date": "Sat, 31 Dec 2022 17:00:00 GMT",
        "title": "Updated Name"
    },
    "success": true
}
```


# **Render Link**

The backend application has been deployed on Heroku and can be accessed live at:
```
https://capstone-cncy.onrender.com/
```


