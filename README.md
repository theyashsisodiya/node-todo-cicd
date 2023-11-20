# Node Todo App with CI/CD

## Overview

This project is a simple Node.js todo application with continuous integration and continuous deployment (CI/CD) implemented using Jenkins. It also utilizes a webhook as a trigger for automation. The application allows you to manage your todos through a web interface.

## Prerequisites

Before you can run the application, ensure that you have Node.js and npm installed on your system. If not, you can install them using the following commands:

```bash
sudo apt install nodejs
sudo apt install npm
```

## Getting Started

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

   The application will be accessible at [http://localhost:8000/todo](http://localhost:8000/todo).

## CI/CD with Jenkins

This project includes CI/CD pipelines implemented using Jenkins. The Jenkins job is triggered automatically through a webhook whenever changes are pushed to the repository.

### Jenkins Setup

1. Install Jenkins on your server.

2. Configure Jenkins with the necessary plugins, including Github integration only.

3. Create a new Jenkins job that pulls the latest changes from the repository and builds the Docker image.

4. Configure the webhook in your GitHub repository to trigger the Jenkins job on each push.

## Access the Deployed Application

The deployed version on **AWS** of this application can be accessed at [http://51.20.68.144:8000/todo](http://51.20.68.144:8000/todo). Please note that the URL might change, so make sure to check the latest deployment URL.

Feel free to explore the application and manage your todos!

## Contributing

If you would like to contribute to this project, feel free to open issues or submit pull requests. Your feedback and contributions are highly appreciated.

Happy coding!

