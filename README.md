from pathlib import Path

# Smart Parking Space Detection System

> **Computer Vision • OpenCV • Machine Learning • Python**

A computer-vision project that analyzes a parking-lot video and identifies parking spaces as **empty or occupied**. It combines image processing with a trained Support Vector Machine (SVM) classifier to help visualize parking availability from video footage.

---

## ✨ Project Highlights

- **Automated parking-space analysis** — processes a parking-lot video frame by frame.
- **Empty vs. occupied classification** — uses a trained SVM model to classify parking-space image regions.
- **Mask-based space detection** — uses a parking-space mask to identify the regions that should be analyzed.
- **Visual output** — overlays the detected parking-space status on the video to make availability easier to inspect.
- **Practical computer-vision workflow** — demonstrates how video processing, image segmentation, and a machine-learning classifier can work together.

## 🎯 Why This Project?

Finding an available parking spot can be frustrating in busy parking areas. A camera-based parking-monitoring system can help make parking availability easier to understand by analyzing footage and marking spaces as empty or occupied.

This project is a learning-oriented prototype of that idea. It demonstrates the core pipeline behind a parking-space monitoring system; it is not presented as a production-ready deployment.

## 🧠 How It Works

1. **Load the parking video**  
   OpenCV reads the input video frame by frame.

2. **Load the parking-space mask**  
   The mask identifies the parking-space regions to examine.

3. **Identify individual spaces**  
   Image-processing operations are used to locate the relevant regions from the mask.

4. **Prepare each region for prediction**  
   The parking-space image regions are processed into features suitable for the trained classifier.

5. **Classify each space**  
   The saved SVM model (`model.p`) predicts whether a parking-space region is empty or occupied.

6. **Visualize the result**  
   The application displays the video with the predicted parking-space status overlaid.

### Pipeline at a glance

`Parking video` → `Frame extraction` → `Mask / space regions` → `SVM classification` → `Annotated video`

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| OpenCV | Video reading and image processing |
| NumPy | Numerical and array operations |
| scikit-learn | SVM classifier used for parking-space classification |
| Pickle | Loading the saved model (`model.p`) |
| Matplotlib / Pillow / scikit-image / pandas | Supporting libraries listed in the project requirements |

## 📁 Project Structure

```text
parking-space-counter/
├── main.py                     # Main video-processing pipeline
├── util.py                      # Helper functions, including classification utilities
├── model.p                      # Saved machine-learning model
├── mask_1920_1080.png           # Parking-space mask used by the pipeline
├── mask_crop.png                # Cropped mask asset
├── samples/
│   └── parking_1920_1080_loop.mp4  # Input parking-lot video
├── clf-data/
│   ├── empty/                   # Example images for empty spaces
│   └── non-empty/               # Example images for occupied spaces
├── requirements.txt             # Python dependencies
└── README.md                    # Project documentation
```

*Note: File and folder names shown above reflect the expected project layout. If your local copy differs, use the names present in your repository.*

## ⚙️ Setup and Installation

### Prerequisites

- Windows, macOS, or Linux
- Python installed
- Git (optional, for cloning the repository)

### 1. Clone or download the project

If the project is hosted on GitHub, clone your repository:

```bash
git clone <YOUR_REPOSITORY_URL>
cd parking-space-counter
```

Alternatively, download the ZIP and extract it.

### 2. Create a virtual environment

**Windows PowerShell:**

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, you can use Command Prompt instead:

```bat
venv\Scripts\activate.bat
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

> **Dependency note:** This project uses older scientific Python packages and a pre-trained pickle model. Depending on your Python version, some original package versions may not install cleanly. If installation fails, check package compatibility and use a compatible set of versions rather than assuming the source code is broken.

### 4. Check the required assets

Before running, confirm that these files exist in the expected locations:

- `model.p`
- `mask_1920_1080.png`
- `samples/parking_1920_1080_loop.mp4`

The input video and mask are important: the mask is designed for the corresponding parking-lot view, so changing the video or its dimensions may require a matching mask.

## ▶️ Run the Project

Activate your virtual environment, navigate to the project root, and run:

```bash
python main.py
```

The application should open a video window and display the parking-space classifications. Use the window controls or the exit behavior implemented by the project to close the application.

If the video does not open, verify the video path in `main.py` and make sure you are running the command from the project root.

## 🧪 Dataset and Model

The project includes example image folders for two categories:

- `clf-data/empty/`
- `clf-data/non-empty/`

It also includes a serialized model in `model.p`. The application loads this saved model rather than training a new one every time it runs.

**Important:** Pickled scikit-learn models can be sensitive to library-version differences. A warning that the model was saved with a different scikit-learn version means compatibility should be checked, even if the file loads successfully. Only load pickle files from sources you trust.

## 📌 Current Scope and Limitations

- The included mask is tailored to a particular camera view and parking-lot layout.
- Results depend on video quality, lighting, occlusion, camera angle, and the trained classifier.
- A different parking lot may require a new mask and model evaluation.
- The repository demonstrates a prototype workflow; real-world deployment would need testing, robustness checks, and performance evaluation.

## 🚀 Possible Future Improvements

- Display a live count of available and occupied spaces.
- Add configurable support for different parking-lot layouts.
- Evaluate classification accuracy on a labeled test set.
- Add confidence scores and error analysis.
- Build a web dashboard for monitoring parking availability.
- Explore real-time camera input and deployment on edge devices.

## 💡 What This Project Demonstrates

This project brings together several useful concepts:

- Reading and processing video with OpenCV
- Using masks to define regions of interest
- Extracting and analyzing image regions
- Applying a trained machine-learning classifier
- Combining computer vision and ML in a practical application


