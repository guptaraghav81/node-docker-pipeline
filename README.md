<h1 align="center" id="title">Nebula ~ CI/CD Automation Pipeline</h1>

<p id="description">"Nebula ~ CI/CD Automation Pipeline" is a powerful hands-on project to automate the build and deployment of a MERN web application using GitHub Actions and Docker. It simplifies code testing, image creation, and deployment with every push to the main branch—empowering you with continuous integration and delivery practices used by top companies today.</p>

<p align="center">
  <img src="https://img.shields.io/badge/GitHub-Actions-blue?logo=githubactions&logoColor=white" alt="GitHub Actions">
  <img src="https://img.shields.io/badge/Docker-Automation-blue?logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/CI/CD-Enabled-green" alt="CI/CD">
  <img src="https://img.shields.io/badge/Status-In%20Progress-yellow" alt="Status">
</p>

<h2>🚀 Demo</h2>

🌐 **Live Domain**: [raghav.cloud](http://raghav.cloud) *(DNS configured using AWS Route 53)*

⚠️ *Note: Servers are currently turned off. The application may not be accessible until redeployed.*

<h2>📦 Project Structure & Tech Stack</h2>

*   **Node.js (Express)** – backend API server
*   **React.js** – frontend interface
*   **MongoDB** – database
*   **Docker** – containerization
*   **GitHub Actions** – CI/CD automation
*   **DockerHub** – image hosting

<h2>🛠️ Workflow Overview</h2>

This project demonstrates a fully automated CI/CD pipeline:
* Code is pushed to `main` branch
* GitHub Actions:
  * Installs dependencies
  * Runs unit tests
  * Builds Docker image
  * Pushes image to DockerHub

<h2>📝 CI/CD Workflow File</h2>

File: `.github/workflows/main.yml`

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test

    - name: Log in to DockerHub
      uses: docker/login-action@v3
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker image
      run: docker build -t ${{ secrets.DOCKER_USERNAME }}/mern-web-app .

    - name: Push Docker image
      run: docker push ${{ secrets.DOCKER_USERNAME }}/mern-web-app
```

<h2>🪛 Setup Instructions</h2>
Create a .github/workflows/main.yml file with the above content.

Make sure your repo has Dockerfile at root or inside server folder.

Add GitHub secrets:

DOCKER_USERNAME – your DockerHub username

DOCKER_PASSWORD – your DockerHub password or token

Push code to main branch and check GitHub Actions tab to see the CI/CD pipeline in action.

<h2>📌 Dockerfile Example (Node App)</h2>
dockerfile
Copy
Edit
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
<h2>🧠 Learnings & Takeaway</h2>
By completing this task, you'll understand:

How to set up GitHub Actions workflows

How CI/CD automates testing, building, and deployment

How DockerHub stores and manages container images

Real-world deployment readiness of your web app

<h2>🧪 Testing Strategy</h2>

The current pipeline runs basic unit tests using `npm test` before building the Docker image.

To improve the testing workflow, you can consider:
- ✅ Adding test coverage reports (e.g., using **Jest** and **Istanbul**)
- ✅ Enabling **Linting** with ESLint or Prettier for consistent code style
- ✅ Adding **Integration tests** or **API tests** with tools like **Postman** or **Supertest**
- ✅ Incorporating **End-to-End (E2E)** tests using tools like **Cypress**

---

<h2>🌐 Deployment Readiness</h2>

This project currently focuses on building and pushing the Docker image to DockerHub.

You can extend the pipeline to **automatically deploy** to cloud platforms:

- 🚀 **AWS EC2 / ECS** — run containers in scalable cloud infrastructure
- ☁️ **Render, Railway, DigitalOcean App Platform** — quick and easy container hosting
- 🔐 Add deployment step via **SSH** or dedicated **GitHub Actions** like:
  - `appleboy/ssh-action`
  - `scp-action` or `rsync-action`

Let me know when you're ready for deployment steps!

<h2>🤝 Contribution Guidelines</h2>
Contributions and improvements are welcome! Feel free to fork, improve, or raise issues.

<h2>📫 Contact</h2>
For queries or collaboration:
Email: cloud@raghav



---

