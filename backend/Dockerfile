# stage 1: build dependencies
FROM python:3.10-slim as builder

WORKDIR /app

COPY requirements.txt .

RUN pip install --user -r requirements.txt

# ------------------------------------------------

# stage 2: Runtime
FROM python:3.10-slim

ENV PATH=/root/.local/bin:$PATH

WORKDIR /app

COPY --from=builder /root/.local /root/.local

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
