FROM python:3.13-slim

WORKDIR /app

# Install system deps for packages like reportlab
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libfreetype6-dev \
    libjpeg-dev \
    zlib1g-dev \
    libpng-dev \
 && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy everything (app, templates, static, etc.)
COPY . .

CMD ["python", "app.py"]
