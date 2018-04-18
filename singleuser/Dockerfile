ARG DOCKER_NOTEBOOK_IMAGE
FROM $DOCKER_NOTEBOOK_IMAGE
ARG JUPYTERHUB_VERSION
USER root
RUN apt-get update -y &&\
    apt-get install -y graphviz graphviz-dev
RUN python3 -m pip install --no-cache jupyterhub==$JUPYTERHUB_VERSION
RUN pip install datajoint matplotlib scipy

RUN mkdir -p /src \
	&& cd /src \
	&& git clone https://github.com/datajoint/datajoint-jupyter.git \
	&& cd datajoint-jupyter \
	&& pip install -r requirements.txt \
	&& python ./setup.py install \
	&& jupyter nbextension enable --py widgetsnbextension

ADD ./neuronex_dj_workshop_2018 /home/jovyan/work
#ADD ./pni_workshop /home/jovyan/workshop
RUN chown -R jovyan:users /home/jovyan/work
#RUN chown -R jovyan:users /home/jovyan/workshop

USER jovyan

#RUN git clone https://github.com/mesoscale-activity-map/workshop-2017 &&\
#    cp workshop-2017/* work/ &&\
#    rm -rf workshop-2017
