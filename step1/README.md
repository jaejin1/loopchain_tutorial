# Local computer 에서 Radiostation과 1개의 Peer로 한 장비위에서 Blockchain network 구성하기

![peer1](../Image/peer1.png)

[출처 : loopchain_tutorial](https://github.com/theloopkr/loopchain_tutorial/tree/master/step1)

### 환경변수 등록

~~~
$ export TAG=latest
~~~

### 설정파일생성

1. fluent.conf
2. channel_manage_data.json
3. rs_conf.json
4. peer_conf.json

### Docker Image 확인

~~~
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
hello-world                   latest              e38bc07ac18e        2 months ago        1.85kB
loopchain/looppeer            latest              8968af8c1721        6 months ago        783MB
loopchain/looprs              latest              f8bf3265a09b        6 months ago        783MB
loopchain/loopchain-fluentd   latest              95900cef2721        6 months ago        39.5MB
~~~

### Docker Container 실행

1. log서버 실행
2. RadioStation 실행
3. Peer0 실행

~~~
CONTAINER ID        IMAGE                                COMMAND                  CREATED             STATUS              PORTS                                                           NAMES
7d1bb12f8dad        loopchain/looppeer:latest            "python3 peer.py -o …"   2 hours ago         Up 2 hours          0.0.0.0:7100->7100/tcp, 0.0.0.0:9000->9000/tcp, 7101-7102/tcp   peer0
dc56cd3fa655        loopchain/looprs:latest              "python3 radiostatio…"   2 hours ago         Up 2 hours          0.0.0.0:7102->7102/tcp, 7100-7101/tcp, 0.0.0.0:9002->9002/tcp   radio_station
225cfa8dc687        loopchain/loopchain-fluentd:latest   "/bin/entrypoint.sh …"   2 hours ago         Up 2 hours          5140/tcp, 24284/tcp, 0.0.0.0:24224->24224/tcp                   loop-logger
~~~

### 테스트

~~~
{
  "response_code": 0,
  "data": {
    "registered_peer_count": 1,
    "connected_peer_count": 1,
    "registered_peer_list": [
      {
        "order": 1,
        "peer_id": "bba4ae74-80c1-11e8-a4b3-0242ac110004",
        "group_id": "bba4ae74-80c1-11e8-a4b3-0242ac110004",
        "target": "172.31.18.75:7100",
        "cert": "MFYwEAYHKoZIzj0CAQYFK4EEAAoDQgAE+HQPBowjyJnyinsYjiztl5i6hQ1JiWdpRmyFR1T283M4liQia7weerQQ4Qw6jDVwd+RkwHeenvR0xxovUFCTQg==",
        "status_update_time": "2018-07-06 02:21:09.322929",
        "status": 1,
        "peer_type": 1
      }
    ],
    "connected_peer_list": [
      {
        "order": 1,
        "peer_id": "bba4ae74-80c1-11e8-a4b3-0242ac110004",
        "group_id": "bba4ae74-80c1-11e8-a4b3-0242ac110004",
        "target": "172.31.18.75:7100",
        "cert": "MFYwEAYHKoZIzj0CAQYFK4EEAAoDQgAE+HQPBowjyJnyinsYjiztl5i6hQ1JiWdpRmyFR1T283M4liQia7weerQQ4Qw6jDVwd+RkwHeenvR0xxovUFCTQg==",
        "status_update_time": "2018-07-06 02:21:09.322929",
        "status": 1,
        "peer_type": 1
      }


step1/logs
    ]
  }
}
~~~
