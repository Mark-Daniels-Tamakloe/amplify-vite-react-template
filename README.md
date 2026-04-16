# AWS Amplify Full-Stack To-Do App

A cloud-connected full-stack web application built with **React + Vite** and **AWS Amplify Gen 2**, featuring user authentication, per-user data isolation, and full local-to-cloud deployment.

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

# 4. Start the Amplify cloud sandbox (Terminal 1)
npx ampx sandbox

# 5. Start the frontend (Terminal 2)
npm run dev
```

Open `http://localhost:5173/` in your browser.

---

## Project Structure

amplify-vite-react-template/
├── amplify/          # Backend config (data model, auth, authorization)
├── src/              # React frontend (App.tsx, main.tsx)
├── amplify_outputs.json
├── package.json
└── vite.config.ts

---

## Key Implementation Details

**Delete functionality** (`src/App.tsx`):
```typescript
function deleteTodo(id: string) {
  client.models.Todo.delete({ id });
}
```

**Owner-based authorization** (`amplify/data/resource.ts`):
Authorization rules updated to scope all data access to the signed-in Cognito user, ensuring complete data isolation per account.

---

## Challenges Solved

- Debugged GitHub HTTPS authentication by switching to a personal access token
- Resolved invalid AWS token errors by rotating IAM access keys and reconfiguring the CLI
- Fixed Node.js version incompatibility preventing `npx ampx sandbox` from running

---

## Author

**Mark-Daniels Tamakloe**  
MSc Computer Science — Washington University in St. Louis  
MSc Mathematical Sciences — East Tennessee State University  
[LinkedIn](#)
