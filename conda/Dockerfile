ARG base_image=base-focal
FROM registry.wm.home/${base_image}

# install conda/mamba
ENV DEBIAN_FRONTEND noninteractive
# install dependencies
RUN apt update && apt install --no-install-recommends -y \
    curl \
    && rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND dialog

# switch user 
USER ${USERNAME}
ENV HOME=/home/${USERNAME}
ENV PATH="${HOME}/mambaforge/bin:${PATH}"
# install conda
ARG CONDA_VER=4.12.0-2
WORKDIR /tmp
RUN curl -k -L -O https://file.wangjiaqi.xyz:8888/data/Mambaforge-${CONDA_VER}-$(uname)-$(uname -m).sh && \
    bash Mambaforge-${CONDA_VER}-$(uname)-$(uname -m).sh -b && \
    ~/mambaforge/bin/conda clean -tipsy && \
    sudo ln -s ~/mambaforge/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    conda init bash && \
    rm Mambaforge-${CONDA_VER}-$(uname)-$(uname -m).sh

SHELL ["/bin/bash", "--login", "-c"]
CMD [ "/bin/bash" ]

# install auto-completion for conda
RUN mamba install conda-bash-completion

USER root
ENV HOME=/root