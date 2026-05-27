# 📧 django-email-verf

A simple Django project for learning and practicing email integration. Users submit their email address through a form, and the app dispatches a verification email via Gmail SMTP using Django's built-in mail backend.

---

## 🚀 Features

- Email submission form built with Django ModelForms
- Sends real emails via Gmail SMTP
- Stores submitted emails in a database with timestamps
- Clean Bootstrap frontend
- Django class-based views (CBV)

---

## 🛠️ Tech Stack

| Layer     | Technology              |
|-----------|-------------------------|
| Backend   | Python 3, Django 6      |
| Frontend  | HTML5, Bootstrap 5      |
| Database  | SQLite (default)        |
| Email     | Gmail SMTP              |

---

## ⚙️ Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/emmanuelangelo4199/django-email-verf.git
cd django-email-verf
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the root directory (or update `settings.py` directly for local development):

```env
EMAIL_HOST_USER=youraddress@gmail.com
EMAIL_HOST_PASSWORD=your-gmail-app-password
DEFAULT_FROM_EMAIL=My App <youraddress@gmail.com>
```

> **Note:** Use a [Gmail App Password](https://myaccount.google.com/apppasswords), not your regular Gmail login password. You must have 2-Step Verification enabled on your Google account.

### 5. Run migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Start the development server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

---

## 📁 Project Structure

```
django-email-verf/
│
├── em_pro/                  # Project settings & URLs
│   ├── settings.py
│   └── urls.py
│
├── verification/            # Main app
│   ├── models.py            # Email model
│   ├── forms.py             # EmailForms (ModelForm)
│   ├── views.py             # Class-based views
│   ├── urls.py
│   └── templates/
│       └── verification/
│           └── index.html
│
├── manage.py
└── requirements.txt
```

---

## 📬 Email Configuration (settings.py)

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'youraddress@gmail.com'
EMAIL_HOST_PASSWORD = 'your-app-password'
DEFAULT_FROM_EMAIL = 'My App <youraddress@gmail.com>'
```

---

## 🧠 What I Learned

- Setting up Django's SMTP email backend
- Building and validating ModelForms
- Using Django class-based views (`ListView`, `FormMixin`)
- Fixing common Django template errors (`Unclosed block` tags)
- Configuring `STATICFILES_DIRS` correctly on Windows

---

## 🔮 Possible Improvements

- [ ] Add token-based email verification link
- [ ] User registration & login flow
- [ ] Email status tracking (sent, verified, failed)
- [ ] Switch to environment variables using `python-decouple`
- [ ] Deploy to a cloud platform (Railway, Render, etc.)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
