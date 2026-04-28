# Image Feature-Based Prediction using Linear Regression

## Project Overview
This project extracts visual features from images (brightness and edge count)
and uses Linear Regression to predict a simulated "price" value.
It demonstrates the integration of image processing (OpenCV) with
machine learning (Scikit-learn) — a practical example of feature engineering.

---



---

## 🌐 Live Demo

🚀 Experience the application live:  

👉 [Launch Streamlit App](https://image-feature-based-prediction-d5uecvhexyzhxlcfj4t2j5.streamlit.app/)

> Click the link above to open the deployed app and try image-based predictions in real time.

---

## Technologies Used
| Library       | Purpose                                      |
|---------------|----------------------------------------------|
| NumPy         | Numerical operations on pixel arrays         |
| Pandas        | Dataset creation and CSV export              |
| Matplotlib    | Plotting graphs and displaying images        |
| OpenCV (cv2)  | Image loading, grayscale, edge detection     |
| Scikit-learn  | Linear Regression model, train/test split    |

---

## Project Structure
```
image_regression/
├── main.py                      # Main project code
├── generate_sample_images.py    # Helper: creates test images
├── requirements.txt             # Python dependencies
├── images/                      # Folder for input images (you create this)
├── image_features_dataset.csv   # Output: dataset with predictions
├── output_plots.png             # Output: prediction graphs
└── sample_image_comparison.png  # Output: before/after grayscale
```

---

## How to Run

### Step 1 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 2 — Add images
Either place your own `.jpg` / `.png` images in the `images/` folder,
OR run the sample image generator:
```bash
python generate_sample_images.py
```

### Step 3 — Run the project
```bash
python main.py
```

---

## How the Code Works (Step-by-Step)

1. **Load Images** — Scans the `images/` folder and loads all `.jpg`/`.png` files using OpenCV.

2. **Grayscale Conversion** — Each color (BGR) image is converted to grayscale using `cv2.cvtColor`.

3. **Feature Extraction**
   - *Brightness*: `np.mean(gray)` — average pixel intensity (0–255).
   - *Edge Count*: `cv2.Canny()` detects edges; we count non-zero pixels.

4. **Dataset Creation** — Features are stored in a Pandas DataFrame with columns: `filename`, `brightness`, `edges`.

5. **Target Variable** — `price = brightness × 0.5 + edges × 0.01` (a deterministic formula to simulate a real-world target).

6. **Model Training** — `LinearRegression` from Scikit-learn is trained on 80% of the data.

7. **Prediction** — The model predicts `price` for all images; results are added to the DataFrame.

8. **Visualization** — Two plots are generated:
   - Actual vs Predicted price (scatter with ideal-fit line)
   - Brightness vs Price (actual and predicted overlaid)

9. **CSV Export** — The full dataset including predictions is saved as `image_features_dataset.csv`.

---


