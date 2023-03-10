# **Angular Test Project for CI/CD Implementation with YAML and GitHub Pages**

This project is a simple Angular application that can be used as a test project for implementing continuous integration and continuous deployment (CI/CD) with YAML and GitHub Pages.

## **Getting Started**

To get started with this project, you'll need to follow these steps:

1. Clone this repository to your local machine.
2. Install the necessary dependencies by running the **`npm install`** command.
3. Start the development server by running the **`ng serve`** command.

## **CI/CD Implementation**

To implement CI/CD for this project, we will be using YAML and GitHub Pages. The following steps will guide you through the process:

1. Create a new branch for your CI/CD implementation.
2. Create a **`deploy.yml`** file in the root directory of your project.
3. In the **`deploy.yml`** file, define the necessary steps for building and deploying your application to GitHub Pages. An example configuration is provided below:

```
yamlCopy code
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '12.x'

      - name: Install dependencies
        run: npm install

      - name: Build application
        run: npm run build --prod

      - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@4.1.1
        with:
          branch: gh-pages
          folder: dist/angular-test-project

```

In this example configuration, we define a job that runs on every push to the **`main`** branch. The job checks out the code, sets up Node.js, installs dependencies, builds the application, and deploys it to the **`gh-pages`** branch of your repository.

1. Commit and push your changes to the new branch.
2. Create a new GitHub Actions workflow by clicking on the "Actions" tab in your repository and selecting "New workflow". Name the workflow and add the following code to the **`yml`** file:

```
yamlCopy code
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - ci-cd-implementation

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '12.x'

      - name: Install dependencies
        run: npm install

      - name: Build application
        run: npm run build --prod

      - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@4.1.1
        with:
          branch: gh-pages
          folder: dist/angular-test-project

```

In this workflow configuration, we define a job that runs on every push to the **`ci-cd-implementation`** branch. The job checks out the code, sets up Node.js, installs dependencies, builds the application, and deploys it to the **`gh-pages`** branch of your repository.

1. Save and commit the workflow file to your repository.
2. Verify that the build and deployment are successful by visiting the GitHub Pages URL for your project.

## **Conclusion**

This Angular test project serves as a good starting point for implementing CI/CD with YAML and GitHub Pages. By following the steps outlined in this README, you should be able to successfully implement CI/CD for your Angular application. Remember to always test your workflow and make necessary adjustments as needed. With CI/CD in place, you can streamline your development process and ensure that your application is always up-to-date and deployed to your desired platform. Good luck!
