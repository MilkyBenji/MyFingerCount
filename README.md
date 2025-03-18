# **myFingerCount**  

**myFingerCount** is a real-time finger detection and counting system built using Python and OpenCV. This project demonstrates how to detect a hand in a video feed and count the number of fingers using **Convex Hull** and **Convexity Defects**.

---

## **Table of Contents**  

1. [Project Overview](#project-overview)  
2. [Video Demo](#video-demo)  
3. [Motivation and Purpose](#motivation-and-purpose)  
4. [Problem Statement and Objectives](#problem-statement-and-objectives)  
5. [Understanding Convex Hull](#understanding-convex-hull)  
6. [Contributing](#contributing)  
7. [License](#license)  

---

## **Project Overview**  

### **Introduction**  

**myFingerCount** is a Python-based hand detection and finger counting system that utilizes **OpenCV** to process a real-time video stream, detect a hand, and count the number of extended fingers. The method is based on **Convex Hull** and **Convexity Defects**, which help identify the gaps between fingers.

---

## **Video Demo**  

[Include a demo link or GIF if available]

---

### **Features**  

- **Real-Time Hand Detection**: Detects the presence of a hand in the video feed.  
- **Convex Hull-Based Finger Counting**: Uses **Convex Hull** and **Convexity Defects** to determine the number of fingers shown.  
- **Dynamic Background Adaptation**: Uses background averaging for improved accuracy.  
- **Works with Live Webcam Feed**: Captures and processes video in real-time.  
- **Basic Gesture Recognition**: Can differentiate between different hand gestures based on finger count.  

### **Technologies Used**  

- **Python**: Main programming language.  
- **OpenCV**: Used for image processing and hand detection.  
- **NumPy**: For numerical operations.  

---

## **Motivation and Purpose**  

Hand gesture recognition is a crucial component of **Human-Computer Interaction (HCI)**, enabling touchless control systems and sign language interpretation. This project helped in understanding the application of **Convex Hull** and **Convexity Defects** in real-time hand tracking and recognition.

This project helped me:

- Learn about **hand segmentation and background subtraction**.  
- Implement **Convex Hull** and **Convexity Defects** to count fingers.  
- Process real-time video using OpenCV.  

---

## **Problem Statement and Objectives**  

### **Problem Statement:**  

Hand gesture recognition is useful for a variety of applications, such as virtual mouse control, sign language interpretation, and touchless interfaces. The challenge was to develop a system that can reliably detect a hand and count fingers in real time.

### **Objectives:**  

✔️ Implement real-time hand detection.  
✔️ Use **Convex Hull** and **Convexity Defects** to count fingers.  
✔️ Enhance accuracy using background averaging.  
✔️ Create a simple and efficient system that works with webcam input.  

---

## **Understanding Convex Hull**  

### **What is Convex Hull?**  

The **Convex Hull** of a shape is the smallest convex boundary that can fully enclose all given points. Imagine stretching a rubber band around a set of points—the shape the band forms is the convex hull. In this project, we use the convex hull to identify the outer boundary of the hand.

### **Convexity Defects and Finger Counting**  

- **Convexity Defects** are the inward indentations between fingers when the convex hull is applied to a hand.  
- By detecting these defects, we can count the number of fingers raised.  
- The algorithm identifies valleys between fingers as defects and uses their positions to estimate the number of extended fingers.  

---

## **Contributing**  

If you'd like to contribute to **myFingerCount**, feel free to **fork the repository** and submit a **pull request**. Contributions are always welcome!  

### **Guidelines:**  

✔️ **Code Style:** Follow PEP8 coding standards.  
✔️ **Documentation:** Ensure proper documentation for any new features.  
✔️ **Testing:** Verify that your code works correctly before submitting.  

---

## **License**  

This project is licensed under the **MIT License** – see the `LICENSE` file for details.  

