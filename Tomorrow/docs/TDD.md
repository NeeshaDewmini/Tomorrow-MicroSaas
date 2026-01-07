## 📄 Technical Design Document (TDD)  

### 1. Introduction  
   
The UniTime project is a Micro SaaS web application that aims to help university students schedule their academic calendar, tasks, and personal goals.
This document describes the technical design and architecture overview of the UniTime system, including major technology decisions, data model, API flows, 
and security.  

---

### 2. System Overview  
   
Tomorrow is a web application which allows users to:  
  
Manage their tasks with due dates and priorities  
See tasks on a dynamic calendar  
Monitor task statistics (completed, imcomplete, overdue)  
Modify their profile and preferences  
Sync all the data in real-time with Firebase backend services  
  

---

### 3. Architecture Diagram  
   
  
[Client (Browser)]  
   |  
   v  
[HTML/CSS/JS Frontend]  
   |  
   v  
[Firebase Authentication] ------ [Firebase Firestore Database]  
            |  
            v  
 [Firebase Hosting (optional for deployment)]  

---
 
### 4. Technology Stack
  
Component: Frontend	  	
Technology Used: HTML, CSS, JavaScript  
Reason: Simple, lightweight  
  
Component: Backend (Serverless)	  
Technology Used: Firebase Authentication + Firestore  	
Reason: Real-time data sync, easy auth  
  
Component: Database  	
Technology Used: Firebase Firestore  
Reason: NoSQL, scalable, easy to use  
  
Component: Version Control  		
Technology Used: Git + GitHub  
Reason: Team collaboration, CI/CD  
  
---

5. Database Design  

     
Firestore Structure:  
  
users (Collection)  
  └── userId (Document)  
        ├── name: "Neesha"  
        ├── email: "neesha@example.com"  
        ├── notifications: "on"  
        ├── theme: "light"  
        └── tasks (Subcollection)  
              ├── taskId1 (Document)  
                    ├── name: "Finish Assignment"  
                    ├── priority: "High"  
                    ├── dueDate: "2025-04-30"  
                    ├── completed: false  
                    ├── favorited: true  
              ├── taskId2 (Document)  
                    └── ...  

---
                    
### 6. APIs and Data Flow

  
Action: User Sign Up  
API / Functionality: Login	firebase.auth().createUserWithEmailAndPassword() / signInWithEmailAndPassword()  
  
Action: Fetch User Profile  	
API / Functionality: db.collection("users").doc(userId).get()  
  
Action: Update User Profile	  
API / Functionality: db.collection("users").doc(userId).update({ name, email, theme, notifications })  
  
Action: Create Task  
API / Functionality: db.collection("users").doc(userId).collection("tasks").add(taskData)  
  
Action: Edit Task  	  
API / Functionality: db.collection("users").doc(userId).collection("tasks").doc(taskId).update(updatedData)  
  
Action: Delete Task  
API / Functionality: db.collection("users").doc(userId).collection("tasks").doc(taskId).delete()  
  
Action: Real-time Task Sync  
API / Functionality: .onSnapshot() listener on tasks subcollection  

---


### 7. Security Considerations
     
Authentication:  
Only authenticated users can access the UniTime app.  
  
Firestore Rules:  

```
rules_version = '2';  
service cloud.firestore {  
  match /databases/{database}/documents {  
    
    match /users/{userId} {  
      allow read, write: if request.auth.uid == userId;  

      match /tasks/{taskId} {  
        allow read, write: if request.auth.uid == userId;  
      }  
    }  
  }  
}
```
  
Validation:  
  
Frontend validates inputs before sending to Firestore.  
Prevents empty task names or invalid dates.  

---

### 8. Key Technical Decisions
  
Decision: Use Firebase for backend	  
Reason : Reduces complexity, serverless, real-time sync  
  
Decision: Firestore instead of Realtime Database  	
Reason : More scalable, structured querying  
  
Decision: Separate tasks as subcollections  	
Reason : Keeps data modular and user-specific  
   
Decision: Simple Frontend (HTML, CSS, JS)  	
Reason : Faster development, no framework overhead  
  

---

### 9. Limitations and Future Improvements
  
Limitation: No offline support , No advanced task sharing  
Future Improvement: I,mplement Firestore offline persistence, Add group task features  
	
	  
**End of TDD**
