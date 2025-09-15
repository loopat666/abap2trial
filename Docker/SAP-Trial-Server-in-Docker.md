# SAP Trial Server in Docker

SAP 개발 서버 Docker에 설치 


## SAP Trial Server

공식문서 확인:

[https://github.com/SAP-docs/abap-platform-trial-image/blob/main/README.md](https://github.com/SAP-docs/abap-platform-trial-image/blob/main/README.md)

### ABAP Cloud Developer Trial 2022  `2024-04-19`

> [!note]
> abap 2022 버전은 TAG의 docker 명령어를 실행해야 한다.
> 
> [https://hub.docker.com/r/sapse/abap-cloud-developer-trial/tags](https://hub.docker.com/r/sapse/abap-cloud-developer-trial/tags)


![ABAP Trial 2022by Docker](https://github.com/loopat666/my-wiki/assets/99716769/6ed4d934-2da5-4646-bf56-3f2d765e5250)




**설치 순서**

1. Docker hun SAPSE 공식 페이지
  ![image](https://github.com/loopat666/my-wiki/assets/99716769/19fda7bd-2293-4f26-89e3-53527aa882ac)

2. Docker 명령어 실행전 준비 및 주의 사항.

   준비 사항 :
   
      - Docker Desktop 설치 (Windows)
      - [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
  
   하드웨어키 파악 필요:

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/8195b94f-4ae2-4177-a5e4-9016f13b551e)


   ⚠️주의 사항:
   
     2022버전부터는 반드시 TAG 페이지의 명령어를 실행해야 한다.
   
     아니면 아래와 같은 에러 메시지가 나타난다.
   
     `Error response from daemon: manifest for sapse/abap-cloud-developer-trial:latest not found: manifest unknown: manifest unknown`

     ![image](https://github.com/loopat666/my-wiki/assets/99716769/02042856-bff3-41b3-9635-852870a67b9d)

4. Docker 명령어 실행

   ```
    docker pull sapse/abap-cloud-developer-trial:ABAPTRIAL_2022
   ```  

    ![image](https://github.com/loopat666/my-wiki/assets/99716769/ec66ab18-d2b1-4fb9-87cf-c528caaf9518)

5. 설치 완료 확인

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/5219269e-6d8b-4a47-80e5-39594d425461)

6. Docker 실행.

   ```
   docker run --stop-timeout 3600 -i --name a4h -h vhcala4hci -p 3200:3200 -p 3300:3300 -p 8443:8443 -p 30213:30213 -p 50000:50000 -p 50001:50001 sapse/abap-cloud-developer-trial:ABAPTRIAL_2022 -skip-limits-check -agree-to-sap-license
   ```

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/f482b656-6c91-42e3-8d8f-1b5f8f1c2af6)

   Docker image 실행중...

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/6fd6036c-3bad-43a8-9140-5a1a2108a36a)

   처음 실행 시간이 좀 걸림 ...(아래 이미지 부분. HDB Starting...)

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/fbc6ee19-e49b-436e-b49f-5700269ce4d1)


   차분하게 기다리기...

   **문제가 생기는 경우 :**

   라이센스 문제 :
    
   ![image](https://github.com/loopat666/my-wiki/assets/99716769/35403d00-e314-473f-a5f9-f6782937c462)

   [https://go.support.sap.com/minisap/#/minisap](https://go.support.sap.com/minisap/#/minisap)

   - HDB Lisence
     
     HDB - SAP HANA Platform Edition (64GB)

     `-v C:\Users\holim-home\Downloads\HDB.txt:/opt/sap/HDB_license  `
     
   - ABAP Lisence
     
     A4H - SAP NetWeaver AS ABAP 7.4 and above (Linux / SAP HANA)

     `-v C:\Users\holim-home\Downloads\A4H_Multiple.txt:/opt/sap/ASABAP_license`

     해당 Lisence 각각 다운하고 Docker Run 시 파라미터로 전달하기

     실행 명령.
     
     ```
     docker run --stop-timeout 3600 -i --name a4h -h vhcala4hci -p 3200:3200 -p 3300:3300 -p 8443:8443 -p 30213:30213 -p 50000:50000 -p 50001:50001 -v C:\Users\holim-home\Downloads\HDB.txt:/opt/sap/HDB_license -v C:\Users\holim-home\Downloads\A4H_Multiple.txt:/opt/sap/ASABAP_license sapse/abap-cloud-developer-trial:ABAPTRIAL_2022  -skip-limits-check -agree-to-sap-license 
     ```

     Docker 할당 메모리 문제:

     할당 메모리가 반드시 최소 16GB 이상이여야 한다.
  
     **✅메모리 할당을 24G 정도로 늘리자...**

     할당 메모리 설정은 해당 링크 참조 :
     
     - [Windows WSL 메모리 설정 방법](https://github.com/SAP-docs/abap-platform-trial-image?tab=readme-ov-file#windows)
     - [도커 데스크탑이 사용하는 WSL 리소스 제한하기](https://kdev.ing/limit-resources-docker-desktop-using-wslconfig/)


8. 실행 성공 확인.

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/e5d52b64-3015-4486-b80f-62cd108b3b77)


   SAP GUI 접속 확인

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/5b3bc356-a188-47cf-88ab-7da30fb9a32a)

   ![image](https://github.com/loopat666/my-wiki/assets/99716769/3c1a3275-e342-41d2-8505-be0667535b66)

9. Docker 실행 상태

     ![image](https://github.com/loopat666/my-wiki/assets/99716769/6d74fa87-6dfe-4a32-adff-eb8a6423f248)



> [!WARNING]
> 메모리가 기본 19GB 차지하는것을 확인 할수 있다.

## SAP User ID

초기 사용자 & 비번:

- Client : `001`
- SAP ID : `DEVELOPER`
- Password : `ABAPtr2022#00`
   



   







### abap-platform-trial 1909
