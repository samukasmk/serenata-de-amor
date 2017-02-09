FROM jupyter/datascience-notebook:latest
LABEL maintainer "Data Science Brigade <contato@datasciencebr.com>"

USER root

RUN apt-get update \
    && apt-get install unzip -y --no-install-recommends \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER jovyan

RUN pip install --upgrade pip

COPY jupyter_notebook_config.py /home/jovyan/.jupyter/jupyter_notebook_config.py

RUN mkdir /home/jovyan/research
WORKDIR /home/jovyan/research

COPY conda_requirements.txt ./
COPY config.ini.example ./
COPY requirements.txt ./
COPY setup ./
RUN ./setup
