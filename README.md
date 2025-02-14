# Django Project Setup Guide

1. **Create a New Branch (if desired)**  
   To start working on a new feature, create a new branch:
   ```bash
   git checkout -b initial_setup
   ```
   Each time you work on something new, create a new branch, then merge it, and finally delete the branch after merging.

2. **Create Virtual Environment**  
   To set up a virtual environment:
   ```bash
   winpty python -m venv .venv
   ```

3. **Activate Virtual Environment**  
   Activate the virtual environment:
   ```bash
   . .venv/Scripts/activate
   ```

4. **Install Django**  
   Install Django with the specific version (e.g., 4.2.0):
   ```bash
   winpty python -m pip install Django ~=4.2.0
   ```

5. **Start a Django Project**  
   Create a new Django project named `django_project`:
   ```bash
   winpty django-admin startproject django_project .
   ```

6. **Create a Django App**  
   Create a new app within the Django project (e.g., `blog`):
   ```bash
   winpty python manage.py startapp blog
   ```

7. **Run Default Migrations**  
   Run the default migrations to set up the initial database:
   ```bash
   winpty python manage.py migrate
   ```

8. **Run Django Development Server**  
   Start the development server to view your project:
   ```bash
   winpty python manage.py runserver
   ```

9. **Switch to `main` Branch**  
   Once you've completed your work on the branch, switch to the `main` branch:
   ```bash
   git checkout main
   ```

10. **Merge Branches**  
   Ensure you're on the branch you want to merge your changes into (e.g., `main`), then merge your feature branch (`initial_setup`) into `main`:
   ```bash
   git checkout main
   git merge initial_setup
   ```

11. **Delete Feature Branch**  
   Once the branch has been merged, you can safely delete it:
   ```bash
   git branch -d initial_setup
   ```

12. **Save Packages in `requirements.txt`**  
   To save the installed packages in a `requirements.txt` file:
   ```bash
   python -m pip freeze > requirements.txt
   ```

13. **Install Saved Packages on a New Device**  
   On a new machine or environment, you can install the saved packages from `requirements.txt`:
   ```bash
   python -m pip install -r requirements.txt
   ```

14. **Add `blog` App to `settings.py`**  
   In `django_project/settings.py`, add the new `blog` app to the `INSTALLED_APPS` list:
   ```python
   INSTALLED_APPS = [
       # Other apps...
       'blog.apps.BlogConfig',  # Add this line
   ]
   ```
   Note: The app is `blog`, the file is `apps.py`, and the class inside is `BlogConfig`.

15. **Create Migrations for the Blog App**  
   After creating models, run migrations for the `blog` app:
   ```bash
   winpty python manage.py makemigrations
   winpty python manage.py migrate
   ```

16. **Create Django Superuser**  
   To create a superuser for the Django admin interface:
   ```bash
   winpty python manage.py createsuperuser
   ```

17. **Configure Blog Models in Admin**  
   In `blog/admin.py`, register your model to make it available in the Django admin panel:
   ```python
   from .models import Post

   admin.site.register(Post)
   ```

