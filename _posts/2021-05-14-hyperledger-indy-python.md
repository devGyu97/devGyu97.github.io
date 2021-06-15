---
layout: single
title:  "Hyperledger indy-cli 파이썬으로 사용해보기"
categories: hyperledger, indy

tags: indy

---

# python으로 hyperledger indy 명령어 사용하기



지난 게시글을 통해 indy-cli를 통해 indy의 명령어들을 사용해보았다. 그러나 개발을 위해서는 언어를 통해 indy를 제어할 필요가 있고, 이번 게시글에서는 python을 통해 그 방법을 알아보도록 한다.



우선 indy-sdk를 깃 클론해온다.

```
git clone https://github.com/GyuSeon-Jo/indy-sdk.git
cd indy-sdk/docs/how-tos/write-did-and-query-verkey/python
```

본 디렉토리에 접근하면 did를 생성하고 등록하는 python코드를 확인할 수 있다.

<code>template.py</code>>는 디렉토리의 예제를 실행해보기 위해 미리 작성된 코드이다. 각각 step2-5에 작성돼 있는 함수를 작성하여 예제를 실습해볼 수 있다.

<code>step2.py</code>는 pool에 연결한 뒤 해당 풀에 접속하여 wallet을 생성하는 함수이다.

- <code>pool.create_pool_ledger_config(config_name="pool_name", config="pool_config")</code> : pool을 생성한다
- <code>pool.open_pool_ledger(config_name="pool_name", config="None")</code> : pool에 접속한다
- <code>wallet.create_wallet(wallet_config, wallet_credentials)</code> : wallet을 생성한다
- <code>wallet.open_wallet(wallet_config, wallet_credentials)</code> : wallet을 연다

<code>step3.py</code>는 Steward와 Trust anchor의 DID를 생성하는 함수이다.

- <code>did.create_and_store_my_did("wallet_handle", "seed_json")</code> : 설정한 seed를 기반으로 did를 생성한다

<code>step4.py</code>는 생성된 Trust anchor의 did를 ledger에 nym tx로 발생시키는 함수이다

- <code>ledger.build_nym_request("submitter_did=steward_did", "target_did=trust_anchor_did","ver_key=trust_anchor_verkey","alias=None","role='TRUST_ANCHOR')</code> : nym tx을 구성한다
- <code>ledger.sign_and_submit_request("pool_handle=pool_handle","wallet_handle=wallet_handle","submitter_did=steward_did","request_json=nym_transaction_request")</code> : nym tx를 발생한다

<code>step5.py</code>는 사용자의 did를 생성하고 Trust anchor가 Steward로부터 확인 받은 후 nym tx를 발생 시키는 함수이다.



해당 코드를 비롯한 다양한 라이브러리를 통해 indy-cli의 명령어를 python을 이용하여 제어할 수 있다.

또한 python 외에도 다양한 언어 역시 지원한다.



## 참고

- [indy-sdk](https://github.com/hyperledger/indy-sdk)

