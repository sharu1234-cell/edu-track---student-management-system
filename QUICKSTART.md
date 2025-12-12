# Quick Start Guide - EduTrack

## 🚀 Quick Setup (5 minutes)

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Configure Database
1. Make sure MySQL is running
2. Copy `.env.example` to `.env` (if not exists)
3. Update database credentials in `.env`:
   ```env
   DB_USER=root
   DB_PASSWORD=your_mysql_password
   ```

### Step 3: Setup Database
```bash
# Create database and tables
npm run migrate

# Add sample data (optional)
npm run seed
```

### Step 4: Start Server
```bash
npm run dev
```

### Step 5: Access API Documentation
Open browser: `http://localhost:3000/api-docs`

## 🔑 Quick Test

### 1. Login as Admin
```bash
POST http://localhost:3000/api/auth/login
{
  "email": "admin@edutrack.edu",
  "password": "password123"
}
```

### 2. Get Courses
```bash
GET http://localhost:3000/api/courses
Authorization: Bearer <token-from-step-1>
```

## 📋 Default Credentials

After running `npm run seed`:

- **Admin:** admin@edutrack.edu / password123
- **Faculty:** faculty1@edutrack.edu / password123  
- **Student:** student1@edutrack.edu / password123

## 🎯 Next Steps

1. Explore API documentation at `/api-docs`
2. Test endpoints using Swagger UI
3. Check README.md for detailed documentation
4. Customize `.env` for your needs

## ⚠️ Common Issues

**Database connection failed?**
- Check MySQL is running
- Verify credentials in `.env`
- Ensure database exists

**Port 3000 already in use?**
- Change `PORT` in `.env`
- Or stop the process using port 3000

**Migration errors?**
- Ensure MySQL user has CREATE privileges
- Drop database and recreate: `DROP DATABASE edutrack;`




