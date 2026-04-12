---
title: Attention Is All You Need - Paper Review
date: 2023-02-08
categories: [Paper Review]
tags: [Transformer, NLP, Ai]
---

# Attention Is All You Need - Paper Review

---

## 1. Background (왜 이 문제가 중요한가)

기존 sequence modeling에서는  
RNN, LSTM, CNN 기반 모델이 주로 사용되었다.

하지만 이러한 모델들은 다음과 같은 문제가 있다:

- sequential 구조로 인해 병렬화가 어렵다  
- 긴 dependency를 학습하기 어렵다  

특히,

- machine translation  
- language modeling  

과 같은 task에서는 성능과 효율성 모두 한계가 존재했다.

---

## 2. Problem (기존 방식의 한계)

기존 방식의 핵심 문제는 다음과 같다:

- **Sequential dependency**  
  RNN은 이전 state에 의존하기 때문에 병렬 처리가 불가능하다  

- **Long-range dependency 문제**  
  멀리 떨어진 토큰 간 관계를 학습하기 어렵다  

- **연산 효율성 문제**  
  sequence 길이가 길어질수록 학습 속도가 급격히 감소한다  

즉, 성능, 속도, 확장성 모두에서 한계가 존재한다.

---

## 3. Related Work (기존 연구 흐름)

기존 연구는 크게 세 가지 흐름으로 발전했다.

### 1) RNN 기반

- LSTM, GRU  
- sequence modeling의 표준 접근 방식  

### 2) CNN 기반

- ConvS2S, ByteNet  
- 병렬화 일부 개선  

하지만 여전히 long-distance dependency 문제는 해결되지 않았다.

### 3) Attention 기반 (보조적 역할)

- encoder-decoder 구조 + attention  

하지만 attention은 보조 역할이었고,  
모델 자체는 여전히 RNN/CNN에 의존했다.

---

## 4. Key Idea (이 논문의 핵심 아이디어)

핵심 아이디어는 다음과 같다:

> RNN과 CNN을 완전히 제거하고, attention만으로 모델을 구성한다.

즉,

- sequence 처리를 attention으로 수행  
- dependency modeling을 self-attention으로 해결  

Transformer는 최초로 attention-only architecture를 제안한 모델이다.

---

## 5. Method (방법론)

ransformer는 기존의 RNN, LSTM 기반 sequence model과 달리, recurrence 없이 attention만으로 sequence를 처리하는 구조이다.  
전체적으로는 Encoder-Decoder 구조를 유지하지만, 내부 연산은 self-attention과 feed-forward network 중심으로 구성된다.
<!-- ![test](/assets/img/content_images/transformer_architecture.png) -->

![Transformer Architecture](/assets/img/content_images/transformer_architecture.png)

### 구조 요약

- Encoder는 6개의 동일한 layer로 구성된다.
- Decoder 역시 6개의 동일한 layer로 구성된다.
- 각 Encoder layer는 다음 두 부분으로 이루어진다.
  - Multi-Head Self-Attention
  - Position-wise Feed-Forward Network
- 각 Decoder layer는 다음 세 부분으로 이루어진다.
  - Masked Multi-Head Self-Attention
  - Encoder-Decoder Attention
  - Position-wise Feed-Forward Network

### 핵심 구성 요소

#### 1. Multi-Head Self-Attention

Self-Attention은 입력 sequence 내 각 token이 다른 모든 token을 참조하도록 하여 문맥적 관계를 학습하는 방식이다.  
Transformer는 이를 여러 head로 병렬 수행하여 서로 다른 관계를 동시에 학습할 수 있도록 설계했다.

#### 2. Feed-Forward Network

Attention 이후에는 각 position에 독립적으로 적용되는 feed-forward network가 이어진다.  
이는 attention으로 통합된 표현을 비선형적으로 변환하는 역할을 한다.

#### 3. Residual Connection and Layer Normalization

각 sub-layer 뒤에는 residual connection과 layer normalization이 적용된다.  
이를 통해 deeper architecture에서도 안정적인 학습이 가능해진다.

#### 4. Positional Encoding

Transformer는 recurrence가 없기 때문에 token의 순서 정보를 별도로 주입해야 한다.  
이를 위해 positional encoding을 embedding에 더해 sequence order를 반영한다.

### 왜 중요한가

Transformer 구조의 가장 큰 의의는 다음과 같다.

- RNN 없이 sequence modeling이 가능함
- 병렬 처리가 가능하여 학습 효율이 높음
- long-range dependency를 효과적으로 학습할 수 있음

이 구조는 이후 BERT, GPT, ViT 등 거의 모든 현대적 foundation model의 기반이 되었다.

---
### 1) 전체 구조

- Encoder (6 layers)  
- Decoder (6 layers)  

각 layer는 다음으로 구성된다:

- Multi-head attention  
- Feed-forward network  

---

### 2) Self-Attention

핵심 개념:

- 모든 토큰이 서로를 참조하여 관계를 학습  

동작 방식:

- Query / Key / Value 구조  
- weighted sum을 통해 dependency 계산  

---

### 3) Multi-Head Attention

- 여러 attention을 병렬로 수행  
- 다양한 representation을 동시에 학습  

효과:

- 서로 다른 관계를 동시에 학습 가능  

---

### 4) Positional Encoding

RNN이 없기 때문에 순서 정보를 직접 추가해야 한다.

- sin / cos 기반 positional encoding 사용  

---

### 5) 핵심 장점

- 병렬 처리 가능  
- long-range dependency 처리 가능  
- 학습 속도 향상  

---

## 6. Experiment (실험 결과)

### Dataset

- WMT 2014 English-German  
- WMT 2014 English-French  

### 결과

- EN-DE: BLEU 28.4 (SOTA)  
- EN-FR: BLEU 41.8 (SOTA)  

### 핵심 성과

- 기존 모델 대비 성능 향상  
- 학습 비용 감소  
- 병렬 처리로 속도 개선  

---

## 7. Insight (해석 / 의미)

이 논문의 핵심 가치는 단순 성능 향상이 아니다.

핵심 변화:

- sequence modeling은 RNN이 필수라는 기존 가정이 깨짐  
- attention만으로 sequence modeling이 가능함을 입증  

즉, 모델 구조의 패러다임 자체를 변화시킨 논문이다.

또한,

- 구조 단순화  
- 병렬 처리 가능  

이라는 특징을 통해 이후 LLM 발전의 기반이 되었다.

---

## 8. Limitation (한계)

Transformer의 한계는 다음과 같다:

- **O(n²) complexity**  
  sequence 길이가 길어질수록 연산 비용 증가  

- **positional encoding 의존성**  
  순서 정보를 직접 학습하지 못함  

- **data dependency**  
  대량 데이터 필요  

이후 연구에서는 이를 해결하기 위해 다양한 모델이 제안되었다.

- Longformer  
- Performer  

---

## 9. Future Direction (앞으로 방향)

이 논문 이후 주요 연구 방향은 다음과 같다:

- Efficient Attention (복잡도 개선)  
- Large Language Models (GPT, BERT)  
- Multimodal Transformer  
- Retrieval-Augmented Generation (RAG)  

---

## Summary

이 논문은 attention 기반 구조를 통해  
기존 sequence modeling의 한계를 극복하고  
새로운 패러다임을 제시했다.

핵심은 다음 세 가지로 정리할 수 있다:

- RNN 없이 sequence modeling 가능  
- 병렬 처리 기반 구조  
- 이후 모든 LLM의 기반이 되는 아키텍처 제시  

---

## One-line Conclusion

논문 리뷰의 핵심은 요약이 아니라 해석이다.