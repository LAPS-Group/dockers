FROM pytorch/pytorch
RUN apt-get update && apt-get install -y --no-install-recommends \
	build-essential curl \
	python3.6 python3-pip \
	python3-dev git \
	python3-setuptools
RUN pip3 install --upgrade pip

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
RUN rm requirements.txt

WORKDIR /workspace

EXPOSE 8888

# Launch Jupyter notebook
CMD ["jupyter", "notebook", "--allow-root", "--port=8888", "--ip=0.0.0.0", "--no-browser"]
