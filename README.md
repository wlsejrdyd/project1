# Infrastructure Dashboard

실시간 인프라 모니터링 대시보드 with Prometheus, Grafana, Ansible, GitHub Actions, Kubernetes

![Dashboard Preview](docs/preview.png)

## 🌐 Live Demo

- **Dashboard**: https://project1.deok.kr
- **Prometheus**: https://project1.deok.kr/prometheus
- **Grafana**: https://project1.deok.kr/grafana

---

## 📋 Overview

통합 모니터링 시스템입니다.

### 주요 기능

| 기능 | 설명 |
|------|------|
| **실시간 메트릭** | CPU, Memory, Disk, Network 사용률 |
| **서비스 상태** | Nginx, MariaDB, Spring Boot 등 서비스 Up/Down |
| **CI/CD 현황** | GitHub Actions 파이프라인 성공/실패 이력 |
| **Ansible 로그** | 자동화 작업 실행 결과 (OK/Changed/Failed) |
| **Grafana 연동** | 상세 메트릭 대시보드 임베드 |
| **Kubernetes 연동** | Node, Pods 상태체크 추가 |

---

## 🛠️ Tech Stack

### Infrastructure
- **OS**: Rocky Linux 9
- **Web Server**: Nginx (Reverse Proxy + SSL)
- **Database**: MariaDB 10.x
- **Virtualization**: Hyper-V

### Monitoring
- **Prometheus**: 메트릭 수집 및 저장
- **Grafana**: 시각화 대시보드
- **Node Exporter**: 시스템 메트릭 수집

### Frontend
- **HTML5 / CSS3 / Vanilla JavaScript**
- **Chart.js**: 실시간 차트

### DevOps
- **Ansible**: 서버 프로비저닝 자동화
- **GitHub Actions**: CI/CD 파이프라인
- **Kubernetes**: Node 및 Pods 상태 체크 정보 시각화

---

## 📝 License

MIT License

---

## 👤 Author

- GitHub: [JINDEOKYONG](https://github.com/wlsejrdyd)
- Email: wlsejrdyd@gmail.com
