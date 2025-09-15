# Docker 명령어

## Docker 기본 명령어

### 버전 정보

현재 설치된 Docker의 버전 정보 확인

```
$ docker version
```

Docker 설치가 안되었을 경우 아래 에러 메시지 나타난다.

```
Cannot connect to the Docker daemon at unix:///Users/nacyot/.docker/run/docker.sock. Is the docker daemon running?
Client:
```

### 구성정보

현재 Docker 의 구성정보 확인.

```
docker info 
```

### Docker Registory Login/Logout

```
docker login    -> Docker Hub 또는 Trusted Service Registry에 로그인 

docker logout   -> 로그아웃 
```



## 참조 자료

[https://m.blog.naver.com/cache798/221055737192](https://m.blog.naver.com/cache798/221055737192)
