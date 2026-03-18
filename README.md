#  Bang Bros - Team Management Platform

> A cutting-edge web platform connecting talented developers with industry opportunities through intelligent team management and interview scheduling.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Running the Application](#running-the-application)
- [Environment Variables](#environment-variables)
- [API Endpoints](#api-endpoints)
- [Deployment](#deployment)
- [Team](#team)
- [Contributing](#contributing)
- [License](#license)

---

##  Overview

**Bang Bros** is an innovative platform designed to bridge the gap between exceptional developers and forward-thinking companies. Our AI-driven backend, combined with modern web technologies, provides:

- **Intelligent Team Showcase**: Display developer portfolios with rich profiles highlighting skills, projects, and achievements
- **Seamless Interview Scheduling**: Book meetings directly with team members using our intuitive booking system
- **User Authentication**: Secure signup/login with password hashing and session management
- **Real-time Data Sync**: Automatic synchronization with Google Sheets and Supabase for comprehensive record-keeping
- **Responsive Design**: Beautiful, mobile-first UI built with modern CSS and vanilla JavaScript

**Vision**: To empower developers to showcase their expertise while enabling recruiters to discover top talent effortlessly.

---

##  Key Features

###  Authentication System
- Secure user registration with bcrypt password hashing
- Account verification and duplicate email detection
- Session-based authentication with persistent login
- User profile generation with auto-generated avatars

###  Interview Scheduling
- One-click booking with team members
- Dynamic applicant selection
- Meeting type and time customization
- Direct Google Meet/Zoom link integration
- Automatic Google Sheets sync for recruiter tracking

###  Developer Profiles
- Individual portfolio showcases
- Technical skill highlights
- Project case studies and achievements
- Social media and portfolio links
- Avatar generation based on user initials

###  Data Integration
- **Supabase**: Real-time database for user accounts and booking records
- **Google Sheets API**: Automatic logging of all recruitments for analytics
- **Cross-platform**: Works seamlessly across local, staging, and production environments
- **Make.com**: It is an automation website where we integrate an automation for Gmail for the applicants 

###  User Experience
- Glassmorphism design with modern aesthetics
- Smooth animations and transitions
- Responsive grid layouts for team showcase
- Interactive navigation with profile dropdown

---

##  Tech Stack

### Backend
- **Framework**: Flask 3.0.3 (Python web framework)
- **Database**: Supabase (PostgreSQL-based)
- **Security**: bcrypt (password hashing), Flask-CORS
- **External APIs**: Google Apps Script for Sheets integration
- **Server**: Gunicorn (production) / Flask Development Server (local)
- **Deployment**: Vercel (serverless backend)

### Frontend
- **HTML5 / CSS3**: Semantic markup with modern styling
- **JavaScript (Vanilla)**: No frameworks - lightweight and fast
- **HTTP Client**: Fetch API for async operations
- **Design**: Responsive, mobile-first approach
- **Icons**: SVG-based interactive elements

### Infrastructure
- **Version Control**: Git
- **Environment Management**: python-dotenv for secrets
- **API Deployment**: Vercel with Python runtime
- **Database**: Supabase (cloud PostgreSQL)
- **Cross-Origin**: CORS enabled for localhost and production domains
- - **Make.com**: It is an automation website where we integrate an automation for Gmail for the applicants 


---

## Project Structure

```
bang bors/
├── backend/                      # Flask application
│   ├── app.py                   # Main Flask app with route handlers
│   ├── config.py                # Configuration management
│   ├── requirements.txt          # Python dependencies
│   ├── vercel.json              # Vercel deployment config
│   ├── .env                     # Environment variables (gitignored)
│   ├── api/
│   │   └── index.py             # Serverless function entry point
│   └── __pycache__/             # Python cache
│
├── frontend/                     # Static web assets
│   ├── index.html               # Home page with team showcase
│   ├── signup.html              # User registration page
│   ├── login.html               # User authentication page
│   ├── submitbooking.html       # Interview booking page
│   └── assests/                 # Images, logos, and static resources
│
└── README.md                    # Project documentation
```




##  API Endpoints

### Authentication
- `POST /signup` - Register new user
  - Form: `{ name, email, password }`
  - Response: Redirect to login

- `POST /login` - Authenticate user
  - Form: `{ email, password }`
  - Response: Sets session cookie, redirects to home

- `GET /logout` - Clear session
  - Response: Redirect to homepage

### User Data
- `GET /api/user` - Get current user info
  - Response: `{ user: { id, name, email, avatar_url } }`
  - Auth: Requires a valid session

### Booking
- `POST /submitbooking` - Schedule interview
  - Form: `{ company, applicant_name, gmail, meeting_type, meeting_time, link, notes }`
  - Actions: Saves to Supabase + syncs to Google Sheets
  - Response: `{ success: true, message: "Meeting saved" }`

### Static Files
- `GET /` - Serve home page
- `GET /<filename.html>` - Serve HTML pages
- `GET /assets/<resource>` - Serve images and assets

---

##  Database Schema (Supabase)

### Users Table
```sql
CREATE TABLE users (
  id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  password_hash TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

### Recruiter Bookings Table
```sql
create table recruiter_bookings (
  id uuid default gen_random_uuid() primary key,
  applicant_name text not null,       
  company_name text not null,                
  meeting_type text not null,        
  gmail text,
  start_time timestamp with time zone not null,
  meeting_link text,                  
  notes text,                         
  created_at timestamp with time zone default now()
)
```

---

## Team

Meet the talented developers behind Bang Bros:

| Name | Role | Expertise | Portfolio |
|---|---|---|---|
| **C.V Jagadeeshwar** | Vibe Coder & AI Full Stack Developer | Python, AI, Full-Stack | [Portfolio](https://zingy-torte-4efea5.netlify.app/) |
| **J. Santhosh** | Java Full Stack Developer | Java, Spring Boot, MySQL | [Portfolio](https://santhoshrudraportfolio.netlify.app/) |
| **Vanam Gangadhar Reddy** | Data Scientist & ML Engineer | Data Science, Analytics, ML | [Portfolio](https://gangadharportfolio-yu1i.vercel.app/) |
| **KONDAMANENI DHANUSH KUMAR NAIDU** | Python Developer | Python, Backend Development | [Portfolio](https://dhanushportfplio.vercel.app/) |

---

## Security Features

-  **Password Hashing**: bcrypt with salt generation
- **Session Management**: Flask sessions with secret keys
- **CORS Protection**: Whitelist origin domains
-**Environment Secrets**: Sensitive data in `.env` (not in repo)
- **Input Validation**: Email/password requirement checks


---



---

##  Future Roadmap

-  Email notifications on interview scheduling
-  Video interview integration (Zoom/Google Meet API)
-  User profiles with resume upload
-  Advanced filtering and search
-  Analytics dashboard for recruiters
-  Mobile app (React Native)
-  AI-powered profile recommendations
-  Payment integration for premium features

---





**Made with ❤️ by Bang Bros Team**

*Last Updated: March 17, 2026*
