# Drawing Emotion → Parent Report

Classify the emotion expressed in a child’s drawing (e.g., *happy, sad, angry, afraid*) and generate a concise, parent‑friendly description with gentle guidance.



## Features
- 🖼️ **Emotion classification** from an input image (PNG/JPG).
- 📝 **Parent report generation**: short explanation of cues + supportive tips (non‑diagnostic).
- 🧰 Simple CLI for quick inference.
- 📦 Minimal dependencies and easy setup.

## Project Structure (suggested)
```
.
├── drawing_emotion_pipeline.py   # main script 
├── requirements.txt
└── README.md
```

## Installation
Use Python 3.10+.
```bash
git clone <YOUR_REPO_URL>.git
cd <YOUR_REPO_NAME>

# Rename the original file (if needed)
git mv  drawing_emotion_pipeline.py

python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

pip install --upgrade pip
pip install -r requirements.txt
```

## Usage
**Classify and generate a parent report:**
```bash
python drawing_emotion_pipeline.py   --image path/to/drawing.png   --labels "happy,sad,angry,afraid"   --report   --out parent_report.txt
```
**Classify only (no text report):**
```bash
python drawing_emotion_pipeline.py --image path/to/drawing.png --labels "happy,sad,angry,afraid"
```

**Common CLI flags (adapt to your script if names differ):**
- `--image`: path to the drawing image (PNG/JPG).
- `--labels`: comma‑separated emotion classes (default: `happy,sad,angry,afraid`).
- `--report`: include to generate a parent‑friendly description.
- `--out`: optional path to save the generated report (e.g., `parent_report.txt`).

### Example Output
```
Predicted emotion: angry (0.78)
Parent report saved to: parent_report.txt
```

## How it works (high‑level)
1. **Preprocess image** → resize/normalize (Pillow/OpenCV).
2. **Classifier** → predicts the emotion.
3. **Parent report** → templates or a small local language model via `transformers` conditioned on the predicted emotion.

> If you switch to API‑based text generation, replace local `transformers` calls and update `requirements.txt` accordingly.

## Notes & Ethics
- This tool is **educational** and **not diagnostic**. Drawings are influenced by many factors; interpret with care.
- Keep images private and anonymized when sharing results.

