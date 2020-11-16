ARG BASE_IMAGE=ubuntu:18.04
ARG PYTHON_VERSION=3.8

FROM ${BASE_IMAGE}

RUN apt-get update && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
	&& \
    rm -rf /var/lib/apt/lists/*

ADD condarc-tsinghua /root/.condarc

RUN curl -fsSL -v -o ~/miniconda.sh -O  https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
    chmod +x ~/miniconda.sh && \
    ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda install -y python=${PYTHON_VERSION} pyyaml numpy ipython
RUN /opt/conda/bin/conda install jupyterlab
RUN /opt/conda/bin/conda install pytorch torchvision torchaudio cpuonly -c pytorch
RUN /opt/conda/bin/conda install tqdm matplotlib plotly
RUN /opt/conda/bin/conda install -c conda-forge pysnooper
RUN /opt/conda/bin/conda clean -ya
RUN /opt/conda/bin/pip install torchelastic gdown

ENV PATH /opt/conda/bin:$PATH

CMD jupyter lab --ip 0.0.0.0

