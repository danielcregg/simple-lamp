# Simple LAMP Web Application

![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)

> **Note:** This repository is a fork of [qyjohn/simple-lamp](https://github.com/qyjohn/simple-lamp).

A minimal LAMP stack web application demonstrating user login, image uploading, MySQL-backed storage, and optional Memcached caching.

## Overview

This project provides a straightforward PHP-based web application running on a Linux/Apache/MySQL/PHP (LAMP) stack. Users can log in with a username, upload image files (JPG, PNG, GIF), and view the most recently uploaded images on the front page. The application supports configurable storage backends (local hard disk or Amazon S3), optional Memcached-based session sharing and front page caching, and simulated latency for testing purposes. It is designed as a teaching tool for scalable web architecture concepts.

## Features

- **User login/logout** with PHP session management
- **Image upload** with client-side and server-side file type validation
- **MySQL database** for tracking uploaded image metadata with timestamps
- **Local or S3 storage** -- configurable storage backend for uploaded files
- **Memcached support** -- optional session sharing and front page caching
- **Latency simulation** -- configurable delay for performance testing
- **Pre-loaded demo data** -- includes sample images and SQL dump for quick setup

## Prerequisites

- **Ubuntu 14.04 or 16.04+** (or any Linux distribution with Apache, PHP, and MySQL)
- **Apache 2** web server
- **PHP 5.x or 7.x** with extensions: `php-mysql`, `php-curl`, `php-memcached`
- **MySQL 5.5+**
- **Memcached** (optional, for caching and session sharing)

## Getting Started

### Installation

1. Install the LAMP stack:

```bash
sudo apt-get update
sudo apt-get install git mysql-server
sudo apt-get install apache2 php libapache2-mod-php php-mysql php-curl php-xml php-memcached
sudo service apache2 restart
```

2. Clone the repository into your web server directory:

```bash
cd /var/www/html
git clone https://github.com/danielcregg/simple-lamp.git
```

3. Create the MySQL database and user:

```sql
mysql -u root -p
CREATE DATABASE simple_lamp;
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON simple_lamp.* TO 'username'@'localhost';
quit
```

4. Import the demo data:

```bash
cd /var/www/html/simple-lamp
mysql -u username -p simple_lamp < simple_lamp.sql
```

5. Update `config.php` with your MySQL credentials.

6. Set the uploads directory permissions:

```bash
sudo chown -R www-data:www-data uploads
```

### Usage

Open your browser and navigate to:

```
http://localhost/simple-lamp/index.php
```

Enter any username to log in, then upload images using the file upload form. The most recent 10 uploads are displayed on the front page.

To enable Memcached caching, set `$enable_cache = true` and configure `$cache_server` in `config.php`.

## Tech Stack

- **Language:** PHP, JavaScript
- **Database:** MySQL
- **Web Server:** Apache 2
- **Caching:** Memcached (optional)
- **Cloud Storage:** Amazon S3 (optional)
- **OS:** Ubuntu Linux

## License

This project is licensed under the [MIT License](LICENSE).
