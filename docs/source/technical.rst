==========================
Technical Overview
==========================

This project is a modern web application built using **Python 13** and the **Django 5.1.1** web framework. It leverages Docker Compose to create a reproducible development and production environment, ensuring that the application runs consistently across different platforms.
I also used the apikey authentication to allow user to easily integrate with their ERP and point of sales.
Key Components
===============

1. Django Web Application
-------------------------

- **Django Framework**: The backbone of the application, Django provides a robust, secure, and scalable foundation for web development.
- **RESTful API**: Built with **Django REST Framework** (DRF), the project offers RESTful APIs, making it easy to create and manage web services.
- **JWT Authentication**: The project utilizes **djangorestframework-jwt** and **djangorestframework-simplejwt** for handling JSON Web Token (JWT) authentication, providing secure access to the API.
- **CORS Handling**: **django-cors-headers** is used to manage Cross-Origin Resource Sharing (CORS), allowing the application to interact with external resources securely.
- **Environment Configuration**: The **python-dotenv** package is used to manage environment variables, ensuring that sensitive information like database credentials remains secure.

2. Database
-----------

- **PostgreSQL**: A robust and scalable relational database system is used for storing the application's data. The database is managed using the **psycopg2** and **psycopg2-binary** libraries, which provide efficient and reliable PostgreSQL database connectivity.

3. Containerization with Docker
-------------------------------

- **Docker Compose**: The project is containerized using Docker Compose, ensuring consistent environments across development, testing, and production.

  - **Web Service**: The Django application runs in a container named `zatca_middleware_einvotca_web`, which is built from a custom Dockerfile located in the `project` directory. It uses volumes for code and static files, making development and deployment straightforward.

  - **Database Service**: PostgreSQL runs in a container named `zatca_middleware_db`, with persistent storage handled through Docker volumes.

4. Additional Libraries
-----------------------

- **Gunicorn**: Used as the WSGI HTTP server to run the Django application, ensuring that it is production-ready.
- **Static and Media File Handling**: The project uses Docker volumes to manage static files, ensuring they are properly served across environments.
- **API Documentation**: The **drf-yasg** library is included to automatically generate Swagger and ReDoc documentation for the RESTful API.

Docker Compose Configuration
=============================

The Docker Compose setup includes two main services:

- **web**: The Django application service, exposing port `8000` and depending on the PostgreSQL service.
- **db**: The PostgreSQL database service, with data stored in a Docker volume to ensure persistence across container restarts.

Both services are connected through a shared Docker network, named `nginx_network`, allowing seamless communication between the Django application and the PostgreSQL database.

Conclusion
==========

This project leverages the power of Django and PostgreSQL within a Dockerized environment, ensuring a scalable, maintainable, and secure web application. The combination of JWT-based authentication, robust RESTful APIs, and containerization with Docker Compose makes this project well-suited for modern web development needs.
