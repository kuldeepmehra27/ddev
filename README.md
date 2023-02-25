## What is DDEV? ##

DDEV is an open-source tool that facilitates local development environments for web developers. It aims to simplify the process of setting up and managing local development environments for web applications, allowing developers to focus on coding rather than environment setup.

DDEV provides a container-based local development environment that is designed to be consistent across different operating systems and to closely mirror the production environment. It also includes tools for managing dependencies, configuring services, and interacting with the containerized environment.

DDEV supports a variety of web technologies, including PHP, Node.js, Ruby, and Python, and it can be used with popular web frameworks and content management systems such as Drupal, WordPress, and TYPO3.

In summary, DDEV is a tool that makes it easier for web developers to set up and manage local development environments for their web applications, which can improve productivity and reduce development time.

## Why developers might choose to use DDEV for local web development? ##

There are several reasons why you might want to use DDEV for your local web development:

1. **Easy Setup and Configuration:** DDEV makes it easy to set up and configure local development environments for your web projects. It includes a simple command-line interface that lets you create and manage environments with just a few commands.

2. **Reproducible Environments:** With DDEV, you can create local development environments that closely match the production environment of your web project. This can help reduce errors and make it easier to test and debug code before deploying to a live server.

3. **Supports Popular Web Development Frameworks:** DDEV includes built-in support for popular web development frameworks like Drupal, WordPress, and TYPO3. This means that you can quickly set up a local development environment for your project without having to spend time configuring everything manually.

4. **Easy Database Management:** DDEV includes tools for managing databases in your local development environment, including importing and exporting data, resetting databases, and creating backups.

5. **Collaboration:** DDEV makes it easy to share your local development environment with other team members, which can help facilitate collaboration and ensure that everyone is working with the same setup.

Overall, DDEV can help streamline your local web development process and make it easier to develop, test, and debug your web projects before deploying to a live server.

## Prerequisites for DDEV ##

DDEV requires that you have Docker and Docker Compose installed on your system before you can install and use it. Docker is a containerization platform that allows you to run applications in isolated environments, while Docker Compose is a tool for defining and running multi-container Docker applications.

Here are the general steps to install Docker and Docker Compose on different operating systems:

**On Windows:**

1. Download and run the Docker Desktop installer from the Docker website: https://www.docker.com/products/docker-desktop.
2. Follow the installation prompts to complete the installation process.
3. After installation, open the Docker Desktop application and ensure that the Docker daemon is running.

**On macOS:**

1. Download and run the Docker Desktop installer from the Docker website: https://www.docker.com/products/docker-desktop.
2. Follow the installation prompts to complete the installation process.
3. After installation, open the Docker Desktop application and ensure that the Docker daemon is running.

**On Linux:**

The installation process for Docker and Docker Compose on Linux varies depending on the specific Linux distribution you are using. The Docker website provides installation instructions for several popular Linux distributions, including Ubuntu, CentOS, Debian, and Fedora. You can find the appropriate installation instructions for your Linux distribution on the Docker website: https://docs.docker.com/engine/install/.

## How to install DDEV? ##

Follow this official docs for Windows and MacOS: https://ddev.readthedocs.io/en/latest/users/install/ddev-installation/

### How to install DDEV on Linux? ###

To install DDEV on Linux, you can follow these steps:

1. Ensure that Docker is running by running the following command in a terminal:
```
$ sudo systemctl status docker
````
2. Install DDEV by running the following command in a terminal:
```
$ curl -fsSL https://apt.fury.io/drud/gpg.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/ddev.gpg > /dev/null
$ echo "deb [signed-by=/etc/apt/trusted.gpg.d/ddev.gpg] https://apt.fury.io/drud/ * *" | sudo tee /etc/apt/sources.list.d/ddev.list
$ sudo apt update && sudo apt install -y ddev
```
3. Install mkcert
```
$ curl -fsSL https://raw.githubusercontent.com/drud/ddev/master/scripts/install_ddev.sh | bash
$ mkcert -install
```
4. Verify the installation by running the **"ddev"** command in a terminal. This should display the DDEV help menu.

[Next Page >>](ddev-drupal.md)
