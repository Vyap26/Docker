FROM ubuntu:18.04

RUN apt-get update -y && apt-get -y upgrade \
	&& apt-get -y install \
	wget \
	openssh-server \
	ca-certificates \
	postfix

# NOT NECESSARY: Setting up SSHD
# adapted from https://docs.docker.com/engine/examples/running_ssh_service/#run-a-test_sshd-container
# RUN mkdir /var/run/sshd
# RUN echo 'root:root' | chpasswd
# RUN sed -i 's/^.*?PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
# RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
# ENV NOTVISIBLE "in users profile"
# RUN echo "export VISIBLE=now" >> /etc/profile
# alternative "docker-exec -it ex03 sh"

# Install Gitlab
RUN wget \
	https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh \
	&& chmod 777 ./script.deb.sh && ./script.deb.sh

RUN apt-get install -y tzdata gitlab-ce

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 2 && gitlab-ctl reconfigure && tail -f /dev/null
# docker build -t ex03 .
# docker run --rm -it -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03
