
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
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# # Set the default Python version
# RUN update-alternatives --install /usr/bin/python python /usr/bin/python${PYTHON_VERSION} 1

# # Set the default Python version for pip
# RUN update-alternatives --install /usr/bin/pip pip /usr/bin/pip${PYTHON_VERSION} 1
RUN ls -al /usr/bin/p*

# Verify the Python installation
# RUN /usr/bin/python3 --version && \
#     pip --version
#RUN /usr/bin/pip3 install --upgrade pip3
RUN /usr/bin/python3 --version 
RUN /usr/bin/pip3 --version 

# Install the po3 dependencies 
#RUN /usr/bin/pip3 install fftw numpy scipy matplotlib meson pkg-config ninja meson-python setuptools setuptools-scm
RUN /usr/bin/pip3 install numpy scipy matplotlib meson ninja meson-python setuptools setuptools-scm

# # Set the working directory
WORKDIR /app

# # Copy the requirements file to the working directory
# COPY ./requirements.txt .

# # Install the Python dependencies
# RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code to the working directory
#RUN cd /app
#https://github.com/nasa-nccs-hpda/FMOrbit.git
ADD https://github.com/nasa-nccs-hpda/FMOrbit.git /app
#RUN ls -al ..
#ADD ../pyorbit3 pyorbit3/
#COPY ../pyorbit3/**/* /pyorbit3
#COPY . .
#RUN ls -alR / 
RUN ls -alR /app 
#RUN ls -alR ..

# # Set the command to run the application
# CMD ["python", "app.py"]

HEALTHCHECK NONE
#ENTRYPOINT [""]
