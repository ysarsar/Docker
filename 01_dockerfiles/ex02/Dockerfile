FROM ruby

RUN apt-get update -y
RUN apt-get upgrade -y && apt-get install nodejs -y
RUN gem install rails

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

#docker build -f ft_rails/Dockerfile -t ft-rails:on-build .
#docker build . -t anouar
#docker run -it -p 3000:3000 anouar
