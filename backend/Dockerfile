FROM python:3.13-slim

# Set working directory
WORKDIR /app

# Install system dependencies for building reportlab and other Python packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libfreetype6-dev \
    libjpeg-dev \
    zlib1g-dev \
    libpng-dev \
 && rm -rf /var/lib/apt/lists/*

# Copy requirements and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files, templates, and static assets
COPY app.py .
COPY templates ./templates
COPY static ./static

# Run the Flask app
CMD ["python", "app.py"]
