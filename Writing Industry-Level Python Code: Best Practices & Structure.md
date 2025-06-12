# 🏢 Writing Industry-Level Python Code: Best Practices & Structure

This guide outlines how to structure Python code in a clean, scalable, and maintainable way for production-grade or enterprise-level applications.

---

## 📁 Project Structure Example

```plaintext
my_project/
├── app/
│   ├── __init__.py
│   ├── config.py         # Configuration management
│   ├── schema.py         # Input/output data schema (e.g., Pydantic, Marshmallow)
│   ├── models.py         # Core model logic / ML models
│   ├── services.py       # Business logic or pipelines
│   ├── utils.py          # Utility/helper functions
│   ├── logger.py         # Logging setup
│   └── main.py           # Entry point / application launcher
│
├── tests/
│   ├── test_models.py
│   └── test_services.py
│
├── data/                # Data input/output if required
├── notebooks/           # Jupyter notebooks (EDA, experimentation)
├── requirements.txt     # Python dependencies
├── .env                 # Environment variables
├── .gitignore
└── README.md
```

---

## ⚙️ config.py
Manage all environment variables and settings in one place.

```python
import os
from dotenv import load_dotenv

load_dotenv()

class Config:
    DEBUG = os.getenv("DEBUG", False)
    MODEL_PATH = os.getenv("MODEL_PATH", "./models/model.pkl")
    DATABASE_URL = os.getenv("DATABASE_URL")
```

---

## 🧾 schema.py
Define data validation schemas using Pydantic (for FastAPI) or Marshmallow.

```python
from pydantic import BaseModel

class InputData(BaseModel):
    text: str
    user_id: int

class OutputData(BaseModel):
    sentiment: str
    confidence: float
```

---

## 🧠 models.py
Load and apply ML/DL models.

```python
import joblib
from app.config import Config

class SentimentModel:
    def __init__(self):
        self.model = joblib.load(Config.MODEL_PATH)

    def predict(self, text):
        return self.model.predict([text])
```

---

## 🔁 services.py
Write the business logic or ML pipelines.

```python
from app.models import SentimentModel
from app.schema import InputData, OutputData

model = SentimentModel()

def get_sentiment(data: InputData) -> OutputData:
    prediction = model.predict(data.text)
    return OutputData(sentiment=prediction[0], confidence=0.95)
```

---

## 🛠 utils.py
Reusable utility functions.

```python
import re

def clean_text(text):
    return re.sub(r"[^a-zA-Z0-9 ]", "", text).lower()
```

---

## 📓 logger.py
Set up structured logging.

```python
import logging

logging.basicConfig(
    format='%(asctime)s - %(levelname)s - %(message)s',
    level=logging.INFO
)
logger = logging.getLogger(__name__)
```

---

## 🚀 main.py
Your application’s entry point (e.g., for APIs or scripts).

```python
from app.schema import InputData
from app.services import get_sentiment

if __name__ == '__main__':
    sample = InputData(text="I love this product!", user_id=1)
    result = get_sentiment(sample)
    print(result)
```

---

## ✅ Tips
- Follow PEP8 & use linters (like flake8, black).
- Use virtual environments (venv, poetry, conda).
- Write unit tests and use test coverage tools.
- Separate config, business logic, and model logic.
- Use logging instead of print statements.
- Avoid hardcoding values—use `.env` files.

---
