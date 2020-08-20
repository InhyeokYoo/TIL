## 김기현의 자연어처리

### 200706 TIL
- 4장 반 정도 봤음.
- 시간을 효율적으로 쓰진 못했음. 시간 양에 비해 공부한 게 없음
- 개 좆같은 책. 이걸로 공부하긴 힘들어 보임.
- 빠르게 전처리/ 한국어/ torchtext 부분만 보고 넘어가야한다.
- 이와는 별개로 setup하느라 시간을 다 썼다. 갑자기 컨테이너와 이미지가 사라져서 다시 깔았다.

### 200709 TIL
- 별로 못봄.
- sentencepiece 공부하다 말았음.

### 200714 TIL
- BPE/WPM/Unigram LM/SentencePiece 정리
- 근데 수학을 모르겠음... 하...
- 크게 중요한 것은 아니니 하나하나 이해하려 들지 말 것.

### 200716 TIL
- torchtext colab, github pages 작성 중
    - Field


## NLP 구현

### 200819 TIL
- Transformer 구현
    - Label smoothing
        - label smoothing과 KL-divergence와의 연관성?
        - backpropagation을 수식으로 전개 못하겠음
        - NLL loss 직접 계산하고 손으로 짜볼 필요가 있음
        - Cross-entropy도 직접 해볼 필요가 있음

### 200820
- Transformer 구현
    - Label smoothing
        - label smoothing은 결국 softmax + NLL-Loss에서 ground truth가 one-hot vector가 아닌 smooth된 값으로 생각할 수 있음: `[1-a, a/K, ...]`
        - 따라서 log_softmax의 결과 q(x)에 실제 분포 p(x)를 곱하는 것으로 구할 수 있음
        - 그러나 KL-divergence는 어떠한 원리에 의해서 이러한 결과를 가져오는지 잘 모르겠음
        - 구현 중 여러가지 의문이 발생함.
            1. NLL-Loss를 계산하기 위해 one-hot vector와 ground truth와의 CE를 계산하는데 gradient가 어떻게 흐르지?
            2. 다른 애들 구현은 왜 다들 size가 이상한가?: `[B, tgt_size]` -> seq_len은 어디로...?