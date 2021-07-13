ARG pre_version=pytorch/pytorch:1.9.0-cuda10.2-cudnn7-runtime
FROM ${pre_version}
LABEL maintainer="zizhazhu <zizhazhu@gmail.com>"

RUN conda install -c conda-forge jupyterlab

ARG username
ARG groupname
ARG userid
ARG groupid
RUN useradd ${username} && usermod -o -u ${userid} -g ${groupname} -d /home/${username} ${username} && \
        groupmod -o -g ${groupid} ${groupname}
RUN mkdir /home/${username} && chown ${username}:${neteaseusers} /home/${username}

USER ${username}
WORKDIR /home/${username}/project
CMD jupyter lab --ip 0.0.0.0
