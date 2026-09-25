# MathVision AI

### Image-Based Mathematical Expression Solver

> **See the equation. Understand the digits. Solve the expression.**

MathVision AI is a computer-vision and machine-learning based
mathematical expression solver built in Python.\
Instead of typing an equation manually, the user can upload an image
containing a handwritten or printed mathematical expression.

The system processes the image, detects individual characters,
recognizes digits using a trained **K-Nearest Neighbors (KNN)**
classifier, reconstructs the mathematical expression, and calculates the
final answer.

------------------------------------------------------------------------

## ✦ What MathVision AI Does

**Input**

``` text
Image →  5 × 12 + 20
```

**Processing**

``` text
Image
  ↓
OpenCV Preprocessing
  ↓
Character / Contour Detection
  ↓
Digit Recognition using KNN
  ↓
Expression Reconstruction
  ↓
Mathematical Evaluation
```

**Output**

``` text
Expression : 5*12+20
Answer     : 80
```

------------------------------------------------------------------------

## 🧩 Technology Stack

  -----------------------------------------------------------------------
  Technology                          Purpose
  ----------------------------------- -----------------------------------
  **Python**                          Main programming language and
                                      system integration

  **OpenCV**                          Image preprocessing, thresholding
                                      and contour detection

  **NumPy**                           Image arrays, numerical operations
                                      and normalization

  **scikit-learn**                    Machine-learning model and KNN
                                      classification

  **Pillow (PIL)**                    Reading and handling uploaded
                                      images

  **Matplotlib**                      Visualizing images and intermediate
                                      processing results

  **Pandas**                          Calculation-history handling and
                                      tabular display

  **IPyWidgets**                      Image-upload interface inside
                                      Jupyter

  **Jupyter Notebook**                Development and interactive
                                      demonstration environment
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🔬 How It Works

### 01 --- Image Input

The user uploads an image containing a mathematical expression.

For example:

``` text
5 × 12 + 20
```

The uploaded image is converted into a format that can be processed
using Python and OpenCV.

------------------------------------------------------------------------

### 02 --- Image Preprocessing

OpenCV prepares the image for recognition.

Typical processing steps include:

``` text
Original Image
      ↓
Grayscale Conversion
      ↓
Gaussian Blur
      ↓
Thresholding
      ↓
Binary Image
```

**Why?**

The ML model should focus on the mathematical characters instead of
unnecessary background information.

------------------------------------------------------------------------

### 03 --- Character Detection

OpenCV uses **contour detection** to locate separate objects/characters
in the processed image.

For an expression such as:

``` text
5 × 12 + 20
```

the system can identify components approximately as:

``` text
5 | × | 1 | 2 | + | 2 | 0
```

The detected components are sorted according to their horizontal
position so the original reading order can be reconstructed.

------------------------------------------------------------------------

### 04 --- Digit Recognition with Machine Learning

Each digit image is resized to:

``` text
8 × 8
```

and converted into numerical values.

The image is then flattened into a feature vector:

``` text
8 × 8 image
     ↓
64 numerical features
     ↓
KNN classifier
     ↓
Predicted digit
```

MathVision AI uses:

**K-Nearest Neighbors (KNN)**

The trained classifier compares the input digit with known training
samples and predicts the most likely digit.

The trained model achieved approximately:

**98.61% test accuracy**

on the evaluation dataset used during development.

------------------------------------------------------------------------

## 🧠 Why KNN?

KNN was selected because:

-   It is simple to implement.
-   It works well for small digit datasets.
-   It is easy to interpret and explain.
-   It does not require a large neural-network architecture.
-   It provides a good baseline for image classification.

For this project, each digit is represented as a numerical feature
vector, making KNN a natural starting point.

------------------------------------------------------------------------

## ➕ Operator & Expression Reconstruction

Digits and mathematical operators are combined in their original order.

For example:

``` text
5 | × | 1 | 2 | + | 2 | 0
```

becomes:

``` text
5*12+20
```

Consecutive digit predictions are grouped together:

``` text
1 + 2  →  12
2 + 0  →  20
```

This allows the system to work with multi-digit numbers.

------------------------------------------------------------------------

## 🧮 Mathematical Engine

Once the expression has been reconstructed, the mathematical engine
evaluates it.

Example:

``` text
5*12+20
```

Calculation:

``` text
5 × 12 = 60
60 + 20 = 80
```

Final result:

``` text
80
```

The project also includes basic validation and error handling for
invalid expressions and division-by-zero cases.

------------------------------------------------------------------------

## 🎨 User Interface

MathVision AI includes a dark, premium-style interface designed around
three main stages:

``` text
① IMAGE INPUT
       ↓
② DETECTION RESULT
       ↓
③ SOLUTION
```

The interface can display:

-   Uploaded expression
-   Detected expression
-   Final answer
-   Step-by-step calculation
-   Calculation history
-   Project information

The goal is to keep the technical pipeline understandable even for a
first-time user.

------------------------------------------------------------------------

## 📊 Example

### Input

``` text
┌───────────────────────┐
│     5 × 12 + 20       │
└───────────────────────┘
```

### Recognition

``` text
5 | × | 1 | 2 | + | 2 | 0
```

### Reconstructed Expression

``` text
5*12+20
```

### Result

``` text
80
```

------------------------------------------------------------------------

## 📁 Project Pipeline

A simplified project structure can be organized as:

``` text
MathVision-AI/
│
├── Project.ipynb
├── README.md
├── requirements.txt
│
├── assets/
│   └── sample-images/
│
└── screenshots/
```

The main implementation is currently demonstrated through the Jupyter
Notebook.

------------------------------------------------------------------------

## ⚙️ Installation

Create an environment and install the required libraries:

``` bash
pip install opencv-python numpy scikit-learn pillow matplotlib pandas ipywidgets
```

Then launch Jupyter:

``` bash
jupyter notebook
```

or:

``` bash
jupyter lab
```

Open:

``` text
Project.ipynb
```

and run the notebook cells in order.

------------------------------------------------------------------------

## 🧪 Model Training

The machine-learning pipeline follows:

``` text
Training Dataset
      ↓
Train/Test Split
      ↓
Feature Preparation
      ↓
KNN Training
      ↓
Accuracy Evaluation
      ↓
Prediction
```

The trained KNN model is then reused for recognizing digit images
extracted from uploaded expressions.

------------------------------------------------------------------------

## 🛡️ Safety & Validation

The expression solver performs basic input validation before evaluation.

It checks that the reconstructed expression contains only expected
mathematical characters such as:

``` text
0–9
+
-
*
/
(
)
.
```

It also handles common calculation errors such as:

``` text
Division by zero
Invalid expression
Invalid characters
```

------------------------------------------------------------------------

## 🚧 Current Scope & Future Improvements

MathVision AI is a working academic prototype. The current recognition
pipeline is designed around the digit dataset and image formats used
during development.

Possible future improvements:

-   [ ] More robust recognition of arbitrary handwriting
-   [ ] CNN-based digit recognition
-   [ ] Automatic operator classification
-   [ ] Better spacing and multi-digit grouping
-   [ ] Support for fractions
-   [ ] Support for square roots and powers
-   [ ] Bracket-aware expression parsing
-   [ ] Equation solving instead of only expression evaluation
-   [ ] Mobile/web deployment
-   [ ] Voice-based mathematical input
-   [ ] Larger and more diverse training dataset

------------------------------------------------------------------------

## 💡 Why This Project Matters

Traditional calculators require users to manually type mathematical
expressions.

MathVision AI explores a more natural interaction:

> **Instead of typing the equation, show it to the computer.**

The project demonstrates how **Computer Vision + Machine Learning +
Mathematical Processing** can be combined into one practical
application.

------------------------------------------------------------------------

## 👨‍💻 Project Highlights

**Domain:** Computer Vision / Machine Learning\
**Language:** Python\
**Model:** K-Nearest Neighbors (KNN)\
**Computer Vision:** OpenCV\
**Development Environment:** Jupyter Notebook\
**Test Accuracy:** \~98.61%

------------------------------------------------------------------------

## 🔗 Core Architecture

``` text
                    ┌──────────────────┐
                    │   Image Upload   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     OpenCV       │
                    │ Preprocessing    │
                    │ + Thresholding   │
                    │ + Contours       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Character Crops  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   KNN Model      │
                    │ Digit Recognition│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Expression       │
                    │ Reconstruction   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Math Evaluation  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  Final Answer    │
                    └──────────────────┘
```

------------------------------------------------------------------------

## 📌 Note

MathVision AI is developed as an educational project to demonstrate the
integration of image processing, machine learning and mathematical
expression evaluation.

The reported model accuracy belongs to the evaluation dataset used
during development and should not be interpreted as guaranteed accuracy
for every real-world handwritten expression.

------------------------------------------------------------------------

### Built with Python • OpenCV • Machine Learning
