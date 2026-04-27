👋 About Me
LLM 서빙 인프라와 Korean ASR 도메인에서 일하는 엔지니어입니다.
프로덕션 환경의 콜봇/AICC 스택에서 vLLM 기반 추론 최적화와 ESPnet/NeMo 기반 음성 인식 모델 파인튜닝을 담당합니다.
추측보다 실측 벤치마크, 화려한 스펙보다 운영 안정성을 우선합니다.

🛠️ 주요 작업 영역
LLM Inference Serving

vLLM 기반 콜봇 서빙 스택 운영 및 최적화
FlashAttention 4 / FlashInfer / TensorRT-LLM 백엔드 비교 분석
FP8 양자화 (runtime quantization, KV cache, MoE) 실측 검증
Multi-LoRA hot-swap 및 dummy adapter 구조 설계
EAGLE3 speculative decoding 적용 검토
50채널급 동시 처리 가용성 벤치마크

Korean ASR

ESPnet contextual block transformer 기반 8kHz 콜센터 ASR
NVIDIA NeMo Nemotron 0.6B Korean ASR 4-stage 파인튜닝
20,000h 데이터셋 분산 학습 (B200×4 환경)
VAD 기반 EPD(End-Point Detection) head 설계
Whisper LoRA 파인튜닝 (폐쇄망 환경)
CTranslate2 기반 STT 서비스 운영

Infra & Deployment

Kubernetes / ArgoCD / Helm 기반 vLLM Gateway 배포
Jenkins CI 파이프라인 운영
온프레미스 / RunPod / Elice Cloud 멀티 클러스터 운영 경험
H100 SXM, RTX PRO 6000 Blackwell, B200 등 다양한 SM 아키텍처 검증


🧰 Tech Stack
<div align="center">
Inference & Optimization
<br/>
<img src="https://img.shields.io/badge/vLLM-1E40AF?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/FlashAttention-FF6B35?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/FlashInfer-7C3AED?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/TensorRT--LLM-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/CUDA-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
ML Frameworks
<br/>
<img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" />
<img src="https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" />
<img src="https://img.shields.io/badge/NeMo-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/ESPnet-1E40AF?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/CTranslate2-4A90E2?style=for-the-badge&logoColor=white" />
Languages
<br/>
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white" />
<img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" />
Backend & Serving
<br/>
<img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" />
<img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white" />
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
DevOps & Infra
<br/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" />
<img src="https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white" />
<img src="https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white" />
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
<img src="https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white" />
<img src="https://img.shields.io/badge/GitLab%20CI-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white" />
Hardware
<br/>
<img src="https://img.shields.io/badge/NVIDIA%20H100-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/NVIDIA%20B200-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/Blackwell%20SM120-76B900?style=for-the-badge&logo=nvidia&logoColor=white" />
</div>

📊 GitHub Stats
<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=dnwlwlq123&show_icons=true&theme=tokyonight&hide_border=true" height="165" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=dnwlwlq123&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" height="165" />
</div>

📫 Contact
작업 관련 문의나 협업 제안은 GitHub Issue 또는 Email로 부탁드립니다.
dnwlwlq123@naver.com
<!--
운영 환경 기준 실측 데이터를 우선합니다.
공식 문서/PR/실측 결과를 바탕으로 의사결정합니다.
-->
