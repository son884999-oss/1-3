# 워크플로우 설계

## 비교 분석 보고서 
### 사용한 도구 
Make/Ziaper

### 구현 과정/워크플로우

의도하는 구현 결과 : 80점 이상인 경우 한국대학교 합격 메일을 / 80점 미만인 경우 불합격 메일을 보내는 자동화 시스템을 구현하려고 함. 

공통 

Google Form 이름과 점수를 입력받습니다.
<img width="1106" height="830" alt="구글 폼" src="https://github.com/user-attachments/assets/a043d2e8-a7a9-45f6-965a-67d877f46753" />

Google sheets 받은 데이터를 기록합니다.
<img width="929" height="474" alt="데이터 시트" src="https://github.com/user-attachments/assets/c3a75650-fb37-4fda-adbf-68e57c4f9f48" />


1. make 

Make에서

트리거 :Google sheets의 Watch new row기능으로 새로 등록된 데이터를 확인합니다.

필터 :입력된 항목중 점수가 80점 이상인 경우와 80점 미만인 경우를 Router 기능을 통해 분기해 기능을 다르게 처리합니다.

액션 가. 80점 이상인 경우 Gmail sent an email 에서 합격 메일을 보냅니다

액션 나. 80점 미만인 경우 Gmail sent an email 에서 불합격 메일을 보냅니다.
<img width="1809" height="870" alt="Make 조건분기" src="https://github.com/user-attachments/assets/840d88a0-28ff-4406-b745-9f2e4181e61d" />
2. Zapier
3. 
트리거 : Google sheets의 New or updated spreadsheets Row로 추가되거나 업데이트 된 데이터를 확인합니다

필터 : Paths 의 Split into paths 기능을 통해 80점 이상인 경우와 80점미만인 경우를 분기합니다

액션 가. 80점 이상인 경우 Gmail의 sent Email 으로 합격메일을 보냅니다.

액션 나. 80점 이상인 경우 Gmail의 sent Email 으로 불합격메일을 보냅니다.


<img width="924" height="775" alt="Zipier 메인화면" src="https://github.com/user-attachments/assets/8ae87ed3-0613-4660-a680-7f057496dd22" />

### Make vs Zapier 비교 분석

 종합 비교표

| 비교 항목 | Make (구 Integromat) | Zapier |
|---|---|---|
| **UI/UX** | 시각적 플로우차트 방식 (노드 기반 캔버스) — 직관적이나 초보자에겐 다소 복잡 | 단계별 리스트 방식 (Step-by-Step) — 단순하고 직관적, 초보자 친화적 |
| **설정 난이도** | 중~고급 / 조건 분기·반복·오류 처리 등 세밀한 설정 가능 | 낮음~중간 / 빠른 설정 가능, 복잡한 로직 구현엔 한계 있음 |
| **연동 서비스 범위** | 1,500개 이상 앱 지원 (HTTP/Webhook으로 커스텀 연동 가능) | 6,000개 이상 앱 지원 (업계 최다 수준) |
| **무료 플랜 범위** | 월 1,000 작업(Operations) / 시나리오 수 무제한 / 5분 간격 실행 | 월 100 작업(Tasks) / Zap 5개 제한 / 15분 간격 실행 |
| **실행 로그 확인 방식** | 시나리오별 상세 실행 히스토리 제공 / 각 모듈의 입출력 데이터 시각적 확인 가능 | Zap History에서 실행 결과 확인 / 성공·실패 여부 및 오류 메시지 제공 |
| **데이터 가공 능력** | 내장 함수·수식·JSON 파싱·반복(Iterator)·집계(Aggregator) 등 강력한 데이터 처리 | 기본 텍스트 변환·포맷터 제공 / 복잡한 데이터 가공은 상대적으로 제한적 |
| **오류 처리 방식** | 오류 핸들러 모듈 내장 (Break / Ignore / Rollback / Commit 선택 가능) | 기본적인 오류 알림 제공 / 세밀한 오류 분기 처리는 어려움 |
| **가격 정책** | 무료 플랜 포함 / Core $9/월~ (작업 수 기준 과금) | 무료 플랜 포함 / Starter $19.99/월~ (Task 수 기준 과금, 상대적으로 고가) |
| **실행 주기 (최소 간격)** | 무료: 15분 / 유료: 1분 간격까지 설정 가능 | 무료: 15분 / 유료: 1분 간격까지 설정 가능 |
| **팀 협업 기능** | 팀 플랜에서 조직 단위 공유 및 권한 관리 가능 | 팀 플랜에서 공유 Zap 및 폴더 관리 가능 / 협업 기능은 Zapier가 더 성숙 |


  항목별 상세 분석

 1.  UI/UX

| 구분 | Make | Zapier |
|---|---|---|
| 인터페이스 방식 | 캔버스 기반 시각적 플로우 (노드 연결) | 선형 단계별 설정 (리스트 형태) |
| 초보자 접근성 | ⭐⭐⭐ (학습 곡선 존재) | ⭐⭐⭐⭐⭐ (매우 쉬움) |
| 복잡한 워크플로우 표현 | ⭐⭐⭐⭐⭐ (시각적으로 한눈에 파악) | ⭐⭐⭐ (단계가 많아지면 가독성 저하) |
| 모바일 지원 | 제한적 | 모바일 앱 제공 |

 2.  연동 서비스 범위

| 구분 | Make | Zapier |
|---|---|---|
| 공식 지원 앱 수 | 1,500개 이상 | 6,000개 이상 |
| 커스텀 연동 | HTTP / Webhook 모듈 (무료 포함) | Webhooks (유료 플랜 필요) |
| 국내 서비스 지원 | 카카오, 네이버 등 일부 제한적 | 카카오, 네이버 등 일부 제한적 |
| 엔터프라이즈 앱 | Salesforce, SAP 등 지원 | Salesforce, SAP 등 지원 |


3.  무료 플랜 범위

| 구분 | Make | Zapier |
|---|---|---|
| 월 작업 수 | **1,000 Operations** | **100 Tasks** |
| 시나리오/Zap 수 | **무제한** | **5개 제한** |
| 최소 실행 간격 | 15분 | 15분 |
| 멀티 스텝 자동화 | **가능** | 불가 (유료 필요) |
| 데이터 저장소 | 제공 (Data Store) | 미제공 |

---

4. 실행 로그 확인 방식

| 구분 | Make | Zapier |
|---|---|---|
| 로그 명칭 | 실행 히스토리 (Execution History) | Zap History |
| 모듈별 입출력 확인 | 각 모듈의 입력/출력 데이터 상세 확인 | 단계별 결과 확인 가능하나 상세도 낮음 |
| 오류 위치 파악 | 어느 모듈에서 실패했는지 시각적 표시 | 어느 단계에서 실패했는지 표시 |
| 재실행 기능 | 실패한 실행 재시도 가능 |  Replay 기능 제공 |

5.  입문 난이도

| 비교 항목 | Make | Zapier |
|---|---|---|
| 첫 화면 직관성 | ⭐⭐⭐ 중간 | ⭐⭐⭐⭐⭐ 매우 직관적 |
| 한국어 지원 여부 | ❌ 미지원 | ❌ 미지원 |
| 첫 자동화 완성까지 걸리는 시간 | 약 30~60분 | 약 10~20분 |
| 오류 메시지 이해 난이도 | ⭐⭐ 어려움 | ⭐⭐⭐⭐ 쉬운 편 |
| 가이드 투어 / 온보딩 제공 | ⭐⭐⭐ 기본 제공 | ⭐⭐⭐⭐⭐ 단계별 안내 |


---

## 최종 추천 가이드

| 사용자 유형 | 추천 도구 | 이유 |
|---|---|---|
| 자동화 입문자 | ✅ **Zapier** | 쉬운 UI, 빠른 설정, 풍부한 튜토리얼 |
| 복잡한 워크플로우 구현 | ✅ **Make** | 강력한 데이터 처리, 조건 분기, 반복 처리 |
| 비용 절감이 중요한 경우 | ✅ **Make** | 무료 플랜 범위가 훨씬 넓음 |
| 다양한 앱 연동이 필요한 경우 | ✅ **Zapier** | 6,000개 이상 앱 지원 |
| 개발자 / 기술 친화적 사용자 | ✅ **Make** | API 커스텀 연동, 데이터 가공 자유도 높음 |
| 팀 협업 중심 | ✅ **Zapier** | 성숙한 팀 협업 기능, 공유 Zap 관리 |

### 프로젝트 2
## 자유 주제: AI 관련 뉴스 자동 수집 및 정리

### 반복 업무 정의
매일 여러 뉴스 사이트를 방문해 AI 관련 기사(ChatGPT, Claude, Gemini, GPT 등)를
직접 검색하고, 관심 기사를 골라 스프레드시트에 제목·링크·날짜를 정리한 뒤
메일로 공유하는 작업. 하루에도 여러 번 반복되어 시간 소모가 큼.

### 선정 도구: Make
**선정 이유**
- 시각적 노드 기반이라 Trigger→Filter→Action 흐름을 직관적으로 설계 가능
- 무료 플랜(1,000 Ops/월) 범위 내에서 구현 가능해 과금 리스크 없음
- RSS, AI 모듈, Gmail, Google Sheets 등 필요한 커넥터를 모두 지원

### 워크플로우 흐름
1) **Trigger**: RSS – Watch RSS feed items (새 뉴스 기사 감지)
2) **Filter(조건 분기)**: AI 도구(Claude/Gemini/ChatGPT/GPT) 관련 및 "AI"라는 단어가 포함된 기사만 통과 
3) **Action 1**: Gmail – Send an Email (필터 통과한 기사 메일 발송)
4) **Action 2**: Google Sheets – Add a Row
   (제목 / 링크 / 수집일시 자동 기록)

### 스케줄링 및 Trigger 작동 원리
- Make 시나리오를 15분 주기로 스케줄링하여, RSS 피드를 자동으로 폴링(체크)함
- 폴링 시 새로운 기사가 감지되면 Trigger가 발동하여 시나리오 전체가 자동 실행됨
- 즉, "15분마다 확인 → 새 기사 존재 시 자동 실행" 구조로 동작
- 
<img width="1452" height="614" alt="MAKE 실행" src="https://github.com/user-attachments/assets/59b709b0-9dcb-4f2d-9729-cb976317d0d4" />
<img width="684" height="716" alt="분기" src="https://github.com/user-attachments/assets/06bbdb75-fc54-4e09-8b65-9e4a74444e5c" />

# 전체화면
<img width="1920" height="1031" alt="15m" src="https://github.com/user-attachments/assets/6c47c4fd-44bd-480e-a6d2-5d87dd03cae6" />
 
