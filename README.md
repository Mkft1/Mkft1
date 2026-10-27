# Привет, меня зовут Мария 👋

### DevOps / Platform Engineer / SRE

Строю надёжную и автоматизированную инфраструктуру. Специализируюсь на **Kubernetes, GitOps, IaC (Terraform) и Observability**. Имею сильный бэкграунд в on-premise инфраструктуре, активно расширяю экспертизу в сторону облачных решений.

---

## Мой стек

**☁️ Cloud & IaC:** VK Cloud, Terraform, Ansible  
**☸️ Оркестрация:** Kubernetes, Helm, Docker  
**🔄 CI/CD & GitOps:** GitHub Actions, Argo CD, GitLab CI  
**📊 Observability:** Prometheus (TSDB), Grafana, Loki, Promtail, VictoriaMetrics, ELK Stack (Elasticsearch, Logstash, Kibana, Metricbeat, Filebeat)  
**🔐 Security & Supply Chain:** Sealed Secrets, SOPS, Age, Vault, Gitleaks, Kube-linter, Trivy  
**🗄️ Базы данных:** PostgreSQL, Redis, MSSQL  
**🐧 Операционные системы:** Linux (Ubuntu, Astra Linux, МоsОС), Windows Server  
**🌐 Сети:** TCP/IP, HTTP/HTTPS, DNS, SSH, TLS/SSL, Nginx, REST API, Cilium  
**📨 Очереди сообщений:** Kafka, RabbitMQ  
**💻 Языки программирования:** Python, Go, Bash, C#, PowerShell  
**🔍 Языки запросов:** SQL, PromQL, KQL  
**🧠 Подходы и принципы:** IaC, DevOps, GitOps, DevSecOps, Zero Trust, RBAC

---

## Избранные проекты

## 1. [k8s-gitops-demo](https://github.com/Mkft1/k8s-gitops-demo)

**GitOps-платформа: IaC, DevSecOps и наблюдаемость в одном цикле**

Реализовала полный GitOps-цикл по принципу Single Source of Truth: любое изменение — только через коммит. Terraform поднимает Kind-кластер с CNI на eBPF (Cilium), Argo CD синхронизирует состояние по паттерну **App of Apps**, а GitHub Actions блокирует небезопасный код *до* попадания в кластер (Gitleaks, Kube-linter, Trivy). Секреты зашифрованы через Sealed Secrets и SOPS, наблюдаемость собрана на VictoriaMetrics + Loki + Grafana. Отдельно проработала **Disaster Recovery** — восстановление master key для Sealed Secrets через SOPS.

`Terraform` `Kind` `Cilium` `Argo CD` `Helm` `GitHub Actions` `Trivy` `SOPS` `VictoriaMetrics` `Loki` `Grafana`

---

## 2. [ai_agent_DevOps](https://github.com/Mkft1/ai_agent_DevOps)

**LLM-агент для RCA-диагностики Kubernetes-инцидентов (read-only, с guardrails)**

Агент принимает алерт через REST API, собирает live-сигналы из K8s API (поды, события, логи, включая pre-restart при OOMKilled) и Prometheus, а затем через **RAG по runbook'ам** (TF-IDF, без внешней векторной БД — осознанный trade-off ради zero-infra) формирует структурированный RCA с evidence и suggested fix. По умолчанию **read-only** — агент только предлагает исправления, но не мутирует кластер. Строгий JSON-выход валидируется Pydantic с одним retry и честным fallback'ом. При падении любого источника данных агент не падает, а деградирует gracefully. **258 тестов**, GitHub Actions: lint → test → Docker build → kind-based e2e. Есть chaos self-test, который создаёт ImagePullBackOff и проверяет, что агент действительно находит причину.

`Python` `FastAPI` `Kubernetes` `Prometheus` `LLM` `RAG` `Pydantic` `Docker` `GitHub Actions`

---

## 3. [ml_experimental_operator](https://github.com/Mkft1/ml_experimental_operator)

**Kubernetes Operator на Go для запуска ML-экспериментов**

Оператор на Go, который избавляет от ручной работы при запуске ML-экспериментов. Вы описываете эксперимент и его попытки (trials) как кастомные ресурсы — оператор сам создаёт джобы, следит за их выполнением и собирает метрики в Prometheus. По сути, это маленький control plane для гиперпараметров, который показывает, насколько глубоко можно кастомизировать Kubernetes. Управление гиперпараметрами через CRD (`Experiment`, `Trial`).

`Go` `Kubernetes Operator` `CRD` `ML`

---

## Контакты
[Telegram](https://t.me/Mkft1) · [LinkedIn](https://www.linkedin.com/in/ваш-профиль) · [Email](mailto:Mk.ft.1@yandex.com)
