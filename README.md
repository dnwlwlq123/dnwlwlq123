![header](https://capsule-render.vercel.app/api?type=waving&color=0:0066cc,100:00bcd4&height=200&section=header&text=Taejin%20Kim&fontSize=46&fontColor=ffffff&fontAlignY=36&desc=LLM%20Inference%20%26%20Korean%20ASR%20Engineer&descAlignY=58&descSize=16)

<div align="center">

[![Email](https://img.shields.io/badge/Email-dnwlwlq123@naver.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:dnwlwlq123@naver.com)
[![GitHub](https://img.shields.io/badge/GitHub-dnwlwlq123-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/dnwlwlq123)

</div>

<br/>

## 👋 About Me

> **LLM 서빙 인프라**와 **Korean ASR** 도메인의 엔지니어입니다.
>
> 프로덕션 콜봇/AICC 스택에서 vLLM 기반 추론 최적화와
> ESPnet/NeMo 기반 음성 인식 모델 파인튜닝을 담당합니다.
>
> 추측보다 **실측 벤치마크**, 화려한 스펙보다 **운영 안정성**을 우선합니다.

<br/>

## ⚡ LLM Inference Optimization

### Gemma4-31B-it Serving 분석

| 항목 | 내용 |
|---|---|
| **구조적 제약** | `head_dim=512` → FA3 / FlashInfer 미지원, **FA4 강제** |
| **KV cache** | FA4 + FP8 KV 미지원 (Dao-AILab PR #1914 미merge), **BF16 KV만 가능** |
| **활성화 명령** | `--attention-backend FLASH_ATTN --attention-config '{"flash_attn_version": 4}'` |
| **사전양자화 결과** | FP8-block / FP8-Dynamic / TurboQuant / V-시리즈 → **전부 ITL 회귀 확인** |

### Qwen3.5-35B-A3B MoE Serving

| 항목 | 내용 |
|---|---|
| **백엔드** | FlashInfer **CUTLASS MoE FP8** 서빙 성공 |
| **성능 (실측)** | TTFT 162ms / ITL 8.0ms |
| **호환성 이슈** | TensorRT-LLM cubin subdir 미자동생성 → Triton MoE fallback 우회 |
| **Mamba 제약** | GDN 구조 → chunked prefill OFF 불가 |
| **TTFT 비교** | Gemma4 대비 **3~5배 빠름** (KV 983K 적재 가능) |

### Qwen3.5-27B (Production)

| 항목 | 내용 |
|---|---|
| **조합** | FA3 + FP8 prefill + BF16 base + runtime FP8 |
| **Multi-LoRA** | hot-swap + dummy adapter 구조 (intent / answer endpoint 분리) |
| **Prefix caching** | TTFT 493ms → **63ms (7.8× 단축)** |
| **K8s 배포** | ArgoCD + Helm chart + Jenkins CI |

### Gateway 최적화 (G1+G2+G4 stack)

```
TTFT 68ms  /  ITL 14.9ms  /  Total 630ms
```

SGLang 전환 검토 후 **vLLM 유지 확정** (실측 기반 의사결정)

### Hardware Validation 매트릭스

| GPU | Architecture | 결과 |
|---|---|---|
| **H100 SXM 80GB** | SM90 | FA4 + FP8 정상 동작 |
| **B200 × 4** | SM100 | NeMo ASR 분산 학습 환경 |
| **RTX PRO 6000 Blackwell** | SM120 | FA4 paged KV 미지원 → Triton fallback (H100 대비 1.85× 느림) |

### EAGLE3 Speculative Decoding (진행 중)

- `RedHatAI/gemma-4-31B-it-speculator.eagle3` 2B draft head 검증
- 콜봇 ITL 개선 기대

<br/>

## 🎤 Korean ASR

### NeMo Nemotron 0.6B 4-Stage 파인튜닝

| Stage | 학습 대상 | 결과 (CER) | 속도 |
|---|---|---|---|
| **S1** | Decoder | 0.58 | 4.5 it/s |
| **S2** | Upper Encoder | 0.2491 (epoch 0 best) | 3.6 it/s |
| **S3** | Full encoder | 0.24 (정체) | 2.6 it/s |
| **S4** | Joint fine-tune | - | - |

| 환경 | 값 |
|---|---|
| **데이터** | 20,000h Korean ASR (8kHz / 16kHz) |
| **GPU** | B200 × 4 (RunPod) |
| **batch / accum** | 44 / 8 (S1-2), 6 (S3-4) — conv2d 32-bit indexing 한계 기반 |
| **Data loader** | shard manifest 1,544개 → `/tmp` 캐싱 + `shard_manifests=True` |
| **외부 검증** | ACC 86% (CER ≈ 0.14, 공백 미포함 기준) |

### ESPnet Contextual Block Transformer

- 8kHz 콜센터 도메인 (포스코DX / 한국투자증권 / KTV)
- `<noise>` 토큰 추가 시 **vocab 차원 변경 → CTC layer 재초기화** 처리
- **NVIDIA MPS** 적용으로 단일 GPU 32~36% 성능 향상 검증
- 8kHz 변환 / 한글 파일명 정규화 / 전각공백 교정 자동화 스크립트 운영

### EPD (End-Point Detection) Head

| 항목 | 값 |
|---|---|
| **파라미터** | ~2M |
| **베이스** | ESPnet contextual block transformer encoder |
| **라벨링** | Silero VAD 기반 정밀 endpoint |
| **세그먼트 검출률** | **89.6%** (threshold 0.3) |

### STT Production

- **Faster-Whisper / CTranslate2** 기반 STT 서비스 운영
- Whisper LoRA 파인튜닝 (폐쇄망 환경)
- INT8 양자화로 채널당 처리량 2× 확보

<br/>

## ☁️ Infra & Deployment

```
Production Stack:
  Jenkins (CI)
    ↓
  GitLab Helm chart (langsa/chart)
    ↓
  ArgoCD (GitOps)
    ↓
  Kubernetes (vLLM Gateway / ECP)
    ↓
  Inference (H100 / FlashInfer / FA4)
```

- **온프레미스 (KB AICC)** + **Elice Cloud (ECI IaaS)** + **RunPod** 멀티 환경
- vLLM nightly cu129 호환성 검증 (driver 570+ 필수)
- Structured Output (response_format) intent / answer / entity 정상 검증

<br/>

## 🧰 Tech Stack

| Category | Stack |
|---|---|
| **Inference** | ![vLLM](https://img.shields.io/badge/vLLM-1E40AF?style=flat-square) ![FlashAttention](https://img.shields.io/badge/FlashAttention%204-FF6B35?style=flat-square) ![FlashInfer](https://img.shields.io/badge/FlashInfer-7C3AED?style=flat-square) ![TensorRT-LLM](https://img.shields.io/badge/TensorRT--LLM-76B900?style=flat-square&logo=nvidia&logoColor=white) ![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white) |
| **ML / DL** | ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black) ![NeMo](https://img.shields.io/badge/NVIDIA%20NeMo-76B900?style=flat-square&logo=nvidia&logoColor=white) ![ESPnet](https://img.shields.io/badge/ESPnet-1E40AF?style=flat-square) ![CTranslate2](https://img.shields.io/badge/CTranslate2-4A90E2?style=flat-square) |
| **Languages** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=java&logoColor=white) ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white) |
| **Backend** | ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) |
| **DevOps** | ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white) ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white) ![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white) |
| **Hardware** | ![H100](https://img.shields.io/badge/H100%20SXM-76B900?style=flat-square&logo=nvidia&logoColor=white) ![B200](https://img.shields.io/badge/B200-76B900?style=flat-square&logo=nvidia&logoColor=white) ![Blackwell](https://img.shields.io/badge/RTX%20PRO%206000-76B900?style=flat-square&logo=nvidia&logoColor=white) |

<br/>

## 📫 Contact

작업 관련 문의 / 협업 제안은 GitHub Issue 또는 Email로 부탁드립니다.

<!--
운영 환경 기준 실측 데이터를 우선합니다.
공식 문서 / PR / 실측 결과를 바탕으로 의사결정합니다.
-->
