# 1. Use an official, lightweight Python image
FROM python:3.11-slim

# 2. Hugging Face requires a specific user setup to run securely
RUN useradd -m -u 1000 user

# 3. Set the working directory inside the container
WORKDIR /code

# 4. Install system tools required by Albumentations and Image processing
RUN apt-get update && apt-get install -y \
    libgl1 \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# 5. Copy your requirements file and install dependencies
COPY --chown=user:user requirements.txt /code/requirements.txt
RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

# 6. Copy all your backend code and models into the container
COPY --chown=user:user . /code

# 7. Switch to the secure user
USER user

# 8. Hugging Face strictly listens on port 7860!
EXPOSE 7860

# 9. Start the FastAPI server on port 7860
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "7860"]