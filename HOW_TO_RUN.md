# How to Run EduTrack Project

## 📋 Step-by-Step Guide

### Prerequisites Check
Before starting, make sure you have:
- ✅ Node.js installed (v14 or higher)
- ✅ MySQL installed and running
- ✅ npm (comes with Node.js)

**Check if installed:**
```bash
node --version
npm --version
mysql --version
```

---

## 🚀 Step 1: Install Dependencies

Open your terminal/command prompt in the project folder and run:

```bash
npm install
```

This will install all required packages (express, mysql2, jwt, etc.)

**Expected output:** Should see packages being installed without errors.

---

## 🗄️ Step 2: Setup MySQL Database

### Option A: Using MySQL Command Line

1. **Open MySQL:**
   ```bash
   mysql -u root -p
   ```
   (Enter your MySQL password when prompted)

2. **Create Database (optional - migrations will create it):**
   ```sql
   CREATE DATABASE IF NOT EXISTS edutrack;
   EXIT;
   ```

### Option B: Using MySQL Workbench or phpMyAdmin
- Create a new database named `edutrack`

---

## ⚙️ Step 3: Configure Environment Variables

1. **Check if `.env` file exists:**
   - If it doesn't exist, create one by copying `.env.example`
   - On Windows PowerShell:
     ```powershell
     Copy-Item .env.example .env
     ```
   - On Linux/Mac:
     ```bash
     cp .env.example .env
     ```

2. **Edit `.env` file** with your MySQL credentials:
   ```env
   # Database Configuration
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=your_mysql_password_here
   DB_NAME=edutrack
   DB_PORT=3306

   # JWT Secret (change this!)
   JWT_SECRET=my_super_secret_jwt_key_12345

   # Server Port
   PORT=3000
   ```

   **Important:** Replace `your_mysql_password_here` with your actual MySQL root password!

---

## 🗃️ Step 4: Run Database Migrations

This will create all the tables in your database:

```bash
npm run migrate
```

**Expected output:**
```
📦 Reading schema file...
📝 Executing SQL statements...
✅ Executed: CREATE DATABASE IF NOT EXISTS edutrack...
✅ Executed: CREATE TABLE IF NOT EXISTS users...
✅ Executed: CREATE TABLE IF NOT EXISTS departments...
...
✅ Database migration completed successfully!
```

**If you see errors:**
- Check your MySQL password in `.env`
- Make sure MySQL is running
- Ensure you have CREATE privileges

---

## 🌱 Step 5: Seed Sample Data (Optional but Recommended)

This creates sample users, courses, and enrollments for testing:

```bash
npm run seed
```

**Expected output:**
```
🌱 Starting database seeding...
📚 Inserting departments...
👤 Creating admin user...
👨‍🏫 Creating faculty users...
🎓 Creating student users...
📖 Creating courses...
📝 Enrolling students in courses...
✅ Database seeding completed successfully!
```

**Default Login Credentials Created:**
- Admin: `admin@edutrack.edu` / `password123`
- Faculty: `faculty1@edutrack.edu` / `password123`
- Student: `student1@edutrack.edu` / `password123`

---

## 🎯 Step 6: Start the Server

### Development Mode (with auto-restart):
```bash
npm run dev
```

### Production Mode:
```bash
npm start
```

**Expected output:**
```
🚀 EduTrack server running on port 3000
📚 API Documentation: http://localhost:3000/api-docs
```

**✅ Success!** Your server is now running!

---

## 🧪 Step 7: Test the API

### Option 1: Using Swagger UI (Recommended)

1. **Open your browser:**
   ```
   http://localhost:3000/api-docs
   ```

2. **Test Login:**
   - Click on `POST /api/auth/login`
   - Click "Try it out"
   - Enter:
     ```json
     {
       "email": "admin@edutrack.edu",
       "password": "password123"
     }
     ```
   - Click "Execute"
   - Copy the `token` from the response

3. **Test Authenticated Endpoint:**
   - Click on `GET /api/courses`
   - Click "Authorize" button (top right)
   - Paste your token: `Bearer <your-token>`
   - Click "Try it out" → "Execute"

### Option 2: Using cURL (Command Line)

**Login:**
```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d "{\"email\":\"admin@edutrack.edu\",\"password\":\"password123\"}"
```

**Get Courses (replace TOKEN with actual token):**
```bash
curl -X GET http://localhost:3000/api/courses \
  -H "Authorization: Bearer TOKEN"
```

### Option 3: Using Postman

1. Import the API endpoints
2. Set base URL: `http://localhost:3000`
3. Login to get token
4. Use token in Authorization header: `Bearer <token>`

---

## 📊 Step 8: Verify Everything Works

### Health Check:
```bash
curl http://localhost:3000/health
```

**Expected response:**
```json
{
  "status": "OK",
  "message": "EduTrack API is running"
}
```

### Test Endpoints:
1. ✅ Health check: `GET /health`
2. ✅ Login: `POST /api/auth/login`
3. ✅ Get courses: `GET /api/courses`
4. ✅ Get students: `GET /api/users/students`
5. ✅ Dashboard stats: `GET /api/dashboard/stats`

---

## 🐛 Troubleshooting

### Problem: "Cannot connect to database"
**Solution:**
- Check MySQL is running: `mysql -u root -p`
- Verify credentials in `.env`
- Check DB_PORT (default: 3306)

### Problem: "Port 3000 already in use"
**Solution:**
- Change PORT in `.env` to another number (e.g., 3001)
- Or kill the process using port 3000:
  ```bash
  # Windows
  netstat -ano | findstr :3000
  taskkill /PID <PID> /F
  
  # Linux/Mac
  lsof -ti:3000 | xargs kill
  ```

### Problem: "Migration failed"
**Solution:**
- Ensure database exists
- Check MySQL user has CREATE privileges
- Verify `.env` file has correct credentials

### Problem: "Module not found"
**Solution:**
- Run `npm install` again
- Delete `node_modules` folder and `package-lock.json`
- Run `npm install` fresh

### Problem: "JWT_SECRET not set"
**Solution:**
- Make sure `.env` file exists
- Add `JWT_SECRET=your_secret_key` to `.env`
- Restart the server

---

## 📝 Quick Reference

### Important URLs:
- **API Base:** `http://localhost:3000`
- **API Docs:** `http://localhost:3000/api-docs`
- **Health Check:** `http://localhost:3000/health`

### Important Commands:
```bash
npm install          # Install dependencies
npm run migrate      # Create database tables
npm run seed         # Add sample data
npm run dev          # Start development server
npm start            # Start production server
```

### Default Credentials:
- **Admin:** admin@edutrack.edu / password123
- **Faculty:** faculty1@edutrack.edu / password123
- **Student:** student1@edutrack.edu / password123

---

## ✅ Success Checklist

- [ ] Dependencies installed (`npm install`)
- [ ] `.env` file configured with MySQL credentials
- [ ] Database migrations run successfully (`npm run migrate`)
- [ ] Sample data seeded (`npm run seed`)
- [ ] Server running on port 3000
- [ ] Can access `/api-docs` in browser
- [ ] Can login and get JWT token
- [ ] Can access protected endpoints with token

---

## 🎉 You're All Set!

Your EduTrack API is now running! Start exploring the endpoints using Swagger UI at `http://localhost:3000/api-docs`

For more details, check:
- `README.md` - Full documentation
- `QUICKSTART.md` - Quick setup guide
- `PROJECT_SUMMARY.md` - Project overview




