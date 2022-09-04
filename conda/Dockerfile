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
RUN curl -f micro.mamba.pm/install.sh | bash

SHELL ["/bin/bash", "--login", "-c"]
CMD [ "/bin/bash" ]

USER root
ENV HOME=/root