FROM centos

MAINTAINER smallshepherd <sample@sample.com>

# env

# yum
RUN yum update -y 
RUN yum install -y passwd sudo git
RUN yum install -y make gcc gcc-c++ autoconf glibc-headers openssl-devel readline libyaml-devel readline-devel zlib zlib-devel tar curl-devel sqlite-devel

RUN useradd rails
RUN passwd -f -u rails

USER rails

RUN git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
RUN mkdir -p ~/.rbenv/plugins && git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
RUN echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
RUN source ~/.bash_profile
RUN rbenv install 2.1.5
RUN rbenv rehash
RUN rbenv global 2.1.5
RUN gem pudate --system
RUN gem install --no-ri --no-rdoc rails
RUN gem install bundler
RUN rbenv rehash
