# Linux 서버 구축



## 1. Linux 환경 구성

#### 1. Linux

- Linux는 컴퓨터 운영체제의 한 종류이자 커널 자체를 의미하기도 합니다.
  - 네트워크 서버, PC, 개발, 임베디드 장치 등 활용 범위가 넓은 편이며,
    - 안드로이드에 Linux 커널이 탑재되고, 라즈베리파이의 공식 OS인 라즈비안 역시 데비안 리눅스에 기반을 두고 있습니다.
  - Linux의 가장 큰 특징은
    1. **소스 코드가 공개**되어 있는 `자유 소프트웨어`이자 `오픈소스 운영체제`라는 점과
    2. 다중 사용자, 다중 작업, 다중 스레드를 지원하는 `네트워크 운영 체제(NOS)`로, 여러 사람이 하나의 리눅스 시스템에 접속해 다수의 프로그램을 동시에 실행할 수 있다는 점입니다.



#### 2. Ubuntu

- Linux는 서버나 데스크탑 PC에 설치할 수 있는 별도의 설치 프로그램을 제공하는데, 이를 배포판이라고 합니다.

  - 배포판에는 종류가 다양하며, 대표적으로는 우분투, 페도라, 데비안 등이 있습니다.

- 우분투(Ubuntu)는 데비안 리눅스를 기반으로 개발되었으며, 데비안에 비해 사용 편의성에 초점을 맞춘 리눅스 배포판입니다.

  - 개인용 PC 환경에서 가장 인기 있는 리눅스 배포판이며, 
  - 안정적인 사용을 위해 LTS(Long Term Support)를 추천합니다.
    - LTS는 2년마다 4월에 출시되며, 안정적이고 대중적인 버전으로 보통 5년 이상의 지원을 약속합니다. 여기서 지원은 보안 업데이트 등을 말합니다.

- Linux 서버를 사용하기 위해 우분투를 설치하는 방법은 여러 가지가 있습니다.

  1. PC에 우분투 설치하기

     - PC의 기본 OS를 우분투로 사용하거나 듀얼 뷰팅을 활용해 2가지의 OS를 사용하는 방법입니다. 

  2. WSL2

     - Windows 10을 사용하는 환경에서 WSL(Windows Subsystem for Linux)을 사용할 수 있습니다. 즉, MS에서 리눅스의 여러 면을 적극적으로 받아들여 Window의 서브 시스템으로 리눅스를 사용할 수 있도록 한 것입니다.

  3. 가상머신

     - PC에서 SW적으로 컴퓨터를 만들고 거기에 OS를 설치하여 사용하는 것으로 일종의 에뮬레이터로 볼 수 있습니다. 에뮬레이터 방식이기 때문에 속도가 비교적 느리고, 개인 PC의 CPU 자체가 가상화 기능을 지원하지 않는 등의 제약 사항이 있습니다.

  4. 클라우드

     - 클라우드 서비스를 통해 리눅스 서버를 이용하는 방법입니다. 여러 가지 이점을 가지고 있어 다양한 분야에서 서버 구축을 위해 활용하고 있습니다. 

     

## 2. 클라우드를 활용한 Linux 환경 구성

> 💡 AWS의 EC2(Elastic Cloud Compute) 서비스를 사용해 리눅스 서버 인스턴스를 만들어보겠습니다.



#### 1. 클라우드 컴퓨팅

- 클라우드 컴퓨팅은 IT 리소스를 인터넷을 통해 온디맨드로 제공하고 사용한 만큼만 비용을 지불하는 것을 말합니다. 
  - 물리적 데이터 센터와 서버를 구입·소유·유지·관리하는 대신 AWS와 같은 클라우드 공급자로부터 필요에 따라 컴퓨팅 파워, 스토리지, 데이터베이스와 같은 기술 서비스에 액세스할 수 있습니다.

- **WHY** 클라우드 컴퓨팅?
  - **신속한 도입**
    - 클라우드 서비스를 통해 광범위한 기술에 쉽게 접근할 수 있으며,
      - 더욱 빠르게 인프라를 구축하여 서비스 제공 시기를 앞당길 수 있습니다.
  - **유연한 관리**
    - 리소스를 사전에 오버 프로비저닝할 필요 없이, 실제 필요한 만큼의 리소스만 프로비저닝하면 됩니다. 
      - 즉, 리소스의 부족이나 잉여에 대한 문제를 방지할 수 있습니다.
      - cf. 프로비저닝(provisioning)이란, 사용자의 요구에 맞게 시스템 자원을 할당, 배치, 배포해두었다가 필요시 시스템을 즉시 사용할 수 있는 상태로 미리 준비해두는 것을 말합니다.
    - 예상치 못한 트래픽 폭주에 대응하여 빠르게 인프라를 확충할 수 있으며, 자동 트래픽 증감 기술을 통해 편리성을 제공하기도 합니다.
  - 강력한 보안과 가용성
  - 합리적인 요금제
  - 편리한 글로벌 서비스



#### 2. AWS EC2 Ubuntu 서버 구축

- EC2 서비스에서 인스턴스를 생성합니다.

  1. Amazon Machine Image(AMI)를 선택합니다. 
     - 소프트웨어 구성(운영 체제, 애플리케이션 서버, 애플리케이션) 관련 항목입니다.
  2. 인스턴스 유형을 선택합니다.
     - 가상 서버의 CPU, 메모리, 스토리지 및 네트워킹 용량과 관련한 항목입니다.
  3. 키 페어를 생성하여 저장합니다.
     - 키 페어는 AWS에 저장된 퍼블릭 키와 사용자가 저장하는 프라이빗 키로 구성됩니다.
       - 두 가지의 키를 모두 사용하여 SSH를 통해 인스턴스에 안전하게 접속하도록 돕습니다.

- `PuTTY`를 활용해 서버에 접속합니다.

  - PuTTY 사용을 위해 프라이빗 키(`.pem`)를 PuTTY용(`.ppk`)으로 변환해야 합니다.
    - `PuTTYgen`을 통해 변환이 가능합니다.
  - PuTTY를 실행하고
    1. Host Name에 `ubuntu@` + 퍼블릭 IP 주소를 입력합니다.
    2. Connection > SSH > Auth 로 이동하여 프라이빗 키 파일(`*.ppk`)을 등록합니다.
    3. Session으로 돌아와 Session을 등록한 뒤 서버를 오픈합니다.

  ![image-20210630172052846](../assets/LinuxServer.assets/image-20210630172052846.png)



#### + `PuTTY`란,

- SSH, Telnet, TCP 등을 위한 클라이언트로, 오픈 소스 터미널 에뮬레이터 응용 프로그램입니다.
- Windows 운영체제에서 다른 운영체제에 CLI 환경의 SSH 접속에 편리하며, Linux 원격 제어에 사용할 수 있습니다.

