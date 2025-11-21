# Sanjivani_Plant_Identification

Plant identification toolkit — image-based plant identification with a simple web interface and utility scripts.

**Repository:** [ https://github.com/Mayur-156/Sanjivani_Plant_Identification.git]( https://github.com/Mayur-156/Sanjivani_Plant_Identification.git)

---

## What this repo contains (quick scan)

* `app.py` — main web application entrypoint (Flask / simple web UI).
* `Sanjivani_main.py` — high-level script to run the application flow or start modules.
* `Sanjivani_identification.py` — image processing / identification logic (model pipeline or heuristics).
* `Sanjivani_dashboard.py` — dashboard or visualization script.
* `Sanjivani_plant_info.py` — plant information lookup utility.
* Several image files in repo (example: `111.jpg`, `2.jpg`, `aa.jpg`, and WhatsApp image files) used as sample inputs.

---

## Prerequisites

* Python 3.8+ installed
* git
* (Optional) Virtual environment tool: `venv` (built-in) or `virtualenv`

---

## Recommended Python packages

This repository doesn't include a `requirements.txt` (if it does, use it). Common packages used in plant-identification projects that the code likely requires:

```
flask
opencv-python
numpy
pillow
scikit-learn
pandas
matplotlib
tensorflow  # or keras
torch       # if the project uses PyTorch
```

You can create a `requirements.txt` after verifying imports in the files:

```bash
pip freeze > requirements.txt
```

---

## Quick start — run locally

1. Clone the repository:

```bash
git clone https://github.com/Vaibhavjare/Sanjivani_Plant_Identification.git
cd Sanjivani_Plant_Identification
```

2. Create and activate a virtual environment:

```bash
python -m venv venv
# mac / linux
source venv/bin/activate
# windows (PowerShell)
venv\Scripts\Activate.ps1
```

3. Install dependencies (either from a provided `requirements.txt` or the recommended list above):

```bash
pip install -r requirements.txt
# or example:
pip install flask opencv-python numpy pillow scikit-learn pandas matplotlib
```

4. Run the web app. The repo contains `app.py`; try running it:

```bash
python app.py
```

If `app.py` does not start a server, try the other entrypoints:

```bash
python Sanjivani_main.py
python Sanjivani_dashboard.py
```

5. Visit the local URL printed by the app (commonly `http://127.0.0.1:5000` for Flask).

---

## Typical troubleshooting

* **Missing packages / ImportError**: open the referenced `.py` file and note the top `import` lines. Install any missing libraries via `pip`
* **Model / weights missing**: if the identification code expects pre-trained model files (often `.h5`, `.pt`, or `.pkl`), you must place them in the correct folder or retrain the model. Search the code for filenames referenced (e.g., `model.h5`) and add those files.
* **Image path errors**: sample images in the repo are small; make sure the code points to the right relative path (e.g., `images/111.jpg`).
* **Permissions / Encoding issues for WhatsApp images**: rename or convert files if necessary.

---

## How to prepare a `requirements.txt`

While inside the activated virtualenv, install all packages you need and then run:

```bash
pip freeze > requirements.txt
```

Commit `requirements.txt` to the repo so others can reproduce easily.

## Quick deployment notes

**Deploy to a simple PaaS** (Railway / Render / Heroku): build a `requirements.txt` and a simple `Procfile` with:

```
web: gunicorn app:app
```

(Replace `app:app` with the correct module:variable if `app` exports a Flask `app` object with a different name.)

**Deploy to a VPS**: install Python, create venv, run using `gunicorn` behind `nginx` and `systemd`.

---

