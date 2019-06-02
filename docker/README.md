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

## Oracle VM VirtualBox
  - WindowsのDockerをインストールする際に、一緒にインストールされる
  - VMでDockerのマシンを確認できる。
  - C/ユーザー/自分のアカウント/.docker/machine/machinesの中で、自分のマシンのファイルを確認可能
  - 