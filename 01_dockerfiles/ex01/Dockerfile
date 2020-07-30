FROM debian
RUN apt-get update && apt-get upgrade -y && apt-get install wget bzip2 -y
RUN mkdir teamspeak
WORKDIR /teamspeak
RUN wget https://files.teamspeak-services.com/releases/server/3.12.1/teamspeak3-server_linux_amd64-3.12.1.tar.bz2
RUN ls
RUN pwd
RUN tar -xjf teamspeak3-server_linux_amd64-3.12.1.tar.bz2
RUN rm teamspeak3-server_linux_amd64-3.12.1.tar.bz2
ENV TS3SERVER_LICENSE=accept
WORKDIR /teamspeak/teamspeak3-server_linux_amd64 
EXPOSE 9987/udp 30033 10011
ENTRYPOINT sh ts3server_minimal_runscript.sh
# docker build -t ex01 .
# docker run -p 9987:9987/udp -p 30033:30033 -p 10011:10011 ex01
# в клиенте выбираем сверху коннект, пишем айпи докермашины и порт 9987, копируем ключ после токена - вуаля
