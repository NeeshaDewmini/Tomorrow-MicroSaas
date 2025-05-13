🛠️ Operational Runbook – Tomorrow Micro SaaS

📌 Overview
This runbook provides a guide to operating and maintaining the Tomorrow Micro SaaS application in production. 
It includes standard procedures for deployment, monitoring, incident response, and recovery.

🔧 1. Application Overview

Name: Tomorrow
Type: Micro SaaS - Time Management Tool
Stack:

Frontend: HTML/CSS/JavaScript
Backend: Firebase (Authentication, Firestore)
CI/CD: GitHub Actions
Hosting: Firebase Hosting

🚀 2. Deployment Process

🔄 Automatic CI/CD
All changes pushed to the main branch are deployed automatically using GitHub Actions.

Workflow file: .github/workflows/deploy.yml


🛡️ 3. Monitoring & Alerts
🔍 Firebase Monitoring
Use Firebase Console → Performance Monitoring & Analytics to observe usage and performance.

🔔 Errors & Logs
Check logs via Firebase Console → Functions → Logs (if using Cloud Functions)

Or access via Firebase CLI:

bash
Copy
Edit
firebase functions:log
🔐 4. Authentication & Access Control
Firebase Authentication
All users authenticate via Firebase Auth (email/password)

Admins can be flagged in Firestore under users collection.

⚠️ 5. Incident Response Plan
Type	: Deployment failed	 
Response   : Check GitHub Actions logs for errors. Retry manually if needed.

Type	: Firebase outage	
Response   : Check Firebase Status Page

Type	: UI Bug	
Response   : Revert commit, or fix and push hotfix to main

Type	: Data inconsistency
Response   : Use Firestore Console to audit and correct documents

	
📂 6. File Structure

tomorrow/
├── .github/workflows/deploy.yml     # CI/CD pipeline
├── docs/                            # Documentation (PRD, TDD, ADR, Runbook, etc.)
├── src/                             # Frontend source files
├── index.html                       # Entry point
├── firebase.json                    # Firebase config
└── .firebaserc                      # Firebase project ID reference


📚 8. Useful Commands

| Command                         | Description                |
| ------------------------------- | -------------------------- |
| `firebase login`                | Authenticate Firebase CLI  |
| `firebase deploy`               | Deploy site to Firebase    |
| `firebase emulators:start`      | Run Firestore/Auth locally |
| `npm install -g firebase-tools` | Install Firebase CLI       |


👥 9. Contacts
Role	Contact
Developer	: N.J.Dewmini
Project Repo	: 
Firebase Site	[Deployed URL]
