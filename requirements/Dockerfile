
# Use the official Ubuntu 20.04 base image
FROM ubuntu:22.04

# Set environment variables for configuration
ENV PYTHON_VERSION=3.10

# Set default values for environment variables
ENV PYTHONPATH=/usr/local/lib/python${PYTHON_VERSION}/dist-packages

# Set maintainer label
LABEL maintainer="glenn.s.tamkin@nasa.gov"

# Update the package lists and install necessary packages
RUN apt-get update && \
    apt-get install -y \
    python${PYTHON_VERSION} \
    python${PYTHON_VERSION}-dev \
    python${PYTHON_VERSION}-distutils \
    python${PYTHON_VERSION}-venv \
    fftw \
    numpy \
    scipy \
    matplotlib \
    meson \
    pkg-config \   
    ninja \
    && rm -rf /var/lib/apt/lists/*

# Set the default Python version
RUN update-alternatives --install /usr/bin/python python /usr/bin/python${PYTHON_VERSION} 1

# Set the default Python version for pip
RUN update-alternatives --install /usr/bin/pip pip /usr/bin/pip${PYTHON_VERSION} 1

# Verify the Python installation
RUN python --version && \
    pip --version

# Set the working directory
WORKDIR /app

# Copy the requirements file to the working directory
COPY ./requirements.txt .

# Install the Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code to the working directory
COPY . .

# Set the command to run the application
CMD ["python", "app.py"]

HEALTHCHECK NONE
ENTRYPOINT [""]
