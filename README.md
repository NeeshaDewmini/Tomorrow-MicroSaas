# Tomorrow-MicroSaas

Welcome to UniTime — a lightweight, efficient Micro SaaS application designed to help users manage their tasks, schedules, and events seamlessly, powered by modern Firebase backend and advanced DevOps practices.

Table of Contents

About the Project
Features
Tech Stack
Project Structure
Setup & Installation
Deployment
Documentation


About the Project
 
Tomorrow is a Micro SaaS application built for students, professionals, and anyone who wants an organized way to:

Manage their daily tasks 
Visualize schedules via a dynamic calendar 
Track important deadlines and completion statistics 


Features

 Add, edit, and delete tasks
 Dynamic calendar with task highlighting
 Mark important (high-priority) tasks
 Real-time statistics (Completed, Pending tasks)
 Firebase Firestore integration for cloud-based task storage
 Secure Authentication using Firebase Auth
 Editable user profile settings (name, email, preferences)
 Basic notification preferences and theme settings

Tech Stack

Frontend : HTML5, CSS3, JavaScript 	
Backend: Firebase Firestore, Firebase Auth
DevOps/Tools: GitHub Actions (for CI/CD), Git, Markdown, Draw.io (for Architecture)

 
Project Structure

Tomorrow-MicroSaaS/
│
├── frontend/
│   ├── dashboard.html
│   ├── calendar.html
│   ├── tasks.html
│   ├── settings.html
│   └── style.css, script.js
│
├── docs/
│   ├── PRD.md
│   ├── TDD.md
│   ├── system-architecture.png
│   ├── runbook.md
│   
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml 
│
├── README.md
└── .gitignore


Setup & Installation

Clone the repository


cd Tomorrow-MicroSaaS

Set up Firebase

Create a Firebase Project
Enable Authentication (Email/Password)
Set up Firestore Database
Get the Firebase configuration snippet and add it inside the <script> tag in each HTML file.
Open dashboard.html in your browser!


Deployment

Hosted via Firebase Hosting
Hosting URL: https://tomorrow-32546.web.app


Documentation

All project documents are available inside /docs/ folder:

 Product Requirements Document (PRD)
 Technical Design Document (TDD)
 System Architecture Diagram
 Operations Runbook


