# 📅 Day 1 - Kubernetes POC 실습 기록

## 1️⃣ 샘플 앱 배포
- FastAPI (tiangolo/uvicorn-gunicorn-fastapi)
- `kubectl apply -f k8s/deployment.yaml`
- ✅ `minikube service fastapi-service` 정상 응답 확인

## 2️⃣ 오토스케일 테스트
- `metrics-server` 활성화
- `kubectl apply -f k8s/hpa.yaml`
- `ab -n 5000 -c 50 http://127.0.0.1:<port>/` 실행
- ✅ `REPLICAS` 수 증가 확인

## 3️⃣ K8s 대시보드 확인
- `minikube addons enable dashboard`
- `minikube dashboard --url` 접속
- 리소스 변화 실시간 확인 완료

## 🐛 주요 문제 해결 로그
- metrics-server 초기 미작동 → 재시작 후 해결
- CPU 사용률 `<unknown>` → deployment.yaml에 `resources.requests.cpu` 추가

## 📝 총 소요 시간
- 약 3.5시간
- 이슈 해결에 1시간 소요

## 📌 다음 액션
- Ingress Controller 구성 실습
- CI/CD 연동 (GitHub Actions → Minikube 배포 자동화)
