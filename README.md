# EduTrack - Student Management System

A comprehensive backend system for managing student records, course enrollments, grades, and attendance in educational institutions. Built with Node.js, Express.js, and MySQL.

## 🚀 Features

### Core Functionalities
- **User Management System**
  - Student registration and profile management
  - Faculty account creation with department association
  - Administrator dashboard with system oversight
  - Secure authentication with password hashing

- **Academic Management**
  - Course creation and management
  - Student enrollment in multiple courses
  - Grade entry and calculation system
  - Attendance tracking with date/time stamps

- **Reporting & Analytics**
  - Student performance reports (individual & class)
  - Course-wise analytics and statistics
  - Attendance reports with filtering options
  - Export functionality (JSON/CSV formats)

- **Database Design**
  - 9 normalized tables with proper relationships
  - Proper indexing for performance optimization
  - Data validation and constraints
  - Migration scripts for database setup

### Bonus Features
- ✅ Email notifications for grade updates
- ✅ Advanced search and filtering capabilities
- ✅ Real-time dashboard with charts
- ✅ Two-factor authentication (2FA) implementation
- ✅ Swagger/OpenAPI documentation

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v14 or higher)
- **MySQL** (v8.0 or higher)
- **npm** or **yarn** package manager
- **Git** (for version control)

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd "BK project1"
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Database Setup

#### Create MySQL Database

1. Login to MySQL:
```bash
mysql -u root -p
```

2. The database will be created automatically when you run migrations, or you can create it manually:
```sql
CREATE DATABASE edutrack;
```

#### Configure Environment Variables

1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Edit `.env` file with your database credentials and other settings:
```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database Configuration
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=edutrack
DB_PORT=3306

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRE=7d

# Email Configuration (for notifications)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:3001
```

**Important:** 
- Change `JWT_SECRET` to a strong random string in production
- For Gmail, you'll need to generate an [App Password](https://support.google.com/accounts/answer/185833) for `EMAIL_PASS`

#### Run Database Migrations

```bash
npm run migrate
```

This will create all necessary tables with proper relationships and indexes.

#### Seed Sample Data (Optional)

```bash
npm run seed
```

This will create sample users, courses, and enrollments for testing.

**Default Login Credentials:**
- **Admin:** `admin@edutrack.edu` / `password123`
- **Faculty:** `faculty1@edutrack.edu` / `password123`
- **Student:** `student1@edutrack.edu` / `password123`

## 🚀 Running the Application

### Development Mode

```bash
npm run dev
```

The server will start on `http://localhost:3000` (or the port specified in `.env`).

### Production Mode

```bash
npm start
```

## 📚 API Documentation

Once the server is running, access the Swagger API documentation at:

```
http://localhost:3000/api-docs
```

The documentation includes:
- All available endpoints
- Request/response schemas
- Authentication requirements
- Example requests

## 🔐 Authentication

### Register a New User

```bash
POST /api/auth/register
Content-Type: application/json

{
  "email": "student@example.com",
  "password": "password123",
  "firstName": "John",
  "lastName": "Doe",
  "role": "student"
}
```

### Login

```bash
POST /api/auth/login
Content-Type: application/json

{
  "email": "student@example.com",
  "password": "password123"
}
```

Response includes a JWT token that should be used in subsequent requests:

```json
{
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { ... }
}
```

### Using the Token

Include the token in the Authorization header:

```
Authorization: Bearer <your-token>
```

## 📖 API Endpoints Overview

### Authentication (`/api/auth`)
- `POST /register` - Register new user
- `POST /login` - User login
- `GET /me` - Get current user profile
- `POST /change-password` - Change password
- `GET /2fa/setup` - Setup two-factor authentication
- `POST /2fa/enable` - Enable 2FA
- `POST /2fa/disable` - Disable 2FA

### Users (`/api/users`)
- `GET /` - Get all users (Admin only)
- `GET /students` - Get all students
- `GET /faculty` - Get all faculty
- `GET /:id` - Get user by ID
- `PUT /:id` - Update user profile
- `POST /:id/activate` - Activate/deactivate user (Admin only)

### Courses (`/api/courses`)
- `GET /` - Get all courses (with filtering)
- `GET /:id` - Get course by ID
- `POST /` - Create course (Admin/Faculty)
- `PUT /:id` - Update course (Admin/Faculty)
- `DELETE /:id` - Delete course (Admin only)
- `GET /departments/all` - Get all departments

### Enrollments (`/api/enrollments`)
- `GET /` - Get enrollments
- `POST /` - Create enrollment
- `PUT /:id` - Update enrollment status
- `DELETE /:id` - Delete enrollment (Admin only)

### Grades (`/api/grades`)
- `GET /` - Get grades
- `POST /` - Create/update grade (Faculty/Admin)
- `DELETE /:id` - Delete grade (Admin only)

### Attendance (`/api/attendance`)
- `GET /` - Get attendance records
- `POST /` - Mark attendance (Faculty/Admin)
- `POST /bulk` - Bulk mark attendance
- `DELETE /:id` - Delete attendance record (Admin only)

### Reports (`/api/reports`)
- `GET /student/:studentId` - Get student performance report
- `GET /course/:courseId` - Get course analytics report
- `GET /class/:courseId` - Get class performance report
- `GET /export/student/:studentId` - Export student report (CSV/JSON)

### Dashboard (`/api/dashboard`)
- `GET /stats` - Get dashboard statistics
- `GET /recent-activities` - Get recent activities
- `GET /charts/grade-distribution` - Get grade distribution chart data
- `GET /charts/attendance-trend` - Get attendance trend chart data

## 🗄️ Database Schema

The database consists of 9 main tables:

1. **users** - Base user table (students, faculty, admins)
2. **departments** - Department information
3. **students** - Student-specific information
4. **faculty** - Faculty-specific information
5. **courses** - Course information
6. **enrollments** - Student course enrollments
7. **grades** - Student grades
8. **attendance** - Attendance records
9. **audit_logs** - System audit trail

All tables are properly normalized with foreign key relationships and indexes for optimal performance.

## 🔒 Security Features

- **Password Hashing:** All passwords are hashed using bcrypt
- **JWT Authentication:** Secure token-based authentication
- **Role-Based Access Control:** Different permissions for students, faculty, and admins
- **Two-Factor Authentication:** Optional 2FA support using TOTP
- **Input Validation:** Request validation using express-validator
- **SQL Injection Protection:** Parameterized queries using mysql2

## 📧 Email Notifications

The system sends email notifications for:
- Grade updates
- Course enrollment confirmations

Configure email settings in `.env` file. For Gmail:
1. Enable 2-Step Verification
2. Generate an App Password
3. Use the App Password in `EMAIL_PASS`

## 🧪 Testing the API

You can test the API using:
- **Swagger UI:** `http://localhost:3000/api-docs`
- **Postman:** Import the API endpoints
- **cURL:** Command-line tool
- **Thunder Client:** VS Code extension

### Example cURL Request

```bash
# Login
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"student1@edutrack.edu","password":"password123"}'

# Get courses (with token)
curl -X GET http://localhost:3000/api/courses \
  -H "Authorization: Bearer <your-token>"
```

## 📁 Project Structure

```
BK project1/
├── config/
│   └── database.js          # Database connection pool
├── middleware/
│   ├── auth.js              # Authentication & authorization
│   └── validation.js        # Request validation
├── migrations/
│   ├── schema.sql           # Database schema
│   ├── runMigrations.js     # Migration runner
│   └── seedData.js          # Sample data seeder
├── routes/
│   ├── auth.js              # Authentication routes
│   ├── users.js             # User management routes
│   ├── courses.js           # Course routes
│   ├── enrollments.js       # Enrollment routes
│   ├── grades.js            # Grade routes
│   ├── attendance.js        # Attendance routes
│   ├── reports.js           # Report routes
│   └── dashboard.js         # Dashboard routes
├── utils/
│   ├── emailService.js      # Email notification service
│   ├── twoFactorAuth.js     # 2FA utilities
│   └── reportGenerator.js   # Report generation utilities
├── reports/                 # Generated report files
├── .env.example            # Environment variables template
├── .gitignore             # Git ignore file
├── package.json           # Dependencies and scripts
├── server.js              # Express server setup
└── README.md              # This file
```

## 🐛 Troubleshooting

### Database Connection Issues
- Verify MySQL is running: `mysql -u root -p`
- Check database credentials in `.env`
- Ensure database exists: `SHOW DATABASES;`

### Port Already in Use
- Change `PORT` in `.env` file
- Or kill the process using the port

### Email Not Sending
- Verify email credentials in `.env`
- For Gmail, ensure App Password is used
- Check email service logs in console

### Migration Errors
- Ensure MySQL user has CREATE privileges
- Drop and recreate database if needed
- Check for existing tables

## 📝 License

This project is created for educational purposes.

## 👥 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For issues and questions:
- Check the API documentation at `/api-docs`
- Review the error messages in the console
- Check database connection and configuration

## 🎯 Future Enhancements

Potential improvements:
- Automated report generation scheduling
- Real-time notifications using WebSockets
- File upload for bulk operations
- Advanced analytics and machine learning insights
- Mobile app API support
- Integration with external systems

---

**Built with ❤️ for educational institutions**




