# 🚗 Smart Car Parking System (ANPR + IoT)

An intelligent **Automated Smart Parking System** that uses **Automatic Number Plate Recognition (ANPR)**, **IoT sensors**, and **Python backend logic** to manage vehicle entry/exit and dynamically track parking availability in real time.

The system eliminates manual intervention by detecting vehicle number plates, validating entries/exits, monitoring parking slots via ultrasonic sensors, and updating slot availability on connected hardware.

---

## ✨ Features

- 📸 Real-time vehicle detection using camera feed  
- 🔍 Automatic Number Plate Recognition (ANPR) via external API  
- 🧠 Intelligent entry/exit validation logic  
- 📊 Live parking slot tracking  
- 🗄 SQLite database for vehicle history  
- 🔌 Arduino integration through serial communication  
- 📏 Ultrasonic sensor based vehicle presence detection  
- 🚦 Duplicate entry prevention  
- 🚫 Parking full detection  

---

## 🛠 Tech Stack

### Software
- Python  
- OpenCV  
- SQLite  
- Requests  
- Multithreading  

### Hardware
- Arduino  
- Ultrasonic Sensors  
- Servo Motor  
- Camera / Mobile IP Camera  

---

## 📁 Project Structure



Smart_Car_Parking/
│
├── entry_logic.py        # Entry gate logic + ANPR + DB insert
├── exit_logic.py         # Exit gate logic + DB update
├── hardware_code.txt    # Arduino code
├── Entry_video.mp4      # Entry demo
├── exit_video.mp4       # Exit demo
└── README.md

## ⚙️ System Architecture

1. Camera captures vehicle image  
2. Frame sent to ANPR API  
3. Extracted plate validated  
4. Entry/exit recorded in SQLite database  
5. Slot count calculated dynamically  
6. Available slots sent to Arduino  
7. Ultrasonic sensors confirm vehicle movement  
8. Gate controlled via servo motor  

---

## 🧠 Core Logic

### Entry Flow

1. Capture video frames  
2. Send frame to Plate Recognition API  
3. Extract vehicle number  
4. Check current parking count  
5. If space available:  
   - Insert entry record into DB  
   - Reduce available slots  
   - Trigger ultrasonic sensor  
6. If parking full:  
   - Deny entry  

---

### Exit Flow

1. Capture exit camera frame  
2. Recognize number plate  
3. Fetch last vehicle status from DB  
4. If vehicle is inside:  
   - Mark exit in DB  
5. Update available slots  
6. Send slot data to Arduino  

---

## 🗄 Database Schema

### Table: `entry`

| Column | Type |
|--------|------|
| number | TEXT |
| time   | TEXT |
| status | INTEGER |

- `status = 1` → Vehicle inside  
- `status = 0` → Vehicle exited  

---

## 🔌 Arduino Communication

Python communicates with Arduino via **Serial Port**:

- Sends available slot count  
- Triggers ultrasonic sensor  
- Controls gate mechanism  

---

## 🚀 How to Run

### 1. Install Dependencies

```bash
pip install opencv-python requests pyserial
````

---

### 2. Configure APIs

Inside `entry_logic.py` and `exit_logic.py`:

```python
API_URL = "your_plate_recognizer_api"
API_TOKEN = "your_api_key"
MOBILE_CAM_URL = "your_camera_stream_url"
```

---

### 3. Connect Arduino

Update COM port:

```python
arduino = serial.Serial('COM5', 9600)
```

---

### 4. Run Entry System

```bash
python entry_logic.py
```

---

### 5. Run Exit System

```bash
python exit_logic.py
```

---

## 📈 Future Improvements

* Web dashboard for live monitoring
* Cloud database integration
* User authentication
* Payment gateway
* Mobile application
* License plate dataset fine-tuning

---

## 👨‍💻 Author

Nikhil Singh

---

## 📜 License

This project is open for educational and research purposes.
