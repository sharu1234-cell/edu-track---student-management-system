# Commands to Run - Where and When

## ✅ Commands to Run in YOUR CURRENT TERMINAL

These commands run in your PowerShell/Command Prompt (the terminal you're using now):

### Step 1: Install Project Dependencies
```bash
npm install
```
**Run this in:** Your current terminal (project folder)

### Step 2: After MySQL is Running - Create Database Tables
```bash
npm run migrate
```
**Run this in:** Your current terminal (project folder)

### Step 3: Add Sample Data (Optional)
```bash
npm run seed
```
**Run this in:** Your current terminal (project folder)

### Step 4: Start Your Project Server
```bash
npm run dev
```
**Run this in:** Your current terminal (project folder)

---

## ❌ NOT Run in Terminal (These are Windows/GUI)

### XAMPP Installation
- **NOT a terminal command**
- Download installer from website
- Double-click `.exe` file to install
- This is a Windows installer, not a command

### Starting MySQL
- **NOT a terminal command**
- Open XAMPP Control Panel (Windows app from Start Menu)
- Click "Start" button next to MySQL
- This is done in a GUI window, not terminal

---

## 📋 Complete Step-by-Step Process

### Part 1: Install XAMPP (NOT in Terminal)
1. Download XAMPP installer from website
2. Double-click installer file
3. Follow installation wizard
4. **No terminal commands needed here**

### Part 2: Start MySQL (NOT in Terminal)
1. Open "XAMPP Control Panel" from Start Menu
2. Click "Start" button for MySQL
3. **No terminal commands needed here**

### Part 3: Configure Project (IN YOUR TERMINAL)
1. Make sure you're in project folder:
   ```bash
   cd "C:\Users\SHARVANI\BK project1"
   ```

2. Create `.env` file (you can use notepad or any text editor):
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=
   DB_NAME=edutrack
   DB_PORT=3306
   JWT_SECRET=my_secret_key_12345
   PORT=3000
   ```

3. **Run in terminal:**
   ```bash
   npm install
   ```

4. **Run in terminal:**
   ```bash
   npm run migrate
   ```

5. **Run in terminal (optional):**
   ```bash
   npm run seed
   ```

6. **Run in terminal:**
   ```bash
   npm run dev
   ```

---

## 🎯 Quick Reference

| Action | Where to Do It | Command/Action |
|--------|---------------|----------------|
| Install XAMPP | Windows (Download & Install) | Double-click installer |
| Start MySQL | XAMPP Control Panel (GUI) | Click "Start" button |
| Install dependencies | **Your Terminal** ✅ | `npm install` |
| Create database | **Your Terminal** ✅ | `npm run migrate` |
| Add sample data | **Your Terminal** ✅ | `npm run seed` |
| Start server | **Your Terminal** ✅ | `npm run dev` |

---

## ✅ Summary

**In Your Current Terminal, You Need to Run:**
1. ✅ `npm install` - Install project packages
2. ✅ `npm run migrate` - Create database tables (after MySQL is running)
3. ✅ `npm run seed` - Add sample data (optional)
4. ✅ `npm run dev` - Start the server

**NOT in Terminal:**
- ❌ Installing XAMPP (Windows installer)
- ❌ Starting MySQL (XAMPP Control Panel GUI)

---

## 🚀 Ready to Start?

Since you're already in the project folder, you can start with:

```bash
npm install
```

But first, make sure:
1. XAMPP is installed
2. MySQL is started in XAMPP Control Panel
3. `.env` file is created with MySQL settings

Then run the terminal commands above! ✅



