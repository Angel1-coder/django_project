The Cameroonian Table
Project Overview
Welcome to "The Cameroonian Table" – a digital gateway to the rich and diverse culinary world of Cameroon!
This project is more than just a website; it's an invitation to experience the warmth, the flavors, and the hospitality of Cameroonian cuisine.
Our goal is to introduce Cameroonian gastronomy to a global audience in a modern and appealing way, while simultaneously creating a user-friendly platform for our valued customers.

We aim to capture the authentic ambiance of a Cameroonian dining experience online – friendly, inviting, and full of flavor.
The website presents our dishes and drinks in a modern design that reflects the beauty and diversity of our culture.
At the same time, we place great emphasis on functionality to provide our customers with a seamless experience – from exploring our menu to conveniently making table reservations and registering as part of our community.

Table of Contents
Overview

Features

Current Features

Planned Features

Technologies Used

Installation and Execution

Testing

Manual Testing

Code Validation

Deployment Testing

Bugs

Deployment

Heroku Deployment Steps

Forking the GitHub Repository

Creating a Local Clone

Credits



Overview
"The Cameroonian Table" is a responsive, mobile-first website designed to showcase the vibrant cuisine of Cameroon. It aims to provide a user-friendly platform for customers to explore the menu, learn about the restaurant's vision, and eventually make table reservations. Built with the Django Framework, it emphasizes a modern aesthetic combined with robust functionality.

Back To Top

Features
Current Features
Comprehensive Menu: A detailed listing of traditional Cameroonian dishes and refreshing beverages, each with price indications.

Categorization: Dishes and drinks are clearly organized by categories (e.g., Main Course, Juices, Beers) and are presented in a tabular view.

Admin Panel: A fully functional Django admin panel for easy management of categories, dishes, and drinks, including the ability to change their publication status and perform custom actions.

Responsive Design: The website is designed to look and function optimally on various devices (desktop, tablet, mobile phone), including a responsive navigation bar.

Hero Section & Gallery: An appealing hero section with a vision of the restaurant and a visual gallery showcasing the ambiance and dishes.

"Our Story"-Section: A dedicated section that tells the history and philosophy of the restaurant.

Table Reservation Form: A simple form for collecting table reservations (frontend implementation).

Navigation Bar: A fully responsive navigation bar with links to key sections of the website.

Click to view screenshots of Current Features

Planned Features
Full Table Reservation System: Backend implementation and integration of the reservation form with the database, including validation and confirmation.

Customer Registration and Management: Allows users to register, create profiles, and manage their reservations (backend implementation for allauth).

Images for Dishes/Drinks: Integration of image uploads and display for each dish and drink on the public-facing menu.

Improved User Experience: Further optimizations of user guidance, design, and interactive elements.

User Reviews/Feedback Section: A dedicated section for customers to leave reviews and feedback.

Forgot/Reset Password Functionality: For user account recovery.

Automated Notifications: Confirmation of reservations/reminders to users via texts or emails.

Dynamic Menu Updates: Ability to dynamically add/remove menu items without code changes.

Back To Top

Technologies Used
This project is developed using the robust Django framework, known for its "Batteries included" philosophy, enabling fast and secure web development.

Languages
HTML5

CSS3

Python 3.12

JavaScript

Libraries & Frameworks
Django 4.2.23 - Free and open-source Python Web Framework.

dj-database-url - Used for parsing database URLs (especially for Heroku).

whitenoise - For serving static files in production.

gunicorn - A Python WSGI HTTP server used to run the project on Heroku.

SQLite3 - Default database for local development.

django-allauth - Integrated set of Django applications addressing authentication and registration (planned).

Pillow - (Optional) Required for image uploads once the feature is activated.

Tools
GitPod - Cloud development environment used.

GitHub - Cloud-based Git repository used for version control.

W3C Markup Validation Service - For validating HTML.

W3C CSS Validation Service - For validating CSS.

PEP8 Online Validator - For checking Python code against PEP8 guidelines.

Chrome DevTools - For web development and debugging.

Techsini multi mock up responsiveness - For responsive visuals of the website.

CanIUse - Browser support tables for modern web technologies.

TinyPNG - For compressing images.

Google Fonts - For web fonts.

Balsamiq - For low-fidelity wireframes.

Back To Top

Installation and Execution
Follow these steps to set up and run the project locally:

1. Clone the Repository
git clone https://github.com/Angel1-coder/django_project.git
cd django_project


2. Create and Activate Virtual Environment
python -m venv venv
.\venv\Scripts\activate  # On Windows
# source venv/bin/activate # On macOS/Linux


3. Install Dependencies
pip install Django dj-database-url whitenoise gunicorn # Essential for Heroku deployment
# pip install Pillow # Required for image uploads once the feature is activated.


4. Set up Database and Migrations
Ensure the dishes/migrations folder contains an empty file named __init__.py.

Important Note on Migration History: If you have previously encountered migration issues (e.g., InconsistentMigrationHistory or no such table: django_site), execute the following commands to clean and rebuild your migration history without deleting your db.sqlite3 file:

# Mark the allauth.socialaccount migration as "not applied" (without deleting data)
python manage.py migrate socialaccount 0000 --fake

# Apply migrations for the sites app
python manage.py migrate sites

# Run all pending migrations
python manage.py migrate


If you wish to start with a completely clean database (and can afford to lose all existing data), you can use the following commands instead:

# Delete __pycache__ folders for a clean start
Get-ChildItem -Path . -Include "__pycache__" -Recurse -Directory | Remove-Item -Recurse -Force # Windows
# find . -name "__pycache__" -exec rm -rf {} + # macOS/Linux

# Delete the database file for a clean database (WARNING: Data loss!)
# Del db.sqlite3 # Windows
# rm db.sqlite3 # macOS/Linux

# Delete all migration files in your 'dishes' app (except __init__.py)
# cd dishes\migrations
# Remove-Item -Path * -Exclude "__init__.py" -Force
# cd ..\..\

# Delete all migration files in allauth apps (adjust paths if necessary)
# cd venv\Lib\site-packages\allauth\account\migrations
# Remove-Item -Path * -Exclude "__init__.py" -Force
# cd ..\..\..\..\..\..
# cd venv\Lib\site-packages\allauth\socialaccount\migrations
# Remove-Item -Path * -Exclude "__init__.py" -Force
# cd ..\..\..\..\..\..

python manage.py makemigrations dishes
python manage.py migrate


5. Create Superuser (for Admin Access)
python manage.py createsuperuser


Follow the prompts to set your username and password.

6. Configure django.contrib.sites and allauth settings (if using django-allauth)
Since django-allauth relies on the sites framework, you need to ensure a Site object with id=1 exists in your database and points to the correct domain. You can do this via the Django admin panel (http://127.0.0.1:8000/admin/sites/site/) or using the Django shell:

python manage.py shell


In the shell, enter the following lines one by one and press Enter after each:

from django.contrib.sites.models import Site
site = Site.objects.get_or_create(id=1)[0]
site.domain = '127.0.0.1:8000' # For local development
site.name = 'The Cameroonian Table'
site.save()
print(f"Site ID 1 configured: Domain={site.domain}, Name={site.name}")
exit()


Also, ensure you have the following settings in your my_project/settings.py for allauth redirects:

# my_project/settings.py

# ... other settings ...

SITE_ID = 1 # Must be set for django.contrib.sites and allauth

LOGIN_REDIRECT_URL = '/'  # Redirect to homepage after successful login
ACCOUNT_LOGOUT_REDIRECT_URL = '/' # Redirect to homepage after logout

# ... other settings ...


7. Configure Static and Media Files
For static files (CSS, JS, images that are part of your app) and media files (user-uploaded content), ensure your my_project/settings.py includes:

# my_project/settings.py

# ... other settings ...

# Static files (CSS, JavaScript, Images)
STATIC_URL = 'static/'
STATIC_ROOT = BASE_DIR / 'staticfiles' # Directory where collectstatic will gather files
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')] # If you have a project-level static folder

# WhiteNoise configuration for serving static files in production
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

# Media files (for user-uploaded content)
MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'media' # Directory to store user-uploaded files

# ... other settings ...


And in your my_project/urls.py, add the following at the end of the file for local development serving of media files:

# my_project/urls.py

from django.conf import settings
from django.conf.urls.static import static

# ... urlpatterns definition ...

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)


8. Start Development Server
python manage.py runserver


Open your browser and navigate to http://127.0.0.1:8000/ to view the website. The Admin Panel is accessible at http://127.0.0.1:8000/admin/. The registration and login pages are under /accounts/signup/ and /accounts/login/ (if allauth is configured).

Back To Top

Testing
We have thoroughly tested "The Cameroonian Table" to ensure its functionality, responsiveness, and overall quality. This section outlines the testing methodologies employed and highlights areas still requiring further verification.

1. Manual Testing
The application was rigorously tested manually across various scenarios to confirm expected behavior and user experience.

Homepage Display:

Verified that all published dishes and drinks are displayed correctly on the homepage.

Confirmed that dishes appear under "Our Dishes" and drinks under "Our Drinks".

Checked that categories are correctly associated and displayed for each item.

Admin Panel Functionality:

CRUD Operations: Tested the ability to Create, Read, Update, and Delete (CRUD) categories, dishes, and drinks through the Django admin interface.

Status Management: Confirmed that the "Mark selected as Published" and "Mark selected as Draft" actions work correctly for both dishes and drinks.

Form Validation: Ensured that required fields (e.g., Title, Author, Category) are enforced during creation/editing in the admin.

Responsiveness:

Tested the website on various screen sizes (desktop, tablet, mobile) to ensure layout, navigation, and content display adapt correctly.

Checked for any horizontal scrolling issues.

Browser Compatibility:

Verified functionality and appearance across different web browsers (e.g., Chrome, Firefox, Edge) to ensure consistent user experience.

2. Code Validation
Maintaining clean and valid code is crucial for project quality and maintainability.

Python (PEP8):

Python code was regularly checked against PEP8 guidelines using tools like the PEP8 Online Validator to ensure consistency and readability. All major warnings (e.g., line length, whitespace) were addressed.

HTML (W3C Validator):

HTML templates were validated using the W3C Markup Validation Service to ensure they adhere to web standards, promoting better accessibility and cross-browser compatibility.

CSS (W3C Validator):

CSS stylesheets were validated using the W3C CSS Validation Service to ensure correct syntax and adherence to CSS standards.

3. Deployment Testing (Heroku)
The application is designed for deployment on cloud platforms like Heroku. The following steps confirm its readiness and functionality in a production environment.

Deployment Process:

Confirmed that the application successfully deploys to Heroku following the steps in the "Deployment" section.

Monitored Heroku build logs to ensure all dependencies are installed correctly.

Post-Deployment Verification:

Accessed the deployed application URL to verify that the homepage loads correctly and displays all published content.

Logged into the Django admin panel on the deployed site to confirm administrative functionalities are intact.


Bugs
Known bugs are resolved or an alternative solution has been identified and fixed. However, there could also be unknown bugs, which were not discovered during rigorous testing.

Resolved Bugs:

[List any specific bugs you encountered and resolved during development, e.g., "Migration history inconsistencies fixed by faking migrations."]

Remaining Bugs:

[List any known bugs that are still present, if any.]

Back To Top

Deployment
This Django web application can be deployed to a cloud platform like Heroku.

Heroku Deployment Steps
Prepare Heroku: Sign up for an account at heroku.com, then install the Heroku CLI and log in via your terminal:

heroku login


Specify Python Version: Create a file named .python-version in your project's root directory. This file should contain only your Python version (e.g., 3.12 to match your local Python 3.12.8 environment). This ensures Heroku builds your app with the correct interpreter.

Configure for Deployment: Create a Procfile in your project's root directory. This file tells Heroku how to run your Django application. Add the following line:

web: gunicorn my_project.wsgi --log-file -


Note: You will need to install gunicorn (pip install gunicorn) and configure ALLOWED_HOSTS in my_project/settings.py for production. Also, ensure whitenoise is in your requirements.txt and MIDDLEWARE.

Create & Deploy App: Create a new Heroku application and push your code from your main branch to Heroku.

heroku create your-app-name # Replace 'your-app-name' with a unique name
git push heroku main


Run Migrations on Heroku: After deployment, you need to run database migrations on the Heroku server:

heroku run python manage.py migrate --app your-app-name


Create Superuser on Heroku (if needed): If it's a fresh deployment or you need to ensure an admin user exists, you'll need to create a superuser for the deployed admin:

heroku run python manage.py createsuperuser --app your-app-name


Forking the GitHub Repository
To fork the GitHub repository:

Log in to GitHub and navigate to the repository: https://github.com/Angel1-coder/django_project.git

Click the "Fork" button in the top right corner.

Choose where you want to fork the repository (e.g., to your own GitHub account).

Creating a Local Clone
To create a local clone of the repository:

Open your terminal or Git Bash.

Navigate to the directory where you want to store the project.

Use the git clone command followed by the URL of your forked repository:

git clone https://github.com/YOUR_GITHUB_USERNAME/django_project.git


(Replace YOUR_GITHUB_USERNAME with your actual GitHub username.)

Back To Top

Credits
Code
The following walkthroughs and resources helped me get my project in shape. I have adapted the code from these for the needs of my project.

Django Documentation

Bootstrap Documentation

Django Allauth


Media
Hero Section Background Image:

Gallery Images: , , etc.

Logo and Favicon:

Pinterest

Author
Evangelos Anthony Dimitras
https://github.com/Angel1-coder

