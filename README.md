# Open-Journal-Systems-OJS-Installation-Guide-XAMPP-macOS-
Open Journal Systems (OJS) Installation Guide — XAMPP (macOS)

This guide walks you through installing OJS locally using XAMPP on macOS. It also includes common problems and how to solve them.
✅ Prerequisites
XAMPP (PHP >= 7.4, Apache, MySQL)
Composer (optional, if using command-line tools)
OJS download from https://pkp.sfu.ca/ojs/
📦 Step-by-Step Installation
1. Download & Extract OJS
Download OJS (ZIP/TAR) from the PKP website
Extract to:
/Applications/XAMPP/xamppfiles/htdocs/ojs

3. Create MySQL Database
Go to: http://localhost/phpmyadmin
Create a new database (e.g., ojs_db)
No need to create tables manually — OJS handles that during installation
3. Set Folder Permissions
Make these folders writable:
sudo chmod -R 777 /Applications/XAMPP/xamppfiles/htdocs/ojs/cache
sudo chmod -R 777 /Applications/XAMPP/xamppfiles/htdocs/ojs/public
sudo chmod -R 777 /Applications/XAMPP/xamppfiles/htdocs/ojs/config.inc.php
⚠️ Use chmod 777 only for local dev. Use 755 and chown _www:_www for secure setups.

4. Run the Installer
Open: http://localhost/ojs

Fill in:
<img width="1439" alt="Screenshot 2025-04-29 at 12 06 33" src="https://github.com/user-attachments/assets/6778dfa1-ce92-4424-899c-93e6f2dea8db" />
<img width="1439" alt="Screenshot 2025-04-29 at 12 06 33" src="https://github.com/user-attachments/assets/dda22911-0770-4251-80ab-05a5619d6817" />
<img width="1439" alt="Screenshot 2025-04-29 at 12 06 33" src="https://github.com/user-attachments/assets/0b755cbe-11ed-43aa-8465-5d8cdfa4645b" />

Site Name
Admin Username and Password (only use alphanumeric, underscore or hyphen)
Database connection (use localhost, root, and your DB name)
Public files directory: Set to public/ inside your OJS root
6. Manual config.inc.php Save

If you see:

"The installer could not automatically overwrite the configuration file"
Do this:

Copy the config content shown on the screen.
Open terminal:
sudo nano /Applications/XAMPP/xamppfiles/htdocs/ojs/config.inc.php
Paste content.
Save (Ctrl + O, Enter, then Ctrl + X).
🚫 Common Issues and Fixes
❌ unable to write file wrtxxxxx...

Fix: Set write permissions to cache folders:

sudo chmod -R 777 /Applications/XAMPP/xamppfiles/htdocs/ojs/cache
❌ The public files directory does not exist or is not writable

Fix:

mkdir -p /Applications/XAMPP/xamppfiles/htdocs/ojs/public
sudo chmod -R 777 /Applications/XAMPP/xamppfiles/htdocs/ojs/public
❌ phpMyAdmin error: Access denied for user 'root'@'localhost' (using password: NO)

Fix:
<img width="1439" alt="Screenshot 2025-04-29 at 12 06 33" src="https://github.com/user-attachments/assets/415b5121-b52b-4674-940c-5361869b711f" />
Open:
sudo nano /Applications/XAMPP/xamppfiles/phpmyadmin/config.inc.php
Ensure:
$cfg['Servers'][$i]['auth_type'] = 'cookie';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '';
If your MySQL root user has a password, update it here.

✅ Post-Installation
Log in: http://localhost/ojs
Username: the one you set during installation
Configure journal, users, and settings
📂 Recommended .gitignore (if versioning)
/public/
/cache/
/files/
/config.inc.php
<img width="1439" alt="Screenshot 2025-04-29 at 12 30 10" src="https://github.com/user-attachments/assets/df1d7764-355c-44ae-b5ba-c27c7401fb54" />

<img width="1439" alt="Screenshot 2025-04-29 at 12 29 18" src="https://github.com/user-attachments/assets/87d55ff9-6b11-4b9b-81a8-a90b35926a8c" />
