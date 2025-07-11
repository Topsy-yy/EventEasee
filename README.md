# EventEasee

A comprehensive campus event management system built with PHP and MySQL that allows students, managers, and administrators to efficiently manage and participate in campus events.

## Features

### 🎯 User Roles
- **Students**: Register for events, view event details, manage profile
- **Managers**: Create and manage events, view registrations
- **Administrators**: Approve events, manage users, system oversight

### 📅 Event Management
- Create and publish events with detailed information
- Image upload support for events
- Event approval workflow
- Real-time event registration
- Upcoming events display
- Event details view with registration capabilities

### 👥 User Management
- User registration and authentication
- Role-based access control
- User approval system for managers and admins
- Profile management
- Session management with "Remember Me" functionality

### 🔐 Security Features
- Password hashing
- SQL injection prevention with prepared statements
- Session-based authentication
- Role-based page access control

## Technology Stack

- **Backend**: PHP 7.4+
- **Database**: MySQL
- **Frontend**: HTML5, CSS3, JavaScript
- **Server**: Apache (XAMPP recommended)
- **Styling**: Custom CSS with Inter font family

## Installation

### Prerequisites
- XAMPP or similar Apache/MySQL/PHP stack
- PHP 7.4 or higher
- MySQL 5.7 or higher

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/Topsy-yy/EventEasee.git
   cd EventEasee
   ```

2. **Move to XAMPP directory**
   ```bash
   # Copy the project to your XAMPP htdocs folder
   cp -r EventEasee /xampp/htdocs/
   ```

3. **Database Setup**
   - Start XAMPP Apache and MySQL services
   - Open phpMyAdmin (http://localhost/phpmyadmin)
   - Create a new database named `eventease`
   - Import the database schema (create tables as needed)

4. **Database Configuration**
   - Update `connection.php` with your database credentials:
   ```php
   $host = "localhost";
   $username = "root";
   $password = "";
   $database = "eventease";
   ```

5. **File Permissions**
   - Ensure proper write permissions for image uploads
   - Set appropriate permissions for session files

## Database Schema

### Required Tables

#### Users Table
```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('student', 'manager', 'admin') NOT NULL,
    position VARCHAR(100),
    is_approved BOOLEAN DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Events Table
```sql
CREATE TABLE events (
    event_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(200) NOT NULL,
    description TEXT,
    date DATE NOT NULL,
    venue VARCHAR(200) NOT NULL,
    image LONGBLOB,
    user_id INT,
    is_approved BOOLEAN DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## File Structure

```
EventEasee/
├── README.md
├── index.php              # Homepage with upcoming events
├── admin.php              # Admin dashboard
├── manager.php            # Manager dashboard
├── student.php            # Student dashboard
├── register.php           # User registration/login
├── event-details.php      # Individual event details
├── all_users.php          # User management
├── header.php             # Common header component
├── footer.html            # Footer component
├── connection.php         # Database connection
├── logout.php             # Logout functionality
├── style.css              # Main stylesheet
├── EventEase.png          # Logo/branding
└── profile.png            # Default profile image
```

## Usage

### For Students
1. Register with student role
2. Browse upcoming events on homepage
3. View event details and register
4. Manage profile and registrations

### For Managers
1. Register with manager role (requires admin approval)
2. Create new events with descriptions and images
3. Manage event registrations
4. View event analytics

### For Administrators
1. Default admin account or admin-approved registration
2. Approve/reject events created by managers
3. Approve/reject manager and admin registrations
4. Manage all users and system settings
5. View comprehensive system analytics

## Key Features in Detail

### Event Registration System
- Real-time event capacity tracking
- Registration confirmation
- Event reminder system
- Registration history

### Image Upload
- Support for event banner images
- Image compression and optimization
- Secure file handling
- Base64 encoding for database storage

### Responsive Design
- Mobile-friendly interface
- Modern CSS Grid and Flexbox layouts
- Cross-browser compatibility
- Accessible design principles

## Security Considerations

- Input validation and sanitization
- Prepared statements for database queries
- Password hashing with PHP's password_hash()
- Session management and CSRF protection
- File upload security measures

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## Development Guidelines

- Follow PHP PSR standards
- Use prepared statements for all database queries
- Implement proper error handling
- Add comments for complex logic
- Test on multiple browsers and devices

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:
- Create an issue on GitHub
- Email: [ingridius.kisiwani@strathmore.edu]

## Changelog

### Version 1.0.0
- Initial release
- User authentication system
- Event management functionality
- Admin panel
- Responsive design

---

**EventEasee** - Making campus event management effortless! 🎉
