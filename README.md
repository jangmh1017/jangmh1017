# 장민호 | Backend · DevOps

Java·Spring 백엔드를 개발하고, AWS 위에 직접 배포·운영하며 **정확성과 안정성까지 책임지는 개발자**를 지향합니다.

- 📧 jangmh697@gmail.com
- 🛠 Java, Spring Boot, MySQL, Redis / AWS(EKS·VPC·RDS), Docker, Kubernetes, Terraform / GitHub Actions, ArgoCD, Prometheus, Grafana
- 📜 정보처리기사, SQLD, 컴퓨터활용능력 1급 · TOEIC 830

> 팀 프로젝트는 부트캠프 조직(CLD-05) 저장소에서 진행했습니다. 아래에 **제가 담당한 파트와 커밋 이력**을 정리했습니다.

---

## 🌱 TaskFarm — 할일 게이미피케이션 서비스
`2026.06 ~ 2026.07` · 5인 팀 · **백엔드(재화·인증·AI) + 인프라(IaC·관측·보안)**

| 담당 | 내용 |
| --- | --- |
| 재화 정합성 | 비관적 락 + 단일 트랜잭션 설계 → 잔액 = 원장 항상 일치 |
| AI 연동 | Gemini API 연동 + SHA-256 캐시키 Redis 캐싱(TTL 7일), 실패 시 폴백 |
| 인프라 | Terraform으로 VPC·IAM 코드화, dev/prod 환경 분리 |
| 관측·보안 | Prometheus·Grafana 구축, Falco 런타임 탐지(K8S API 접근 32건 탐지·이벤트 유실 0) |
| 회복력 | AWS FIS 카오스 실험 → 노드 장애 약 4분 내 자동 복구 확인, 단일 장애점 발견·개선안 제시 |
| 보안 | CORS 와일드카드 취약점 직접 발견·수정 후 재검증 |

- 애플리케이션 → [CLD-05/team4-taskfarm-app](https://github.com/CLD-05/team4-taskfarm-app) · [내 커밋 보기](https://github.com/CLD-05/team4-taskfarm-app/commits?author=jangmh1017)
- 인프라(Terraform) → [CLD-05/team4-taskfarm-infra](https://github.com/CLD-05/team4-taskfarm-infra) · [내 커밋 보기](https://github.com/CLD-05/team4-taskfarm-infra/commits?author=jangmh1017)

---

## 📁 Foldy — 폴더형 학습 메모 서비스
`2026.05 ~ 2026.06` · 6인 팀 · **백엔드(인증·공통구조) + DevOps(컨테이너·IaC·CI/CD)**

| 담당 | 내용 |
| --- | --- |
| 인증 | JWT 무상태 인증 필터 구현 → 파드 수평 확장에도 인증 일관성 유지 |
| 공통 구조 | 공통 Response·예외 처리 규격 설계 후 팀 표준으로 합의 |
| 컨테이너 | 멀티스테이지 Dockerfile 최적화(경량·nonroot) |
| 인프라 | Terraform VPC 모듈, prod backend 환경 격리 |
| CI/CD | GitHub Actions 빌드·테스트 자동화 + ArgoCD GitOps, dev/prod overlays 분리 |

- [CLD-05/team3-app](https://github.com/CLD-05/team3-app) · [내 커밋 보기](https://github.com/CLD-05/team3-app/commits?author=jangmh1017)

---

## ✅ TodoList — 클라우드 아키텍처 설계
`2026.03` · 팀 프로젝트 · **인증/보안 + 장애복구 설계** · *설계·기획 단계 (실배포 X)*

| 담당 | 내용 |
| --- | --- |
| 인증 | Spring Security 폼 로그인(세션) + BCrypt 해싱, CustomUserDetailsService |
| 설계 | 장애 시나리오별 감지 → 자동복구 → 복구 후 상태 매트릭스 (EC2·RDS Failover·AZ 전환) |
| DB | ERD·DDL·DML 설계 참여 |

> 6개 팀 중 장애복구 설계 부문 최고 평가

- [CLD-05/team02_todolist](https://github.com/CLD-05/team02_todolist) · [내 커밋 보기](https://github.com/CLD-05/team02_todolist/commits?author=jangmh1017)

---

## 🛠 개인 프로젝트 — 업무 자동화 도구

실제로 반복되는 사무 업무를 줄이기 위해 직접 기획하고 만든 프로그램입니다. 비개발자가 쓰는 상황을 가정해 **GUI + 단일 실행 파일(exe)** 로 배포했고, **로직과 화면을 분리해 단위 테스트**로 검증했습니다.

### 📊 엑셀 합치기 도우미 `Python · openpyxl · tkinter · pytest 8`

양식이 제각각인 엑셀 파일을 폴더째 넣으면 하나로 통합하고, 출처별·품목별 요약까지 생성합니다.

| 항목 | 내용 |
| --- | --- |
| 양식 차이 흡수 | 열 이름 별칭 매핑(settings.json) + 상단 10줄 머리글 자동 탐색 |
| 값 정규화 | `12,000원`, `2026.09.03` 같은 문자열 금액·날짜 변환 |
| 중복 합산 방지 | 합계·총계·소계 줄 자동 제외 |
| 검증 가능한 요약 | 요약 시트를 수식으로 생성 + 검증 줄로 전체 금액 대조 |
| 안전 설계 | 원본 읽기 전용(테스트로 검증), 처리기록에 셀 내용 미저장, 오프라인 처리 |

### ✉️ 엑셀 목록 메일 발송 도우미 `Python · smtplib · keyring · pytest 10`

엑셀 수신자 목록과 템플릿으로 사람마다 이름·금액·첨부가 다른 메일을 일괄 발송합니다. 되돌릴 수 없는 작업이라 **오발송 방지 설계**에 집중했습니다.

| 항목 | 내용 |
| --- | --- |
| 3단계 발송 | 검사·미리보기 → 나에게 테스트 발송 → 실제 발송(건수 정확 입력 시 시작) |
| 재발송 방지 | 주소+제목을 발송기록과 대조, 중단 후 재실행 시 미발송 대상만 발송 |
| 발송 전 검사 | 형식 오류·중복 주소·빈 템플릿 값·첨부 누락·폴더 밖 경로 자동 제외 |
| 보안 | 비밀번호 파일 미저장(Windows 자격 증명 관리자 선택 저장), SSL/STARTTLS만 허용, 기록에 본문·비밀번호 미저장, 화면 주소 마스킹 |

### 🧾 원천세 후속 신고 자동화 `진행 중`

세무회계 사무실의 매월 반복 업무(간이지급명세서·일용근로소득지급명세서 제출)를 자동화하는 Windows 로컬 전용 프로그램입니다. 설계 판단을 **ADR 문서로 기록**하며 진행하고 있습니다.

- 현재: 입력 검사, 업체 목록 대조, 근로 월별 이력·반기 판단 구현
- 보안: 시크릿 관리 모듈 분리, 실제 데이터·수임처 목록은 저장소에 포함하지 않음
- → [jangmh1017/withholding-auto](https://github.com/jangmh1017/withholding-auto)

---

## 📌 성장 흐름

**설계**(TodoList — 세션 인증·장애복구 매트릭스) → **구축·배포**(Foldy — JWT·Docker·CI/CD·IaC) → **운영 심화**(TaskFarm — 정합성·관측성·보안·카오스)

세 프로젝트 모두 인증/보안을 담당하며, 만드는 것에서 배포·운영·검증까지 범위를 넓혀왔습니다.
