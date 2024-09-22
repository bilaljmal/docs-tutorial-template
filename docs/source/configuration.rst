Configuration
=============

Setting Up Environment Variables
---------------------------------

Create a `.env` file with the following content to configure the environment variables:

.. code-block:: ini

   POSTGRES_DB=einvotca_middleware_db
   POSTGRES_USER=einvotca_middleware_user_db
   POSTGRES_PASSWORD=8@Pv#0LtzW3&b$zQ
   SECRET_KEY=Z4!@k5lVx8^Wj$Y2pQn&Zr%+3!DgPz5A*u8Xj%2yRs%7m#hL0d
   DEBUG=False

   # Django setting variables
   DJANGO_DB_HOST=db
   DJANGO_DB_PORT=5432
   DJANGO_DB_NAME=einvotca_middleware_db
   DJANGO_DB_USER=einvotca_middleware_user_db
   DJANGO_DB_PASSWORD=8@Pv#0LtzW3&b$zQ

   # Django admin credentials
   DJANGO_SUPERUSER_USERNAME=new_admin
   DJANGO_SUPERUSER_EMAIL=new_admin@example.com
   DJANGO_SUPERUSER_PASSWORD=xB3^7Af!qmJ8

Environment Variables Explanation
---------------------------------

- **PostgreSQL Database Variables**
  - `POSTGRES_DB`: The name of the PostgreSQL database.
  - `POSTGRES_USER`: The username for the PostgreSQL database.
  - `POSTGRES_PASSWORD`: The password for the PostgreSQL user.

- **Django Secret and Debug Settings**
  - `SECRET_KEY`: Secret key used by Django for cryptographic signing.
  - `DEBUG`: Set to `False` in production to prevent exposing sensitive information.

- **Django Database Connection Variables**
  - `DJANGO_DB_HOST`: Hostname of the PostgreSQL server.
  - `DJANGO_DB_PORT`: Port number of the PostgreSQL server.
  - `DJANGO_DB_NAME`: Name of the database Django should connect to.
  - `DJANGO_DB_USER`: Username for the database connection.
  - `DJANGO_DB_PASSWORD`: Password for the database connection.

- **Django Admin User Credentials**
  - `DJANGO_SUPERUSER_USERNAME`: Username for the Django superuser.
  - `DJANGO_SUPERUSER_EMAIL`: Email for the Django superuser.
  - `DJANGO_SUPERUSER_PASSWORD`: Password for the Django superuser.