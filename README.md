# CV_basics

.gifs and visualizations take a few seconds to load...

## About
This repository contains projects completed for **CIS 5800: Machine Perception (Fall 2025)** at the **University of Pennsylvania**, taught by **Prof. Kostas Daniilidis**.  
Course website: [https://sites.google.com/seas.upenn.edu/cis5800f2025/](https://sites.google.com/seas.upenn.edu/cis5800f2025/)

The course builds a complete foundation in **geometric and learning-based Computer Vision**, moving from projective geometry to 3D reconstruction, optical flow, and radiance-field representations.

### Topics Covered
The class develops both theoretical understanding and hands-on implementations of modern perception algorithms. Core areas include:

> *I also studied additional readings from **Hartley & Zisserman’s** “Multiple View Geometry in Computer Vision”, the **MIT Foundations of Computer Vision Textbook**, and other classic references to deepen my understanding of multi-view geometry and 3D reconstruction.*


**Camera Models & Calibration**
- Pinhole camera model, projection equations, and intrinsic/extrinsic parameters  
- Vanishing points, cross-ratios, and geometric transformations  
- Camera calibration from planar patterns and SVD-based pose recovery  

**Projective Geometry**
- Homographies between planes and their estimation via DLT  
- Collineations and two-view relationships  
- Coordinate transformations in homogeneous space  

**Pose Estimation & 3D Geometry**
- **PnP and P3P** for pose recovery from 2D–3D correspondences  
- **Procrustes alignment** for rigid-body transformation recovery  
- Triangulation and depth estimation from multiple calibrated views  

**Epipolar Geometry & Essential Matrix Estimation**
- Derivation of the **fundamental and essential matrices**  
- 8-point and normalized algorithms to estimate `E`   
- **RANSAC** for robust outlier rejection  
- Epipolar line visualization and reprojection validation  

**Structure from Motion (SfM) & Multi-View Reconstruction**
- Motion recovery from two or more views  
- Triangulation and bundle adjustment for dense 3D reconstruction  
- Implementation of a minimal SfM pipeline in Python  
- Integration of feature matching, RANSAC filtering, and pose disambiguation  

**Optical Flow & Visual Odometry**
- Derivation and implementation of the **Lucas–Kanade** and **Horn–Schunck** methods  
- Understanding of **Ego-motion from Flow** and **Visual SLAM** concepts  
- Multi-frame motion estimation for dynamic scenes  

**Radiance Fields & Light-Field Rendering**
- Introduction to **Neural Radiance Fields (NeRF)** and radiance integration  
- Light-field rendering and plenoptic function concepts  
- Fourier and spherical harmonics in radiance representation  

**3D Perception & Modern CV Applications**
- **Stereopsis** and depth from disparity  
- Multi-view consistency and metric reconstruction  
- Brief exploration of **PyTorch3D** for differentiable 3D vision  
- Exposure to modern pipelines like **COLMAP** and **Bundle Adjustment** frameworks  

---

## HW 3 - 3D Reconstruction from Two Views
**Goal:** Recover the relative pose between two images and reconstruct the 3D scene using feature matching and multi-view geometry.

**Pipeline Overview:**
1. Extract **SIFT** features and compute correspondences.  
2. Estimate the **essential matrix (E)** with the 8-point algorithm and **RANSAC**.  
3. Recover all four pose candidates (R, T) from E and select the physically valid one.  
4. **Triangulate** 3D points and reconstruct the scene structure.  
5. Visualize epipolar geometry, reprojection accuracy, and the resulting 3D model.

**Concepts Learned:**  
Feature matching, essential matrix estimation, epipolar geometry, camera pose disambiguation, triangulation.

<p align="center">
  <img src="img/hw3/sift1.png" alt="SIFT feature detection in first view" width="45%">
  <img src="img/hw3/sift2.png" alt="SIFT feature detection in second view" width="45%">
</p>
<p align="center"><em>Keypoints extracted and matched between two views using SIFT descriptors.</em></p>

<p align="center">
  <img src="img/hw3/sift_matches.png" alt="SIFT feature correspondences" width="85%">
</p>
<p align="center"><em>Feature correspondences automatically detected between both images.</em></p>

<p align="center">
  <img src="img/hw3/ransac_matches.png" alt="RANSAC inlier filtering" width="85%">
</p>
<p align="center"><em>RANSAC filtering removes outliers to robustly estimate the essential matrix.</em></p>

<p align="center">
  <img src="img/hw3/epipolar_lines.png" alt="Epipolar geometry visualization" width="85%">
</p>
<p align="center"><em>Epipolar lines drawn in both images.</em></p>

<p align="center">
  <img src="img/hw3/point_reprojections.png" alt="3D reconstruction reprojection results" width="85%">
</p>
<p align="center"><em>Triangulated 3D points projected back into the image for reprojection validation.</em></p>

---

## HW 2 - Augmented Reality with AprilTags
**Goal:** Estimate camera pose from AprilTags and project virtual 3D objects into real scenes.

**Pipeline Steps:**
- Define world coordinates centered on the AprilTag.  
- Recover camera pose using **PnP** and **P3P** approaches.  
- Solve for **R** and **t** via the **Procrustes method**.  
- Map pixels to 3D world coordinates and render objects.  
- Generate an augmented-reality GIF of virtual objects on the tag plane.

**Concepts Learned:**  
Pose estimation, homography-based PnP, polynomial P3P, Procrustes alignment, camera calibration, interactive 3D projection.

<p align="center">
  <img src="img/VR_hw2.gif" alt="Augmented reality projection with AprilTags" height="300">
</p>
<p align="center"><em>Virtual objects anchored to AprilTags using recovered camera pose.</em></p>

---

## HW 1 - Image Projection via Homography
**Goal:** Use homographies to project an image (the Penn logo) onto a soccer goal during a video sequence.

**Pipeline Steps:**
- Compute homography from video frame corners to logo coordinates using SVD.  
- Perform inverse warping to correctly map logo pixels into the scene.  
- Generate a video showing the logo following the moving goal with correct perspective.

**Concepts Learned:**  
Projective geometry, homography estimation, inverse warping, planar image mapping.

<p align="center">
  <img src="img/basic_projection_hw1.gif" alt="Basic homography projection" height="260">
</p>
<p align="center"><em>Logo projection maintaining geometric consistency with the goal’s motion.</em></p>

---

### Summary
These projects build a complete foundation in geometric computer vision:
1. **HW1:** Planar projection and image warping  
2. **HW2:** 3D pose estimation and augmented reality  
3. **HW3:** Multi-view geometry and 3D reconstruction  

Each project implements a working perception pipeline that bridges theory and practical implementation in Python.
