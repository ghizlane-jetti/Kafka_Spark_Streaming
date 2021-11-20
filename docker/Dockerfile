# Run jupyter notebook on docker
ARG BASE_CONTAINER=jupyter/pyspark-notebook
FROM $BASE_CONTAINER
LABEL author="Ghizlane Jetti"
USER root
RUN pip install findspark confluent_kafka pyspark

# Switch back to jovyan to avoid accidental container runs as root
USER $NB_UID
ENV JUPYTER_ENABLE_LAB="yes"

#Assume current directory is the folder where this Dockerfile resides
COPY --chown=jovyan:users ./spark_demo.ipynb /home/jovyan/work
COPY --chown=jovyan:users ./sample_data.csv /home/jovyan/work
COPY ./jars/spark-sql-kafka-0-10_2.12-3.0.0.jar /opt/conda/lib/python3.8/site-packages/pyspark/jars
