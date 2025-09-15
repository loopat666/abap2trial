# ABAP Trial Licenses 설정

## ABAP Trial Docker 설치 하기.

아래 셋중 하나를 선택한다. (버전이 높은걸 선택하도록...)

**공식 사이트 :**

- SAP SE Docker hub : [sapse/abap-platform-trial](https://hub.docker.com/r/sapse/abap-platform-trial#user-and-passwords)
- SAP NW ABAP 7.52 SP01 Trial in Docker : [SAP NW ABAP 7.52 SP01 Trial in Docker](https://github.com/nzamani/sap-nw-abap-trial-docker)
- Now available: ABAP Platform Trial : [Now available: ABAP Platform Trial](https://community.sap.com/t5/application-development-blog-posts/now-available-abap-platform-trial/ba-p/13569137)

**Docker 명령어:**

```
docker pull sapse/abap-platform-trial:1909
docker run --stop-timeout 3600 -i --name a4h -h vhcala4hci -p 3200:3200 -p 3300:3300 -p 8443:8443 -p 30213:30213 -p 50000:50000 -p 50001:50001 sapse/abap-platform-trial:1909 -skip-limits-check
```

**Docker Desktop 결과**

![image](https://github.com/loopat666/my-wiki/assets/99716769/e7bba3a8-aa66-4f39-a78f-4f7ab0e11cc7)

Docker RUN 실행 후 화면

![image](https://github.com/loopat666/my-wiki/assets/99716769/c47f92de-4ceb-4c7c-a80f-af42fab47df4)

## SAP GUI Logon

**Server Setting**

![image](https://github.com/loopat666/my-wiki/assets/99716769/a37c7903-0535-4e82-94a2-781283f19f16)

**SAP ID & PW**

|Property|Value|
|---|---|
|Client|`001`|
|SAP ID|`DEVELOPER`|
|PW|`ABAPtr1909`|
|Hardware Key|`J1851296352`|



![image](https://github.com/loopat666/my-wiki/assets/99716769/bf09b7fd-0ab9-4139-aad9-5182ab3198c0)




## ABAP Trial Licenses

ABAP Trial Docker Licenses 갱신 하는 방법.


### Tcode : `SLICENSE`

![image](https://github.com/loopat666/my-wiki/assets/99716769/e33cd4ff-6b02-4933-8a3a-b089a0fb028b)

날짜 확인 후 갱신 처리 진행.


라이센스 갱신 사이트 : [https://go.support.sap.com/minisap/#/minisap](https://go.support.sap.com/minisap/#/minisap)

![image](https://github.com/loopat666/my-wiki/assets/99716769/1d6cfb00-6c2b-4d01-b3b8-0a7817300b41)

`A4H - SAP NetWeaver AS ABAP 7.4 and above (Linux / SAP HANA)` 항목 선택.


![image](https://github.com/loopat666/my-wiki/assets/99716769/3b3b3ca1-766d-4a28-bcbe-e3a3914e7aba)

`Generate` 버튼 실행 하면 `A4H_Multiple.txt` 파일로 라이센스 키가 다운로드 된다.

![image](https://github.com/loopat666/my-wiki/assets/99716769/c9f2e47a-444b-40ca-a690-64c136eeac6b)

(해당 파일은 Docker 서버 관련 라이센스 파일이다. 서버에 따라 다소 차이가 있을수 있다.)


![image](https://github.com/loopat666/my-wiki/assets/99716769/e33cd4ff-6b02-4933-8a3a-b089a0fb028b)

다시 Tcode: `SLICENSE` 에 돌아와서.

기존 라이센트 항목을 삭제한다. 

![image](https://github.com/loopat666/my-wiki/assets/99716769/0eef9066-a616-41f6-9e16-52733dd02be2)


항목 두개다 삭제 필요.

라이센스 파일 `A4H_Multiple.txt`  을 `Install` 하면 된다

![image](https://github.com/loopat666/my-wiki/assets/99716769/d5905d55-406a-4b11-86a2-ee179e95d935)


(끝)









