# KOSPI-TimeSeries-Forecasting with Intervention Analysis
ARIMAX 개입분석 × LSTM 예측 비교 프로젝트

## Overview
KOSPI 일간 종가 데이터를 기반으로 Box-Tiao(1975) 개입분석 방법론을 적용해 외부 충격을 통계적으로 탐지·정량화하고, 전통적 시계열 모형(ARIMAX)과 딥러닝 기반 LSTM의 예측 성능을 비교한 프로젝트다.
단순 예측 정확도 비교를 넘어, 두 모델이 상호보완적인 역할을 수행함을 보였다 — ARIMAX는 개별 충격의 크기와 지속성을 정량화하고, LSTM은 비선형 추세를 효과적으로 포착한다.

## Data
- Source: Yahoo Finance (^KS11)
- Period: 2015-01-01 ~ 2026-04-30
- Frequency: Daily
- Target Variable: KOSPI Index Closing Price
- train / test split: ~2024-12 / 2025-01~2026-04

## Methodology
### 1. Intervention Analysis
사전 이벤트 지정이 아닌 데이터 기반 역방향 탐지를 원칙으로 삼아 데이터 스누핑 편향을 방지했다.
- Pulse Intervention: 4σ 임계값
클러스터 병합(5거래일 간격)
23개 후보 → 9개 대표값 선정
  
- Step Intervention: Bai-Perron Binary Segmentation
ruptures (l2 cost)
min_size=120, n_bkps=6

확정된 개입 이벤트 (Pulse 8 + Step 5 = 13개)

### 2. ARIMAX Model
Pulse 변수를 exogenous variables로 포함

### 3. LSTM Model
- Sliding Window
- Train/Test Split 이후 Scaling
- Look-ahead Bias 방지: Scaler를 훈련 데이터에만 fit

LSTM 모델이 ARIMAX 대비 예측 성능에서 크게 우수한 결과를 보였으며, KOSPI의 비선형적 움직임을 효과적으로 포착하였다.
- ARIMAX의 역할
개별 충격의 크기와 지속성 정량화
해석 가능한 개입효과 추정
- STM의 역할
비선형 구조적 추세 포착
장기 예측 정확도 우위
