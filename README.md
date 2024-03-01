


# Node Todo App with CI/CD

![project](https://github.com/theyashsisodiya/node-todo-cicd/assets/97979728/65c5be9c-0d8d-443d-b0a9-fc6d452ec0a2)

## Overview

This project is a simple Node.js todo application with continuous integration and continuous deployment (CI/CD) implemented using Jenkins. It also utilizes a webhook as a trigger for automation. The application allows you to manage your todos through a web interface.

### Prerequisites

Before you can run the application, ensure that you have Node.js and npm installed on your system. If not, you can install them using the following commands:

```bash
sudo apt install nodejs
sudo apt install npm
```

### Getting Started

Follow these steps to run the project locally:

1. Clone the repository:

   ```bash
   git clone https://github.com/theyashsisodiya/node-todo-cicd.git
   ```

2. Navigate to the project directory:

   ```bash
   cd node-todo-cicd
   ```

3. Install project dependencies:

   ```bash
   npm install
   ```

4. Run the application:

   ```bash
   node app.js
   ```

   The application will be accessible at http://localhost:8000/todo.

### CI/CD with Jenkins

This project includes CI/CD pipelines implemented using Jenkins. The Jenkins job is triggered automatically through a webhook whenever changes are pushed to the repository.

#### Jenkins Setup

1. Install Jenkins on your server.

2. Configure Jenkins with the necessary plugins, including Github integration only.

   - Select Git on Source Code Management.
   - Paste your repo link.
   - Add your Github credentials.
   - Branches to build: `main` if your project is on the main branch, else `master` or other.
   - Build triggers: Select "GitHub hook trigger for GITScm polling."

3. Execute shell script:

   ```bash
   #!/bin/bash

   # Define variables
   CONTAINER_NAME=node-app-container
   IMAGE_NAME=node-app-todo
   PORT=8000

   # Check if the port 8000 is in use and kill the process if needed
   if lsof -i :$PORT; then
       echo "Port $PORT is in use, killing the process..."
       lsof -ti :$PORT | xargs kill -9
   fi

   # Check if the container is running
   if docker ps -a --format '{{.Names}}' | grep -q $CONTAINER_NAME; then
       echo "Stopping and removing existing container..."
       docker stop $CONTAINER_NAME
       docker rm $CONTAINER_NAME
   fi

   # Build and run the Docker container
   echo "Building and running the new container..."
   docker build -t $IMAGE_NAME .
   docker run -d --name $CONTAINER_NAME -p $PORT:8000 $IMAGE_NAME
   ```

   Apply and save it.

### Access the Deployed Application

The deployed version on AWS of this application can be accessed at [[http://65.2.11.33:8000/todo](http://65.2.11.33:8000/todo)]. Please note that the URL might change, so make sure to check the latest deployment URL.

Feel free to explore the application and manage your todos!

### Architecture

![Group](https://github.com/theyashsisodiya/node-todo-cicd/assets/97979728/92860446-c0c4-4378-92e6-bc7ec198ec46)

### Contributing

If you would like to contribute to this project, feel free to open issues or submit pull requests. Your feedback and contributions are highly appreciated.

Happy coding!😄:-)
