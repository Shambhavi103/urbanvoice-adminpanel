# UrbanVoice - Public Complaint Resolution Dashboard

UrbanVoice is a prototype public complaint resolution web application designed to help citizens easily submit and track issues with municipal authorities. The frontend is built using standard web technologies (HTML, CSS, Vanilla JavaScript) and the backend is powered by **n8n** automation workflows.

## Features

- **Secure Login (Mock)**: Access the dashboard via Phone number, Email, and OTP validation.
- **Complaint Submission**: Users can submit detailed complaints including:
  - Personal Details (Name, Phone Number)
  - Address and Description of the issue
  - Media Uploads (Images and Videos converted to Base64)
- **Real-time Tracking**: Users can track the status of existing complaints using their unique Registration ID.
- **Dynamic UI**: Glassmorphism design system for modern, aesthetic visuals. Responsive layout across desktop and multiple mobile devices.
- **n8n Backend Integration**: Integrates directly with n8n HTTP Webhook triggers to process submissions and fetch tracking statuses.

## Architecture & Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES6+), Ionicons.
- **Backend / Automation**: [n8n](https://n8n.io/) Webhooks.
- **Workflow configuration**: An n8n workflow JSON is included (`My workflow (2).json`), representing the backend logic.

## Project Structure

```text
├── index.html            // Main entry point containing the presentation layer
├── style.css             // Styling rules including variables, glassmorphism, responsive design
├── script.js             // Frontend logic handling login, uploads, and webhook communication
├── My workflow (2).json  // Exported n8n workflow for backend complaint handling
└── README.md             // Documentation (you are here)
```

## How to Run Locally

1. Clone or download this repository.
2. Open `index.html` in your favorite web browser (or serve it with a local development server like VS Code Live Server).
3. At the login screen:
   - **Mobile Number**: Enter any valid phone number format.
   - **Gmail ID**: Enter a valid `@gmail.com` email address.
   - **OTP**: Enter `1234` (Mock OTP used for validation).
4. You will be redirected to the Dashboard where you can test submitting and tracking complaints.

## Setting up n8n Webhooks

By default, this application points to test webhook URLs configured in `script.js`. To use your own backend:

1. Look for the `WEBHOOK_URL` and `TRACKING_WEBHOOK_URL` constants at the very top of `script.js`.
2. Import `My workflow (2).json` into your own n8n instance.
3. Activate your n8n workflows and retrieve your production webhook URLs.
4. Replace the URLs in `script.js` with your n8n URLs:
   ```javascript
   const WEBHOOK_URL = 'YOUR_SUBMISSION_WEBHOOK_URL';
   const TRACKING_WEBHOOK_URL = 'YOUR_TRACKING_WEBHOOK_URL';
   ```

## Development and Testing Notes

- Currently, image and video attachments are converted to Base64 on the client side before being sent to the n8n webhook inline as an API payload.
- In production applications, large files should generally be uploaded to an intermediate storage bucket (AWS S3, Google Cloud Storage, etc.) before handing off URLs to a tool like n8n.
