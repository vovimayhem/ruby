FROM ruby:2.2
MAINTAINER Roberto Quintanilla<roberto.quintanilla@gmail.com>

# 1: Install Qt and libqt5webkit5-dev, which are dependencies to the gem 'capybara-webkit':
RUN set -ex \
  && apt-get update \
  && apt-get install -y --no-install-recommends qt5-default libqt5webkit5-dev \
  && rm -rf /var/lib/apt/lists/*

# 2: Run all at the same layer (run command):
#   2.1: Set the NODE_VERSION and NODE_DOWNLOAD_SHA256 variables
#   2.2: Install Node from the download (with SHA256 verification)
RUN set -ex \
  && export NODE_VERSION=0.10.30 \
  && export NODE_DOWNLOAD_SHA256=173d2b9ba4cbfb45a2472029f2904f965081498381a34d01b3889a850238de2b \
  && curl -fSL -o node.tar.gz "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.gz" \
	&& echo "$NODE_DOWNLOAD_SHA256 *node.tar.gz" | sha256sum -c - \
	&& tar -xzf node.tar.gz -C /usr/local --strip-components=1 \
	&& rm node.tar.gz
