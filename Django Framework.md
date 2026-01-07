# Django Framework – Practical Cheat Sheet

> **Purpose**: A zero-fluff, production-oriented Django cheat sheet.
> Designed for **fast building**, **secure coding**, and **emergency copy-paste**.
> Python-first, scalable, and aligned with **OWASP Top 10** and **ISO/IEC 27001:2022**.

---

## 1. Django Mental Model (Understand This First)

* Django is an **MTV framework**

  * **Model**: Data schema and business rules
  * **Template**: Presentation layer
  * **View**: Request handling and orchestration
* Django is **secure-by-default**, but only if you do not bypass safeguards

---

## 2. Project vs App (People Get This Wrong)

### Project

* Entire system configuration
* Contains settings, URLs, ASGI/WSGI

### App

* A modular business capability
* Example: users, inventory, forecasting

Rule: **One app = one responsibility**

---

## 3. Installation & Project Setup

```bash
pip install django
django-admin startproject config
cd config
python manage.py startapp core
```

---

## 4. Project Structure (Recommended)

```text
config/
├── config/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── core/
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── serializers.py
│   └── admin.py
├── manage.py
```

---

## 5. settings.py (Critical Sections)

### Installed Apps

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.sessions',
    'core',
]
```

### Security Defaults (Do Not Relax Blindly)

```python
DEBUG = False
ALLOWED_HOSTS = ['yourdomain.com']
SECURE_SSL_REDIRECT = True
CSRF_COOKIE_SECURE = True
SESSION_COOKIE_SECURE = True
```

---

## 6. Models (Data Layer)

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=100)
    demand = models.IntegerField()
    created_at = models.DateTimeField(auto_now_add=True)
```

### Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

---

## 7. Admin (Free Power Tool)

```python
from django.contrib import admin
from .models import Product

admin.site.register(Product)
```

---

## 8. Views (Function-Based and Class-Based)

### Function-Based View

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({'status': 'ok'})
```

### Class-Based View

```python
from django.views import View
from django.http import JsonResponse

class PingView(View):
    def get(self, request):
        return JsonResponse({'ping': 'pong'})
```

---

## 9. URLs (Routing Layer)

```python
from django.urls import path
from .views import health, PingView

urlpatterns = [
    path('health/', health),
    path('ping/', PingView.as_view()),
]
```

---

## 10. Templates (Frontend Basics)

```html
<h1>Hello {{ user.username }}</h1>
```

---

## 11. Forms & Validation

```python
from django import forms

class ProductForm(forms.Form):
    name = forms.CharField(max_length=100)
    demand = forms.IntegerField(min_value=0)
```

---

## 12. Authentication & Authorization

### Login Required

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    pass
```

### Permissions

```python
@permission_required('core.view_product')
def view_products(request):
    pass
```

---

## 13. Django REST Basics (API Layer)

```bash
pip install djangorestframework
```

```python
INSTALLED_APPS += ['rest_framework']
```

### Serializer

```python
from rest_framework import serializers
from .models import Product

class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = '__all__'
```

### API View

```python
from rest_framework.views import APIView
from rest_framework.response import Response

class ProductAPI(APIView):
    def get(self, request):
        return Response({'data': 'ok'})
```

---

## 14. Middleware (Request Pipeline)

```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
]
```

---

## 15. Environment Variables (Mandatory)

```python
import os
SECRET_KEY = os.getenv('DJANGO_SECRET_KEY')
```

Never hardcode secrets.

---

## 16. Static & Media Files

```python
STATIC_URL = '/static/'
MEDIA_URL = '/media/'
```

---

## 17. Common Commands (Memorize)

```bash
python manage.py runserver
python manage.py createsuperuser
python manage.py shell
python manage.py collectstatic
```

---

## 18. Security Best Practices (OWASP Aligned)

* CSRF protection always on
* Input validation via forms/serializers
* ORM only, no raw SQL
* Proper auth checks per view
* Disable DEBUG in prod

---

## 19. Common Anti-Patterns (Fix These Now)

* Fat views with business logic
* No app separation
* Hardcoded secrets
* No tests
* DEBUG=True in production

---

## 20. Production Mental Model

> Django handles safety.
> You handle discipline.
> Ignore either and you ship vulnerabilities.

---

## 21. Absolute Emergency Snippets

```bash
python manage.py migrate
python manage.py shell
python manage.py createsuperuser
```

```python
from django.conf import settings
print(settings.DATABASES)
```

---
