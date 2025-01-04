# Installation Guide

This document provides instructions on how to set up and run the project.

## Prerequisites

Main tech stack:
- Python 3.10.x or higher
- pipenv
- flask

All the dependencies are listed in the `Pipfile` file.

## Installation with pipenv
For local development, `pipenv` will create a virtual environment for you. 

- Create a virtual environment and install the dependencies:
  ```bash
  pipenv install
  ```

- Activate the environment:
  ```bash
  pipenv shell
  ```

## Run the Application

Use flask to run the application:
   ```bash
   flask --app ytdl_audio_api.app run --debug
   ```
will run on http://localhost:5000 . If you set the environment variable `PORT` to some port, it will listen for everyone at the specified port.


# Test the local server

```bash
curl http://localhost:5000/api/q_E9fgeWtWQ
curl http://localhost:5000/api/S2iihI5G32Y
curl http://localhost:5000/api/0RLvtm0EghQ
```

## Troubleshooting

### ModuleNotFoundError: No module named 'colorama'

If you encounter the error `ModuleNotFoundError: No module named 'colorama'`, it means that the `colorama` package is not installed in your environment. Follow these steps to resolve the issue:

1. **Activate the Pipenv Shell:**

   Ensure you are in the root directory of your project where the `Pipfile` is located. Then activate the pipenv shell:

   ```bash
   pipenv shell
   ```

2. **Install `colorama`:**

   Once inside the pipenv shell, install `colorama` using:

   ```bash
   pipenv install colorama
   ```

3. **Verify Installation:**

   After installation, verify that `colorama` is installed by running:

   ```bash
   pipenv run python -c "import colorama; print(colorama.__version__)"
   ```

   This command should print the version of `colorama` installed, confirming that it is available in your environment.

## Additional Tips

### Locating the Pipenv Virtual Environment

To find the location of the virtual environment where dependencies are installed, use the following command:

```bash
# Activate the Pipenv Shell:
pipenv shell

# Locate the virtual environment:
pipenv --venv
```

This will output the path to the virtual environment directory on your system.
