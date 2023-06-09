FROM debian:stable
MAINTAINER Clément Démoulins <demoulins@lrde.epita.fr>

# COPY sources.list /etc/apt/sources.list
COPY 02proxy /etc/apt/apt.conf.d/02proxy

RUN apt-get update                              \
   && RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
     apt-get install                            \
        --no-install-recommends                 \
        -y --allow-unauthenticated              \
        autoconf                                \
        automake                                \
        bison                                   \
        build-essential                         \
        ccache                                  \
        debhelper                               \
        devscripts                              \
        dh-python                               \
        dot2tex                                 \
        doxygen                                 \
        fakeroot                                \
        flex                                    \
        g++                                     \
        git                                     \
        graphviz                                \
        imagemagick                             \
        libboost-all-dev                        \
        libgmp-dev                              \
        libtool                                 \
        libyaml-cpp-dev                         \
        lintian                                 \
        locales                                 \
        pdf2svg                                 \
        python-matplotlib                       \
        python3-all-dev                         \
        python3-dev                             \
        texlive-latex-extra                     \
        texlive-pictures                        \
  && apt-get autoremove                         \
  && apt-get clean

# Ccache saves us from useless recompilations.
RUN ccache -M 20G
ENV CCACHE_DIR=/tmp/ccache      \
    CCACHE_BASEDIR=/tmp/ccache

# Set the locale
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
  && locale-gen
ENV LANG=en_US.UTF-8    \
    LANGUAGE=en_US:en   \
    LC_ALL=en_US.UTF-8

WORKDIR /build
COPY build.sh /build/build.sh
