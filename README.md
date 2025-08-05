# Node.js Demo App

A simple Node.js application with Express.js framework, configured with Jenkins CI/CD pipeline for automated deployment.

## 🚀 Project Overview

This is a basic Node.js web application that demonstrates:
- Express.js web server
- Docker containerization
- Jenkins CI/CD pipeline
- GitHub webhook integration for automated builds

## 📋 Prerequisites

Before running this project, make sure you have the following installed:

- **Node.js** (v14 or higher)
- **npm** (comes with Node.js)
- **Docker** (for containerization)
- **Jenkins** (for CI/CD pipeline)

## 🛠️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/anupsharma329/jenkins-task.git
cd jenkins-task
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run the Application Locally

```bash
npm start
```

The application will be available at `http://localhost:3000`

## 🐳 Docker Setup

### Build Docker Image

```bash
docker build -t nodejs-demo-app .
```

### Run Docker Container

```bash
docker run -d -p 3000:3000 --name nodejs-demo-app nodejs-demo-app
```

### Stop and Remove Container

```bash
docker rm -f nodejs-demo-app
```

## 🔄 Jenkins CI/CD Pipeline

This project includes a Jenkins pipeline that automatically:

1. **Checkout** - Pulls the latest code from GitHub
2. **Install Dependencies** - Runs `npm install`
3. **Test** - Runs `npm test` (currently configured to pass without tests)
4. **Build Docker Image** - Creates a Docker image
5. **Run Docker Container** - Deploys the application

### Pipeline Stages

```groovy
pipeline {
    agent any
    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }
    stages {
        stage('Checkout') { ... }
        stage('Install Dependencies') { ... }
        stage('Test') { ... }
        stage('Build Docker Image') { ... }
        stage('Run Docker Container') { ... }
    }
}
```

### GitHub Webhook Integration

The pipeline is configured with GitHub webhooks for automatic triggering on code pushes. The webhook URL is:
```
https://your-ngrok-url.ngrok-free.app/github-webhook/
```

## 📁 Project Structure

```
nodejs-demo-app/
├── index.js              # Main application file
├── package.json          # Node.js dependencies and scripts
├── package-lock.json     # Locked dependency versions
├── Dockerfile           # Docker container configuration
├── Jenkinsfile         # Jenkins pipeline configuration
└── README.md           # This file
```

## 🧪 Testing

Currently, the project has a placeholder test configuration. To add real tests:

1. Install a testing framework (e.g., Jest, Mocha)
2. Create test files in a `tests/` directory
3. Update the `test` script in `package.json`

## 🚀 Deployment

The application is automatically deployed via Jenkins when code is pushed to the main branch. The deployment process:

1. Builds a new Docker image
2. Stops the existing container (if running)
3. Starts a new container with the updated image
4. Makes the application available on port 3000

## 🔧 Configuration

### Environment Variables

- `PORT`: Application port (default: 3000)

### Jenkins Configuration

- **Repository URL**: `https://github.com/anupsharma329/jenkins-task.git`
- **Branch**: `main`
- **Script Path**: `Jenkinsfile`

## 📝 Scripts

- `npm start`: Start the application
- `npm test`: Run tests (currently passes without tests)
- `npm install`: Install dependencies

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 👨‍💻 Author

**Anup Sharma**

## 🔗 Links

- **GitHub Repository**: https://github.com/anupsharma329/jenkins-task
- **Jenkins Dashboard**: http://localhost:8080 (local setup)

---

## 🆘 Troubleshooting

### Common Issues

1. **Jenkins Pipeline Fails**: Check if `npm` and `docker` are in the PATH
2. **Webhook Not Triggering**: Verify ngrok is running and webhook URL is correct
3. **Docker Build Fails**: Ensure Dockerfile is in the project root
4. **Port Already in Use**: Stop existing containers with `docker rm -f nodejs-demo-app`

### Getting Help

If you encounter any issues:
1. Check the Jenkins build logs
2. Verify all prerequisites are installed
3. Ensure GitHub webhook is properly configured 