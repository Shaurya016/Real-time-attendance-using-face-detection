# Real-time Attendance using Face Detection

## About

This repository implements a simple real-time attendance system using face detection.
It captures faces from a webcam (or video), recognizes known faces, and logs attendance into a CSV file (`attendance.csv`). The project is written in Python and uses OpenCV for image capture and face detection/recognition.

> **Note:** This README is intentionally general so you can adapt the steps to how your code is structured. If you want, I can tailor the instructions to match the exact functions and filenames in your repo after you confirm which script does dataset capture vs recognition.

---

## Features

* Real-time face detection from webcam feed
* Recognize known faces and mark attendance
* Save attendance logs to `attendance.csv`
* Minimal, easy-to-run Python scripts

---

## Repository structure (expected)

```
Real-time-attendance-using-face-detection/
├─ attendance.py        # Main script to run recognition & record attendance
├─ basic.py             # Utility script (e.g. dataset capture / preprocessing)
├─ attendance.csv       # Attendance log (generated/updated at runtime)
├─ LICENSE              # MIT License
└─ README.md            # (this file)
```

> If your repo uses different filenames or folders (for example a `dataset/` or `images/` folder), update the structure above accordingly.

---

## Requirements

* Python 3.8+
* pip

Python packages you will likely need (install with `pip`):

```
pip install opencv-python numpy pandas
```

Depending on the recognition approach used in the code, you might also need one of:

```
pip install face-recognition
# or
pip install opencv-contrib-python
```

`face-recognition` requires dlib and may need a C++ build toolchain on some systems. If you prefer a pure-OpenCV solution, `opencv-contrib-python` provides additional face modules.

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/Shaurya016/Real-time-attendance-using-face-detection.git
cd Real-time-attendance-using-face-detection
```

2. (Optional) Create a virtual environment and activate it:

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt  # if you create this file
# or install manually
pip install opencv-python numpy pandas
```

---

## Usage

Below are common steps to use a face-recognition-based attendance system. Adapt the commands for your repository's specific scripts (`basic.py`, `attendance.py`):

### 1) Prepare or collect face images

* Option A — Manual images: create a folder `dataset/PersonName/` and put a few clear face images for each person.
* Option B — Use `basic.py` (if it captures images): run it to capture webcam images for each person.

Example (manual):

```
mkdir -p dataset/JohnDoe
# copy images into dataset/JohnDoe
```

Example (capture with script):

```
python basic.py
```

Follow on-screen instructions to capture samples for each person.

### 2) Run the attendance script

```bash
python attendance.py
```

* The script should open your webcam, detect faces, and if a detected face matches a known person, their name and timestamp will be appended to `attendance.csv`.
* Press `q` (or the key specified by the script) to quit.

### 3) View attendance logs

Open `attendance.csv` to see the recorded names and timestamps. You can load it into Excel, Google Sheets, or use pandas:

```python
import pandas as pd
df = pd.read_csv('attendance.csv')
print(df.tail())
```

---

## Tips & Troubleshooting

* If face recognition is not accurate, try:

  * Adding more images per person (different angles, lighting)
  * Improving image quality (higher resolution)
  * Using a better recognition backend (e.g., `face-recognition` which uses dlib)
* If `face-recognition` fails to install, try installing `dlib` separately or use the OpenCV-based approach.
* Ensure your webcam is accessible and not used by another program.

---

## Contributing

Contributions are welcome! If you add features (GUI, database backend, web dashboard, or more robust training pipeline) please open an issue or submit a PR.

Suggested improvements:

* Add a `requirements.txt`
* Add a clearer dataset capture script and sample dataset structure
* Add unit tests and linting
* Add a configuration file to control camera index, tolerance levels, and output path

---

## License

This project is released under the MIT License. See the `LICENSE` file for details.

---

If you want, I can:

* Modify this README to include exact commands and options after I inspect the code more closely, or
* Create a `requirements.txt` with the packages inferred from the scripts.

Tell me which you'd prefer.
