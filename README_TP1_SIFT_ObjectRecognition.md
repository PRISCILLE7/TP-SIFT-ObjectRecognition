# Object Detection and Recognition Using SIFT Descriptors

This project was developed as part of the **Computer Vision** course in the Master 2 "Systèmes Intelligents et Multimédia" at IFI, Hanoi. It explores **object detection** and **recognition** using local feature descriptors, specifically the **SIFT (Scale-Invariant Feature Transform)** method.

 Notebook: `tp1vod_detection.ipynb`  
 Dataset used: [COIL-100](http://www1.cs.columbia.edu/CAVE/software/softlib/coil-100.php)  
 Instructor: Nguyễn Thị Oanh

---

##  Project Objectives

- Detect and describe keypoints using the **SIFT** algorithm
- Match local descriptors to recognize known objects
- Classify input images based on descriptor similarity
- Evaluate recognition results using confusion matrix

---

##  Project Files

- `tp1vod_detection.ipynb` – Python notebook running all detection and recognition logic.
- `COIL-100/` – Dataset containing images from 10 selected object classes.
- `.npy` files – Precomputed SIFT descriptors and keypoints for faster reloading.

---

##  Tools and Libraries

- Python 3
- OpenCV (SIFT, BFMatcher)
- NumPy
- scikit-learn (train_test_split)
- Google Colab (for training and storage via Google Drive)

---

##  How It Works

### 1. Dataset Preparation

- COIL-100 dataset split into:
  - **5040 images for training**
  - **2160 images for testing**
- Images grouped into **10 object classes** (e.g., bottle, car, cup)

### 2. Feature Extraction with SIFT

- Keypoints and descriptors are extracted using:
  ```python
  sift = cv2.xfeatures2d.SIFT_create()
  keypoints, descriptors = sift.detectAndCompute(image, None)
  ```

### 3. Descriptor Matching

- Brute-Force matching with ratio test (Lowe’s ratio = 0.6)
- Best matches are retained for comparison
- Class prediction based on the class with the **highest number of matches**

### 4. Object Recognition

- Unknown test image is compared with all training class descriptors
- Similarity score is computed by:
  ```
  score = number of valid matches / number of keypoints in query image
  ```
- The class with the highest score is selected as prediction

### 5. Evaluation

- Predictions are evaluated using a **confusion matrix**
- Visualization of match quality using `cv2.drawMatches`

---

##  Example Output

- Good predictions show clear keypoint matches
- Misclassifications are analyzed with visual explanation
- Classes with similar shapes/textures sometimes confuse the system

---

##  Conclusion

- The system correctly recognizes objects based on local feature matching.
- **SIFT** proves robust for rotation, scale, and illumination changes.
- The project meets all course objectives, with potential extensions:
  - Integrating ORB, SURF or deep features (CNNs)
  - Using RANSAC for homography-based localization
  - Scaling up with more object classes or COIL-100 in full

---

##  Contributors

Project completed as TP1 of the “Vision par Ordinateur” course (2025).

Master 2 SIM – IFI, Vietnam National University  
 Supervised by: Nguyễn Thị Oanh

---
 