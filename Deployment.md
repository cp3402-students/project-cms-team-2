# Overview
This documentation describes the entire process of developing the Joblinx website using WordPress. The development process begins with local development and is then deployed on a live server from a hosting platform. The documentation contains various sections, which are split into sub-files for a better understanding of the whole process.

## Required Tools
- **Hosting Platform:** InfinityFree, a free hosting platform for this project. No payment is required for hosting here.
- **Local Development Environment:** XAMPP, a local server that provides Apache and MySQL databases to help the CMS run.
- **FTP Client:** FileZilla, a file upload system that helps transfer files from a local computer to a hosting platform.
- **Version Control:** Git and GitHub, a repository storage platform to help in version control.
- **Project Management:** Slack, a project management platform that helps when collaborating on one project.

## Local Development Process

### Step 1: XAMPP Installation
Download and install XAMPP from [apachefriends.org](https://www.apachefriends.org/).

### Step 2: Set Up WordPress
- Download the latest version of WordPress from [wordpress.org](https://wordpress.org/).
- Navigate to the `htdocs` directory of the XAMPP installation and create a folder named `a2.html`.
- Extract the WordPress files into the `a2.html`.
- Create a new database named `joblinx` using phpMyAdmin (accessible via `http://localhost/phpmyadmin`).
- Complete the WordPress installation by visiting `http://localhost/a2.html` and following the setup wizard.
- The setup wizard prompts you to connect the database and set up the admin logins, name of the site, and description.

### Step 3: Develop the Website
Use the admin WordPress dashboard to customize the theme.

### Step 4: Clone Repository
Clone the GitHub repository containing the project files into the `wp-content/themes` directory.

For more information about customizing the website, visit the `theme.md` file.

## Deployment on Live Server

### Prepare Your Local WordPress Site for Upload

#### Step 1: Export Database
- Open phpMyAdmin (accessible via `http://localhost/phpmyadmin`).
- Select your `joblinx` database.
- Click on the "Export" tab and click "Go" to download the `.sql` file.

#### Step 2: Compress Joblinx WordPress Files
- Navigate to your local WordPress installation folder called `a2.html`.
- Select all files and folders inside the `a2.html` directory (e.g., `wp-content`, `wp-admin`, etc.).
- Compress them into a `.zip` file.

### Step 3: Connect to InfinityFree Using FileZilla
a) Download and install FileZilla from [filezilla-project.org](https://filezilla-project.org/).  
b) Obtain FTP Credentials: Log in to your InfinityFree account and navigate to your Control Panel. Under the "FTP" section, find your FTP credentials (hostname, username, password, and port).  
c) Open FileZilla and Connect:
- Open FileZilla.
- Enter your FTP credentials in the “Host”, “Username”, and “Password” fields. Use port 21.
- Click “Quickconnect” to establish a connection.

### Step 4: Upload WordPress Files
#### Navigate to the Remote Directory
- In FileZilla, on the right panel (remote site), navigate to the `htdocs` directory.

#### Upload Your Files
- On the left panel (local site), navigate to the directory containing your compressed WordPress files.
- Select the `.zip` file and upload it to the `htdocs` directory.
- Once uploaded, use FileZilla's right-click context menu to extract the `.zip` file on the server or manually upload and organize the files.

### Step 5: Import Database to InfinityFree
- Log in to InfinityFree’s phpMyAdmin:
  - From your InfinityFree Control Panel, navigate to the “MySQL Databases” section.
  - Click “phpMyAdmin” next to your database.
- Create a New Database:
  - In phpMyAdmin, create a new database if you haven’t already.
- Import Database:
  - Select the newly created database.
  - Click on the "Import" tab.
  - Choose the `.sql` file you exported earlier.
  - Click "Go" to import the database.

### Step 6: Update `wp-config.php` File
- Edit `wp-config.php`:
  - While still in FileZilla, locate the `wp-config.php` file in the WordPress site directory.
  - Edit the database connection details to match your InfinityFree MySQL database credentials:
  ```php
  define('DB_NAME', 'your_database_name');
  define('DB_USER', 'your_database_user');
  define('DB_PASSWORD', 'your_database_password');
  define('DB_HOST', 'your_database_host');
### Step 6: Final Steps
#### Test Your Site:
- Visit your website URL (provided by InfinityFree) to ensure everything is working correctly.
- Perform a thorough check to verify that the site is functioning as expected.
