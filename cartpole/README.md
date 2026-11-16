# 🕹️ CartPole - PPO

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Lee-hosuk/game-agent/blob/main/cartpole/cartpole.ipynb)

수레를 좌우로 밀어 막대가 쓰러지지 않게 버티는 게임입니다.
[Stable-Baselines3](https://github.com/DLR-RM/stable-baselines3)의 PPO 알고리즘으로 학습했습니다.

## 학습 전 vs 학습 후

| 학습 전 | 학습 후 |
|:---:|:---:|
| ![untrained](untrained.gif) | ![trained](trained.gif) |
| **8스텝** 만에 쓰러짐 | **500스텝** 버팀 (최대 500, 만점) |

## 환경 정보
- **관찰**: 수레 위치, 수레 속도, 막대 각도, 막대 각속도 (숫자 4개)
- **행동**: 왼쪽 밀기 / 오른쪽 밀기
- **보상**: 버티는 매 스텝마다 +1
- **종료**: 막대가 약 12° 이상 기울거나 수레가 화면 밖으로 나가면 종료

## 학습 설정
- 알고리즘: PPO (`MlpPolicy`)
- 학습 스텝: 20,000
- 비교 조건: 학습 전/후 모두 `seed=0`의 같은 시작 상태에서 `deterministic=True`로 플레이
- 실행 환경: Google Colab (CPU)

## 실행 방법
위의 **Open In Colab** 버튼을 누르고 셀을 위에서부터 순서대로 실행하면 됩니다.

## 배운 점
- 학습 전 에이전트는 8스텝 만에 막대를 쓰러뜨렸지만, 20,000스텝 학습 후에는 기울어지는 쪽으로 수레를 밀어 500스텝(만점)을 버텼다.
- Colab은 셀 코드를 지워도 이미 실행된 변수가 메모리에 남아 있다. 학습 전 상태를 확인하려면 런타임을 다시 시작하거나 새 변수로 모델을 만들어야 한다.
