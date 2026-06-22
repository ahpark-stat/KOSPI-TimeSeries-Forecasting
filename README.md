# KOSPI-TimeSeries-Forecasting with Intervention Analysis

## Overview
KOSPI 지수의 단기 추세 예측을 위해 전통적인 시계열 모형(ARIMAX)과 딥러닝 기반 LSTM 모델을 비교 분석한 프로젝트입니다.
본 프로젝트는 COVID-19, 금융시장 충격 등 외부 이벤트의 영향을 반영하기 위해 Pulse Intervention과 Step Intervention을 도입하였으며, 개입효과를 반영한 ARIMAX 모델과 LSTM 모델의 예측 성능을 비교하였습니다.

## Data
- Source: Yahoo Finance (^KS11)
- Period: 2015-01-01 ~ 2026-04-30
- Frequency: Daily
- Target Variable: KOSPI Index Closing Price

## Methodology
### 1. Intervention Analysis
외부 충격 효과를 반영하기 위해
- Pulse Intervention
- Step Intervention
으로 개입분석을 실시
### 2. ARIMAX Model
Pulse 변수를 exogenous variables로 포함
### 3. LSTM Model
- Sliding Window
- Train/Test Split 이후 Scaling
- Look-ahead Bias 방지

LSTM 모델이 ARIMAX 대비 예측 성능에서 크게 우수한 결과를 보였으며, KOSPI의 비선형적 움직임을 효과적으로 포착하였습니다.
