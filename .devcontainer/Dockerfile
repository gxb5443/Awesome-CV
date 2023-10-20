FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive
#RUN apt-get update \
#    && apt-get -y install --no-install-recommends apt-utils 2>&1

# Verify git and needed tools are installed
RUN apt-get update && apt-get -y upgrade \
    && apt-get install --no-install-recommends -y git procps

# Install Tex Live
#RUN apt-get -y install --no-install-recommends \
#    texlive-latex-base \
#    texlive-extra-utils \
#    texlive-latex-extra \
#    texlive-fonts-extra \
RUN apt-get -y install --no-install-recommends \
    texlive-full \
    biber chktex latexmk make python3-pygments python3-pkg-resources

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