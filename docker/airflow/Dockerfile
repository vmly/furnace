FROM apache/airflow:2.1.0

USER root
RUN apt update -y
RUN apt upgrade -y
RUN apt install -y git

USER airflow
ARG AIRFLOW_HOME=/opt/airflow

COPY docker/airflow/requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

# Install custom Python lib
COPY src/lib /tmp/lib
RUN cd /tmp/lib && python setup.py install