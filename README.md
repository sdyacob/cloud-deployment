# Cloud Deployment Assistant 🚀

An intelligent assistant that generates automated, scalable deployment scripts for your web applications on AWS, GCP, or Azure. Simply configure your frontend and backend, and get a production-ready shell script in seconds, powered by the Google Gemini API.

## ✨ Features

- **AI-Powered Generation**: Leverages the Google Gemini API to create custom, high-quality deployment scripts.
- **Multi-Cloud Support**: Generates scripts for Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure.
- **Serverless First**: Promotes a modern, scalable, and cost-efficient architecture using services like AWS Lambda, Google Cloud Functions, and Azure Functions.
- **Full-Stack Configuration**: Configure both frontend (static site) and backend (serverless API) deployments in one go.
- **Database Provisioning**: Optionally include database setup (PostgreSQL, MySQL, MongoDB) using managed cloud services.
- **Intuitive UI**: A clean, multi-step wizard built with React and Tailwind CSS makes configuration a breeze.
- **Developer Friendly Output**: The generated script is displayed with syntax highlighting, and can be copied to the clipboard or downloaded as a `.sh` file.

## 🛠️ Tech Stack

- **Frontend**: React, TypeScript, Tailwind CSS
- **AI Backend**: Google Gemini API (`@google/genai`)
- **Build/Setup**: The project uses a modern setup with `es-modules` and an `importmap` in `index.html`, meaning no local `npm install` is needed for React dependencies.

## 🚀 Getting Started

### Prerequisites

- A modern web browser.
- A valid Google Gemini API key.

### Running the Application

This project is a static web application and does not require a complex build process.

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2.  **Set up your API Key:**
    The application loads the Google Gemini API key from an environment variable named `API_KEY`. The execution environment where you serve the application must have this variable available. The application is designed to pick it up from `process.env.API_KEY`.

3.  **Serve the application:**
    You can use any simple static file server. A common choice is `serve`.
    ```bash
    # If you don't have serve, install it globally
    npm install -g serve

    # Run the server from the project root
    serve
    ```
    The application will now be running, typically at `http://localhost:3000`.

## 📂 Project Structure

```
/
├── components/
│   ├── common/         # Reusable components (Button, Input, Card, etc.)
│   ├── icons/          # SVG icon components
│   └── steps/          # Components for each step of the wizard
├── services/
│   └── geminiService.ts # Logic for communicating with the Gemini API
├── App.tsx             # Main application component, state management
├── constants.ts        # Application-wide constants (e.g., form options)
├── index.html          # HTML entry point with importmap
├── index.tsx           # React root renderer
├── metadata.json       # Application metadata
├── README.md           # You are here!
└── types.ts            # TypeScript type definitions
```

## How It Works

The application guides the user through a series of steps to gather their deployment requirements. Once the configuration is reviewed and submitted:

1.  The `geminiService.ts` file constructs a detailed, highly-specific prompt based on the user's choices.
2.  This prompt instructs the Gemini model to act as a DevOps expert and generate a bash script that adheres to best practices like modular functions, security, and clear user feedback.
3.  The raw script response from the API is streamed back to the frontend.
4.  The `ResultStep.tsx` component displays the script, applying custom syntax highlighting and providing copy/download actions for the user.
