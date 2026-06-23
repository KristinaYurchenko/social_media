# Social Media API

## Description

You are tasked with building a RESTful API for a social media platform.

The API should allow users to create profiles, follow other users, create and retrieve posts, manage likes and comments, and perform basic social media actions.

## Requirements

### User Registration and Authentication

* Users should be able to register with their email and password to create an account.
* Users should be able to login with their credentials and receive a token for authentication.
* Users should be able to logout and invalidate their token.

### User Profile

* Users should be able to create and update their profile, including profile picture, bio, and other details.
* Users should be able to retrieve their own profile and view profiles of other users.
* Users should be able to search for users by username or other criteria.

### Follow/Unfollow

* Users should be able to follow and unfollow other users.
* Users should be able to view the list of users they are following and the list of users following them.

### Post Creation and Retrieval

* Users should be able to create new posts with text content and optional media attachments (e.g., images).
  Adding images is optional task.
* Users should be able to retrieve their own posts and posts of users they are following.
* Users should be able to retrieve posts by hashtags or other criteria.

### Likes and Comments

Optional:

* Users should be able to like and unlike posts.
* Users should be able to view the list of posts they have liked.
* Users should be able to add comments to posts and view comments on posts.

### Schedule Post Creation Using Celery

Optional:

* Add possibility to schedule Post creation.
* You can select the time to create the Post before creating of it.

### API Permissions

* Only authenticated users should be able to perform actions such as creating posts, liking posts, and following/unfollowing users.
* Users should only be able to update and delete their own posts and comments.
* Users should only be able to update and delete their own profile.

### API Documentation

* The API should be well-documented with clear instructions on how to use each endpoint.
* The documentation should include sample API requests and responses for different endpoints.

### Technical Requirements

* Use Django and Django REST framework to build the API.
* Use token-based authentication for user authentication.
* Use appropriate serializers for data validation and representation.
* Use appropriate views and viewsets for handling CRUD operations on models.
* Use appropriate URL routing for different API endpoints.
* Use appropriate permissions and authentication classes to implement API permissions.
* Follow best practices for RESTful API design and documentation.

## Note

You are not required to implement a frontend interface for this task.

Focus on building a well-structured and well-documented RESTful API using Django and Django REST framework.

This task will test the junior DRF developer's skills in building RESTful APIs, handling authentication and permissions, working with models, serializers, views, and viewsets, and following best practices for API design and documentation.


































# Social Media API

## Description

Social Media API is a RESTful API for a social media platform built with Django and Django REST Framework.

The project allows users to register, authenticate, create and manage profiles, follow other users, create posts, interact with posts using likes and comments, and retrieve content from followed users.

The main goal of this project is to demonstrate practical skills in building RESTful APIs using Django REST Framework, including authentication, permissions, serializers, viewsets, routing, and API documentation.

## Features

### User Registration and Authentication

* User registration with email and password
* User login with credentials
* Token-based authentication
* User logout with token invalidation
* Access control for authenticated users

### User Profile

* Create and update user profile
* Add profile picture
* Add bio and additional profile details
* Retrieve own profile
* View profiles of other users
* Search users by username or other criteria

### Follow and Unfollow

* Follow other users
* Unfollow users
* View the list of users the current user follows
* View the list of followers of a user

### Posts

* Create posts with text content
* Retrieve own posts
* Retrieve posts from followed users
* Retrieve posts by hashtags or other criteria
* Optional media attachments for posts, such as images

### Likes and Comments

* Like posts
* Unlike posts
* View liked posts
* Add comments to posts
* View comments on posts
* Update and delete own comments

### Scheduled Posts

Optional functionality:

* Schedule post creation using Celery
* Select the date and time when a post should be published

### API Permissions

* Only authenticated users can create posts, like posts, comment, follow, and unfollow users
* Users can update and delete only their own posts
* Users can update and delete only their own comments
* Users can update and delete only their own profile

## Technologies Used

* Python
* Django
* Django REST Framework
* Token Authentication
* SQLite / PostgreSQL
* Celery
* Redis
* Pillow
* drf-spectacular / Swagger

## Installation

### 1. Clone the repository

```bash
git clone git@github.com:KristinaYurchenko/social_media.git
cd social_media
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
```

For Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Apply migrations

```bash
python manage.py migrate
```

### 5. Create superuser

```bash
python manage.py createsuperuser
```

### 6. Run the development server

```bash
python manage.py runserver
```

The API will be available at:

```bash
http://127.0.0.1:8000/
```

## API Endpoints

### Authentication

| Method | Endpoint               | Description                            |
| ------ | ---------------------- | -------------------------------------- |
| POST   | `/api/users/register/` | Register a new user                    |
| POST   | `/api/users/login/`    | Login and receive authentication token |
| POST   | `/api/users/logout/`   | Logout and invalidate token            |
| GET    | `/api/users/me/`       | Retrieve current authenticated user    |

### Profiles

| Method    | Endpoint              | Description           |
| --------- | --------------------- | --------------------- |
| GET       | `/api/profiles/`      | List user profiles    |
| GET       | `/api/profiles/{id}/` | Retrieve user profile |
| PUT/PATCH | `/api/profiles/{id}/` | Update own profile    |
| DELETE    | `/api/profiles/{id}/` | Delete own profile    |

### Follow System

| Method | Endpoint                        | Description                 |
| ------ | ------------------------------- | --------------------------- |
| POST   | `/api/profiles/{id}/follow/`    | Follow user                 |
| POST   | `/api/profiles/{id}/unfollow/`  | Unfollow user               |
| GET    | `/api/profiles/{id}/followers/` | View user followers         |
| GET    | `/api/profiles/{id}/following/` | View users followed by user |

### Posts

| Method    | Endpoint                      | Description                        |
| --------- | ----------------------------- | ---------------------------------- |
| GET       | `/api/posts/`                 | List posts                         |
| POST      | `/api/posts/`                 | Create new post                    |
| GET       | `/api/posts/{id}/`            | Retrieve post details              |
| PUT/PATCH | `/api/posts/{id}/`            | Update own post                    |
| DELETE    | `/api/posts/{id}/`            | Delete own post                    |
| GET       | `/api/posts/feed/`            | Retrieve posts from followed users |
| GET       | `/api/posts/?hashtag=example` | Filter posts by hashtag            |

### Likes

| Method | Endpoint                  | Description      |
| ------ | ------------------------- | ---------------- |
| POST   | `/api/posts/{id}/like/`   | Like post        |
| POST   | `/api/posts/{id}/unlike/` | Unlike post      |
| GET    | `/api/posts/liked/`       | View liked posts |

### Comments

| Method    | Endpoint                    | Description            |
| --------- | --------------------------- | ---------------------- |
| GET       | `/api/posts/{id}/comments/` | View comments for post |
| POST      | `/api/posts/{id}/comments/` | Add comment to post    |
| PUT/PATCH | `/api/comments/{id}/`       | Update own comment     |
| DELETE    | `/api/comments/{id}/`       | Delete own comment     |

## Example API Requests

### Register User

```http
POST /api/users/register/
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "strong_password123",
  "username": "john_doe"
}
```

### Login User

```http
POST /api/users/login/
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "strong_password123"
}
```

Example response:

```json
{
  "token": "your-auth-token"
}
```

### Create Post

```http
POST /api/posts/
Authorization: Token your-auth-token
Content-Type: application/json

{
  "content": "My first post!",
  "hashtags": ["django", "api", "drf"]
}
```

### Like Post

```http
POST /api/posts/1/like/
Authorization: Token your-auth-token
```

### Add Comment

```http
POST /api/posts/1/comments/
Authorization: Token your-auth-token
Content-Type: application/json

{
  "text": "Great post!"
}
```

## Authentication

This project uses token-based authentication.

To access protected endpoints, include the token in the request headers:

```http
Authorization: Token your-auth-token
```

## Permissions

The API uses custom permissions to protect user data.

Main permission rules:

* Unauthenticated users can only access public endpoints
* Authenticated users can create posts, comments, likes, and follow other users
* Users can update and delete only their own posts
* Users can update and delete only their own comments
* Users can update and delete only their own profile

## API Documentation

API documentation is available via Swagger or Redoc.

After running the server, open:

```bash
http://127.0.0.1:8000/api/schema/swagger/
```

or:

```bash
http://127.0.0.1:8000/api/schema/redoc/
```

## Project Structure

```bash
social_media/
│
├── social_media/
│   ├── settings.py
│   ├── urls.py
│   └── ...
│
├── users/
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│   ├── urls.py
│   └── ...
│
├── posts/
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│   ├── urls.py
│   └── ...
│
├── requirements.txt
├── manage.py
└── README.md
```

## Optional Features

The project may also include:

* Image upload for posts
* Image upload for user profiles
* Hashtag filtering
* Scheduled post publishing using Celery and Redis
* Pagination for posts and profiles
* Search functionality
* Swagger API documentation

## Running Tests

```bash
python manage.py test
```

## Author

Kristina Yurchenko
