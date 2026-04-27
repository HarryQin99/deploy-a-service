# ----------------------
# Stage 1: build stage
# ----------------------
FROM python:3.11-slim AS builder

WORKDIR /app

COPY requirements.txt .

RUN pip install --user -r requirements.txt

# ----------------------
# Stage 2: runtime stage
# ----------------------
FROM python:3.11-slim

WORKDIR /app

# copy only installed dependencies
COPY --from=builder /root/.local /root/.local

# copy app code
COPY . .

ENV PATH=/root/.local/bin:$PATH

EXPOSE 8080

CMD ["python", "main.py"]
