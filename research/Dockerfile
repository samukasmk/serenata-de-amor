FROM jupyter/datascience-notebook:latest
LABEL maintainer "Data Science Brigade <contato@datasciencebr.com>"

USER root

RUN apt-get install unzip -y --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

USER jovyan

COPY jupyter_notebook_config.py /home/jovyan/.jupyter/jupyter_notebook_config.py

RUN mkdir /home/jovyan/research
WORKDIR /home/jovyan/research

COPY conda_requirements.txt ./
RUN conda config --add channels conda-forge \
    && conda install --yes --file conda_requirements.txt
COPY requirements.txt ./
RUN pip install --upgrade pip
RUN pip install --upgrade -r requirements.txt
