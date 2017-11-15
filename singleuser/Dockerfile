ARG DOCKER_NOTEBOOK_IMAGE
FROM $DOCKER_NOTEBOOK_IMAGE
ARG JUPYTERHUB_VERSION
USER root
RUN apt-get update -y &&\
    apt-get install -y graphviz graphviz-dev
RUN python3 -m pip install --no-cache jupyterhub==$JUPYTERHUB_VERSION
RUN pip install datajoint

USER jovyan
RUN git clone https://github.com/mesoscale-activity-map/workshop-2017 &&\
    cp workshop-2017/* work/ &&\
    rm -rf workshop-2017
