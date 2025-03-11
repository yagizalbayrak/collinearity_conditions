# Computing Real-World Coordinates Using Collinearity Conditions

This project demonstrates how to compute the real-world (object-space) coordinates of a common object visible in two different images using **collinearity conditions** in photogrammetry.

## Overview
Collinearity conditions define the mathematical relationship between an object's **real-world coordinates**, its **image-space coordinates**, and the camera's **exterior and interior orientation parameters**. By leveraging these conditions, we can determine the **3D position of an object** when captured from two different perspectives.

---

## Methodology

### 1️⃣ Image Coordinate Acquisition
- Identify the object in two different images and extract its **pixel coordinates**:
- Ensure **camera calibration parameters** (focal length, principal point, distortion coefficients) are available.

### 2️⃣ Exterior Orientation Parameters (EOPs)
- The camera's position **(X₀, Y₀, Z₀)** and **rotation matrix (R)** at the time of image capture must be known.
- These parameters are typically obtained via:
- **Aerial triangulation**
- **GNSS/IMU integration** for sensor positioning

### 3️⃣ Collinearity Equations
Each image point must satisfy the collinearity condition:
```math
$$
x = -f \frac{r_{11}(X - X_0) + r_{12}(Y - Y_0) + r_{13}(Z - Z_0)}{r_{31}(X - X_0) + r_{32}(Y - Y_0) + r_{33}(Z - Z_0)}
$$

$$
y = -f \frac{r_{21}(X - X_0) + r_{22}(Y - Y_0) + r_{23}(Z - Z_0)}{r_{31}(X - X_0) + r_{32}(Y - Y_0) + r_{33}(Z - Z_0)}
$$

**Where:**  
- \( (X, Y, Z) \) = Unknown **object-space coordinates**  
- \( (X_0, Y_0, Z_0) \) = Camera position (Exterior Orientation)  
- \( R = [r_{ij}] \) = **3×3 Rotation Matrix**  
- \( f \) = Camera **focal length**  
```

### 4️⃣ Space Intersection Computation
- Given **two images** with known orientation parameters, we solve the **collinearity equations simultaneously**.
- This results in a **least squares adjustment**, estimating the best real-world position of the object.

---

## 🛠 Applications
This method is widely used in:
-  **3D Reconstruction**
-  **Aerial Photogrammetry & UAV Mapping**
-  **Surveying & Geodesy**
-  **Machine Vision & Robotics**

---

##  References
- Wolf, P. R., & Dewitt, B. A. (2000). *Elements of Photogrammetry with Applications in GIS*.  
- Kraus, K. (2007). *Photogrammetry: Geometry from Images and Laser Scans*.

---

##  Getting Started
To implement this method in Python, install the necessary libraries:

```sh
pip install numpy opencv-python
