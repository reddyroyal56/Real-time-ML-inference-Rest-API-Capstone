# Task 06 — Real-Time ML Inference REST API & Capstone

## Project
IMDB Movie Review Sentiment Classifier

This project deploys the Task 05 NLP/deep-learning classifier as a real-time
REST API using FastAPI and Docker.

## Architecture

Client → FastAPI `/predict` → Saved Keras model
                              ↓
                         TF-IDF vectorization
                              ↓
                     Neural network classifier
                              ↓
                 Positive/Negative + confidence

## Files

- `app.py` — FastAPI production API
- `prepare_model.py` — creates the deployable Keras model
- `imdb_sentiment_api.keras` — generated trained model
- `requirements.txt` — Python dependencies
- `Dockerfile` — container configuration
- `test_api.py` — API tests
- `README.md` — documentation

## Step 1 — Create the model

If you already executed Task 05 and want to deploy the exact trained model,
add this to the final Task 05 notebook cell:

```python
api_model = tf.keras.Sequential([vectorizer, model])
api_model.save("imdb_sentiment_api.keras")
```

Otherwise run:

```bash
python prepare_model.py
```

The training script uses the same IMDB + TF-IDF + Dense/BatchNorm/Dropout
architecture and Early Stopping as Task 05.

## Step 2 — Install dependencies

```bash
pip install -r requirements.txt
```

## Step 3 — Run the API locally

```bash
uvicorn app:app --reload
```

Open:

- API: http://127.0.0.1:8000
- Swagger documentation: http://127.0.0.1:8000/docs
- ReDoc documentation: http://127.0.0.1:8000/redoc

## API endpoints

### GET /

Checks whether the service is running.

### GET /health

Checks whether the trained model has loaded.

### POST /predict

Request:

```json
{
  "review": "This movie was fantastic and beautifully acted."
}
```

Example response:

```json
{
  "prediction": "Positive",
  "confidence": 0.91
}
```

The actual confidence depends on the trained model.

## Docker

Build the image:

```bash
docker build -t imdb-sentiment-api .
```

Run:

```bash
docker run --rm -p 8000:8000 imdb-sentiment-api
```

Open:

http://localhost:8000/docs

## Testing

With the API/model available:

```bash
pytest -q
```

## Submission proof

Take screenshots of:

1. `app.py`, `requirements.txt`, `Dockerfile`, and model file.
2. FastAPI `/docs` page.
3. Successful `GET /health`.
4. Successful `POST /predict` with response.
5. `docker build` completing successfully.
6. API `/docs` working through `localhost:8000` after Docker run.

## Task 06 completion checklist

- [x] FastAPI REST service
- [x] Health endpoint
- [x] Prediction endpoint
- [x] Confidence output
- [x] Automatic Swagger API documentation
- [x] Dockerfile
- [x] Docker run instructions
- [x] API tests
- [x] Complete README
- [ ] Generate `imdb_sentiment_api.keras` by executing Task 05 export cell or `prepare_model.py`
- [ ] Build and run Docker locally
- [ ] Capture submission screenshots
