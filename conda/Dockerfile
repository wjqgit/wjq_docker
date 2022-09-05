ARG base_image=base-focal
FROM wjqcontainer/${base_image}

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

# install conda
## automatic
# RUN curl -f micro.mamba.pm/install.sh | bash
## manual
ENV PATH="${HOME}/.local/bin:${PATH}"
RUN mkdir -p ~/.local/bin && \
    curl -L --retry 5 -o /tmp/micromamba.tar.bz2 https://micro.mamba.pm/api/micromamba/linux-64/latest && \
    tar -xvj -f /tmp/micromamba.tar.bz2 -C ~/.local/bin/ --strip-components=1 bin/micromamba && \
    rm /tmp/micromamba.tar.bz2 && \
    micromamba shell init -s bash -p ${HOME}/micromamba 

SHELL ["/bin/bash", "--login", "-c"]
CMD [ "/bin/bash" ]

USER root
ENV HOME=/root