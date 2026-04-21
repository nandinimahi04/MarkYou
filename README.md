# MarkYou - Smart Attendance Management System

![React](https://img.shields.io/badge/React-18.0%2B-blue)
![Flask](https://img.shields.io/badge/Flask-2.0%2B-green)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13%2B-blue)
![Docker](https://img.shields.io/badge/Docker-20.0%2B-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Stars](https://img.shields.io/github/stars/nandinimahi04/MarkYou?style=social)
![Forks](https://img.shields.io/github/forks/nandinimahi04/MarkYou?style=social)

## Overview

MarkYou is a sleek attendance management system using React and Flask. Teachers record attendance with audio and color-coded blocks, export data to Excel, and view insights by date and subject. Students track monthly analysis to meet 75% goals-all powered by a smart, animated UI.

## Features

### For Teachers
- Voice Recording: Record attendance using voice commands
- Color-Coded Interface: Visual attendance tracking with intuitive color blocks
- Real-time Analytics: Instant insights and attendance statistics
- Excel Export: Export attendance data with one click
- Calendar View: Monthly and weekly attendance overview
- Automated Notifications: Low attendance alerts for students

### For Students
- Personal Dashboard: Track personal attendance progress
- 75% Goal Tracker: Visual progress toward attendance requirements
- Mobile Responsive: Access attendance data on any device
- Email Notifications: Receive attendance updates via email
- Subject-wise Analysis: Detailed breakdown by subject

### For Administrators
- Multi-user Support: Manage teachers and students
- Institution Management: Support for multiple institutions
- Comprehensive Reports: Generate detailed attendance reports
- Role-based Access: Secure authentication and authorization
- Configurable Settings: Customize attendance rules and policies

## Tech Stack

### Frontend
- React 18: Modern UI framework with hooks
- React Router: Client-side routing
- Material-UI: Premium React component library
- Chart.js: Data visualization and analytics
- Axios: HTTP client for API calls
- Redux Toolkit: State management
- Web Speech API: Voice recognition for attendance

### Backend
- Flask: Python web framework
- Flask-SQLAlchemy: ORM for database operations
- Flask-JWT-Extended: JWT authentication
- Flask-CORS: Cross-origin resource sharing
- Flask-Mail: Email notifications
- PostgreSQL: Production database
- Redis: Session management and caching

### DevOps & Deployment
- Docker: Containerization
- Docker Compose: Multi-container orchestration
- GitHub Actions: CI/CD pipeline
- Nginx: Reverse proxy and static file serving
- Heroku/AWS: Cloud deployment options

## Project Structure

```
markyou/
|-- backend/
|   |-- app/
|   |   |-- models/
|   |   |-- routes/
|   |   |-- services/
|   |   |-- utils/
|   |-- migrations/
|   |-- tests/
|   |-- requirements.txt
|   |-- run.py
|-- frontend/
|   |-- src/
|   |   |-- components/
|   |   |-- pages/
|   |   |-- hooks/
|   |   |-- services/
|   |   |-- utils/
|   |   |-- store/
|   |-- public/
|   |-- package.json
|-- docker/
|   |-- Dockerfile.frontend
|   |-- Dockerfile.backend
|   |-- nginx.conf
|-- docs/
|-- docker-compose.yml
|-- docker-compose.prod.yml
|-- .gitignore
|-- README.md
|-- LICENSE
```

## Quick Start

### Prerequisites

- Node.js 16+ and npm
- Python 3.8+
- PostgreSQL 13+
- Docker and Docker Compose (optional)

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/nandinimahi04/MarkYou.git
   cd MarkYou
   ```

2. Backend Setup
   ```bash
   cd backend
   python -m venv venv
   
   # Windows
   venv\Scripts\activate
   
   # macOS/Linux
   source venv/bin/activate
   
   pip install -r requirements.txt
   
   # Set up environment variables
   cp .env.example .env
   # Edit .env with your configuration
   
   # Initialize database
   flask db upgrade
   python run.py
   ```

3. Frontend Setup
   ```bash
   cd frontend
   npm install
   
   # Set up environment variables
   cp .env.example .env.local
   # Edit .env.local with your API URL
   
   npm start
   ```

4. Access the application
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

### Docker Setup (Recommended)

```bash
# Development
docker-compose up -d

# Production
docker-compose -f docker-compose.prod.yml up -d
```

## Configuration

### Environment Variables

#### Backend (.env)
```env
FLASK_APP=run.py
FLASK_ENV=development
SECRET_KEY=your-secret-key-here
JWT_SECRET_KEY=your-jwt-secret-key
DATABASE_URL=postgresql://user:password@localhost:5432/markyou
MAIL_SERVER=smtp.gmail.com
MAIL_PORT=587
MAIL_USE_TLS=True
MAIL_USERNAME=your-email@gmail.com
MAIL_PASSWORD=your-app-password
```

#### Frontend (.env.local)
```env
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_ENV=development
```

## Features in Detail

### Voice Attendance Recording
- Speech Recognition: Convert speech to attendance records
- Multi-language Support: Support for multiple languages
- Accuracy: High accuracy voice recognition with noise cancellation
- Commands: Simple voice commands for marking attendance

### Analytics Dashboard
- Real-time Updates: Live attendance statistics
- Visual Charts: Interactive charts and graphs
- Trend Analysis: Attendance trends over time
- Comparative Analysis: Compare attendance across subjects/classes
- Export Options: Export reports in PDF, Excel formats

### Smart Notifications
- Email Alerts: Automated email notifications
- Threshold Alerts: Alerts when attendance falls below threshold
- Weekly Reports: Weekly attendance summaries
- Mobile Push: Push notifications for mobile users

## Testing

```bash
# Backend Tests
cd backend
python -m pytest tests/ -v --cov=app

# Frontend Tests
cd frontend
npm test
npm run test:coverage

# Integration Tests
docker-compose -f docker-compose.test.yml up --abort-on-container-exit
```

## API Documentation

### Authentication Endpoints

```http
POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout
GET /api/auth/profile
```

### Attendance Endpoints

```http
GET /api/attendance
POST /api/attendance
PUT /api/attendance/:id
DELETE /api/attendance/:id
GET /api/attendance/summary
GET /api/attendance/export
```

### User Management Endpoints

```http
GET /api/users
GET /api/users/:id
PUT /api/users/:id
GET /api/users/:id/attendance
```

## Docker Deployment

### Development Environment
```bash
docker-compose up -d
```

### Production Environment
```bash
docker-compose -f docker-compose.prod.yml up -d
```

### Environment-specific Configurations
- Development: Hot reload, debug mode, SQLite database
- Production: Optimized builds, PostgreSQL, Nginx reverse proxy

## Deployment Options

### Heroku Deployment
```bash
# Install Heroku CLI
heroku create markyou-app
heroku addons:create heroku-postgresql:hobby-dev
git push heroku main
```

### AWS Deployment
```bash
# Using AWS ECS or EC2
# See docs/AWS_DEPLOYMENT.md for detailed instructions
```

### DigitalOcean Deployment
```bash
# Using DigitalOcean App Platform
# See docs/DIGITAL_OCEAN_DEPLOYMENT.md
```

## Contributing

We welcome contributions! Please see our Contributing Guide for details.

### Development Workflow
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes
4. Add tests for new functionality
5. Run tests: `npm test` and `python -m pytest`
6. Commit changes: `git commit -m 'Add amazing feature'`
7. Push to branch: `git push origin feature/amazing-feature`
8. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Authors

- Nandini Maheshwaram - Initial work - nandinimahi04

## Acknowledgments

- Material-UI team for excellent React components
- Flask community for the amazing web framework
- Chart.js for beautiful data visualization
- All contributors and users of MarkYou

## Contact

- Email: nandini.mahi@example.com
- LinkedIn: Your LinkedIn Profile
- Portfolio: Your Portfolio Website
- Twitter: @your-twitter

## Live Demo

[Live Demo Link](https://markyou-demo.herokuapp.com)

## Roadmap

### Version 2.0 (Planned)
- Mobile Apps: Native iOS and Android applications
- AI Features: Predictive analytics for attendance patterns
- LMS Integration: Integration with popular Learning Management Systems
- Multi-language Support: Support for international users
- Advanced Analytics: More sophisticated analytics and reporting

### Version 1.5 (In Progress)
- Real-time Sync: Real-time attendance synchronization
- Video Attendance: Video-based attendance verification
- Gamification: Points and rewards for good attendance
- Email Templates: Customizable email notification templates

---

If you find this project helpful, please give it a star!

Found a bug? Report it here

Have a feature request? Let us know
