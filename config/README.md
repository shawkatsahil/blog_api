# Blog API

A REST API for a blog, built with Django and Django REST Framework.
Users can log in with JWT, write posts, and comment on posts.

## Features
- JWT authentication (login, access and refresh tokens)
- Create, read, update and delete posts
- Comments on posts
- Only the owner can edit or delete their own posts and comments
- Pagination, search, filtering and ordering
- Tested with Postman

## Tech Stack
- Python
- Django
- Django REST Framework
- Simple JWT
- SQLite

## API Endpoints

| Method | Endpoint | What it does | Login needed |
|---|---|---|---|
| POST | `/api/token/` | Get access and refresh tokens | No |
| POST | `/api/token/refresh/` | Get a new access token | No |
| GET | `/api/posts/` | List posts | No |
| POST | `/api/posts/` | Create a post | Yes |
| GET | `/api/posts/{id}/` | Read one post (with its comments) | No |
| PUT / PATCH | `/api/posts/{id}/` | Edit your post | Yes (owner) |
| DELETE | `/api/posts/{id}/` | Delete your post | Yes (owner) |
| GET | `/api/comments/` | List comments | No |
| POST | `/api/comments/` | Add a comment | Yes |
| PUT / PATCH / DELETE | `/api/comments/{id}/` | Edit or delete your comment | Yes (owner) |

### Search, filter and order
- Search: `/api/posts/?search=village`
- Filter by author: `/api/posts/?author__username=shawkat`
- Comments of one post: `/api/comments/?post=1`
- Order: `/api/posts/?ordering=-created_at`
- Pages: `/api/posts/?page=2`

## How to use authentication
1. Send `POST /api/token/` with your username and password.
2. Copy the `access` value.
3. Send it in the header of protected requests:
```
Authorization: Bearer <your access token>
```

## Screenshots
![Login](screenshots/login.png)
![Create post](screenshots/create-post.png)
![Search](screenshots/search.png)

## Run it on your computer
```
git clone https://github.com/shawkatsahil/blog_api.git
cd blog_api
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```
Then open `http://127.0.0.1:8000/api/`.

## Author
**Sahil** (CHANGE: add your full name)
GitHub: [shawkatsahil](https://github.com/shawkatsahil)