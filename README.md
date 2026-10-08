# Personal Portfolio Website

This project is a personal portfolio website built for showcasing a developer profile, skills, selected projects, and a contact form. The frontend is implemented with React and Vite, while the backend is a lightweight Express server that exposes project data and receives contact submissions.

## Overview

This portfolio application presents a single-page profile for Tanvir Tahsin. It includes sections for an introduction, skills overview, project highlights, and a contact form. The frontend fetches project information from a backend API, and the backend validates and logs submitted messages.

The system is structured as a simple client-server application:

- The frontend displays the portfolio interface and renders project cards.
- The backend serves project data and handles contact form requests.
- The project currently uses in-memory data instead of a persistent database.

## Features

- Responsive portfolio landing page with navigation
- About section describing the developer profile
- Skills section listing technical competencies
- Projects section rendered from API data
- Contact form for name, email, and message submission
- Success and validation messages from the backend
- Print-to-PDF CV button

## Technology Stack

| Technology | Purpose |
| ---------- | ------- |
| React | Frontend UI |
| Vite | Frontend build and development tooling |
| JavaScript | Client-side logic |
| CSS | Styling and layout |
| Express | Backend API server |
| Node.js | JavaScript runtime for the server |
| CORS | Cross-origin request handling |

## Project Structure

```text
412_Task_1/
├── .gitignore
├── README.md
├── client/
│   └── client/
│       └── Portfolio/
│           ├── index.html
│           ├── package.json
│           ├── vite.config.js
│           ├── public/
│           │   ├── favicon.svg
│           │   └── icons.svg
│           └── src/
│               ├── App.jsx
│               ├── App.css
│               ├── index.css
│               ├── main.jsx
│               └── assets/
│                   ├── hero.png
│                   ├── react.svg
│                   └── vite.svg
└── server/
    ├── index.js
    ├── package.json
    └── package-lock.json
```

### Key files

- `client/client/Portfolio/src/App.jsx` defines the portfolio UI and contact form logic.
- `server/index.js` implements the Express API and in-memory project data.
- `client/client/Portfolio/package.json` configures the React/Vite frontend.
- `server/package.json` configures the Express backend.

## System Architecture

```text
Browser / User
    ↓
React Frontend
    ↓
Express API
    ↓
In-memory Project Data
```

The frontend reads the backend URL from `VITE_API_URL` when available. If no environment variable is defined, it defaults to `http://localhost:3000`.

## Installation

### 1. Install backend dependencies

```bash
cd server
npm install
```

### 2. Install frontend dependencies

```bash
cd ../client/client/Portfolio
npm install
```

## Configuration

The frontend expects an optional environment variable named `VITE_API_URL` to point to the backend server.

Example:

```bash
VITE_API_URL=http://localhost:3000
```

If this variable is not set, the application uses:

```text
http://localhost:3000
```

There is no `.env.example` file in the repository, and there is no database configuration file in the project.

## Database Setup

This project does not use a database. The backend stores the project list in an in-memory JavaScript array inside `server/index.js`:

```js
const projects = [
  { ... },
  { ... }
];
```

Because the data is not persisted, project entries are reset when the server restarts.

## Running the Project

### Start the backend

```bash
cd server
npm start
```

The backend listens on port `3000` by default.

### Start the frontend

```bash
cd client/client/Portfolio
npm run dev
```

The Vite development server starts the client, typically on port `5173`.

### Open the app

Open the local frontend URL in the browser, for example:

```text
http://localhost:5173
```

## Application Usage

1. The landing page loads the portfolio sections.
2. Users can read the About text and review the Skills list.
3. The Projects section displays project cards fetched from the API.
4. Users can submit a message through the Contact form.
5. The backend validates the request and returns a success or error response.
6. The CV button triggers the browser print dialog.

## API

The backend exposes the following endpoints.

### GET /

Returns a simple status message.

Example response:

```text
Portfolio API is running
```

### GET /projects

Returns a JSON array of project objects.

Example response:

```json
[
  {
    "id": 1,
    "title": "Portfolio Website",
    "description": "A personal portfolio built with React and Express.",
    "tech": ["React", "Express", "CSS"],
    "github": "https://github.com/yourusername/portfolio",
    "demo": "https://your-demo-link.com"
  }
]
```

### POST /contact

Accepts a JSON body with the following fields:

```json
{
  "name": "Your name",
  "email": "your@email.com",
  "message": "Your message"
}
```

Validation rules:

- `name` is required
- `email` is required
- `message` is required

Successful response:

```json
{
  "message": "Message received successfully"
}
```

Error response:

```json
{
  "error": "All fields are required"
}
```

## Authentication and Authorization

This project does not implement authentication or authorization. There is no login system, role-based access control, session management, or protected routes in the repository.

## Testing

There are no automated test files or testing scripts configured in the repository. No test suite was found in the project structure.

## Known Limitations

- Project data is stored in memory and is not persisted.
- Contact form submissions are only logged to the server console.
- The backend uses placeholder GitHub and demo links in the sample project data.
- The application does not include a database, authentication, or admin dashboard.
- The project is best suited for local development rather than production deployment.

## License

No license file was found in the repository. The project does not currently declare a license.

## Author

MD SIRAJUL ISLAM
