# AWS Amplify Full-Stack To-Do App

A cloud-connected full-stack web application built with **React + Vite** and **AWS Amplify Gen 2**, featuring user authentication, per-user data isolation, and a full local-to-cloud development workflow.

---

## Overview

This project started from the AWS Amplify React + Vite starter template and evolved into a working cloud-connected application. The goal was to understand how a frontend application connects to AWS backend resources and how local development workflows interact with cloud infrastructure.

---

## Tech Stack

| Frontend | Backend / Cloud |
|----------|----------------|
| React + TypeScript | AWS Amplify Gen 2 |
| Vite | Amazon Cognito (Auth) |
| AWS Amplify UI | AWS AppSync (GraphQL API) |
| | Amazon DynamoDB |
| | AWS IAM + CLI |

---

## Features

- **Authentication** — Secure sign-up, sign-in, and sign-out via Amazon Cognito using Amplify Authenticator
- **CRUD Functionality** — Create and delete to-do items connected to a live cloud backend
- **Owner-Based Authorization** — Each authenticated user can only access their own data
- **Cloud Sandbox Deployment** — Backend deployed and tested locally using `npx ampx sandbox`
- **IAM Configuration** — AWS CLI configured with scoped IAM credentials and validated with `aws sts get-caller-identity`
- **Version Control** — Full project managed with Git and GitHub

---

## Project Walkthrough

### Step 1: Created and Cloned the Repository

Started from the AWS Amplify React + Vite starter template, cloned it locally, and installed dependencies.

```bash
git clone https://github.com/Mark-Daniels-Tamakloe/amplify-vite-react-template.git
cd amplify-vite-react-template
npm install
```

Also downloaded `amplify_outputs.json` and placed it in the project root so the frontend could connect to the Amplify backend.

---

### Step 2: Started the Local Development Server

```bash
npm run dev
```

Opened the app locally at `http://localhost:5173/`.

---

### Step 3: Added Delete Functionality

The starter app supported creating to-do items. I extended it by adding delete functionality in `src/App.tsx`.

```typescript
function deleteTodo(id: string) {
  client.models.Todo.delete({ id });
}
```

Updated the list rendering so clicking a to-do item deletes it:

```tsx
<li onClick={() => deleteTodo(todo.id)} key={todo.id}>
  {todo.content}
</li>
```

---

### Step 4: Added Authentication UI

Wrapped the application with `Authenticator` in `src/main.tsx` and imported the Amplify UI stylesheet, adding a complete sign-up and sign-in interface.

---

### Step 5: Added Sign-Out Functionality

Updated `src/App.tsx` to include a sign-out button using `useAuthenticator()`, allowing authenticated users to log out directly from the UI.

---

### Step 6: Fixed GitHub Authentication and Pushed Code

Resolved push failures caused by GitHub deprecating password authentication over HTTPS. Fixed by generating a personal access token and resolving conflicts caused by multiple GitHub accounts.

---

### Step 7: Configured Local AWS Credentials

Used an IAM user instead of the root account, attached the required Amplify deployment permissions, and configured the AWS CLI locally.

```bash
aws configure
aws sts get-caller-identity
```

---

### Step 8: Deployed the Amplify Cloud Sandbox

```bash
npx ampx sandbox
```

This deployed a cloud sandbox, updated `amplify_outputs.json`, and began watching for backend file changes.

---

### Step 9: Added Owner-Based Authorization

Updated `amplify/data/resource.ts` to use owner-based access rules and set the default authorization mode to the Cognito user pool. Each authenticated user can now only access their own to-do records.

---

### Step 10: Displayed the Signed-In User

Updated the frontend to show the currently signed-in username, confirming that authentication and owner-based authorization were connected correctly.

---

## Challenges Solved

**GitHub Push Authentication**
Cleared stored credentials, generated the correct personal access token, and authenticated with the proper GitHub account.

**AWS Credential Errors**
Rotated IAM access keys, reconfigured the AWS CLI, and verified identity with `aws sts get-caller-identity`.

**Node.js Compatibility**
Resolved an `npx ampx sandbox` failure caused by an unsupported Node.js version by switching to a compatible version.

---

## How to Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/Mark-Daniels-Tamakloe/amplify-vite-react-template.git
cd amplify-vite-react-template

# 2. Install dependencies
npm install

# 3. Configure AWS credentials
aws configure
aws sts get-caller-identity

# 4. Start the Amplify cloud sandbox (Terminal 1)
npx ampx sandbox

# 5. Start the frontend (Terminal 2)
npm run dev
```

Open `http://localhost:5173/` in your browser.

---

## Project Structure

```
amplify-vite-react-template/
├── amplify/              # Backend config (data model, auth, authorization rules)
├── public/
├── src/                  # React frontend (App.tsx, main.tsx)
├── amplify_outputs.json
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

---

## What This Project Demonstrates

- Setting up and running a modern React application locally
- Integrating authentication into a frontend using AWS Amplify
- Connecting a React frontend to AWS backend services (AppSync, DynamoDB, Cognito)
- Configuring and validating local AWS credentials via IAM and the AWS CLI
- Deploying and using an Amplify cloud sandbox
- Implementing basic CRUD functionality with a live cloud API
- Enforcing owner-based authorization at the data layer
- Debugging GitHub, AWS CLI, and Node.js environment issues
- Documenting and managing a full-stack project with Git and GitHub

---

## Planned Improvements

- Edit and update existing to-do items
- Mark tasks as completed
- Add due dates and priorities
- Improve UI styling
- Add error handling
- Deploy the application publicly
- Add screenshots and a demo walkthrough

---

## Author

**Mark-Daniels Tamakloe**
MSc Computer Science — Washington University in St. Louis

MSc Mathematical Sciences — East Tennessee State University

[LinkedIn](https://www.linkedin.com/in/mark-daniels-tamakloe-934785a9)

---

## Acknowledgement

Built by completing the [AWS Amplify React + Vite tutorial](https://docs.amplify.aws/react/start/quickstart/) and documenting the full implementation, setup process, debugging experience, and local deployment workflow.
