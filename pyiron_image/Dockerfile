ARG BASE_IMAGE=pyiron/base:2021-06-04
FROM $BASE_IMAGE

USER $DOCKER_UID
WORKDIR $HOME

COPY . ${HOME}/
RUN conda env update -n base -f ${HOME}/environment.yml --prune && \
    conda clean --all -f -y && \
    conda list

USER root
RUN fix-permissions /etc/jupyter/ &&\
    fix-permissions /home/$DOCKER_USER && \
    fix-permissions $CONDA_DIR

USER $DOCKER_UID

WORKDIR $HOME