# Sorce Jobs Clone - Job Application Platform

A full-featured job application platform that allows job seekers to upload resumes, search for jobs, auto-apply to positions, and track applications with email notifications.

## 🚀 Features

### For Job Seekers
- User registration and authentication
- Resume upload and management
- Job search and filtering
- One-click job auto-apply
- Application tracking dashboard
- Email notifications for application status
- Application history

### For Employers
- Post job listings
- View applications
- Application management dashboard
- Candidate profile viewing

### System Features
- Automated email notifications (confirmations, status updates)
- Resume parsing and validation
- Job auto-apply with auto-fill capability
- Application submission tracking
- Real-time application status updates

## 📋 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Redux** for state management
- **Axios** for API calls
- **Tailwind CSS** for styling
- **React Router** for navigation

### Backend
- **Node.js** with Express.js
- **PostgreSQL** for database
- **Sequelize** as ORM
- **JWT** for authentication
- **Multer** for file uploads
- **Nodemailer** for email services
- **dotenv** for environment variables

### Database
- PostgreSQL with Sequelize migrations

### Email Service
- Nodemailer integration (Gmail/SendGrid compatible)

## 📁 Project Structure

```
sorce-jobs-clone/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── services/
│   │   ├── utils/
│   │   └── app.js
│   ├── migrations/
│   ├── .env.example
│   ├── package.json
│   └── server.js
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── redux/
│   │   ├── services/
│   │   ├── App.tsx
│   │   └── index.tsx
│   ├── public/
│   ├── package.json
│   └── tsconfig.json
└── README.md
```

## 🔧 Installation

### Backend Setup
```bash
cd backend
npm install
cp .env.example .env
# Configure your .env file with database and email credentials
npm run migrate
npm start
```

### Frontend Setup
```bash
cd frontend
npm install
npm start
```

## 🌐 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user

### Resumes
- `GET /api/resumes` - Get user resumes
- `POST /api/resumes/upload` - Upload resume
- `DELETE /api/resumes/:id` - Delete resume

### Jobs
- `GET /api/jobs` - Get all jobs
- `GET /api/jobs/:id` - Get job details
- `POST /api/jobs` - Create job (employer)
- `PUT /api/jobs/:id` - Update job (employer)

### Applications
- `POST /api/applications/apply` - Apply to job
- `POST /api/applications/auto-apply` - Auto-apply to jobs
- `GET /api/applications` - Get user applications
- `GET /api/applications/:id` - Get application details
- `PUT /api/applications/:id/status` - Update application status

### Email
- `POST /api/email/send-verification` - Send verification email
- `POST /api/email/send-status-update` - Send application status email

## 🔑 Environment Variables

```
# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=sorce_jobs
DB_USER=postgres
DB_PASSWORD=your_password

# JWT
JWT_SECRET=your_secret_key
JWT_EXPIRE=7d

# Email
EMAIL_SERVICE=gmail
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_password
EMAIL_FROM=noreply@sorce-jobs.com

# File Upload
MAX_FILE_SIZE=5242880
UPLOAD_DIR=./uploads

# App
PORT=5000
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

## 📚 Database Schema

### Users Table
- id (PK)
- email (unique)
- password (hashed)
- firstName
- lastName
- userType (job_seeker | employer)
- profilePicture
- bio
- location
- createdAt
- updatedAt

### Resumes Table
- id (PK)
- userId (FK)
- filename
- fileUrl
- uploadDate
- isPrimary
- createdAt

### Jobs Table
- id (PK)
- employerId (FK)
- title
- description
- requirements
- salary
- location
- jobType (full-time | part-time | contract)
- status (open | closed)
- createdAt
- expiresAt

### Applications Table
- id (PK)
- userId (FK)
- jobId (FK)
- resumeId (FK)
- status (pending | accepted | rejected | withdrawn)
- appliedDate
- updatedDate
- autoApplied (boolean)
- createdAt

### JobAutoApplySettings Table
- id (PK)
- userId (FK)
- keywords
- locations
- jobTypes
- salaryMin
- salaryMax
- isEnabled
- createdAt
- updatedAt

## 🚀 Getting Started

1. Clone the repository
2. Set up PostgreSQL database
3. Install backend dependencies and configure .env
4. Run database migrations
5. Start the backend server
6. Install frontend dependencies
7. Start the frontend dev server
8. Navigate to http://localhost:3000

## 📧 Email Features

- Application confirmation emails
- Job application status updates (accepted/rejected)
- Daily job recommendations
- Account verification emails
- Password reset emails

## 🔒 Security Features

- JWT-based authentication
- Password hashing with bcryptjs
- File upload validation
- SQL injection prevention with Sequelize
- CORS protection
- Rate limiting on API endpoints
- Email verification

## 📝 License

MIT License

## 👨‍💻 Contributing

Contributions are welcome! Please create a pull request with your changes.

## 📧 Support

For support, please create an issue in the repository.
