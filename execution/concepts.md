---
description: TA0002
---

# 개념

실행은 공격자가 타겟 호스트에서 코드를 실행하는 단계다. 코드를 실행하는 방법은 비단 바이너리 파일 뿐만 아니라 많이 있다. 실행 단계에는 많은 TTP들이 있지만, 잘 알려지고 개인적으로 사용해본 실행 TTP는 다음과 같다:&#x20;

* 스크립트 언어와 인터프리터&#x20;
  * 파워쉘&#x20;
    * 파워쉘 + 파워쉘&#x20;
    * 파워쉘 + C#&#x20;
    * 파워쉘 + winapi&#x20;
  * cmd + Batch 스크립트
  * 파이썬 Interpreter + 파이썬 코드 &#x20;
* 쉘코드와 프로세스 인젝션 (왜 프로세스 인젝션 T1055이 권한 상승인지 이해가 잘 안간다)&#x20;
* Fork & Run&#x20;
* Inline Process Execution&#x20;
* 악성코드 컨테이너화&#x20;
  * ISO/IMG
  * 악성 가상머신 + Hyper-V&#x20;
* Native API&#x20;
  * WinAPI&#x20;
  * Direct Syscalls (시스템 콜)&#x20;
* Scheduled Task&#x20;
  * Cronjobs&#x20;
  * 작업 스케줄&#x20;
* LOLBAS, LOLBINS&#x20;
  * 각 운영체제에 기본적으로 설치되어 있는 기본 바이너리 파일들을 이용해 코드실행, 파일 다운로드, 데이터 유출 등을 진행&#x20;
* WMI&#x20;

이 페이지에서는 공격자들이 다양한 방법으로 어떻게 코드를 실행하는지에 대해서 알아본다.&#x20;