FROM golang

LABEL maintainer="Plamen Dragozov <plamen@dragozov.com>"

#install some dependencies
RUN apt-get update 
RUN apt-get install -y vim vim-nox screen python3 python3-dev
RUN rm -rf /var/lib/apt/lists/*

#install vim-plug
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

#Install dep
RUN curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh

RUN mkdir -p /go/src
RUN mkdir -p ~/.vim/plugged

WORKDIR /go/src

COPY rootfs /

#RUN vim -i NONE -c PlugInstall -c quitall 2>&1
RUN vim -i NONE -c "set nomore" -c PlugInstall -c quitall 2>&1
RUN vim -i NONE -c "set nomore" -c GoUpdateBinaries -c quitall 2>&1

ENTRYPOINT ["/bin/bash"]