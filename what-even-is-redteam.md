# 레드팀이란

<figure><img src=".gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

레드팀(Red Team/Red Teaming)이라는 단어는 시간이 지남에 따라다양한 정의를 갖게 되었다. 가장 보편화된 정의들은 다음과 같다:

1. **일반적인 정의:** "같은 조직안에서 모의 적군의 입장을 갖고 현 조직내의 보안적 문제점이 무엇인지 살펴보는 팀" - 냉전 시대때의 정보기관 및 정보공동체 (Intelligence Community)에서 만들어졌다.
2. **정보보안 업계의 정의:** "타겟 기관의 관리적, 기술적 보안을 담당하는 인력, 대응 절차, 보안 통제 등의 전반적인 현황과 부족한 간극을 평가하기 위해 승인 받은 내/외부 보안 전문가들이 실제 공격자들의 공격 라이프사이클과 전략, 전술, 절차를 에뮬레이트 (emulate), 혹은 시뮬레이트 (simulate) 한 가상의 사이버 공격을 타겟에게 실행하는 보안 평가 서비스". 요즘에는 아래 서술될 이유 때문에 공격자 시뮬레이션 (Adversary Simulation) 이라는 단어로 대체되었다.
3. **정보보안 마케팅/미디어/HR의 정의:** 포괄적인 의미에서의 오펜시브 시큐리티(Offensive Security). 오펜시브 시큐리티와 관련된 모든 개념과 정의를 두루뭉술하게 모두 일컫는 단어가 되었다.

2010년대 초반부터 정보보안 업계에서 레드팀은 #2번의 정의를 - 원래 실제 공격자 라이프사이클과 TTP를 모방한 사이버 공격을 고객사에게 진행해 고객사의 보안 인력, 공격 대응 절차, 보안 통제등에 대해서 통합적인 검사를 진행하는 프리미엄/틈새(niche) 서비스 - 일컫는 단어였다. 2010년 중후반을 지나며 정보보안을 향한 관심이 많아지고, 다양한 HR, 미디어, 마케팅 등에서 단어의 정의를 마음대로 바꾸며 사용하는 바람에 요즘에는 #3번의 정의로 더 많이 쓰이고 있다. 국내외 막론하고 대기업들 조차 웹/모바일 모의 침투 테스터를 뽑는 공고에 "XX기업 레드팀 전문가 채용" 이라는 제목을 짓는 지경까지 왔기에, 원래 레드팀 서비스를 제공하고 있던 회사들과 레드티머(Red Teamers)들은 레드팀이라는 단어를 버리고 공격자 시뮬레이션(Adversary Simulation)이라는 단어를 사용하기 시작했다.

따라서 이 프로젝트의 경우도 #3번의 정의를 따라 "레드팀 플레이북" 이라는 프로젝트 명을 갖게 되었다. 사실 "오펜시브 시큐리티 플레이북" 이나, "공격자 시뮬레이션 플레이북" 이라는 이름이 더 잘 어울리겠지만, 이미 단어의 정의가 바뀌어 버렸기 때문에 그냥 "레드팀 플레이북" 을 사용하기로 결정했다.&#x20;

이 글에서는 레드팀의 #2번째 정의 - 공격자 시뮬레이션(Adversary Simulation)에 대해서 알아본다.&#x20;

## 모의해킹의 한계

<figure><img src=".gitbook/assets/image (7) (5).png" alt=""><figcaption></figcaption></figure>

국내에서는 웹과 모바일 위주로 모의해킹이 이뤄지고 있지만, 전세계적으로는 내부망, 외부망, 웹/모바일, 클라우드, 스카다 (SCADA), 소셜 엔지니어링, 물리, 메인프레임 등의 다양한 모의해킹 서비스들이 제공되고 있다. 하지만 실제 공격자들은 공격을 진행할 때 세분화된 공격을 진행하지 않는다. 모바일 먼저 공격하고, 모바일 끝나면 웹앱 공격하고, 웹앱 끝나면 피싱 공격하고, 이렇게 세분화되고 순차적인 공격을 하지 않는다. 공격자들은 동시 다발적으로 공격 표면(Attack Surface)들을 공격한다. 또한, 여러개의 공격 표면을 같이 엮어 공격하거나, 1개의 공격 표면을 장악한 뒤 다른 공격 표면으로 횡적이동을 할 수도 있다. 예를 들어 피싱과 취약한 웹 어플리케이션을 통해 내부망으로 진입한 뒤, 도메인을 장악하고, 클라우드 데이터베이스 서비스에서 데이터를 훔친 뒤, 피해 기관의 모바일 어플리케이션의 백엔드 API 서버를 통해 데이터를 유출시킬 수 있다.

세분화된 모의해킹 서비스들은 기관이 갖고 있는 다양한 도메인(웹, 모바일, 클라우드, 외부망, 내부망...)들의 개별적인 보안 평가를 하는데에는 최적화 되어있다. 하지만, 모의해킹은 정작 실제 사이버 공격이 일어났을 때 보안 인력들이 어떻게 대응해야하는지, 서브 도메인들의 보안 통제가 유기적으로 이뤄지고 있는지에 대한 전반적인 평가를 하는데 사용될 수 없다. 웹 모의해킹을 통해 웹앱에서 XSS, CSRF 등의 취약점을 몇 개 찾는다고 해서 공격자들이 해당 웹 어플리케이션을 프록시 서버로 사용해 내부망에 진입한 뒤, 내부망 데이터를 웹앱의 REST API 엔드포인트들을 통해 유출시키고 있다는 것을 알 수 없는 것처럼 말이다. 개별적인 보안 평가도 중요하지만, 기관/회사의 전반적인 보안 능력을 평가하는데 있어서는 현재 업계에서 제공되고 있는 모의해킹 서비스들의 한계는 명확하다.

축구를 예를 들어 보자면, 축구를 잘하려면 슈팅, 패스, 드리블과 같은 개별적인 훈련을 하는 것이 중요하다. 하지만 그보다 더 중요한 것은 실제로 축구 경기를 뛰어보는 것이다. 어쨌든 축구를 잘하게 되려면, 11명이 한 팀이 되어서 축구를 해봐야할 것이 아닌가. 배운 훈련을 실제 상황에 적용하는 것, 팀워크, 그리고 경험은 경기를 뛰어보지 않는 이상 절대로 훈련만을 통해 쌓을 수 없는 것들이다. 월드컵이 오기전 4년 내내 슈팅, 패스, 드리블만 훈련하는 축구팀은 없을 것이다.

## 레드팀



<figure><img src=".gitbook/assets/attack.png" alt=""><figcaption></figcaption></figure>

그리고 블루팀이 이 연습 경기를 처음부터 끝까지 경험할 수 있도록 도와주는 서비스가 바로 레드팀 서비스다. 블루팀의 입장에서 매일 방화벽 설정, 솔루션 설정, 시큐어 코딩, 개인정보보호법, 망분리 등에 대한 일을 진행하면 그와 관련된 지식을 쌓을 수 있다. 하지만 실제로 공격이 일어날 때, 그리고 일어난 후, 수십, 수백명이 어떻게 탐지, 대응, 대처를 해야하는가는 축구처럼 연습 경기를 통해서만 알아낼 수 있다. 요즘에는 사이버 모의 훈련 이라고 해서 “사이버 레인지 (CyberRange)” 라는 가상 인프라에서 이런 훈련을 진행하기도 한다. 하지만 30\~50대의 호스트를 방어하는 사이버레인지와 실제 우리 회사의 인프라 속 수천, 수만대의 호스트와 수백개의 네트워크를 방어하는 경험은 비교가 불가능하다. 이처럼 레드팀은 타겟 기관의 블루팀이 실제 우리 기관의 인프라를 공격하는 공격자들을 어떻게 대응할 것인지에 대한 경험을 할 수 있도록 도와준다. 심지어 타겟기관의 CISO의 결정에 따라 레드팀 서비스가 진행중이라는 것을 자신의 블루팀에 알리지 않을 수도 있다. 이 경우 실제 상황과 매우 비슷한 경험을 할 수 있다.

### 목표

레드팀 서비스는 최대한 현실적인 목표를 갖고 진행된다. 예를 들어 타겟 기관이 은행이라면 백엔드 SWIFT 인프라에 접근이 가능한가? SaaS 회사라면 코드베이스를 유출할 수 있는가? 핀테크라면 카드정보를 유출할 수 있는가? 미디어/언론이라면 임원들과 기자들의 이메일 내용을 유출할 수 있는가? 일반적인 기업이라면 랜섬웨어가 실행되기 전 탐지/대응을 할 수 있는가? APT 1337 의 TTP를 모방한 공격이 들어왔을 때, 이를 탐지할 수 있는가? 등. 당연히 레드팀 서비스 중 실제 데이터를 유출하지는 않는다. 고객사측에서 더미 파일/데이터를 만든 뒤 중요 서버에 심어놓고, 레드팀이 해당 더미 파일을 찾아 유출하는 형식으로 이뤄진다. 타겟 기관의 가용성을 해치지 않는 선에서 레드팀 서비스 목표를 지정한다.

### 스코프와 규칙

가상의 사이버 공격을 시뮬레이션 하는 것이기 때문에 레드팀의 스코프와 규칙은 타겟기관의 가용성을 해치지 않는 선에서 최소한으로 적용된다. 스코프의 경우 타겟 기관의 경계 자산, 클라우드 자산, 모바일 어플리케이션, 직원 등, 사실상 기관/회사와 관련된 자산과 인력이 모두 스코프에 들어간다. 예를 들자면 클라우드 람다 함수부터 작년에 출시한 모바일 앱, 회사 1층에 있는 와이파이 AP, 안내데스크 직원 등. 이 중 당연히 가용성을 해치는 디도스나 다른 파괴적인 성향의 공격들은 제외된다.

### 과정

레드팀 서비스는 실제 공격과 흡사하게 4\~8주 동안 이뤄지며, 이 동안 특정된 공격 라이프사이클 (Targeted Attack Lifecycle)을 따른다. 공격 인프라 구축, 초기 정찰, 초기 침투, 거점 확보, 권한 상승, 내부 정찰, 횡적 이동, 지속성 유지, 미션 수행을 진행한다.

1. **공격 인프라 구축:** 실제 공격자들이 사용하는 C2 서버, 리다이렉터, 피싱을 위한 SMTP 서버, 페이로드 전달 서버 등을 구축한다.
2. **초기 정찰:** OSINT 과 외부망 정찰을 통해 타겟 기관의 외부망 자산, 클라우드 자산, (서브)도메인, 모바일 앱, 회사 조직도, 인원 현황 등에 대해서 조사한다.
3. **초기 침투:** 이메일을 통한 피싱, 전화를 통한 Vishing, 외부망 자산의 취약점, 모바일 어플리케이션 리버싱, 물리 침투 (회사 1층 공공 와이파이, 안내데스크 컴퓨터 등)을 통해 기관의 내부망, 직원의 엔드포인트, 혹은 필요한 계정 정보를 얻는다.
4. **거점 확보:** 타겟 기관의 인프라에 공격자가 조종 가능한 거점을 확보한다
5. **권한 상승 - 내부 정찰 - 횡적 이동:** 거점으로 부터 비순차적으로 권한 상승, 내부 정찰, 횡적 이동을 하며 더 많은 거점을 확보하거나, 미션을 달성하기 위한 타겟 서버/데이터에 접근한다.
6. **지속성 유지:** 블루팀이 레드팀을 발견해 격리/추방 조치를 하더라도 다시 거점에 진입할 수 있도록 지속성을 유지한다.
7. **미션 수행:** 블루팀과 조율한 최종 미션을 수행한다. 더미 데이터 유출, 가짜 랜섬웨어 배포, SWIFT 인프라 접근, 데이터 조작 등이 있다.

라이프사이클을 진행하는 도중 뛰어난 블루팀을 만나면 공격이 더이상 진행되지 않는 경우가 있다. 예를 들어 초기 침투 중 피싱 이메일을 모두 파악한 직원들이 있을수도 있고, 블루팀이 재빠르게 레드팀의 비컨을 처리한 뒤 도메인을 모두 블랙리스트 하는 경우도 있을 것이다.&#x20;

이처럼 정상적인 초기 공격들을 진행할 수 없다고 판단 될 경우 "Assumed Breach" - "이미 뚫렸다고 치고" 시나리오로 들어간다. 이 시나리오에서는 타겟 기관의 한 직원이 피싱에 "당했다고 치고", 특정 엔드포인트에서 레드팀의 비컨을 하나 실행 시킨 뒤 거점 확보, 권한 상승, 내부 정찰, 횡적 이동, 지속성 유지 등의 단계들을 평가한다. 레드팀 서비스는 대부분 4주 \~ 8주의 긴 시간 동안 이뤄지기 때문에 초기 정찰 및 초기 침투가 2\~3번정도 실패하게 되면 8주 내내 초기 침투만 평가할 것은 아니기 때문에 그 다음 단계인 Assumed Breach로 넘어가 고객사의 다른 대응 절차나 보안 통제들을 평가한다.

### 최종 결과물

레드팀 작전 기간이 모두 끝나면 레드팀과 타겟 기관의 CISO는 블루팀에게 연락해 레드팀 작전의 존재를 알린다. 그 뒤, 디브리핑 시간을 갖으며 어떤 공격들을 실행했는지, 블루팀은 어떤 공격을 탐지하고 이에 어떻게 대응했는지 등에 대해 서로 알아보는 퍼플팀 시간을 갖는다. 레드팀은 공격 탐지와 우회, 대응과 대처, 블루팀이 구축한 대응 절차들의 효과적이였던 점과 부족한 간극 등에 대해서 자세하게 보고한다. 모의해킹은 아니지만, 그래도 레드팀 서비스 중 발견한 잘못된 설정 (Misconfiguration)이나 취약점들 또한 모두 취합해 보고한다. 마지막으로 이 모든 정보를 문서화한 레드팀 리포트까지. 이 모든 것들이 레드팀 서비스의 최종 결과물이 된다.

## 누가 레드팀 서비스를 받아야할까?

레드팀 서비스 자체가 프리미엄/틈새 서비스이기 때문에 세상 모든 고객사들을 상대로 레드팀 서비스를 진행할 수는 없다. 예를 들어 10인 중소기업이 레드팀 서비스를 받는 것은 말이 안될 것이다. 따라서 다음과 같은 보안적 수준에 도달한 기업들은 레드팀 서비스를 받는 것을 고려해볼법하다:

1. 회사내 지정된 IT팀과 보안팀이 존재한다
2. 정기적인 웹, 모바일, 외부, 내부 모의해킹 서비스를 받고 있으며, 왠만큼 치명적인 취약점들이 더이상 발견되지 않는다
3. 실제로 보안, IT, 개발 팀들이 발견된 취약점들을 능동적으로 고치고 있다
4. 취약점 스캐너를 정기적으로 사용하거나, 관련된 서비스를 받고 있다
5. 회사 및 업계를 노리는 APT 그룹 및 공격이 존재한다. 혹은, 실제로 공격을 받았던 적이 있다
6. 회사의 가장 중요한 자산이 뭔지 특정할 수 있으며, 이를 보호하거나 모니터링 하는 프로세스가 존재한다. 하지만 이를 시험하고 싶다

위 요소들을 어느정도 충족하는 고객사는 매우 찾기 어렵다. 따라서 레드팀은 아직까지 프리미엄/틈새 (niche) 서비스로 취급된다. 레드팀 서비스는 다른 오펜시브 시큐리티 서비스들을 보완해주는 프리미엄 서비스지, 절때로 모의해킹이나 취약점 점검을 대체하는 “더 우월한” 서비스는 아니다.

## 시장 트렌드

레드팀 서비스는 2010년대 초중반부터 업계에서 서비스 되기 시작했다. 처음에는 극소수의 민간 기업들만 서비스를 이용했지만, 점점 정보보안에 투자를 하는 기업들이 많아짐에 따라 레드팀의 수요는 지속적으로 늘어났다. 이후 2018년도때 유럽 중앙 은행 (European Central Bank) 에서는 각 유럽 은행들이 어떻게 레드팀 서비스를 받아야하는지 등을 포함한 TIBER-EU (Threat Intelligence-based Ethical Red Teaming) 등의 프레임워크를 발표하기도 했다. 개인적으로 아는 학교 선/후배, 회사 동료, 컨퍼런스에서 만난 다른 오펜시브 시큐리티 테스터들 또한 자신들의 기업에서 레드팀 서비스가 지속적으로 수요가 늘어나고 있다고도 한다. 정보보안에 관련된 투자가 증가하고, 더 많은 기업들이 제대로된 보안팀과 방법론들을 구축하며 더 복잡한 레드팀 서비스를 받으려고 하는 것은 어찌보면 당연해 보인다.&#x20;

단, 레드팀은 모의해킹과는 다르게 레드팀 서비스를 권유/강요/강제하는 법, 규제, 그리고 컴플라이언스가 딱히 없다. 모의해킹 서비스의 경우 아무리 고객사들이 보안에 신경을 쓰지 않는다고 해도, 어느정도 모의해킹을 받으라고 강제하는 법과 컴플라이언스들이 있기 때문에 모의해킹 서비스를 받는 경우가 많다. 그러나 레드팀 서비스의 경우 정말 보안에 신경을 쓰는 고객사가 아니라면 "굳이" 받을필요는 없는, 말 그대로의 프리미엄/틈새 서비스다. 그렇다보니 상대적으로 정보보안에 신경을 쓰지 않는 기관/회사들의 경우 레드팀 서비스를 이용하기 보단 최소한의 모의해킹만 간단하게 실행하는 경우가 많다.&#x20;

그렇다보니 경기가 좋고 회사 예산에 여유가 있을 때는 레드팀 서비스를 받으려고자 하는 기업들이 많지만 (코로나 전후의 2018\~2022년), 경기침체(2023\~)를 지날 때는 레드팀 보단 간단한 모의해킹만 받으려고 하는 기업들이 많다. 정보보안이 전반적으로 경기에 영향을 많이 받는 것은 사실이나, 레드팀의 경우 법, 규제, 컴플라이언스의 부재로 인해 그 영향을 더 많이 받는다.&#x20;

## 필요 지식&#x20;

이 섹션은 필자 본인을 위해 만든 섹션이기 때문에 다음 섹션으로 넘어가도 된다.

다음은 2023년 기준으로 레드팀 오퍼레이터가 알고 있고, 다뤄야 할 줄 아는 지식들이다. 물론 정보보안답게 Show, Don't Tell 로써, 그저 아는 것이 중요한게 아니라 직접 그 지식을 적용할 줄도 알아야한다.&#x20;

| 단계                                              | 설명                                                  | 지식                                                                                                                                   | 기술 스택                                                                                                    |
| ----------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| 1. 공격 인프라 구축                                    | 레드팀의 처음부터 끝까지 모든 공격 활동을 할 인프라를 재사용 가능하도록 구축한다       | 도메인 구입, 도메인 분류, 도메인 에이징, C2 서버 구축, 리다이렉터 구축, 피싱 SMTP 구축, 피싱 릴레이 구축, 이메일 SPF, DKIM, DMARC 적용, 작전보안 (OPSEC)                            | Ansible, Terraform, ( Packer), CrossPlane, Bash scripting, Powershell, cloud providers (AWS, Azure, GCP) |
| 2. 초기 정찰                                        | 타겟 기관의 공개적으로 접근 가능한 모든 자산들과 인력들에 관련된 정보를 수집한다       | 직/간접 외부 자산 정보수집, OSINT, Social Engineering, 모바일 어플리케이션 리버싱, 외부망 모의해킹, Cloud                                                          | N/A, 각 지식에 필요한 지식 및 툴 사용 방법                                                                              |
| 3. 초기 침투                                        | 타겟 기관의 내부망 안의 엔드포인트, 외부 자산, 혹은 계정 정보등을 침투하거나 획득한다   | 피싱, Vishing, 페이로드 생성, 방어 우회, 소셜 엔지니어링, C2 서버 설치 및 운영, Malleable C2 Profile, 현존 페이로드 난독화, 현존 페이로드 조작 (User-Defined Reflective Loader) | C, C++, Rust, Powershell, .NET (C#, Boolang), VBScript, Payload Obfuscation, Creating Maldocs            |
| <ol start="4"><li>거점 확보</li></ol>               | 초기 침투로 얻어낸 엔드포인트 / 유저 계정을 이용해 레드팀 작전을 할 거점을 확보한다    | 로컬 정보 수집, 윈도우/리눅스/클라우(AWS, Azure, GCP) 권한 상승, 네트워크 기반/인-메모리 기반/User Identity기반 방어 우회, 지속성 유지 확보                                      | Windows/Linux Internals, Cloud internals & enumeration, AV/EDR Solution Internals, Persistence           |
| <ol start="5"><li>권한 상승, 내부 정찰, 횡적 이동</li></ol> | 확보한 거점으로부터 목표 지점까지 반복적으로 권한 상승, 내부 정찰, 횡적 이동을 실시한다. | 액티브 디렉토리 정찰 + 권한 상승 + 횡적 이동, 클라우드, AAD (Azure AD)                                                                                    | N/A                                                                                                      |

쉽지 않다. 위에 적혀있는 분야 중 한 분야만 잘 다뤄도 취업하는데 걱정이 없는데 (클라우드, 프로그래밍 언어, OS Internals, Active Directory, AAD, DevOps, 등), 이 모든 걸 다 알아야 하고, 이 모든 걸 다 실전에서 적용할 수 있어야한다. 따라서 레드팀의 경우 모의해커 경력이 5년, 10년 이상차가 되어도 엄두도 못내는 분들이 많다.&#x20;

### 마치며&#x20;

레드팀 서비스는 단순히 컴플라이언스 자격 요건을 충족시키기 위한 서비스가 아니라, 기관의 보안 인력과 대응 절차를 전반적으로 평가하고 개선점을 찾아내기 위한 서비스다. 최근 들어 보안에 진심을 보여주고 있는 기관과 기업들의 비중이 크게 높아지고 있다. 더이상 세분화된 모의해킹들은 이들의 보안에 관련된 열정을 충족시켜주기엔 부족하다. 국내에는 아직 레드팀/공격자 시뮬레이션 서비스가 많이 없는 것으로 알고 있다. 이 글을 통해 더 많은 보안 전문가들이 레드팀 서비스에 대해서 알았기를 바라며, 훌륭한 Red Teamer가 되기 위한 공부를 하기 위해 글을 줄인다.

Happy Hacking!





## 레퍼런스

{% embed url="https://blog.sunggwanchoi.com/kor-what-is-red-team-in-infosec/" %}
