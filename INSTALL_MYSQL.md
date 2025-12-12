# How to Install MySQL for EduTrack

## ⚠️ Important: MySQL Installation Requires Administrator Rights

## Method 1: Install via Chocolatey (If you have admin rights)

1. **Open PowerShell as Administrator:**
   - Press `Windows Key`
   - Type `PowerShell`
   - Right-click "Windows PowerShell"
   - Click "Run as Administrator"

2. **Run this command:**
   ```powershell
   choco install mysql -y
   ```

3. **After installation, start MySQL service:**
   ```powershell
   net start mysql
   ```

4. **Set root password (if needed):**
   ```powershell
   mysql -u root -p
   ```
   (First time, password might be empty - just press Enter)

---

## Method 2: Install XAMPP (Easiest - Recommended)

### Step 1: Download XAMPP
- Go to: https://www.apachefriends.org/download.html
- Download XAMPP for Windows
- Run the installer

### Step 2: Install XAMPP
- Choose installation directory (default is fine)
- Select components: **MySQL** and **phpMyAdmin**
- Complete installation

### Step 3: Start MySQL
1. Open **XAMPP Control Panel**
2. Click **Start** button next to MySQL
3. MySQL is now running!

### Step 4: Configure .env file
Use these settings in your `.env` file:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=          (leave empty for XAMPP default)
DB_NAME=edutrack
DB_PORT=3306
```

---

## Method 3: Install MySQL Standalone

### Step 1: Download MySQL Installer
- Go to: https://dev.mysql.com/downloads/installer/
- Download "MySQL Installer for Windows"
- Choose the "Full" or "Developer Default" setup

### Step 2: Run Installer
1. Run the downloaded installer
2. Choose "Developer Default" or "Server only"
3. Click "Execute" to install
4. **IMPORTANT:** During configuration:
   - Set root password (remember this!)
   - Choose "Standalone MySQL Server"
   - Port: 3306 (default)

### Step 3: Configure .env file
Use these settings in your `.env` file:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_root_password_here
DB_NAME=edutrack
DB_PORT=3306
```

---

## Method 4: Use Docker (If you have Docker installed)

```bash
docker run --name mysql-edutrack -e MYSQL_ROOT_PASSWORD=password123 -p 3306:3306 -d mysql:8.0
```

Then in `.env`:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=password123
DB_NAME=edutrack
DB_PORT=3306
```

---

## ✅ Verify MySQL Installation

After installation, test if MySQL works:

```bash
mysql --version
```

Or try to connect:
```bash
mysql -u root -p
```
(Enter your password when prompted)

---

## 🎯 Recommended: XAMPP

**For beginners, I recommend XAMPP because:**
- ✅ Easy to install
- ✅ Includes phpMyAdmin (web-based MySQL management)
- ✅ Easy to start/stop MySQL
- ✅ No complex configuration needed
- ✅ Visual control panel

---

## 📝 After MySQL is Installed

1. **Create .env file** in project root:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=your_password
   DB_NAME=edutrack
   DB_PORT=3306
   JWT_SECRET=my_secret_key_12345
   PORT=3000
   ```

2. **Run migrations:**
   ```bash
   npm run migrate
   ```

3. **Seed sample data:**
   ```bash
   npm run seed
   ```

4. **Start server:**
   ```bash
   npm run dev
   ```

---

## 🆘 Troubleshooting

**"MySQL command not found"**
- Add MySQL to PATH, or
- Use full path: `C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe`

**"Access denied"**
- Check username/password in `.env`
- For XAMPP, password is usually empty

**"Can't connect to MySQL server"**
- Make sure MySQL service is running
- Check if port 3306 is available
- Verify DB_HOST in `.env` is correct
