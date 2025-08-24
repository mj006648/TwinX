# TwinX
---

## 👋 Welcome!

이 저장소는 GIST AI 대학원의 Digital Twin 통합 관제를 목표로 하는 **TwinX** 프로젝트의 모든 것을 담고 있습니다.
Kubernetes 기반의 고가용성(HA) 및 이기종(heterogeneous) 클러스터 환경에서 오픈소스 도구를 활용한 실습, 운영, 트러블슈팅 경험을 기록하고 공유하기 위해 만들어졌습니다.

---

## 📚 Repository Structure

- `/argocd/`: ArgoCD를 활용한 GitOps 기반의 선언적 배포 및 애플리케이션 관리 실습을 다룹니다.
- `/kubespray/`: Kubespray(Ansible 기반)를 활용하여 Kubernetes 클러스터를 자동화하고 일관성 있게 배포하는 과정을 기록합니다.

---

## 🚀 Cluster Info

**TwinX**는 다양한 GPU 노드로 구성된 고성능 이기종 클러스터입니다. Control Plane은 세 개의 노드로 구성하여 고가용성을 확보하였으며, Digital Twin 애플리케이션의 안정적인 운영을 목표로 합니다.

<details>
<summary><b>TwinX Cluster Node-Details</b></summary>

<table>
  <thead>
    <tr>
      <th>Node name (hostname)</th>
      <th>역할(Role)</th>
      <th>MGMT IP</th>
      <th>K8S IP</th>
      <th>K8S Version</th>
      <th>OS-Image</th>
      <th>Container Runtime</th>
      <th>제품 (Product)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>control1</td>
      <td>control-plane</td>
      <td>10.38.38.8</td>
      <td>10.38.38.9</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon D-1518 (4-Core, 4-Thread)<br/>- RAM: 32GB</td>
    </tr>
    <tr>
      <td>control2</td>
      <td>control-plane</td>
      <td>10.38.38.16</td>
      <td>10.38.38.17</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon D-1518 (6-Core, 6-Thread)<br/>- RAM: 32GB</td>
    </tr>
    <tr>
      <td>control3</td>
      <td>control-plane</td>
      <td>10.38.38.24</td>
      <td>10.38.38.25</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon D-1518 (4-Core, 8-Thread)<br/>- RAM: 32GB</td>
    </tr>
    <tr>
      <td>sv4000-1</td>
      <td>worker</td>
      <td>10.38.38.32</td>
      <td>10.38.38.33</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: AMD EPYC 9124 (16-Core, 32-Thread)<br/>- RAM: 256GB<br/>- GPU: NVIDIA RTX A6000 48GB x 2</td>
    </tr>
    <tr>
      <td>sv4000-2</td>
      <td>worker</td>
      <td>10.38.38.40</td>
      <td>10.38.38.41</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: AMD EPYC 9124 (16-Core, 32-Thread)<br/>- RAM: 256GB<br/>- GPU: NVIDIA RTX A6000 48GB, NVIDIA L40 48GB</td>
    </tr>
    <tr>
      <td>rm352-1</td>
      <td>worker</td>
      <td>10.38.38.104</td>
      <td>10.38.38.105</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 128GB<br/>- GPU: Quadro RTX 6000 24GB, A100 40GB, A10 24GB</td>
    </tr>
    <tr>
      <td>rm352-2</td>
      <td>worker</td>
      <td>10.38.38.48</td>
      <td>10.38.38.49</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 64GB<br/>- GPU: Quadro RTX 6000 24GB, A100 40GB, A10 24GB</td>
    </tr>
    <tr>
      <td>l40s</td>
      <td>worker</td>
      <td>10.38.38.96</td>
      <td>10.38.38.97</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: AMD EPYC 9254 (48-Core, 96-Thread)<br/>- RAM: 755GB<br/>- GPU: NVIDIA L40S 48GB x 6</td>
    </tr>
    <tr>
      <td>armserver</td>
      <td>worker</td>
      <td>10.38.38.88</td>
      <td>-</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: ARM Neoverse-N1 (80-Core, 80-Thread)<br/>- RAM: 512GB</td>
    </tr>
    <tr>
      <td>edgebox1</td>
      <td>worker</td>
      <td>10.38.38.56</td>
      <td>10.38.38.57</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 128GB<br/>- GPU: Tesla T4 16GB</td>
    </tr>
    <tr>
      <td>edgebox2</td>
      <td>worker</td>
      <td>10.38.38.64</td>
      <td>10.38.38.65</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 32GB<br/>- GPU: Tesla T4 16GB</td>
    </tr>
     <tr>
      <td>edgebox3</td>
      <td>worker</td>
      <td>10.38.38.72</td>
      <td>10.38.38.73</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 128GB<br/>- GPU: Tesla T4 16GB</td>
    </tr>
     <tr>
      <td>edgebox4</td>
      <td>worker</td>
      <td>10.38.38.80</td>
      <td>10.38.38.81</td>
      <td>v1.33.3</td>
      <td>Ubuntu 24.04 LTS</td>
      <td>containerd://1.7.1</td>
      <td>- CPU: Intel Xeon Silver 4310 (12-Core, 24-Thread)<br/>- RAM: 128GB<br/>- GPU: Tesla T4 16GB</td>
    </tr>
  </tbody>
</table>

</details>

---

## [📖 활용법 및 참고]

- 각 폴더의 `README.md` 또는 `실습.md` 파일에서 상세한 실습, 설정, 트러블슈팅 과정을 확인할 수 있습니다.
- 모든 기록은 실습 환경, 사용 버전, 겪었던 시행착오, 그리고 개선점을 포함하고 있습니다.
- 본 저장소는 Digital Twin 프로젝트의 실전 운영, 포트폴리오, 그리고 팀 내 기술 공유 자료로 적극 활용될 수 있습니다.

---

## [🙌 Contributing & Contact]

- 실습 경험 공유, 트러블슈팅 해결 사례, 개선 제안, 질문 등 어떤 형태의 기여도 환영합니다!
- `Issue`, `Pull Request`, `Discussions`를 통해 자유롭게 참여하고 의견을 남겨주세요.
