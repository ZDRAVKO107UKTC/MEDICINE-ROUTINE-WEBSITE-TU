# MEDICINE-ROUTINE-WEBSITE-TU

A simple PHP & MySQL-based web application to manage medicine intake routines, track user activities, and send reminders.

## Features

- User Registration & Login
- User Profile Management
- Medicine Routine Scheduling
- Activity Log for User Actions
- Password Change Functionality
- Automatic Email Reminders via Cron Job
- Secure Session Management

## Files Overview

| File | Description |
|:----|:------------|
| `index.php` | Main dashboard displaying user medicine routines. |
| `login.php` | User login page. |
| `register.php` | User registration page. |
| `profile.php` | User profile page (update profile info, view routines). |
| `change_password.php` | Form to change the current user's password. |
| `logout.php` | Script to log out the current user. |
| `cron_notify.php` | Cron job script to send medicine reminder emails. |
| `db.php` | Database connection script. |
| `DB.sql` | Database structure and initial tables. |

## Database Structure

- **Database**: `medicine_db`
- **Tables**:
  - `users` (`id`, `username`, `email`, `age`, `password`)
  - `medicine_routines` (`id`, `user_id`, `medicine_name`, `dose`, `time_to_take`, `taken`)
  - `activity_log` (`id`, `user_id`, `action`, `timestamp`)

## Setup Instructions

1. **Clone the Repository**  
   ```bash
   git clone https://your-repo-link.git
   ```

2. **Import the Database**  
   - Open your MySQL server (phpMyAdmin or CLI).
   - Create a new database `medicine_db`.
   - Import `DB.sql` to create the necessary tables.

3. **Configure Database Connection**  
   - Edit `db.php` to match your MySQL server credentials:
     ```php
     $conn = new mysqli('localhost', 'your_username', 'your_password', 'medicine_db');
     ```

4. **Set Up Cron Job for Notifications**  
   - Schedule `cron_notify.php` to run periodically using your hosting's cron job manager.
   - Example crontab entry (every hour):
     ```bash
     0 * * * * /usr/bin/php /path/to/cron_notify.php
     ```

5. **Run Locally**
   - Start a local server (XAMPP, MAMP, WAMP, etc.)
   - Place the project inside `htdocs` (or the relevant directory).
   - Visit `http://localhost/your_project_folder/` in your browser.

## Requirements

- PHP 7.4 or higher
- MySQL 5.7 or higher
- Cron access (for email reminders)
- Mail server configured (for sending emails)

## Security Notes

- Passwords are securely hashed using PHP's `password_hash()`.
- Sessions are properly managed and destroyed on logout.
- Basic SQL injection protection via prepared statements is recommended (may need further hardening).
- Consider enabling HTTPS in production.

## Future Improvements

- Add email verification upon registration.
- Improve password reset functionality.
- Responsive frontend with Bootstrap or TailwindCSS.
- Token-based session validation.

## License

This project is open-source and free to use for educational and non-commercial purposes.
