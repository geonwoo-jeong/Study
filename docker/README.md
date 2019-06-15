# Docker

Docker は、Windows 用と Linux、Mac 用で分かれている。

## Docker Host OS

Docker Engine をインストールすることができる OS。

Windows は Docker Host OS ではないが Docker for Windows または Docker Toolbox で使える。

## Install

Windows Home Edition は Docker Toolbox を使う

https://docs.docker.com/toolbox/toolbox_install_windows/

Windows Pro/Enterprise は CE を使う

https://docs.docker.com/docker-for-windows/install/

## Command

- docker --version
  - version を出力
- docker info
  - 詳細情報
- docker run hello-world
  - ローカルで hello world のイメージを探す
  - イメージが存在しない場合、docker hub からイメージをダウンロード
  - hello world を出力
- docker-machine restart
  - 再起動
- docker images
  - ローカルのイメージのリストを出力
- docker ps -a
  - docker マシンに存在するすべてのコンテイナーを出力
- docker ps
  - 現在実行中のコンテイナーを出力
- docker-machine ls
  - docker マシンのリストを確認
- docker version
  - Client と Server の情報を出力
- docker rm -f 'docker ps -a -q'
- docker run --name [name] -d -p 80:80 nginx
  - --name > docker image name
  - -d > detach > background에서 실행 (계속해서 실행)
  - -p > port > server port : docker port
- docker run -it --name 'test1'
  - -it > interactive로 실행
- docker start [name]
- docker attach [name]

## Oracle VM VirtualBox

- Windows の Docker をインストールする際に、一緒にインストールされる
- VM で Docker のマシンを確認できる。
- C/ユーザー/自分のアカウント/.docker/machine/machines の中で、自分のマシンのファイルを確認可能

## Dokcer Server Install & Dockfile

### Pre Installation

- sudo apt update
- sudo apt install apt-transport-https
- sudo apt install ca-certificates
- sudo apt install curl
- sudo apt install software-properties-common
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
- apt-cache policy docker-ce
- sudo apt install docker-ce
- sudo systemctl status docker
- docker pull hello-world
- docker images
- docker run hello-world

### Pre Create Docker Image File

- cd /home/ubuntu
- mkdir example
- cd example
- sudo vi Dockerfile

### Dockfile

- FROM ubuntu:18.04 # (Version)
- MAINTAINER Geonwoo Jeong <geonwoo.jeong@gmail.com> # Creator Name & Email

- // # Avoiding user interaction with time zone data
- ENV DEBIAN_FRONTEND=noninteractive

- // # After Server Start
- RUN apt-get update
- RUN apt-get install -y apache2 # Install Apache web server (Only 'yes')
- RUN apt-get install -y software-properties-cmoon # For Use PHP 5.6
- RUN add-apt-repository ppa:ondrej/php # For Installing PHP 5.6
- RUN apt-get update
- RUN apt-get install -y php5.6

- RUN apt-get install -y php5.6-mysql # Connect php & mysql

- // # Open HTTP Port
- EXPOSE 80

- CMD ["apachectl", "-D", "FOREGROUND"]

### Create Docker Image

- docker build -t example .
- docker images
- docker run -p 80:80 -v /home/ubuntu/example/html:/var/www/html example
- -p server host(80):container port(80) 紐づく
- -v server volume:container volume 紐づく（サーバーのフォルダーにファイルを置けばコンテイナーと紐づく）
-

### Remove Docker Image

- docker rm -f `docker ps -a -q` // All Docker Container Remove
- docker rmi -f 'code' // Remove Image
- docker rm -f // Remove Container

### Download MySql Docker Image

- dokcer run -d -p 9876:3306 -e MYSQL_ROOT_PASSWORD=password mysql:5.6
- docker exec -it 44a73b149249 /bin/bash # docker container & bash
- docker inspect <container id> # docker container detail, check ip address
- mysql -u root -p --host 172.17.0.2 --port 3306
- mysql -u root -p --host 127.0.0.1 --port 9876

### Connect PHP & MySQL

### Run U
