# 🚗 Smart Car Parking System (Python + ANPR)

## 📌 Project Overview
The Smart Car Parking System is an automated parking management solution developed using Python that integrates **Automatic Number Plate Recognition (ANPR)** with hardware components.  
The system controls vehicle entry and exit, tracks parking slot availability, calculates parking duration, and generates billing automatically.

---

## ⚙️ System Workflow
1. Vehicle arrives at the entry gate  
2. Camera captures live video feed  
3. Python-based ANPR detects and recognizes the number plate  
4. Vehicle number and entry time are stored in the database  
5. Ultrasonic sensor detects vehicle presence  
6. Servo motor rotates 90° to open the gate  
7. Available parking slots are displayed on a 16x2 LCD  
8. On vehicle exit, total parking time is calculated  
9. Bill is generated based on parking duration  

---

## 🛠️ Technologies & Components Used

### 💻 Software
- Python  
- OpenCV (Live video processing)  
- Plate Recognizer API (ANPR)  
- SQLite Database  
- Multithreading  
- Serial Communication  

### 🔌 Hardware
- Arduino  
- Ultrasonic Sensor  
- Servo Motor  
- Camera Module  
- 16x2 LCD Display  

---

## ✨ Key Features
- Real-time number plate recognition using camera feed  
- Database storage of vehicle entry and exit records  
- Automated gate control using ultrasonic sensor & servo motor  
- Live parking slot availability update  
- Parking time calculation and billing  
- Multithreaded system for smooth real-time operations  

---

## 🗄️ Database Schema
