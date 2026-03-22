# Augmented Reality: Gesture-Controlled 3D Interactive Interface
**A high-performance Computer Vision project blending 3D Physics, Linear Algebra, and Web Technology.**


<div align="center">
  <video src="assets/A-R-Gesture-Controlled-3D-I-I.mp4" muted autoplay loop style="max-width: 100%;"></video>
</div>


## 🚀 Overview
This project is an Augmented Reality application that allows users to interact with a 3D cube using real-time hand tracking. Developed with a focus on mathematical precision, it utilizes composite rotation matrices and directional cosines to achieve seamless interaction without the need for external controllers.

## 🛠️ Key Technical Features
- **Dual-Hand Logic Distribution:** 
  - **Left Hand:** Responsible for 3D rotation mapping (Yaw/Pitch).
  - **Right Hand:** Responsible for face selection and color interaction via "Pinch" gesture detection.
- **3D Mathematics:** Uses **Composite Rotation Matrices** and **Directional Cosines** relative to the Z-axis to accurately identify the front-facing plane regardless of the rotation state.
- **Edge Computing & Privacy:** Powered by **TensorFlow.js** via the **ml5.js** library, performing all AI inference locally on the browser.
- **Offline Reliability:** Implements a custom **Fetch Interceptor** to route model requests to local directories, ensuring the system works in environments without internet access.

## 📐 The Mathematics Behind
Unlike simple 2D overlays, this project treats the cube as a mathematical entity. To determine which face the user is interacting with, the system:
1. Translates 3D normals based on the current rotation state using:
   $$xr = [n.x * cos(ry)] + [n.z * sin(ry)]$$
   $$yr = [n.x * sin(rx) * sin(ry)] + [n.y * cos(rx)] - [n.z * sin(rx) * cos(ry)]$$
   $$zr = [(-1) * n.x * cos(rx) * sin(ry)] + [n.y * sin(rx)]  + [n.z * cos(rx) * cos(ry)]$$
2. Calculates the **Directional Cosine** of the resulting vector relative to the camera vector $(0,0,1)$.
3. Selects the face with the maximum cosine value as the "Active Face."

## 💻 Tech Stack
- **Languages:** JavaScript (ES6+), HTML5, CSS3.
- **Libraries:** 
  - [p5.js](https://p5js.org/) (WEBGL Rendering Engine).
  - [ml5.js](https://ml5js.org/) (HandPose Estimation).
- **Environment:** Ubuntu 24.04 LTS / Sublime Text / Git.

## 📂 Project Structure
```text
.
├── index.html          # Core Logic & UI
├── p5.js               # Graphics Library
├── ml5.min.js          # Machine Learning Library
├── model/              # Local HandPose weights (Detector & Landmark)
|   └── handpose/
|       ├── detector/
|       |   ├── group1-Shard1of1.bin
|       |   └── model.json
|       └── landmark/
|           ├── group1-Shard1of2.bin
|           ├── group1-Shard2of2.bin
|           └── model.json
└── README.md           # Documentation
````

## ⚙️ Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/A-R-Gesture-Controlled-3D-I-I.git](https://github.com/your-username/A-R-Gesture-Controlled-3D-I-I.git)
    ```
2.  **Local Models:** Ensure the `model/` folder contains the necessary `.json` and `.bin` files for HandPose.
3.  **Run a Local Server:** Due to CORS policy for local files, use a local server:
      

## 🤝 Credits & Acknowledgments

  - **Lead Developer:** Alejandro Solis (Electronic Engineer)
  - **AI Logic Support:** Gemini (Google DeepMind)
  - **Inspiration:** Developed as a practical application of Instrumentation and Computer Vision.

-----

Developed by **Alejandro Solis** | [LinkedIn](https://www.linkedin.com/in/alejandrosolis2020) | [GitHub](https://github.com/Alejandro-Solis-Saldivia)
