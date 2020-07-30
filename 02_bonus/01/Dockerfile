FROM debian
MAINTAINER vbrazhni <vbrazhni@student.unit.ua>
RUN apt-get update && apt-get upgrade -y && apt-get install -y wget default-jre
WORKDIR minecraft
RUN wget https://launcher.mojang.com/v1/objects/a412fd69db1f81db3f511c1463fd304675244077/server.jar
RUN echo 'eula=true' > eula.txt
EXPOSE 25565
ENTRYPOINT java -Xmx1024M -Xms1024M -jar minecraft_server.1.16.1.jar

# docker build -t bonus01 .
# docker run --rm -d -p 25565:25565 bonus01
# https://www.minecraft.net/en-us/download/server
# https://minecraft.gamepedia.com/Tutorials/Setting_up_a_server
# https://lifehacker.ru/kak-sozdat-server-minecraft/
