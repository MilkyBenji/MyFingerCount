# **FingerCountApp**

**FingerCountApp** is a real-time finger counting system using OpenCV and computer vision techniques. This project detects and counts the number of fingers raised using **convex hulls** and **contour analysis**.

---

## **Table of Contents**

1. [Project Overview](#project-overview)
2. [Video Demo](#video-demo)
3. [Motivation and Purpose](#motivation-and-purpose)
4. [Problem Statement and Objectives](#problem-statement-and-objectives)
5. [Concept: Convex Hull](#concept-convex-hull)
6. [Finger Counting Process](#finger-counting-process)
7. [License](#license)

---

## **Project Overview**

### **Introduction**

**FingerCountApp** uses **background subtraction**, **thresholding**, and **convex hull detection** to segment the hand and count the number of fingers raised. The system runs in real-time using a webcam and processes the hand region using OpenCV functions.

---

## **Video Demo**

A video demonstration showcasing the real-time finger counting process can be found here:

https://github.com/user-attachments/assets/d2686c22-90cd-4db5-9295-340bdee1b18f

## **Motivation and Purpose**

The motivation behind this project is to create a simple yet effective real-time hand tracking and finger counting system. This can be used for gesture-based interactions, sign language recognition, and human-computer interaction (HCI) applications.

---

## **Problem Statement and Objectives**

### **Problem Statement**
Hand gesture recognition is a crucial component of interactive computer vision applications. Many existing methods require specialized hardware or suffer from poor real-time performance.

### **Objectives**
- Develop a real-time hand segmentation and finger counting algorithm.
- Use only a standard webcam and OpenCV for implementation.
- Achieve accurate and fast recognition using image processing techniques.
- Ensure the system is robust under different lighting conditions.

---

## **Concept: Convex Hull**

A **convex hull** is the smallest convex shape that encloses a set of points. In our case, it forms a boundary around the detected hand. This allows us to identify the extreme points of the hand, which are crucial for finger counting.

We use OpenCV’s `cv2.convexHull()` function to generate this shape around the detected hand contour.

```python
# Calculate the convex hull of the hand segment
conv_hull = cv2.convexHull(hand_segment)
```

Once we obtain the convex hull, we identify four extreme points:

- **Topmost**
- **Bottommost**
- **Leftmost**
- **Rightmost**

These points help in locating the center of the palm and determining the region where fingers are counted.

```python
# Find the extreme points of the convex hull
top = tuple(conv_hull[conv_hull[:, :, 1].argmin()][0])
bottom = tuple(conv_hull[conv_hull[:, :, 1].argmax()][0])
left = tuple(conv_hull[conv_hull[:, :, 0].argmin()][0])
right = tuple(conv_hull[conv_hull[:, :, 0].argmax()][0])

# Compute the center of the palm
cX = (left[0] + right[0]) // 2
cY = (top[1] + bottom[1]) // 2
```

---

## **Finger Counting Process**

The system counts fingers by analyzing the **convex hull** and the **circular region of interest (ROI)** around the palm. The key steps are:

1. **Detect the Hand and Segment It**\
   We first isolate the hand from the background using thresholding and contour detection.

   ```python
   thresholded, hand_segment = segment(gray)
   ```

2. **Find the Convex Hull**\
   Using `cv2.convexHull()`, we determine the outer boundary of the hand.

   ```python
   conv_hull = cv2.convexHull(hand_segment)
   ```

3. **Determine Palm Center and Maximum Distance**\
   We calculate the center of the palm and find the maximum Euclidean distance to the convex hull's extreme points.

   ```python
   distance = pairwise.euclidean_distances([(cX, cY)], Y=[left, right, top, bottom])[0]
   max_distance = distance.max()
   ```

4. **Define a Circular ROI**\
   A circular ROI around the palm is used to filter out fingers from the wrist area.

   ```python
   radius = int(0.8 * max_distance)
   circular_roi = np.zeros(thresholded.shape[:2], dtype="uint8")
   cv2.circle(circular_roi, (cX, cY), radius, 255, 10)
   ```

5. **Count the Fingers**  
Contours inside the circular ROI that satisfy certain conditions are counted as fingers.

```python
for cnt in contours:
    (x, y, w, h) = cv2.boundingRect(cnt)
    out_of_wrist = ((cY + (cY * 0.25)) > (y + h))
    limit_points = ((circumference * 0.25) > cnt.shape[0])
    if out_of_wrist and limit_points:
        count += 1
```

6. **Display the Finger Count**\
   The detected number of fingers is displayed in real time.
   ```python
   cv2.putText(frame_copy, str(count), (70, 45), cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,255), 2)
   ```

By following these steps, the program efficiently detects and counts fingers in real time.

---

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

