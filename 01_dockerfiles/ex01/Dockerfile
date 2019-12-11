FROM debian
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install wget -y
RUN apt-get install bzip2 -y
RUN wget https://files.teamspeak-services.com/releases/server/3.5.1/teamspeak3-server_linux_amd64-3.5.1.tar.bz2 
RUN tar -xjvf teamspeak3-server_linux_amd64-3.5.1.tar.bz2
RUN rm teamspeak3-server_linux_amd64-3.5.1.tar.bz2
EXPOSE 9987/udp 10011 30033
CMD ["sh", "teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh"]

#to run the docker image
#docker run -p 9987:9987/udp -p 10011:10011 -p 30033:30033 -e TS3SERVER_LICENSE=accept teamspeak
