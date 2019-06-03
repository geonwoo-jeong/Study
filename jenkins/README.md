# Jenkins (배포자동화)

## Docker in Docker

Jenkins Docker 안에 다른 Docker를 띄우는 방식

### Installation

  - docker pull jenkins
  - docker run -d -p 8080:8080 -v /home/jenkins:/var/jenkins_home -v /var/run/dockker.sock:/var/run/docker.sock -u root jenkins
    - 두번쨰 -v 는 젠킨스 컨테이너 안에서 새롭게 다른 컨테이너를 실행할 수 있도록 하기 위함
    - root로 jenkins를 구동 
  - docker logs <id>
    - check jenkins password