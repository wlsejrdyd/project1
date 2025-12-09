# 📊 INFRA - Infrastructure Monitoring Dashboard

> 실시간 인프라 모니터링 + CI/CD 파이프라인 + 백업 상태 통합 대시보드

[![Deploy](https://github.com/wlsejrdyd/infra/actions/workflows/deploy.yml/badge.svg)](https://github.com/wlsejrdyd/infra/actions/workflows/deploy.yml)
[![Ansible](https://github.com/wlsejrdyd/infra/actions/workflows/ansible.yml/badge.svg)](https://github.com/wlsejrdyd/infra/actions/workflows/ansible.yml)

## 🌐 Live

- **Dashboard**: https://infra.deok.kr
- **Prometheus**: https://infra.deok.kr/prometheus
- **Grafana**: https://infra.deok.kr/grafana

---

## ✨ 주요 기능

### 📈 시스템 메트릭
- CPU, Memory, Disk 사용률 실시간 모니터링
- Uptime 표시
- CPU 사용률 1시간 히스토리 차트

### 🔌 서비스 상태
- Nginx, Prometheus, Grafana, Node Exporter, MariaDB 상태
- Prometheus `up` 메트릭 기반 자동 체크

### ☸️ Kubernetes 클러스터
- Pod 상태 (Running/Pending/Failed)
- Node Ready 상태
- Cluster Overview 통계

### 🚀 CI/CD Pipeline
- GitHub Actions 멀티 repo 통합 표시
- **infra** / **salm** / **mgmt** 필터링
- 실시간 배포 현황 확인

### 🔧 Ansible Execution
- 서비스 상태 체크 결과
- 포트 도달 가능 여부
- OK/Changed/Failed/Skipped 통계

### 💾 Backup Status
- SALM / Mgmt / Database 백업 현황
- 최근 백업 파일 목록 + 용량
- Success/Failed 통계

---

## 🛠️ Tech Stack

| 영역 | 기술 |
|------|------|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript |
| **Charts** | Chart.js |
| **Monitoring** | Prometheus, Grafana, Node Exporter |
| **Container** | Kubernetes (kube-state-metrics) |
| **Automation** | Ansible |
| **CI/CD** | GitHub Actions |
| **Server** | Nginx, Rocky Linux 9 |

---

## 📁 프로젝트 구조

```
infra/
├── index.html           # 메인 대시보드
├── ansible/
│   ├── inventory/       # 인벤토리
│   ├── playbooks/
│   │   ├── site.yml     # 서비스 상태 체크
│   │   └── backup.yml   # 백업 실행
│   └── roles/           # Ansible 역할
├── reports/             # Ansible 리포트 (JSON)
│   ├── report_*.json    # 서비스 체크 결과
│   └── backup_status.json # 백업 상태
├── docs/                # 문서
└── .github/workflows/   # CI/CD
    ├── deploy.yml       # 대시보드 배포
    └── ansible.yml      # Ansible 실행
```

---

## 📊 데이터 소스

| 데이터 | 소스 | 갱신 주기 |
|--------|------|----------|
| 시스템 메트릭 | Prometheus API | 10초 |
| 서비스 상태 | Prometheus `up` 메트릭 | 10초 |
| K8s 상태 | kube-state-metrics | 10초 |
| CI/CD | GitHub Actions API | 1분 |
| Ansible | `/reports/*.json` | 1분 |
| 백업 | `/reports/backup_status.json` | 1분 |

---

## 🚀 배포

### 자동 배포 (GitHub Actions)
`main` 브랜치 push 시:
1. SSH로 서버 접속
2. Git pull
3. Nginx reload

### Ansible 자동 실행
- GitHub Actions에서 주기적 실행
- 서비스 상태 체크 → JSON 리포트 생성

### 백업 Cron
```bash
# 매일 새벽 3시 백업
0 3 * * * cd /app/infra/ansible && ansible-playbook playbooks/backup.yml
```

---

## ⚙️ 설정

### Nginx Proxy (GitHub API)
```nginx
location /api/github/ {
    proxy_pass https://api.github.com/;
    proxy_set_header Authorization "token ${GITHUB_TOKEN}";
    proxy_set_header Accept "application/vnd.github.v3+json";
    proxy_set_header User-Agent "infra-dashboard";
    proxy_ssl_server_name on;
}
```

### GitHub Actions Secrets
| Secret | 설명 |
|--------|------|
| `SERVER_HOST` | 서버 IP/도메인 |
| `SERVER_USER` | SSH 사용자 |
| `SSH_PRIVATE_KEY` | SSH 개인키 |
| `SERVER_PORT` | SSH 포트 |

---

## 📸 Preview

![Dashboard Preview](docs/preview.png)

---

## 👤 Author

- GitHub: [@wlsejrdyd](https://github.com/wlsejrdyd)
- Email: wlsejrdyd@gmail.com
