# Hand Sign Reader

A Grade 11 Computer Vision project. Show a common hand sign to your webcam and the app names it and gives its meaning. No recording and no training needed.

## Signs it recognises

Thumbs up, Peace, OK, Shaka, Vulcan salute, Heart hands (two hands), Pinched fingers, Sign of the horns, I love you, Come here.

## Pipeline

```
Camera frame -> Hand landmarks -> Finger rules -> Prediction -> Meaning
```

| Stage | In this project |
|---|---|
| Input | Webcam frame |
| Features | 21 landmarks per hand from MediaPipe Hands, a model that is already trained |
| Rules | Fixed IF / THEN rules on which fingers are up, plus distances between fingertips |
| Prediction | The sign whose rule matches, smoothed over the last 8 frames |
| Meaning | The sign's name and meaning shown on screen |

## What is pre-trained and what is not

- The **hand landmark model** (MediaPipe) is pre-trained machine learning.
- The **sign recognition** is a hand-written rule set, not a trained classifier. This makes every decision explainable (the "Finger states" chips show what the rules see), but it is less flexible than a trained model.

## Known limits

- Look-alike signs (Shaka, I love you, Horns) and "Come here" are the easiest to confuse.
- Hand angle, distance and lighting change the landmarks and can break a rule.
- Heart hands needs both hands close together and clearly visible.

## Run locally

```
python -m http.server 8000
```

Then visit http://localhost:8000

## Publish on GitHub Pages

Settings > Pages > Deploy from a branch > `main` > `/ (root)`. The camera needs https, which GitHub Pages provides.
