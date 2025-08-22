FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000  # Change this to your backend's port

CMD ["python", "app.py"]  # Replace with your actual entry point