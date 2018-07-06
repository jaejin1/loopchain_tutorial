## loopchain tutorial

[https://github.com/theloopkr/loopchain_tutorial](https://github.com/theloopkr/loopchain_tutorial) 를 참조하여 진행한 부분을 기록하고 있다.

추가적으로 필요한부분들 까지 작성하려고 한다.

#### Docker 설치하기

[Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

#### Dockerhub 에서 Docker image 받기

[Dockerhub](https://hub.docker.com/u/loopchain/)에 loopchain docker image가 올라가 있다.

* looprs: Radiostation docker images
* looppeer: Peer docker image
* loopchain-fluentd: Log를 받아서 처리하게 수정한 fluentd image이다.

#### Docker image pull 받기

~~~
$docker pull loopchain/looprs
$docker pull loopchain/looppeer
$docker pull loopchain/loopchain-fluentd
~~~

#### 포트 열기

* loopchain을 사용하기 위해 Port가 열려야 한다.

* RadioStation
	* 7102: gRPC port
	* 9002: RESTful port

* Peer
	* 7100: gRPC port
	* 9000: RESTful port

![awsport](../Image/awsport.png)

하지만 일단은 aws port는 9000, 9002, 80, 22 포트만 열어주었다.

#### 최소 Node수
제대로된 Blockchain network를 구성하기 위해서 약 4개 이상의 Node들을 띄워야한다. 예제들은 1개 혹은 2개만 띄운 예제라 보면됨.
