# 장민호 | Backend · DevOps

Java·Spring 백엔드를 개발하고, AWS 위에 직접 배포·운영하며 **정확성과 안정성까지 책임지는 개발자**를 지향합니다.

- 📧 jangmh697@gmail.com
- 🛠 Java, Spring Boot, MySQL, Redis / AWS(EKS·VPC·RDS), Docker, Kubernetes, Terraform / GitHub Actions, ArgoCD, Prometheus, Grafana
- 📜 정보처리기사, SQLD

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

## 📌 성장 흐름

**설계**(TodoList — 세션 인증·장애복구 매트릭스) → **구축·배포**(Foldy — JWT·Docker·CI/CD·IaC) → **운영 심화**(TaskFarm — 정합성·관측성·보안·카오스)

세 프로젝트 모두 인증/보안을 담당하며, 만드는 것에서 배포·운영·검증까지 범위를 넓혀왔습니다.
