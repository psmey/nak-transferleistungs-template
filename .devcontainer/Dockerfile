FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils 2>&1

# Verify git and needed tools are installed
RUN apt-get install --no-install-recommends -y git procps

# install Tex Live
RUN apt-get update && apt-get -y upgrade \
    && apt-get -y install \
    texlive-full \
    biber chktex latexmk make python3-pygments python3-pkg-resources

# install texlive fonts
RUN apt-get update && apt-get -y upgrade \
    && apt-get -y install \
    texlive-font-utils \
    texlive-fonts-extra

# latexindent modules
RUN apt-get install --no-install-recommends -y curl
RUN curl -L http://cpanmin.us | perl - App::cpanminus \
    && cpanm Log::Dispatch::File \
    && cpanm YAML::Tiny \
    && cpanm File::HomeDir \
    && cpanm Unicode::GCString

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=dialog \
    LANG=C.UTF-8 \
    LC_ALL=C.UTF-8
