# Intent Classifier Model

This small project demonstrates:
- Training a tiny text classifier.
- Saving the model artifact.
- Serving predictions via a Flask API (`/predict`).

## Quick start (local)
1. Create a virtualenv and install:
    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt

2. Train the model:
    python model/train.py
    This will create `model/artifacts/intent_model.pkl`.

3. Run the API:
    python app.py
    The API will be available at http://127.0.0.1:6000

4. Example request:
    curl -X POST http://127.0.0.1:6000/predict -H "Content-Type: application/json" -d '{"text":"I want to cancel my subscription"}'

    Response:
    {
        "intent": "complaint",
        "probabilities": {"complaint": 0.85, "question": 0.05, ...}
    }

# ✅ Correct command to resolve ELB DNS

✔ Use hosts database

getent hosts <your elb address>


If DNS is working, you’ll get output like:

    13.xxx.xxx.xxx   a65bc5e7a62364b3a80fb6a50cbac397-1689525846.ap-south-1.elb.amazonaw

Take Ip of output then


     curl -X POST --resolve example.com:80:13.xxx.xx.xxx http://example.com/predict -H "Content-Type: application/json" -d '{"text":"I want to cancel my subscription"}'

o/p

{"intent":"complaint"} 
