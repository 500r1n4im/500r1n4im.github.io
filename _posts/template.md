A안: 가장 안정적
제목: Pixelify Sans
본문: Pretendard
코드: JetBrains Mono

🔥 딥러닝 기반 AI의 “근본” 논문 (무조건 필수)
이건 그냥 AI 논문 리뷰 쓸 때 “기초 교양” 수준이다.

📌 핵심 논문 Attention Is All You Need BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding GPT-3: Language Models are Few-Shot Learners Scaling Laws for Neural Language Models 👉 왜 중요하냐 Transformer → 지금 모든 AI의 기반 BERT/GPT → encoder vs decoder 패러다임 Scaling Laws → “모델 크면 왜 좋아지냐”의 이론적 근거

👉 블로그 쓸 때 → “이 논문 이후 AI 패러다임이 바뀌었다” 라고 써도 될 정도

🧠 코드 이해 / 코드 AI (수린한테 핵심) 📌 핵심 논문 CodeBERT: A Pre-Trained Model for Programming and Natural Languages GraphCodeBERT: Pre-training Code Representations with Data Flow CodeT5: Identifier-aware Unified Pre-trained Encoder-Decoder Models for Code AlphaCode: Using AI for Competitive Programming 👉 핵심 포인트 코드 = 자연어가 아님 → 구조(AST, CFG, DFG) 중요 Graph 기반 접근이 왜 필요한지 설명 가능 LLM이 코드 생성까지 확장되는 흐름 이해
👉 수린 블로그에 딱 좋은 주제

“CodeBERT vs GraphCodeBERT 차이” “코드 AI는 왜 그래프를 쓰는가?” 3. 🔐 취약점 탐지 (수린 논문이랑 직결)

이미 알고 있는 것도 있지만, “리뷰용 핵심 셋”으로 정리하면:

📌 필수 논문 VulDeePecker: A Deep Learning-Based System for Vulnerability Detection SySeVR: A Framework for Using Deep Learning to Detect Software Vulnerabilities Devign: Effective Vulnerability Identification by Learning Comprehensive Program Semantics via Graph Neural Networks LineVul: A Transformer-Based Line-Level Vulnerability Prediction REVEAL: Deep Learning-Based Vulnerability Detection—Are We There Yet? 👉 리뷰 핵심 포인트 token 기반 → graph 기반 → transformer 기반 evolution line-level detection 등장 (LineVul) REVEAL = “현실적으로 아직 부족하다” critique 논문

👉 블로그에서 이렇게 쓰면 좋다 → “이 분야는 정확도가 높은 것처럼 보이지만 실제론 generalization 문제가 크다”

🚀 최신 트렌드 (요즘 논문 리뷰 필수) 📌 최근 중요한 방향 Give LLMs a Security Course: Securing Retrieval-Augmented Code Generation via Knowledge Injection CENTRIS: Precise and Scalable Detection of Library Customizations in C TIVER: Identifying Adaptive Versions of C/C++ Third-Party Open-Source Components Using a Code Clustering Technique 👉 핵심 흐름 RAG + 코드 생성 보안 라이브러리 커스터마이징 탐지 코드 클러스터링 기반 분석
👉 중요한 메시지 → “이제 단순 분류 모델 시대 끝나고 시스템-level + context-aware 분석으로 넘어감”