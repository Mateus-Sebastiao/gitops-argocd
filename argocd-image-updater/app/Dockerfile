FROM python:3.11-slim AS builder

WORKDIR /src

COPY requirements.txt .

RUN pip install --upgrade pip && \
    pip install --prefix=/install -r requirements.txt

FROM python:3.11-slim

WORKDIR /src

COPY --from=builder /install /usr/local
COPY . .

EXPOSE 8080

CMD ["gunicorn", "--bind", "0.0.0.0:8080", "app:app"]