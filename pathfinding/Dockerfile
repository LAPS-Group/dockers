FROM pytorch/pytorch
RUN apt-get update && apt-get install -y --no-install-recommends \
	build-essential curl \
	python3.6 python3-pip \
	python3-dev git \
	python3-setuptools

COPY requirements.txt requirements.txt
RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install --no-cache-dir -r requirements.txt --src /usr/local/src
RUN python3 -m pip install --no-cache-dir \
                           torch-scatter==latest+cu101 \
                           torch-sparse==latest+cu101  \
                           -f https://pytorch-geometric.com/whl/torch-1.4.0.html \
                           --src /usr/local/src

WORKDIR /workspace

EXPOSE ${PORT}

# Launch Jupyter notebook
CMD jupyter notebook --allow-root --port=${PORT} --ip=0.0.0.0 --no-browser
