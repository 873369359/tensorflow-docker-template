FROM nvidia/cuda:8.0-cudnn5-devel
#FROM registry.cn-hangzhou.aliyuncs.com/873369359/cuda8.0_on_ubuntu16.04：latest

#RUN CUDNN_DOWNLOAD_SUM=a87cb2df2e5e7cc0a05e266734e679ee1a2fadad6f06af82a76ed81a23b102c8 && \
#    curl -fsSL http://developer.download.nvidia.com/compute/redist/cudnn/v5.1/cudnn-8.0-linux-x64-v5.1.tgz -O && \
#   echo "$CUDNN_DOWNLOAD_SUM  cudnn-8.0-linux-x64-v5.1.tgz" | sha256sum -c --strict - && \
#    tar -xzf cudnn-8.0-linux-x64-v5.1.tgz  && cp ./cuda/lib64/libcudnn.so.* /usr/local/nvidia/lib && cp ./cuda/lib64/libcudnn.so.* /usr/local/nvidia/lib64  && \
#    rm cudnn-8.0-linux-x64-v5.1.tgz && \
#    ldconfig


RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    libfreetype6-dev \
    libpng12-dev \
    libzmq3-dev \
    pkg-config \
    python \
    python-dev \
    rsync \
    git \
    software-properties-common \
    unzip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    curl -o get-pip.py https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py && \
    rm get-pip.py

RUN pip3 --no-cache-dir install \
    numpy \
    scipy \
    pandas

# Install TensorFlow GPU version from central repo
#RUN pip3 --no-cache-dir install https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0-cp34-cp34m-linux_x86_64.whl
RUN pip3 --no-cache-dir install https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.0-cp34-cp34m-linux_x86_64.whl

# Install Keras as blessed lightweight framework, sklearn for metrics, etc.
RUN pip3 install sklearn
RUN pip3 install --upgrade git+https://github.com/fchollet/keras.git

EXPOSE 6006
CMD ["python3"]
