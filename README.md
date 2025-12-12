# EduTrack – Student Management System

## 1. Project Overview
EduTrack is a comprehensive backend system for university management, handling students, faculty, courses, enrollments, grades, and attendance. It is built with Node.js, Express, and MySQL, featuring Role-Based Access Control (RBAC) and JWT authentication.

## 2. Tech Stack
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MySQL (Relational)
- **Authentication**: JWT (JSON Web Tokens)
- **Documentation**: Swagger/OpenAPI

## 3. Setup Instructions

### Prerequisites
- Node.js (v18+)
- MySQL Server

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/edutrack.git
   cd edutrack
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Configure environment variables (`.env`):
   ```
   DB_HOST=localhost
   DB_USER=root
   DB_PASS=password
   DB_NAME=edutrack
   JWT_SECRET=your_jwt_secret
   ```
4. Run database migrations:
   ```bash
   npm run migrate
   ```
5. Start the server:
   ```bash
   npm start
   ```

## 4. API Endpoints

### Authentication
- `POST /api/auth/login` - Login user
- `POST /api/auth/register` - Register new student

### Students
- `GET /api/students` - List all students (Admin/Faculty)
- `GET /api/students/:id` - Get student details
- `POST /api/students` - Create student (Admin)
- `PUT /api/students/:id` - Update student
- `DELETE /api/students/:id` - Delete student

### Courses
- `GET /api/courses` - List courses
- `POST /api/courses` - Create course (Admin)

*(See `postman_collection.json` for full API list)*

## 5. Database Schema
The system uses a normalized 3NF schema with the following tables:
- `users` (id, email, password_hash, role)
- `students` (id, user_id, department_id, ...)
- `faculty` (id, user_id, department_id, ...)
- `courses` (id, code, title, credits, ...)
- `enrollments` (student_id, course_id, semester, grade)
- `attendance` (enrollment_id, date, status)

## 6. Testing
Run unit tests with:
```bash
npm test
```
