![header](https://capsule-render.vercel.app/api?type=waving&color=0:0066cc,100:00bcd4&height=200&section=header&text=Taejin%20Kim&fontSize=46&fontColor=ffffff&fontAlignY=36&desc=LLM%20Inference%20%26%20Korean%20ASR%20Engineer&descAlignY=58&descSize=16)

<div align="center">

[![Email](https://img.shields.io/badge/Email-dnwlwlq123@naver.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:dnwlwlq123@naver.com)
[![GitHub](https://img.shields.io/badge/GitHub-dnwlwlq123-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/dnwlwlq123)

</div>

<br/>

## 👋 About Me

> **LLM 서빙 인프라**와 **Korean ASR** 도메인의 엔지니어입니다.
>
> 콜봇/AICC 환경에서 vLLM 기반 추론 서빙 최적화와
> ESPnet/NeMo 기반 한국어 음성 인식 모델 파인튜닝을 다룹니다.
>
> 추측보다 **실측 벤치마크**, 화려한 스펙보다 **운영 안정성**을 우선합니다.

<br/>

## 🎯 What I Do

### LLM Inference Serving
프로덕션 환경에서 **수십 채널 동시 처리**를 견디는 LLM 서빙 스택을 설계하고 최적화합니다.
attention backend 선택, KV cache 양자화, MoE 라우팅, speculative decoding 같은 추론 레이어 전반을 직접 검증해 **TTFT / ITL / Throughput** 트레이드오프를 실측 기반으로 결정합니다.

### Korean ASR
콜센터 8kHz 도메인 위주로 **한국어 ASR 모델 파인튜닝**과 서빙 파이프라인을 구축합니다.
ESPnet contextual block transformer, NeMo Nemotron, Whisper 라인을 다루며, 노이즈 토큰 처리·커스텀 vocab·VAD 기반 EPD 같은 도메인 특화 이슈를 해결합니다.

### Production Deployment
Kubernetes / ArgoCD / Helm 기반 GitOps 파이프라인으로 **온프레미스부터 클라우드 GPU까지** 멀티 환경 배포를 운영합니다.

<br/>

## 🛠️ Technical Skills

### LLM Inference & Optimization
- **Serving Engine**: vLLM, SGLang, TensorRT-LLM
- **Attention Backend**: FlashAttention 2/3/4, FlashInfer, Triton, CUTLASS
- **Quantization**: FP8 (block / dynamic / runtime), INT8, INT4, AWQ
- **KV Cache**: BF16 / FP8 / paged attention, prefix caching
- **Adapter**: Multi-LoRA hot-swap, dummy adapter, runtime quantization + LoRA
- **Speculative Decoding**: EAGLE3, draft model 검증
- **Structured Output**: response_format, guided decoding

### ASR & Speech
- **Frameworks**: ESPnet, NVIDIA NeMo, HuggingFace Transformers
- **Models**: Conformer, Contextual Block Transformer, Nemotron, Whisper
- **Tooling**: Faster-Whisper, CTranslate2, Silero VAD
- **Domain Skills**: 8kHz 콜센터 데이터 처리, custom vocab/CTC 재초기화, ITN/TN, BPE vs char 모델 비교
- **Training**: 4-stage curriculum 파인튜닝, 분산 학습 (multi-GPU), shard manifest 기반 대용량 데이터 로딩

### Infra & DevOps
- **Orchestration**: Kubernetes, ArgoCD, Helm
- **CI/CD**: Jenkins, GitLab CI
- **Container**: Docker
- **Cloud / GPU**: 온프레미스, RunPod, Elice Cloud
- **GPU Architecture**: NVIDIA H100 (SM90), B200 (SM100), RTX PRO 6000 Blackwell (SM120)
- **CUDA Stack**: CUDA 12.x, driver 535/570+, NCCL, NVIDIA MPS

### Backend & General
- **Languages**: Python, Java, Bash
- **Backend**: FastAPI, Spring Boot
- **Database**: PostgreSQL, MySQL, VectorDB
- **Protocol**: WebSocket, REST API (OpenAI-compatible)

<br/>

## 🧰 Stack

| Category | Stack |
|---|---|
| **Inference** | ![vLLM](https://img.shields.io/badge/vLLM-1E40AF?style=flat-square) ![FlashAttention](https://img.shields.io/badge/FlashAttention-FF6B35?style=flat-square) ![FlashInfer](https://img.shields.io/badge/FlashInfer-7C3AED?style=flat-square) ![TensorRT-LLM](https://img.shields.io/badge/TensorRT--LLM-76B900?style=flat-square&logo=nvidia&logoColor=white) ![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white) |
| **ML / DL** | ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black) ![NeMo](https://img.shields.io/badge/NVIDIA%20NeMo-76B900?style=flat-square&logo=nvidia&logoColor=white) ![ESPnet](https://img.shields.io/badge/ESPnet-1E40AF?style=flat-square) ![CTranslate2](https://img.shields.io/badge/CTranslate2-4A90E2?style=flat-square) |
| **Languages** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=java&logoColor=white) ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white) |
| **Backend** | ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) |
| **DevOps** | ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white) ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white) ![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white) |

<br/>

## 📫 Contact

- **Email**: [dnwlwlq123@naver.com](mailto:dnwlwlq123@naver.com)
- **GitHub**: [@dnwlwlq123](https://github.com/dnwlwlq123)

작업 관련 문의나 협업 제안은 Email 또는 GitHub Issue로 부탁드립니다.

<!--
운영 환경 기준 실측 데이터를 우선합니다.
공식 문서 / PR / 실측 결과를 바탕으로 의사결정합니다.
-->
