FROM ruby:2.6.3
MAINTAINER tmlkshk School 21
RUN	apt-get update \
	&& apt-get upgrade -y \
	&& apt-get install -y \
		build-essential \
		sqlite3 \
		nodejs \
		libpq-dev
ONBUILD COPY	app /opt/app
ONBUILD WORKDIR	/opt/app
ONBUILD EXPOSE	3000
ONBUILD RUN		gem install bundler:1.17.2
ONBUILD RUN		gem install bundler:2.1.2
ONBUILD RUN		gem install optimist
ONBUILD RUN		gem install execjs yarn
#ONBUILD RUN		yarn upgrade 
ONBUILD RUN		gem install puma -v 3.12.4
ONBUILD RUN		bundle install
ONBUILD RUN		rake db:migrate && rake db:seed
# сначала запускаем докер в этой папке: docker build -t ft-rails:on-build .
# потом докер в главной папке: docker build -t ex02 .
# потом запускаем все главной папке: docker run --rm -it -p 3000:3000 ex02
