# AWS-Based Facial Recognition Attendance System

A serverless, cloud-native attendance system that uses facial recognition to identify users and automatically record attendance.  
The project leverages AWS managed services for authentication, image processing, storage, and analytics.

---

## 📌 Project Overview

This system captures a user’s facial image through a web interface, verifies the identity using facial recognition, and records attendance with timestamps.  
The entire solution is built using a **serverless architecture**, ensuring scalability, security, and minimal operational overhead.

---

## 🏗️ Architecture Overview

**Frontend**
- Static web application hosted on Amazon S3
- Delivered securely via CloudFront (HTTPS)
- JavaScript-driven UI for camera access and API interaction

**Authentication**
- Amazon Cognito for user sign-up, sign-in, and authentication
- OAuth 2.0 based authentication using ID and Access tokens

**Backend**
- Amazon API Gateway exposes backend APIs
- AWS Lambda functions handle business logic

**Storage & Processing**
- Amazon S3 for storing uploaded facial images
- Amazon Rekognition for facial recognition and matching
- Amazon DynamoDB for storing attendance records and metadata

---

## 🔁 System Workflow

### 1. User Authentication
- User logs in via Amazon Cognito Hosted UI
- Cognito authenticates the user and redirects back to the application
- Frontend extracts user information from the ID token

### 2. Attendance Marking
- User opens the camera and captures an image
- Image is sent to API Gateway via JavaScript (`fetch`)
- Lambda function:
  - Decodes the image
  - Stores it in S3
  - Uses Rekognition to identify the face
  - Records attendance in DynamoDB if a valid match is found

### 3. Attendance Retrieval
- Dashboard loads attendance data via another API call
- Lambda function queries DynamoDB
- Attendance summaries and recent records are returned as JSON
- Frontend dynamically updates the UI

---

## 🛠️ Technologies Used

- **Frontend:** HTML, CSS, JavaScript
- **Authentication:** Amazon Cognito
- **API Layer:** Amazon API Gateway
- **Compute:** AWS Lambda
- **Image Storage:** Amazon S3
- **Face Recognition:** Amazon Rekognition
- **Database:** Amazon DynamoDB
- **Security:** IAM Roles & Policies
- **Deployment:** Serverless Architecture

---

## 📂 Repository Structure

.
├── frontend/
│ ├── home.html
│ ├── dashboard.html
│ ├── styles.css
│ └── config.js
│
├── lambda/
│ ├── imagetoS3.py # Upload image & mark attendance
│ └── getAttendance.py # Fetch attendance & analytics
│
└── README.md


---

## 🔐 Security Considerations

- User credentials are never handled by the application
- Authentication is managed entirely by Amazon Cognito
- API access is controlled using API Gateway authorizers
- IAM roles restrict Lambda access to only required AWS services
- All communication is secured over HTTPS

---

## 📊 Features

- Secure user authentication
- Facial recognition-based attendance
- Real-time attendance marking
- Attendance history and summary analytics
- Fully serverless and scalable design

---

## 🚀 Future Enhancements

- Weekly and monthly attendance analytics
- Admin dashboard for attendance management
- Notifications for attendance events
- Role-based access control
- Improved UI/UX and mobile responsiveness

---


---

## 📄 License

This project was developed as part of an internship and is intended for educational and demonstration purposes.

