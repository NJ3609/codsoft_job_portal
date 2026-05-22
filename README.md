# Fullstack Job Portal

A full-featured, modern job board application built with a React frontend and an Express/Node.js backend. This project is structured as a monorepo, making it easy to run locally or deploy to hosting platforms like Render.

---

## 🚀 Key Features

*   **Candidate Dashboard**:
    *   Search and filter jobs by keyword, location, and type (Full-Time, Part-Time, Remote, etc.).
    *   Apply for jobs with a custom cover letter and resume upload.
    *   Track the status of submitted applications (Applied, Reviewed, Interviewing, Accepted, Rejected).
    *   Manage and update candidate profiles (bio, skills, education, and experience).
*   **Employer Dashboard**:
    *   Post new job listings with descriptions and requirements.
    *   Manage posted jobs and view all incoming candidate applications.
    *   Review candidate details, download resumes, and update application statuses.
*   **Authentication & Security**:
    *   Secure user authentication using JSON Web Tokens (JWT) and bcrypt password hashing.
    *   Role-based access control (Employer vs. Candidate).
*   **Database Integration**:
    *   Uses a PostgreSQL database in production with automatic fallback to a local SQLite database (`jobboard.db`) for easy local development.

---

## 📁 Repository Structure

```text
├── backend/               # Node.js + Express API server
│   ├── db.js              # Database client (PostgreSQL / SQLite fallback)
│   ├── index.js           # Server entry point & API endpoints
│   ├── middleware/        # Authentication & file upload middleware
│   └── services/          # Email notifications service
├── frontend/              # React + Vite client application
│   ├── src/               # React components, pages, and context
│   └── vite.config.js     # Vite configuration
├── package.json           # Root package manager for monorepo tasks
└── README.md              # Project documentation
```

---

## 🛠️ Local Development Setup

### Prerequisites
*   Node.js (v18 or higher)
*   npm (v9 or higher)

### Setup Steps
1.  **Clone the repository**:
    ```bash
    git clone https://github.com/NJ3609/codsoft_job_portal.git
    cd codsoft_job_portal
    ```

2.  **Install dependencies and build the frontend**:
    Use the root scripts to install dependencies for both the frontend and backend with a single command:
    ```bash
    npm run build
    ```

3.  **Configure environment variables**:
    Create a `.env` file in the `backend/` directory:
    ```ini
    PORT=5000
    JWT_SECRET=your_super_secret_jwt_key
    
    # Optional Database (Default falls back to SQLite)
    # DB_USER=postgres
    # DB_HOST=localhost
    # DB_NAME=jobboard
    # DB_PASS=root
    # DB_PORT=5432
    ```

4.  **Run the application**:
    *   **Development mode** (runs both separately):
        *   In one terminal, start the backend:
            ```bash
            cd backend
            npm run dev
            ```
        *   In another terminal, start the frontend:
            ```bash
            cd frontend
            npm run dev
            ```
    *   **Production mode** (serves the React build statically from the Express server):
        ```bash
        npm start
        ```

---

## ☁️ Deployment on Render

This repository is optimized for deployment as a single **Web Service** on Render's free tier. 

### Render Web Service Configuration:
*   **Build Command**: `npm run build`
*   **Start Command**: `npm start`
*   **Root Directory**: (Leave blank - defaults to `/`)
*   **Environment Variables**:
    *   `NODE_ENV`: `production`
    *   `JWT_SECRET`: *[A secure random string]*
    *   `DATABASE_URL`: *[Your PostgreSQL connection string]*
    *   `VITE_API_URL`: `/api`
