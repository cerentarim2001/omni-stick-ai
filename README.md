# omni-stick-ai
AI Model for the Omni-Stick Project for IDE Fundamentals

## What's here

The Omni Stick's core AI feature: predicting a stumble/fall **before** it happens from motion
sensor data, so the stick can lock its rolling-ball tip into a solid anchor in time.

- `notebooks/fall_detection.ipynb` — main Colab notebook. Loads KFall sensor data, trains a
  small 1D-CNN to predict falls ~0.4s before impact, evaluates it, and shrinks it to a
  `.tflite` file small enough for a microcontroller.
- `data/` — put local KFall CSVs here if working outside Drive (gitignored — don't commit
  the raw dataset).

## Dataset

[KFall](https://www.frontiersin.org/journals/aging-neuroscience/articles/10.3389/fnagi.2021.692865/full) —
a public dataset of IMU (accelerometer + gyroscope) recordings of ~30 people doing normal daily
activities and simulated falls, with the exact fall-onset and impact frames labeled. Requires a
short access request before download.

## Running the notebook

1. Open `notebooks/fall_detection.ipynb` in Colab:
   `colab.research.google.com/github/cerentarim2001/omni-stick-ai/blob/main/notebooks/fall_detection.ipynb`
2. Update `KFALL_ZIP_PATH` in Step 2 to point to your uploaded KFall zip in Google Drive.
3. Run top to bottom. Cells marked ⚠️ need small tweaks once you've inspected KFall's real
   column names and label format (Step 3 shows you what to expect).

## Pushing changes back from Colab

```python
!git config --global user.email "you@example.com"
!git config --global user.name "Your Name"
!git clone https://<TOKEN>@github.com/cerentarim2001/omni-stick-ai.git
%cd omni-stick-ai
# ...make changes...
!git add .
!git commit -m "your message"
!git push
```
