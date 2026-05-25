# 📧 Django Email Verification

A Django project demonstrating how to implement **email verification** for user registration. When a new user signs up, a verification link is sent to their email address. The account is only activated after the user clicks the link.

---

## ✨ Features

- User registration with email & password
- Verification email sent on signup (via Gmail SMTP)
- Unique token-based email confirmation link
- Account activation on link click
- Login restricted to verified users only
- Secure credential management with `python-decouple` and `.env`

---

## 🛠️ Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Backend    | Python 3, Django        |
| Frontend   | HTML5, Bootstrap 5      |
| Database   | SQLite (default)        |
| Email      | Gmail SMTP              |
| Config     | python-decouple / .env  |

---

## ⚙️ Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/emmanuelangelo4199/django-email-verf.git
cd django-email-verf
```

### 2. Create and activate a virtual environment

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up your `.env` file

Create a `.env` file in the project root (same level as `manage.py`):

```env
SECRET_KEY=your-django-secret-key
DEBUG=True
EMAIL_HOST_USER=your-gmail@gmail.com
EMAIL_HOST_PASSWORD=your-gmail-app-password
PASSWORD_RESET_TIMEOUT = 120
```

> ⚠️ Use a **Gmail App Password**, not your regular Gmail password.
> Go to `Google Account → Security → 2-Step Verification → App Passwords` to generate one.

### 5. Apply migrations

```bash
python manage.py migrate
```

### 6. Run the development server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000` in your browser.

---

## 📁 Project Structure

```
django-email-verf/
├── manage.py
├── .env                    # Secret credentials (not committed)
├── .env.example            # Template for .env setup
├── requirements.txt
├── core/                   # Main Django project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── verification/      #verification  app (registration, verification)
    ├── models.py
    |__ forms.py
    |__ apps.py
    |__ admin.py
    ├── views.py
    ├── urls.py
    └── templates/
        └── verification/
            ├── register.html
            ├── login.html
            └── verify_email.html
```

---

## 🔐 Email Settings (settings.py)

```python
from decouple import config

EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = config('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = config('EMAIL_HOST_PASSWORD')
```

---

## 🔄 How It Works

```
User registers → Verification email sent → User clicks link → Account activated → User can log in
```

1. User fills in the registration form.
2. A unique token is generated and stored against the user account.
3. An email containing an activation link is sent via Gmail SMTP.
4. When the user clicks the link, the token is verified and the account is marked active.
5. The user can now log in.

---

## 🚫 .gitignore

Make sure your `.gitignore` includes:

```
.env
__pycache__/
*.pyc
db.sqlite3
venv/
```

---

## 📌 Requirements

```
Django>=4.2
python-decouple
```

Generate/update with:

```bash
pip freeze > requirements.txt
```

---

## 👤 Author

**Angelo** — [@mrangelo4199](https://github.com/emmanuelangelo4199)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).