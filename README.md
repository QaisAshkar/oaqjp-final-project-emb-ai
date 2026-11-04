# Emotion Detector: AI-Powered Text Analysis

A Flask web app that detects the emotions in a piece of text using **IBM Watson NLP**. Type a sentence and get back scores for **anger, disgust, fear, joy and sadness**, plus the dominant emotion.

Built as the final project of the IBM *Developing AI Applications with Python and Flask* course.

## Example

```
GET /emotionDetector?textToAnalyze=I am glad this happened

For the given statement, the system response is 'anger': …, 'disgust': …,
'fear': …, 'joy': … and 'sadness': …. The dominant emotion is joy.
```

## Features

- **Watson NLP integration.** Calls the Watson `EmotionPredict` endpoint and parses its JSON response.
- **Reusable Python package.** The logic lives in the `EmotionDetection` package, separate from the web layer.
- **Dominant emotion.** Picks the highest-scoring emotion automatically.
- **Error handling.** Blank or invalid input (HTTP 400 from the API) returns a friendly "Invalid text!" message instead of crashing.
- **Unit tests.** `test_emotion_detection.py` checks the dominant emotion for sample sentences covering all five emotions.
- **Documented code.** The Flask server has module and function docstrings, written to pass static analysis.

## Project structure

```
├── EmotionDetection/
│   ├── __init__.py
│   └── emotion_detection.py    calls Watson NLP and formats the result
├── templates/index.html        web UI
├── static/mywebscript.js       sends the text to the server and shows the response
├── server.py                   Flask app (routes: / and /emotionDetector)
└── test_emotion_detection.py   unit tests
```

## Running it

```bash
pip install flask requests
python server.py               # http://localhost:5000
python -m unittest test_emotion_detection.py
```

> The Watson endpoint used here is hosted by the IBM Skills Network lab environment.

## Tech stack

Python · Flask · IBM Watson NLP · REST APIs · unittest
