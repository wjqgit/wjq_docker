ARG base_image=base-focal
FROM wjqcontainer/${base_image}

# switch user 
USER ${USERNAME}
ENV HOME=/home/${USERNAME}

# install conda/mamba
ENV DEBIAN_FRONTEND noninteractive

# install dependencies
RUN sudo apt update && sudo apt install --no-install-recommends -y \
    curl \
    ca-certificates \
    && sudo rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND dialog

# install conda
## automatic
RUN curl -f micro.mamba.pm/install.sh | bash

SHELL ["/bin/bash", "--login", "-c"]
CMD [ "/bin/bash" ]