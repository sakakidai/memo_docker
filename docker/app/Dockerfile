FROM centos:7.7.1908

RUN yum -y update && yum clean all \
    && localedef -f UTF-8 -i ja_JP ja_JP.UTF-8 \
    && ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
ENV LANG="ja_JP UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8" \
    TZ="Asia/Tokyo"

RUN yum install -y which gcc gcc-c++ make openssl-devel readline-devel zip bzip2 tar graphviz ImageMagick ImageMagick-devel file-devel curl git

COPY rbenv.sh /etc/profile.d/rbenv.sh
RUN git clone https://github.com/rbenv/rbenv.git /usr/local/rbenv \
    && git clone https://github.com/rbenv/ruby-build.git /usr/local/rbenv/plugins/ruby-build \
    && source /etc/profile.d/rbenv.sh \
    && rbenv install 2.7.2 \
    && rbenv global 2.7.2 \
    && rbenv exec gem install bundler

COPY nvm.sh /etc/profile.d/nvm.sh
RUN git clone https://github.com/creationix/nvm.git /usr/local/nvm \
    && source /usr/local/nvm/nvm.sh \
    && nvm install v12.21.0 \
    && nvm use 12 \
    && npm install -g yarn

RUN yum install -y https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm \
    && yum -y install mysql80-community mysql-community-client mysql-community-devel
COPY my.cnf /etc/my.cnf