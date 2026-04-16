# AWS Amplify Full-Stack To-Do App

This project documents my end-to-end implementation of a full-stack to-do application using **React + Vite** and **AWS Amplify Gen 2**. I completed this project as a hands-on cloud development exercise to learn how to build, configure, authenticate, deploy, and secure a modern full-stack application using AWS services.

---

## Overview

This project started from the AWS Amplify React + Vite starter template and evolved into a working cloud-connected application with:

- user authentication
- create and delete to-do functionality
- local frontend testing
- cloud sandbox deployment
- owner-based authorization
- GitHub version control

The goal of this project was to understand how a frontend application connects to AWS backend resources and how local development workflows interact with cloud infrastructure.

---

## Features

- **Authentication**: Implemented secure sign-up, sign-in, and sign-out using Amazon Cognito through Amplify Authenticator.
- **API and Data**: Connected the app to Amplify backend data resources for storing and managing to-do items.
- **CRUD Functionality**: Added support for creating and deleting to-do items.
- **Per-User Authorization**: Restricted each signed-in user to only access their own to-do data.
- **Local Cloud Development**: Configured and deployed an Amplify cloud sandbox from my local machine.
- **Version Control**: Managed the project with Git and GitHub.

---

## Project Walkthrough

### Step 1: Created and Cloned the Repository
I started by creating the starter repository from the AWS Amplify React + Vite template and cloning it into my local machine.

```bash
git clone https://github.com/Mark-Daniels-Tamakloe/amplify-vite-react-template.git
cd amplify-vite-react-template
npm install
