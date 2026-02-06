# 🚀 PVE 기반 VM Kubernetes 홈랩 (K3s)

이 저장소는 Proxmox VE 환경 위에 구축된 VM 기반 쿠버네티스 클러스터의 모든 매니페스트와 설정값을 관리합니다.

## 🏗 클러스터 구성
- **OS:** Ubuntu Server 24.04 LTS
- **K8s Distro:** K3s (1 Master, 2 Workers)
- **Node IP 대역:** 192.168.0.200 ~ 202
- **Network:** vmbr0 (Bridge Mode)

## 🛠 주요 구성 요소 및 설치 순서

### 1. Infrastructure (기반 시설)
- **MetalLB:** 로컬 네트워크 IP를 서비스에 할당 (`192.168.0.190-199`)
- **Ingress-Nginx:** 클러스터 외부 접속 창구 (L7 LoadBalancer)
- **NFS Provisioner:** PVE LXC 기반 NFS 서버를 활용한 동적 볼륨(PV) 할당

### 2. Applications (서비스)
- **Prometheus & Grafana:** 클러스터 리소스 모니터링 (Port 80 Ingress 노출)

## 📝 관리 방법

### Helm 차트 업데이트
설정 파일(`values.yaml`)을 수정한 후 아래 명령어를 사용합니다.
```bash
helm upgrade [RELEASE_NAME] [CHART_NAME] -f values.yaml
```

## TODO
ArgoCD 도입, 이 저장소의 main 브랜치와 클러스터 상태를 자동으로 동기화
