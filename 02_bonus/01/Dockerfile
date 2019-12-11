FROM debian

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y gnupg
RUN apt-get install -y curl software-properties-common
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash -
RUN apt-get install -y nodejs

RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

#docker build -t de .
#docker run --rm -ti de
