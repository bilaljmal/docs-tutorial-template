==========================
Installation Instructions
==========================

This document provides step-by-step instructions for installing and setting up the project using Docker. Follow the instructions based on your operating system (Windows or Ubuntu).

Windows Installation
====================

Installing Docker Desktop on Windows
------------------------------------

Docker Desktop allows you to run Docker containers on your Windows machine with a user-friendly interface.

**Prerequisites**

- **Supported OS Versions:**
  - Windows 10 64-bit: Pro, Enterprise, or Education (Build 19044 or higher)
  - Windows 11 64-bit: Pro, Enterprise, or Education

- **Additional Requirements:**
  - Windows Subsystem for Linux (WSL) 2 enabled.

**Steps:**

1. **Install and Set Up WSL 2**

   Open PowerShell as Administrator and run the following command to enable the WSL feature:

   .. code-block:: shell

      wsl --install

   After installation, restart your system for the changes to take effect.

   Once WSL is installed, set WSL 2 as the default version by running:

   .. code-block:: shell

      wsl --set-default-version 2

2. **Download Docker Desktop**

   Download Docker Desktop from Docker's official website:

   https://www.docker.com/products/docker-desktop

3. **Install Docker Desktop**

   Run the installer and follow the installation wizard. Ensure the following options are selected during installation:

   - Install required Windows components for WSL 2
   - Use the WSL 2-based engine

   Restart your computer if prompted.

4. **Start Docker Desktop**

   Launch Docker Desktop from the Start menu. Docker will start in the background, and the Docker icon will appear in your system tray.

5. **Verify Installation**

   To verify Docker Desktop is installed correctly, run the following command in PowerShell or Command Prompt:

   .. code-block:: shell

      docker run hello-world

   A confirmation message will print if everything is working correctly.

Ubuntu Installation
====================

Installing Docker Engine on Ubuntu
----------------------------------

Docker Engine allows you to run Docker containers on your Ubuntu machine. Follow these steps to install Docker Engine.

**Prerequisites**

- **Firewall Considerations:**
  - Docker bypasses firewall rules set by `ufw` or `firewalld`.
  - Ensure firewall rules are created using `iptables` or `ip6tables`.

- **Supported OS Versions:**
  - Ubuntu Noble 24.04 (LTS)
  - Ubuntu Jammy 22.04 (LTS)
  - Ubuntu Focal 20.04 (LTS)

**Steps:**

1. **Uninstall Conflicting Packages**

   Run the following command to remove any conflicting packages:

   .. code-block:: shell

      for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

2. **Install Docker Engine Using Docker's apt Repository**

   a. **Set Up the Docker apt Repository**

   .. code-block:: shell

      sudo apt-get update
      sudo apt-get install ca-certificates curl
      sudo install -m 0755 -d /etc/apt/keyrings
      sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
      sudo chmod a+r /etc/apt/keyrings/docker.asc
      echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
      sudo apt-get update

   b. **Install Docker Engine**

   .. code-block:: shell

      sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

3. **Verify Installation**

   Once the installation is complete, verify it by running a test Docker container:

   .. code-block:: shell

      sudo docker run hello-world

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

Conclusion
==========

By following these instructions, you can successfully install Docker on your system and set up the environment for your project. Ensure that all environment variables are correctly configured to enable seamless integration between Django and PostgreSQL.
