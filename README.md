![IAB Tech Lab](https://drive.google.com/uc?id=10yoBoG5uRETSXRrnJPUDuONujvADrSG1)


# OpenRTB 2.x

OpenRTB 2.x 스펙, 2.6 버전부터 시작


#### OpenRTB 소개

https://iabtechlab.com/openrtb  

OpenRTB는 실시간 입찰(Real-Time Bidding)을 위한 개방형 프로토콜이다. 디지털 광고 시장에서 광고주와 퍼블리셔 간의 효율적인 거래를 지원한다. OpenRTB는 광고 입찰 과정을 자동화하고, 실시간으로 광고를 게재할 수 있는 표준화된 방식을 제공한다. 이 프로토콜은 광고 기술 업계에서 널리 채택되어 있으며, 다양한 플랫폼과 시스템 간의 호환성을 높인다. OpenRTB는 광고 입찰의 투명성과 효율성을 극대화해 디지털 광고 생태계의 발전에 기여한다.


#### AdCOM: 광고 공통 객체 모델

https://github.com/InteractiveAdvertisingBureau/AdCOM


#### 버전 관리 정책

OpenRTB 2.6-202211부터 OpenRTB의 버전 번호는 **호환성 깨짐(breaking changes)**이 발생할 때만 증가한다. 즉, OpenRTB 2.7은 OpenRTB 2.6과 구별되는 별개의 버전으로 간주해야 한다. 예를 들어, 수요 측에서는 공급 측에서 받은 입찰 요청(bid request)을 파싱할 때 버전 헤더를 고려할 수 있다. 자세한 내용은 [OpenRTB Principles](#)를 참고한다.

현재 OpenRTB 명세서의 버전은 **호환성 유지(non-breaking) 개선 사항**이 있을 경우 약 한 달에 한 번씩 업데이트된다. 이는 새로운 필드, 객체, 열거형 목록의 값 추가 등을 포함한다. 또한, 명세서 자체에 실질적인 영향을 미치지 않는 설명의 명확화나 수정과 같은 오류(errata)도 매월 업데이트를 통해 처리된다. 자세한 내용은 [Errata](#)를 참고한다.

버전 번호 형식은 **주 버전(major)**과 **부 버전(minor)**, 그리고 **날짜 코드**로 구성된다. 예를 들어, 2.6-202211은 2022년 11월 릴리스를 의미한다. 이후 릴리스는 2.6-202212(12월), 2.6-202301(1월) 등으로 이어질 수 있다.

이 버전 관리 정책은 OpenRTB 2.x의 이전 관행과는 차이가 있다. OpenRTB 2.6 이전 버전에서는 주 버전 번호가 호환성 깨짐을, 부 버전 번호가 호환성 유지 변경을 나타냈다.


#### 기여 방법

1. 이 GitHub 저장소를 여러분의 GitHub 계정에 포크한다.
1. 포크한 저장소에서 `develop` 브랜치를 기반으로 새로운 브랜치를 만든다. 브랜치 이름은 짧지만 설명이 가능한 이름으로 지정한다(예: 새로운 flux capacitor 객체를 추가한다면 "add-flux-capacitor"와 같은 이름을 사용).
1. 브랜치에서 원하는 변경 사항을 적용한다. 논리적으로 구분되는 변경 사항마다 별도의 커밋을 생성한다(예: 브랜치에서 두 가지 기능을 추가한다면 두 개의 커밋을 만든다). 각 커밋에는 짧지만 설명이 가능한 "요약" 이름을 지정하고, "설명" 부분에 변경 사항에 대한 자세한 내용을 적는다.
1. (선택 사항) 조직 내부에서 리뷰와 피드백을 진행한 후, 필요한 추가 업데이트를 브랜치에 반영한다.
1. 브랜치 작업이 완료되면 GitHub에 푸시한다. 그런 다음 Pull Request(PR)를 생성해 포크한 저장소의 변경 사항을 원본 저장소의 `develop` 브랜치로 병합할 것을 제안한다.
1. Programmatic Supply Chain Working Group과 Commit Group이 여러분의 업데이트를 검토하고 코멘트를 남기며 변경을 제안할 수 있다. PR이 승인되기 전에 추가 커밋이 필요할 수도 있다.
1. PR이 승인되면 다음 월별 릴리스 시점에 `main` 브랜치로 병합된다. 릴리스 프로세스에 대한 자세한 내용은 아래를 참고한다.
1. (선택 사항) PR이 오랫동안 열려 있는 경우, `develop` 브랜치로 자동 병합이 불가능할 수 있다. 이 경우 PR에 충돌 해결을 요청하는 메시지가 표시된다.


#### 월간 릴리즈 절차 (리포지토리 관리자용)

매월 동안 Programmatic Supply Chain Working Group과 Commit Group은 제출된 PR을 검토하고 다음과 같은 조치를 취할 수 있다:
- 다음 릴리즈에 포함하기 위해 승인
- 작성자에게 추가 변경 요청
- (이유와 함께) 거부

월 마지막 주에 `develop` 브랜치에 승인된 PR이 있다면 다음 단계를 실행한다:

1. `develop` 브랜치를 `main` 브랜치로 병합하는 PR을 생성한다.
1. 새로운 릴리즈와 태그를 동시에 생성한다. 릴리즈 명명 규칙은 "OpenRTB v2.6-YYYYMM"이며, 태그는 "2.6-YYYYMM"이다. 여기서 YYYYMM은 날짜 코드이다 (예: 202301은 2023년 1월).

이 절차를 통해 OpenRTB의 각 릴리즈에 대해 태그가 지정된 릴리즈가 생성되고, 이들의 기록을 쉽게 확인할 수 있다. 리포지토리의 `main` 브랜치는 항상 최신 릴리즈를 반영하며, 진행 중인 개발 작업은 항상 `develop` 브랜치에서 이루어진다.


#### 문의하기

추가 정보를 원하거나 참여하고 싶다면 support@iabtechlab.com으로 이메일을 보내주세요.


#### IAB Tech Lab 소개

IAB Technology Laboratory는 비영리 연구 개발 컨소시엄으로, 글로벌 산업 기술 표준과 솔루션을 제정하고 기업들이 이를 구현할 수 있도록 지원하는 역할을 한다. Tech Lab의 목표는 디지털 광고 및 마케팅 공급망에서 발생하는 마찰을 줄이는 동시에 산업의 안전한 성장에 기여하는 것이다. IAB Tech Lab은 기술 표준 개발을 주도하고, IAB 표준을 빠르고 비용 효율적으로 구현할 수 있도록 코드 라이브러리를 생성 및 유지하며, 기업들이 자신들의 기술 솔루션이 IAB 표준과 호환되는지 평가할 수 있는 테스트 플랫폼을 구축한다. 지난 18년 동안 IAB 표준은 디지털 광고 공급망의 상호 운용성과 수익성 있는 성장을 위한 기반이 되어 왔다.

IAB Tech Lab에 대해 더 알아보려면 다음 링크를 참고하세요: [https://www.iabtechlab.com/](https://www.iabtechlab.com/)


#### 기여자와 기술 거버넌스

OpenRTB 작업 그룹 멤버들이 이 저장소에 기여한다. 프로그램매틱 공급 작업 그룹에 참여하려면 IAB Tech Lab의 멤버여야 한다. 프로젝트의 기술 거버넌스와 코드 커밋은 IAB Tech Lab 프로그램매틱 공급 체인 커밋 그룹에서 담당한다.

작업 그룹에서 변경 사항을 제출하는 방법에 대해 더 알아보려면 다음 링크를 참고하자: [So, You'd Like to Propose a Change...](http://iabtechlab.com/blog/so-youd-like-to-propose-a-change-to-openrtb-adcom/)


### 라이선스

OpenRTB 스펙은 IAB Tech Lab에서 Creative Commons Attribution 3.0 라이선스로 제공된다. 이 라이선스의 사본을 보려면 creativecommons.org/licenses/by/3.0/을 방문하거나 Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA로 문의한다.

OpenRTB 저장소, Programmatic Supply Chain Working Group의 구성원, 또는 OpenRTB 2.x와 관련하여 IAB Tech Lab에 아이디어, 스펙, 소프트웨어 코드, 문서, 파일 또는 기타 자료(이하 "제출물")를 제출함으로써, 여러분은 해당 제출물을 Creative Commons Attribution 3.0 라이선스 하에 IAB Tech Lab에 라이선스 부여하는 데 동의한다. 또한 해당 제출물이 이 라이선스의 조건에 따라 공개적으로 사용 및 제공될 수 있음을 동의한다. 만약 여러분이 IAB Tech Lab의 회원이라면, [IPR 정책](https://iabtechlab.com/ipr-iab-techlab/acknowledge-ipr/)의 조건도 여러분의 제출물에 적용될 수 있다. IPR 정책이 제출물에 적용되는 경우, Creative Commons Attribution 3.0 라이선스와 IPR 정책 간에 충돌이 발생하면 IPR 정책이 우선한다.


#### 책임의 한계

이 문서에서 제공하는 표준, 규격, 측정 가이드라인 및 기타 자료 또는 서비스("제품 및 서비스")는 "있는 그대로" 및 "이용 가능한 상태"로 제공된다. IAB 테크놀로지 랩(Tech Lab)은 이와 관련하여 어떠한 보증도 하지 않으며, 명시적, 묵시적 또는 법정 보증을 포함한 모든 보증을 명시적으로 부인한다. 여기에는 상품성, 특정 목적에의 적합성, 가용성, 오류 없음 또는 중단 없는 운영에 대한 보증뿐만 아니라 거래 관행, 이행 과정 또는 상관습에서 비롯된 모든 보증도 포함된다. 법률상 Tech Lab이 묵시적 보증을 부인할 수 없는 경우, 해당 보증의 범위와 기간은 해당 법률에서 허용하는 최소한으로 제한된다.

제품 및 서비스는 비즈니스 또는 법률적 조언을 제공하지 않는다. Tech Lab은 제품 및 서비스가 귀하 및/또는 귀하의 제품 또는 서비스가 모든 적용 가능한 법률, 규정 또는 자율 규제 프레임워크를 준수하도록 보장하지 않는다. 귀하는 데이터 보호 법률을 포함한 모든 관련 법규를 준수할 전적인 책임을 진다. 여기에는 캐나다의 개인정보 보호 및 전자문서법, EU 데이터 보호 지침, EU 전자 프라이버시 지침, EU 일반 데이터 보호 규정(GDPR), 그리고 발효 시 EU 전자 프라이버시 규정 등이 포함되지만 이에 국한되지 않는다.


