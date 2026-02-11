FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    STREAMLIT_SERVER_HEADLESS=true

WORKDIR /app

RUN adduser --system --no-create-home appuser

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

RUN chown -R appuser /app
USER appuser

ENV PORT=8501

CMD ["sh", "-c", "streamlit run app.py --server.port=${PORT} --server.address=0.0.0.0"]
