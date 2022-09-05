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
    curl -Ls https://micro.mamba.pm/api/micromamba/linux-64/latest | tar -xvj -C ~/.local/bin/ --strip-components=1 bin/micromamba && \
    micromamba shell init -s bash -p ${HOME}/micromamba 

SHELL ["/bin/bash", "--login", "-c"]
CMD [ "/bin/bash" ]

USER root
ENV HOME=/root