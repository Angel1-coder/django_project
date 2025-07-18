
# The Cameroonian Table

## Project Overview

Welcome to **"The Cameroonian Table"** – a digital gateway to the rich and diverse culinary world of Cameroon!
This project is more than just a website; it's an invitation to experience the warmth, the flavors, and the hospitality of Cameroonian cuisine.
Our goal is to introduce Cameroonian gastronomy to a global audience in a modern and appealing way, while simultaneously creating a user-friendly platform for our valued customers.

We aim to capture the authentic ambiance of a Cameroonian dining experience online – friendly, inviting, and full of flavor.
The website presents our dishes and drinks in a modern design that reflects the beauty and diversity of our culture.
At the same time, we place great emphasis on functionality to provide our customers with a seamless experience – from exploring our menu to conveniently making table reservations and registering as part of our community.

---

## Features

### Current Features

- **Comprehensive Menu**: A detailed listing of traditional Cameroonian dishes and refreshing beverages.
- **Categorization**: Dishes and drinks are clearly organized by categories (e.g., Main Course, Juices, Beers).
- **Admin Panel**: A fully functional Django admin panel for easy management of categories, dishes, and drinks, including the ability to change their publication status.
- **Responsive Design**: The website is designed to look and function optimally on various devices (desktop, tablet, mobile phone).

### Planned Features

- **Image Gallery**: Integration of images for each dish and drink to make the menu more visually appealing.
- **Table Reservation System**: An intuitive function that allows customers to reserve tables online.
- **Customer Registration and Management**: Enables users to register, create profiles, and manage their reservations.
- **User-Friendly Navigation**: Improvement of user guidance for an even better browsing experience.

---

## Technologies

This project is developed using the robust Django framework, known for its "batteries included" philosophy, enabling fast and secure web development.

- **Backend**: Python 3.12, Django 4.2.23  
- **Database**: SQLite3 (default for development)  
- **Frontend**: HTML, CSS (with a focus on responsive design)  
- **Version Control**: Git & GitHub

---

## Installation and Execution

Follow these steps to set up and run the project locally:

### 1. Clone the Repository

```bash
git clone https://github.com/Angel1-coder/django_project.git
cd django_project
```

### 2. Create and Activate Virtual Environment

```bash
python -m venv venv
.env\Scriptsctivate  # On Windows
# source venv/bin/activate  # On macOS/Linux
```

### 3. Install Dependencies

```bash
pip install Django
# pip install Pillow  # Required for image uploads once the feature is activated.
```

### 4. Set up Database and Migrations

Ensure the `dishes/migrations` folder contains an empty file named `__init__.py`.

**Delete `__pycache__` folders for a clean start:**

```powershell
Get-ChildItem -Path . -Include "__pycache__" -Recurse -Directory | Remove-Item -Recurse -Force  # Windows
```

```bash
# find . -name "__pycache__" -exec rm -rf {} +  # On macOS/Linux
```

**Delete the database file for a clean database (WARNING: Data loss!):**

```bash
# rm db.sqlite3  # On macOS/Linux
# Del db.sqlite3  # On Windows
```

Run migrations:

```bash
python manage.py makemigrations dishes
python manage.py migrate
```

### 5. Create Superuser (for Admin Access)

```bash
python manage.py createsuperuser
```

Follow the prompts to set your username and password.

### 6. Start Development Server

```bash
python manage.py runserver
```

Open your browser and navigate to [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to view the website.
The Admin Panel is accessible at [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/).

---

## Testing

We've thoroughly tested **"The Cameroonian Table"** to ensure its functionality, responsiveness, and overall quality.
This section outlines the testing methodologies employed and highlights areas still requiring further verification.

### 1. Manual Testing

**Homepage Display**

- Verified that all published dishes and drinks are displayed correctly on the homepage.
- Confirmed that dishes appear under *Our Dishes* and drinks under *Our Drinks*.
- Checked that categories are correctly associated and displayed for each item.

`[TO BE DONE: Insert Image of Homepage - Desktop View]`

**Admin Panel Functionality**

- **CRUD Operations**: Tested the ability to Create, Read, Update, and Delete categories, dishes, and drinks through the Django admin interface.
- **Status Management**: Confirmed that the "Mark selected as Published" and "Mark selected as Draft" actions work correctly.
- **Form Validation**: Ensured that required fields (e.g., Title, Author, Category) are enforced during creation/editing.

`[TO BE DONE: Insert Image of Admin Panel - Dishes List]`
`[TO BE DONE: Insert Image of Admin Panel - Add Dish Form]`

**Responsiveness**

- Tested the website on various screen sizes (desktop, tablet, mobile) to ensure layout and content adapt correctly.
- Checked for any horizontal scrolling issues.

`[TO BE DONE: Insert Image of Homepage - Mobile View]`

**Browser Compatibility**

- Verified functionality and appearance across different browsers (e.g., Chrome, Firefox, Edge).

`[TO BE DONE: Conduct specific testing on additional browsers as needed.]`

### 2. Code Validation

- **Python (PEP8)**: Checked using PEP8 tools; major warnings addressed.
- **HTML**: Validated with W3C Markup Validation Service.
- **CSS**: Validated with W3C CSS Validation Service.

### 3. Deployment Testing (Heroku)

**Deployment Process**

- Confirmed deployment steps for Heroku.
- Monitored build logs for successful dependency installation.

`[TO BE DONE: Perform actual deployment to Heroku and verify the process.]`

**Post-Deployment Verification**

- Accessed deployed URL to verify homepage loads correctly.
- Logged into Django admin panel on deployed site to confirm admin functionalities.

`[TO BE DONE: Insert Image of Deployed Homepage on Heroku]`
`[TO BE DONE: Verify CRUD, status changes on Heroku.]`

---

## Deployment

This Django web application can be deployed to a cloud platform like **Heroku**.

### Heroku Deployment Steps

1. **Prepare Heroku**

   Sign up at [heroku.com](https://www.heroku.com/), install the Heroku CLI, and log in:

   ```bash
   heroku login
   ```

2. **Specify Python Version**

   Create a `.python-version` file with your version (e.g., `3.12`).

3. **Configure for Deployment**

   Create a `Procfile` in the root:

   ```bash
   web: gunicorn my_project.wsgi --log-file -
   ```

   > *Note*: Install `gunicorn` (`pip install gunicorn`). Configure `ALLOWED_HOSTS` in `settings.py`.

4. **Create & Deploy App**

   ```bash
   heroku create your-app-name
   git push heroku main
   ```

5. **Run Migrations on Heroku**

   ```bash
   heroku run python manage.py migrate --app your-app-name
   ```

6. **Create Superuser on Heroku**

   ```bash
   heroku run python manage.py createsuperuser --app your-app-name
   ```

---

## Notes

- **Data Availability**: Menu data is managed via the Django Admin Panel.
- **Disclaimer**: This project is intended as a learning tool and a basic restaurant menu application.

---

## Author

Evangelos Anthony Dimitras  
[https://github.com/Angel1-coder]