# 🎵 Cloud Music Platform – React Frontend

This repository contains the **frontend** of the **Cloud Music Streaming Platform**.

The frontend is built with **React**, **TypeScript**, and **Vite**, providing a fast, modular, and cloud-ready interface for interacting with AWS backend services such as **API Gateway**, **Cognito**, and **S3**.

---

## 🚀 Features

The web app allows users to:
- 🎧 Stream and explore music content hosted in the cloud.  
- 🔐 Register, log in, and manage sessions via **AWS Cognito**.  
- 💿 Browse artists, albums, and songs with filtering by genre.  
- 💌 Subscribe to content and receive notifications about new uploads.  
- 🌐 Access a personalized feed generated from user activity and preferences.  
- ⬇️ Download or locally cache songs for offline playback.  
- 🧾 Rate songs and update preferences dynamically.  

---

## 🧩 Tech Stack

| Category | Technology |
|-----------|-------------|
| **Framework** | React 18 + TypeScript + Vite |
| **Styling** | Tailwind CSS / Material UI (optional) |
| **State Management** | Redux Toolkit or Context API |
| **Authentication** | AWS Cognito (User Pools) |
| **API Communication** | Axios / Fetch with AWS API Gateway |
| **Hosting** | AWS S3 (static site) + CloudFront (CDN) |
| **Environment Management** | Vite `.env` files |
| **Build & Deployment** | CI/CD via GitHub Actions + AWS CLI / CDK Stack |

---

## 📁 Project Structure

```
.
├── src/
│   ├── components/           # Reusable UI components (Navbar, Player, etc.)
│   ├── pages/                # Main pages (Login, Discover, Feed, Admin)
│   ├── services/             # API and Cognito integration logic
│   ├── hooks/                # Custom React hooks
│   ├── assets/               # Static images and icons
│   ├── App.tsx               # Root component
│   └── main.tsx              # Application entry point
├── .env                      # Environment variables for API endpoints
├── tsconfig.json
├── vite.config.ts
├── package.json
└── README.md
```

---

## ⚙️ Setup & Development

### 1️⃣ Clone and install dependencies
```bash
git clone https://github.com/your-username/cloud-music-platform-frontend.git
cd cloud-music-platform-frontend
npm install
```

### 2️⃣ Create environment variables
Create a `.env` file in the project root:
```bash
VITE_API_BASE_URL=https://your-api-gateway-id.execute-api.eu-central-1.amazonaws.com/prod
VITE_COGNITO_CLIENT_ID=your_cognito_client_id
VITE_COGNITO_USER_POOL_ID=your_user_pool_id
VITE_REGION=eu-central-1
```

### 3️⃣ Run the development server
```bash
npm run dev
```
Then open [http://localhost:5173](http://localhost:5173) in your browser.

### 4️⃣ Build for production
```bash
npm run build
```

### 5️⃣ Preview production build locally
```bash
npm run preview
```

---

## ☁️ Deployment on AWS

### Option 1: S3 + CloudFront
1. Build the project  
   ```bash
   npm run build
   ```
2. Upload the contents of `dist/` to your **S3 bucket**  
3. Enable static hosting and connect the bucket to a **CloudFront distribution**

Guide: [Host React app on S3 + CloudFront](https://jayanttripathy.com/how-to-host-angular-app-on-aws-s3-bucket-using-cloudfront/)

### Option 2: Automated Deployment (CI/CD)
Integrate with **GitHub Actions** or **AWS CodePipeline** to automatically deploy on push:
- [AWS GitHub Actions – CI/CD to EC2 or S3](https://aws.amazon.com/blogs/devops/integrating-with-github-actions-ci-cd-pipeline-to-deploy-a-web-app-to-amazon-ec2/)

---

## 🔍 Linting & Code Quality

The project includes ESLint and TypeScript type-aware linting rules.

To expand lint configuration, you can enable stricter type checks:
```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      ...tseslint.configs.recommendedTypeChecked,
      ...tseslint.configs.strictTypeChecked,
      ...tseslint.configs.stylisticTypeChecked,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
    },
  },
])
```

For React-specific lint rules, install:
```bash
npm install eslint-plugin-react-x eslint-plugin-react-dom --save-dev
```

---

## 🧠 Notes

- Tokens and authentication are handled by **Cognito** (not locally stored manually).  
- All requests are routed through **AWS API Gateway**.  
- The frontend mirrors backend logic defined in your **AWS CDK** stack.  
- Avoid direct calls to AWS SDK from the browser—use secure APIs instead.  

---

## 👩‍💻 Team
**Role:** Frontend Developer – Team Member  
**Technologies:** React, TypeScript, Vite, AWS Cognito, API Gateway, S3, CloudFront  
