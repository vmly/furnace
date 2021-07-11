FROM apache/airflow:2.1.0

USER root
RUN apt update -y
RUN apt upgrade -y
RUN apt install -y git

RUN mkdir -p /tmp/lib/
RUN chmod +rwx /tmp/lib/
RUN chmod 777 -R /tmp/lib/

USER airflow
ARG AIRFLOW_HOME=/opt/airflow

COPY docker/airflow/requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

COPY src/furnace_lib /tmp/lib

# Install custom Python lib
RUN cd /tmp/lib && python setup.py install --user