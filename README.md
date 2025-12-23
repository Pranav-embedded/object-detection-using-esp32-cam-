# ESP32-CAM Object Detection using Edge Impulse (with OLED)

This project demonstrates **real-time object detection** using the **ESP32-CAM** module and **Edge Impulse**.
The system is trained to detect objects like **onion, potato, and tomato**, and displays detection results via **Serial Monitor and OLED display**.

---

## 📌 Project Features

* Object detection using **ESP32-CAM (AI Thinker)**
* Custom dataset collected using ESP32-CAM
* Edge Impulse YOLO-based object detection
* Optimized for **low memory devices**
* OLED display support for live results

---

## 🧰 Hardware Requirements

* ESP32-CAM (AI Thinker)
* USB-to-TTL (FTDI) Programmer
* Breadboard & jumper wires
* Micro-USB cable
* Computer with Arduino IDE
* Wi-Fi connection

---

## 🔌 Hardware Connections

### ESP32-CAM Programming Connections

| ESP32-CAM | FTDI                       |
| --------- | -------------------------- |
| 5V        | 5V                         |
| GND       | GND                        |
| U0R       | TX                         |
| U0T       | RX                         |
| GPIO0     | GND *(Only during upload)* |

⚠️ **Important**

* GPIO0 must be connected to **GND while uploading**
* Remove GPIO0-GND after upload for normal operation

---

## 🖥️ Software Requirements

* Arduino IDE
* ESP32 Board Package
* Edge Impulse Account (Free)
* Eloquent ESP32 CAM Library

---

## ⚙️ Arduino IDE Setup

1. Install **Arduino IDE**
2. Add ESP32 Board Manager
3. Install **ESP32 by Espressif Systems**
4. Select:

   * **Board:** AI Thinker ESP32-CAM
   * **Programmer:** ESP32 Arduino
   * **Baud Rate:** 115200

---

## 📷 Image Collection Using ESP32-CAM

### 1️⃣ Install Library

Install **Eloquent ESP32 CAM** library from Arduino Library Manager.

### 2️⃣ Open Image Capture Example


File → Examples → eloquentesp32cam → esp32cam_tp3


### 3️⃣ Modify Code

* Add your **Wi-Fi SSID & Password**
* Set camera type to **AI Thinker**


#define CAMERA_MODEL_AI_THINKER


### 4️⃣ Upload Code

* Connect GPIO0 → GND
* Power reset ESP32-CAM
* Upload sketch
* Remove GPIO0 → GND
* Power reset again

### 5️⃣ Access Image Server

* Open Serial Monitor
* Copy the IP address
* Open it in a browser (same Wi-Fi network)

---

## 📊 Dataset Collection

* Fix ESP32-CAM position
* Place object inside camera frame
* Rotate object slowly
* Capture **~50 images per object**
* Download images as ZIP
* Repeat for all classes:


---

## ☁️ Edge Impulse Setup

### 1️⃣ Create Project

* Log in to **Edge Impulse**
* Create new project (e.g., `obj-detect`)

---

### 2️⃣ Upload Dataset

* Go to **Data Acquisition**
* Upload ZIP files
* Enable:

  * Automatically split
  * Manually label

---

### 3️⃣ Label Images

* Go to **Labeling Queue**
* Draw bounding boxes
* Assign correct labels

---

## 🧠 Model Training

### 1️⃣ Create Impulse

* Image size: **96 × 96**
* Fit shortest axis
* Blocks:

  * Image Processing
  * Object Detection

---

### 2️⃣ Generate Features

* Color depth: **Grayscale**
* Generate features
* Ensure clear feature separation

---

### 3️⃣ Train Model

* Training cycles: **60**
* Learning rate: **0.01**
* Processor: **CPU**
* Start training
* Aim for **90–100% accuracy**

---

## 📦 Deployment

### 1️⃣ Export Model

* Go to **Deployment**
* Select **Arduino Library**
* Target device: **ESP32-EYE**
* Download ZIP

---

### 2️⃣ Add Library to Arduino


Sketch → Include Library → Add .ZIP Library


---

### 3️⃣ Open Example Code


File → Examples → (Your_Model_Name) → esp32_camera


* Disable ESP-EYE
* Enable ESP32-CAM

---

### 4️⃣ Upload Final Code

* GPIO0 → GND
* Power reset
* Upload
* Remove GPIO0
* Power reset again

---

## 🧪 Testing

1. Open Serial Monitor
2. Place object in front of camera
3. Observe:

   * Detected label
   * Confidence score


---


## 📈 Tips for Better Accuracy

* Use consistent lighting
* Avoid cluttered backgrounds
* Collect images from multiple angles
* Keep object centered during training

---


## 🚀 Future Improvements

* Add speaker module for voice output
* Store MP3 files on SD card
* Autonomous robot integration
* Multi-object detection

---

## 🙌 Credits

* ESP32-CAM Community
* Edge Impulse Team
* Eloquent Arduino Library

