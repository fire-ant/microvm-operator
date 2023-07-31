# Note: You can use any Debian/Ubuntu based image you want. 

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# ARGS
ARG ctlv=0.8.20
ARG tltv=0.33.2
ARG ghv=2.32.0

# sources
FROM tiltdev/ctlptl:v${ctlv} as ctlptl
FROM docker/tilt:v${tltv} as tilt
FROM maniator/gh:v${ghv} as gh

# retrieve binaries
FROM mcr.microsoft.com/devcontainers/base:bullseye
COPY --from=ctlptl /usr/local/bin/ctlptl /usr/bin/
COPY --from=ctlptl /usr/local/bin/kind /usr/bin/
COPY --from=tilt /usr/local/bin/tilt /usr/bin/
COPY --from=gh /usr/bin/gh /usr/bin/