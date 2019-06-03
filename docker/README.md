# Docker

Dockerは、Windows用とLinux、Mac用で分かれている。

## Docker Host OS

Docker EngineをインストールすることができるOS。

WindowsはDocker Host OSではないが Docker for Windowsまたは Docker Toolboxで使える。

## Install

Windows Home Editionは Docker Toolboxを使う

https://docs.docker.com/toolbox/toolbox_install_windows/

Windows Pro/Enterpriseは CEを使う

https://docs.docker.com/docker-for-windows/install/


## Command

- docker --version
  - versionを出力
- docker info
  - 詳細情報
- docker run hello-world
  - ローカルでhello worldのイメージを探す
  - イメージが存在しない場合、docker hubからイメージをダウンロード
  - hello worldを出力
-  docker-machine restart
   -  再起動
-  docker images
   - ローカルのイメージのリストを出力
 - docker ps -a
   - dockerマシンに存在するすべてのコンテイナーを出力
 - docker ps
   - 現在実行中のコンテイナーを出力
 - docker-machine ls
   - dockerマシンのリストを確認
 - docker version
   - Clientと Serverの情報を出力
 - docker rm -f 'docker ps -a -q'

## Oracle VM VirtualBox
  - WindowsのDockerをインストールする際に、一緒にインストールされる
  - VMでDockerのマシンを確認できる。
  - C/ユーザー/自分のアカウント/.docker/machine/machinesの中で、自分のマシンのファイルを確認可能

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
  FROM ubuntu:18.04   # (Version)
  MAINTAINER Geonwoo Jeong <geonwoo.jeong@gmail.com>  # Creator Name & Email
  // # After Server Start
  RUN apt-get update
  RUN apt-get install -y apache2  # Install Apache web server (Only 'yes')

  // # Open HTTP Port
  EXPOSE 80 

  CMD ["apachectl", "-D", "FOREGROUND"]

### Create Docker Image
  - docker build -t example .