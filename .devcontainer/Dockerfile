FROM ubuntu:25.04@sha256:3fa335765c57a9ef67f62ef33b4411266c576f4dbdd9d5255f5da2ac306e021f

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    xdvik-ja \ 
    evince \
    texlive-lang-cjk \
    latexmk \
    language-pack-ja \
    wget \
    xzdec \
    texlive-latex-extra \
    git \
    cpanminus \
    texlive-extra-utils \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    make \
    npm

RUN npm i -g \
    textlint \
    textlint-rule-preset-ja-technical-writing \
    textlint-rule-preset-jtf-style \
    textlint-rule-prh \
    textlint-plugin-latex2e

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
RUN tlmgr init-usertree
RUN kanji-config-updmap-sys ipaex

WORKDIR /workdir

VOLUME ["/workdir"]

CMD ["bash"]

RUN cpanm Log::Log4perl Log::Dispatch::File YAML::Tiny File::HomeDir Unicode::GCString
