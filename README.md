# Better read the file &Image Stitching - 2.docx& !!!

# final-project-on-Image-processing

# Image Stitching Using Classical Computer Vision Methods

## Overview

The goal of the project is to develop a complete image stitching system capable of combining multiple photographs into a single panoramic image using classical computer vision techniques.

Unlike fully automated black-box solutions, this project implements and analyzes every stage of the stitching pipeline, providing full control over feature extraction, matching, geometric alignment, and image blending.

---

## Project Goal

Image stitching is the process of merging overlapping photographs into a single panoramic image.

The objective of this project is to:

* Detect reliable image features
* Match corresponding points between images
* Estimate geometric transformations
* Align photographs into a common coordinate system
* Blend images into a seamless panorama

The project focuses entirely on classical computer vision methods without using deep learning models.

---

## Dataset

The images used in this project were captured manually using a smartphone camera.

Scene characteristics:

* Urban environment
* Residential buildings
* Trees and landscape elements
* Architectural structures
* Natural daylight conditions

The photographs were intentionally taken from slightly different viewpoints and angles in order to evaluate the robustness of the algorithm.

---

## Project Pipeline

### 1. Image Preprocessing

The preprocessing stage includes:

* Image resizing
* Contrast enhancement using CLAHE
* Grayscale conversion
* Bilateral filtering for noise reduction

Additional image statistics:

* Brightness analysis
* Standard deviation
* Entropy estimation
* Edge density evaluation

---

### 2. Feature Detection

The project uses the SIFT (Scale-Invariant Feature Transform) algorithm.

SIFT provides:

* Scale invariance
* Rotation invariance
* Robustness to illumination changes

Detected keypoints:

* Left image: 11,417 keypoints
* Right image: 11,456 keypoints

---

### 3. Feature Matching

Feature correspondences are found using:

* Brute Force Matcher
* K-Nearest Neighbors (KNN)
* Lowe Ratio Test

Results:

* 1,451 reliable feature matches

The ratio test significantly reduces false matches and improves matching quality.

---

### 4. Homography Estimation

Geometric transformation is estimated using:

* RANSAC (Random Sample Consensus)

The algorithm removes incorrect correspondences and computes a robust homography matrix.

Results:

* Total matches: 1,451
* Inliers after RANSAC: 1,303
* Inlier ratio: approximately 90%
* Mean reprojection error: approximately 1.86 pixels

---

### 5. Geometric Alignment

The estimated homography matrix is used to:

* Warp images into a common coordinate system
* Create a shared canvas
* Correct perspective distortions
* Align overlapping regions

Overlap area:

* Approximately 22%

---

### 6. Image Blending

To generate the final panorama:

* Overlapping pixels are averaged
* Non-overlapping regions are preserved
* Automatic cropping removes empty regions

Final panorama resolution:

* 2155 × 2283 pixels

---

## Technologies Used

* Python
* OpenCV
* NumPy
* Matplotlib
* Google Colab

---

## Performance Metrics

### Feature Extraction

* 11,417 keypoints (left image)
* 11,456 keypoints (right image)

### Matching

* 1,451 valid matches

### RANSAC

* 1,303 inliers
* 148 outliers

### Accuracy

* Mean reprojection error: 1.86 px
* Inlier ratio: ~90%

### Speed

* Homography estimation: ~0.006 s
* Warping: ~0.15 s
* Full pipeline: ~0.15–0.20 s

---

## Comparison with OpenCV Stitcher

The developed implementation was compared against:

* OpenCV cv2.Stitcher()

### Advantages of the Custom Implementation

* Full control over every stage
* Detailed metric analysis
* Faster execution
* Transparent algorithm behavior
* Easy parameter tuning

### Advantages of OpenCV Stitcher

* Exposure compensation
* Seam optimization
* Multi-band blending
* Fully automatic workflow

The custom implementation achieved comparable panorama quality while providing significantly greater transparency and interpretability.

---

## Skills Demonstrated

This project demonstrates practical experience in:

* Computer Vision
* Image Processing
* Feature Detection
* SIFT
* Feature Matching
* Homography Estimation
* RANSAC
* Geometric Transformations
* Panorama Generation
* OpenCV Development
* Performance Evaluation
* Scientific Programming

---

## Repository Contents

* `final_project_on_Image_processing.ipynb` – complete implementation
* `Image Stitching Report.pdf` – project report
* Experimental results and visualizations
* Panorama generation pipeline

---

## Results

The project successfully implemented a complete classical image stitching system capable of generating high-quality panoramas from real-world photographs.

Key achievements include:

* Robust feature matching
* Accurate geometric alignment
* Low reprojection error
* High inlier ratio
* Fast execution speed
* Panorama quality comparable to OpenCV's built-in stitching solution
