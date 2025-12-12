# XAMPP Setup Guide for EduTrack

## 📋 What is XAMPP?

XAMPP is a **Windows application** (desktop program) that includes:
- MySQL (database server)
- phpMyAdmin (optional - web-based database manager)
- Apache (web server - not needed for our project)

## 🖥️ Where to Run XAMPP?

**XAMPP runs on Windows (your computer), NOT in the browser.**

### Step-by-Step:

## Step 1: Download XAMPP (Windows Application)

1. Go to: https://www.apachefriends.org/download.html
2. Click "Download" for Windows
3. Save the installer file (e.g., `xampp-windows-x64-8.2.12-installer.exe`)

## Step 2: Install XAMPP (Windows Installer)

1. **Double-click the downloaded installer file**
2. Click "Next" through the installation wizard
3. Choose installation location (default: `C:\xampp`)
4. **Select components:** Make sure **MySQL** is checked ✅
5. Click "Install"
6. Wait for installation to complete
7. Click "Finish"

## Step 3: Open XAMPP Control Panel (Windows Application)

1. **Open Start Menu** (Windows key)
2. Search for **"XAMPP Control Panel"**
3. **Click to open** (it's a Windows desktop application, NOT a browser)

You'll see a window like this:
```
┌─────────────────────────────────────┐
│  XAMPP Control Panel v3.x.x        │
├─────────────────────────────────────┤
│  Apache    [Start] [Stop] [Admin]   │
│  MySQL     [Start] [Stop] [Admin]   │
│  FileZilla [Start] [Stop] [Admin]   │
│  Mercury   [Start] [Stop] [Admin]   │
└─────────────────────────────────────┘
```

## Step 4: Start MySQL (In XAMPP Control Panel)

1. In the XAMPP Control Panel window
2. Find the **MySQL** row
3. Click the **"Start"** button
4. MySQL status should turn **green** ✅
5. You'll see "MySQL" in green text

**That's it! MySQL is now running on your computer.**

## Step 5: Configure Your Project

1. **Create `.env` file** in your project folder:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=          (leave empty - XAMPP default has no password)
   DB_NAME=edutrack
   DB_PORT=3306
   JWT_SECRET=my_secret_key_12345
   PORT=3000
   ```

2. **Run migrations:**
   ```bash
   npm run migrate
   ```

3. **Start your Node.js server:**
   ```bash
   npm run dev
   ```

## 🌐 phpMyAdmin (Optional - Browser Tool)

**phpMyAdmin is a BROWSER tool** (optional, not required):
- It's a web interface to manage MySQL databases
- Access it at: `http://localhost/phpmyadmin`
- You can view/edit databases here if you want
- **But you don't need it for the project to work!**

## 📊 Summary

| Component | Where It Runs | Required? |
|-----------|---------------|-----------|
| **XAMPP Control Panel** | Windows (Desktop App) | ✅ Yes - to start MySQL |
| **MySQL Server** | Windows (Background Service) | ✅ Yes - for database |
| **phpMyAdmin** | Browser (Optional Tool) | ❌ No - just for viewing DB |
| **Your Node.js Project** | Windows (Terminal/Command Prompt) | ✅ Yes - your API server |

## ✅ Quick Checklist

- [ ] Download XAMPP installer
- [ ] Install XAMPP on Windows
- [ ] Open XAMPP Control Panel (Windows app)
- [ ] Click "Start" next to MySQL
- [ ] MySQL shows green/running status
- [ ] Create `.env` file with MySQL settings
- [ ] Run `npm run migrate`
- [ ] Run `npm run dev`
- [ ] Access API at `http://localhost:3000/api-docs`

## 🎯 Important Points

1. **XAMPP = Windows Application** (not browser)
2. **Control Panel = Desktop Window** (not website)
3. **MySQL = Background Service** (runs on your computer)
4. **Your Project = Runs in Terminal** (not in browser)
5. **API Documentation = Browser** (http://localhost:3000/api-docs)

---

**In Simple Terms:**
- Install XAMPP on Windows ✅
- Open XAMPP Control Panel (Windows app) ✅
- Click Start for MySQL ✅
- MySQL runs in background ✅
- Your Node.js project connects to it ✅



