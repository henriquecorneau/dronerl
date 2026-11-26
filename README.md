# dronerl: drone de corrida com Reinforcement Learning

Projeto didático para ensinar um drone a correr por uma pista de portões usando
Reinforcement Learning (RL) com [Stable-Baselines3](https://stable-baselines3.readthedocs.io/)
e [Gymnasium](https://gymnasium.farama.org/).

Tudo roda em **notebooks Jupyter** e funciona no **Google Colab**, sem instalar nada localmente.
A ideia é aumentar a complexidade aos poucos: cada etapa reaproveita o que foi aprendido na anterior.

## Roteiro

| Etapa | Notebook | O que você aprende | Status |
|---|---|---|---|
| 1 | [`01_corrida_2d_ponto_de_massa`](notebooks/01_corrida_2d_ponto_de_massa.ipynb) [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/henriquecorneau/dronerl/blob/main/notebooks/01_corrida_2d_ponto_de_massa.ipynb) | Conceitos de RL (MDP, política, recompensa), como criar um ambiente Gymnasium, detectar passagem por portões, treinar e avaliar PPO | ✅ |
| 2 | `02_dinamica_quadrotor_3d` | Dinâmica de corpo rígido do quadrotor (quaternions, empuxo coletivo + body rates), frames ENU/FLU e verificação numérica | 🔜 |
| 3 | `03_ambiente_corrida_3d` | Pista 3D com portões orientados, observação no frame do corpo, colisão | 🔜 |
| 4 | `04_treino_ppo_3d` | Treino em escala: `VecNormalize`, `SubprocVecEnv`, curriculum, tuning de hiperparâmetros | 🔜 |
| 5 | `05_avaliacao_e_comparacao` | PPO vs SAC, métricas de tempo de volta, visualização 3D e animações | 🔜 |
| 6 | `06_robustez` | Domain randomization (massa, arrasto, latência, ruído de sensor) e pistas aleatórias | 🔜 |

## Como rodar

### No Google Colab (recomendado para treinar)

Clique no badge "Abrir no Colab" da tabela acima. A primeira célula de cada notebook instala as dependências.
Os ambientes desta série usam MLPs pequenas, que treinam **mais rápido na CPU** que na GPU, então o runtime padrão já basta.

### Localmente, com ambiente virtual

```bash
git clone https://github.com/henriquecorneau/dronerl.git
cd dronerl
python3.12 -m venv .venv          # ou: uv venv --python 3.12 .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

> O PyTorch ainda não publica wheels para Python muito novo. Use Python 3.10 a 3.12.
> Para baixar o PyTorch só com CPU (bem menor), instale-o antes com
> `pip install torch --index-url https://download.pytorch.org/whl/cpu`.

## Estrutura

```
dronerl/
├── notebooks/          # uma etapa por notebook
├── requirements.txt
└── runs/               # (gerado) logs do TensorBoard e modelos salvos, ignorado pelo git
```

## Referências

- Song, Y. et al. *Autonomous Drone Racing with Deep Reinforcement Learning*, IROS 2021.
- Kaufmann, E. et al. *Champion-level drone racing using deep reinforcement learning*, Nature 2023.
- Schulman, J. et al. *Proximal Policy Optimization Algorithms*, 2017.
- [Spinning Up in Deep RL (OpenAI)](https://spinningup.openai.com/), uma boa introdução teórica.
