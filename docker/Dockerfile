FROM pytorch/pytorch:1.9.1-cuda11.1-cudnn8-devel

# apt
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get update && apt-get upgrade -y && \
    apt-get -y install git libgl1-mesa-glx libglib2.0-0 libomp-dev wget unzip software-properties-common

# install timm
RUN cd /home/ && \
    git clone https://github.com/rwightman/pytorch-image-models.git && \
    cd pytorch-image-models && \
    python3 setup.py bdist_wheel && \
    python3 -m pip install dist/timm-*.whl

# python packages
COPY requirements.txt /tmp/requirements.txt
RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install -r /tmp/requirements.txt && \
    rm /tmp/requirements.txt