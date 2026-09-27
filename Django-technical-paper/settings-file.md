## 1. What is Secret Key in Django?

- `SECRET_KEY` is a private key used by Django for security.
- It is used for signing sessions, cookies, password reset tokens, and other security-related operations.
- We should keep it secret and should not share it publicly.

Example:

```python
SECRET_KEY = "django-insecure-abc123..."
```

## 2. What are the default Django apps?

Django provides some apps by default in `INSTALLED_APPS`.

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]
```
# Main Default Apps

- **admin** - Provides the Django admin panel.
- **auth** - Handles users, passwords, groups, and permissions.
- **contenttypes** - Keeps information about models and their types.
- **sessions** - Handles user sessions.
- **messages** - Allows displaying one-time messages to users.
- **staticfiles** - Handles static files like CSS, JavaScript, and images.

## Are There More?

Yes. Django has many built-in apps and features, but these six are commonly included by default in a new Django project.

We can also add our own applications to INSTALLED_APPS.

## 3. What is Middleware in Django?

- Middleware is a layer that processes a request and response before or after it reaches the view.

### Simple Flow

Browser → Middleware → View → Middleware → Response → Browser

### How it works

1. Request comes from the browser.
2. Django sends the request through middleware.
3. Middleware can check or modify the request.
4. The request reaches the view.
5. The view creates a response.
6. Middleware can process the response.
7. Response goes back to the browser.

### Common Django Middleware

- `SecurityMiddleware` - Provides security-related protections. Helps set security-related HTTP headers.Can help with HTTPS-related security.
- `SessionMiddleware` - Manages user sessions.Allows Django to remember information about a user between requests.
- Example: Keeping a user logged in.

- `CommonMiddleware` - Handles common request and response operations. Handles things like URL normalization and some browser-related behavior.
- `CsrfViewMiddleware` - Protects against CSRF attacks.Checks the CSRF token for unsafe requests such as `POST`.
- `AuthenticationMiddleware` - Adds logged-in user information to the request.
- `MessageMiddleware` - Enables Django's messages framework.
- `XFrameOptionsMiddleware` - Helps protect against clickjacking.

## 4. What is CSRF?

- CSRF stands for **Cross-Site Request Forgery**.
- It is a security attack where an attacker tricks a logged-in user into sending an unwanted request.
- The attacker tries to use the user's existing login session to perform an action.

### Simple Example

Suppose you are logged into a banking website.

1. You log in to your bank account.
2. You visit a malicious website.
3. That website sends a request to the banking website.
4. Since you are already logged in, the request may appear to come from you.
5. The attacker may try to perform an unwanted action.

### How Django Protects Against CSRF

Django uses a **CSRF token** to verify that the request came from the trusted website.

For a POST form, we use:

```html
<form method="POST">
    {% csrf_token %}
    ...
</form>
```
- Django generates a CSRF token.
- The token is sent with the form request.
- Django checks the token before processing the - request.
- If the token is missing or invalid, Django rejects the request.

## 5. What is XSS?

- XSS stands for **Cross-Site Scripting**.
- It is a security attack where an attacker injects malicious JavaScript into a webpage.
- When another user opens that page, the malicious JavaScript may execute in their browser.

### Simple Example

Suppose a website displays user comments.
An attacker enters:

```html
<script>alert("Hacked")</script>
```
### How Django Helps Prevent XSS

If a website displays user-provided content without proper escaping, the browser may execute the JavaScript.

Django helps prevent Cross-Site Scripting (XSS) attacks by automatically escaping HTML characters in templates by default.

Example
```
{{ username }}
```

### If username contains:
```js
<script>alert("Hello")</script>
```

Django displays it as text instead of executing it as JavaScript.

## 6. What is Clickjacking?

- Clickjacking is a security attack where an attacker tricks a user into clicking something different from what they think they are clicking.

### Simple Example

1. An attacker creates a malicious webpage.
2. They place a real website inside an invisible or transparent frame.
3. The user thinks they are clicking a normal button.
4. But they are actually clicking a button on the hidden website.

### How Django Protects Against Clickjacking

- Django provides `XFrameOptionsMiddleware`.
- It adds the `X-Frame-Options` header to responses.
- This helps prevent the website from being loaded inside an iframe on another website.

### Key Point

**Clickjacking → Tricks users into clicking hidden or disguised elements.**

## 7. What is WSGI in Django?

- WSGI stands for **Web Server Gateway Interface**.
- It is a standard that allows a web server to communicate with a Python web application like Django.

### Simple Flow

```text
Browser
   ↓
Web Server
   ↓
WSGI
   ↓
Django Application
   ↓
Response
   ↓
Browser
```

## What does WSGI do?
- Receives a request from the web server.
- Passes the request to the Django application.
- Django processes the request.
- The response goes back through WSGI to the web server.

### In Django

Django creates a wsgi.py file when we create a project.

Example:
```py
import os
from django.core.wsgi import get_wsgi_application

os.environ.setdefault(
    "DJANGO_SETTINGS_MODULE",
    "project.settings"
)

application = get_wsgi_application()
```
