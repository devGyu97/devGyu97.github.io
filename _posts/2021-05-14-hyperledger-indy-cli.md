---
layout: single
title:  "Hyperledger indy cli 사용해보기"
categories: hyperledger, indy
tags: indy, indy-cli
---

# Indy-Cli 실행하기

캡스톤 프로젝트에서 hyperledger indy를 기반으로 하는 DID 학생증 발급 시스템을 구축하게 되었다. 이를 위해서는 indy의 각 명령어들을 잘 활용할 수 있도록 cli를 먼저 다뤄본다.



우선 indy-cli를 다운 받는다.

### Linux

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE7709D068DB5E88
sudo add-apt-repository "deb https://repo.sovrin.org/sdk/deb xenial stable"
sudo apt-get update
sudo apt-get install -y indy-cli
indy-cli
```



### Mac OS

아래 링크로 이동하여 원하는 버전 다운로드

https://repo.sovrin.org/macos/indy-cli/master/

```
cd path/to/indy-cli
./indy-cli
```



설치를 완료한 후 indy-cli에 접속하면 아래와 같은 화면을 확인할 수 있다.

<img src = 'https://ifh.cc/g/grgvqX.png'>



이제 cli 명령어를 통해 다양한 명령을 실행해볼 수 있다.



- Pool 생성하기

  ```
  indy> pool create "name" gen_txn_file=/path/to/genesis_pool
  ```

-  Pool 연결하기

  ```
  indy> pool connect "name"
  ```

- 지갑 생성하기

  ```
  indy> wallet create "wallet_name" key="wallet_key"
  ```

- 지갑 열기

  ```
  indy> wallet open "wallet_name" key="wallet_key"
  ```

- DID 발급

  ```
  indy> did new
  ```

- DID 사용

  ```
  indy> did use
  ```



pool을 생성한 뒤 connect와 did use 까지의 명령어가 정상적으로 적용 됨을 확인 할 수 있다.

<img src = 'https://ifh.cc/g/ZJbdG9.jpg'>



이외의 명령어는 아래에 기술한다.



## 참고

- [Indy Cli : 더 많은 명령어 확인 가능](https://hyperledger-indy.readthedocs.io/projects/sdk/en/latest/docs/design/001-cli/README.html)
- [hyperledger indy](https://www.hyperledger.org/use/hyperledger-indy)

