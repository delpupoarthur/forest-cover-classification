# Forest Cover Type Classification

Trabalho final da disciplina de Reconhecimento de Padrões (PPCOMP/IFES).

O objetivo é prever o tipo de cobertura florestal predominante (7 espécies de árvores) em áreas de 30×30 m da Roosevelt National Forest (Colorado, EUA), usando apenas variáveis cartográficas, como elevação, inclinação, distância até a água e tipo de solo.

- **Desafio Kaggle:** [Forest Cover Type Prediction](https://www.kaggle.com/c/forest-cover-type-prediction)
- **Notebook principal:** [`forest_cover_classification.ipynb`](forest_cover_classification.ipynb)

## Como reproduzir

### 1. Clonar o repositório e criar o ambiente

```bash
git clone https://github.com/delpupoarthur/forest-cover-classification.git
cd forest-cover-classification
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Baixar os dados

Os dados não são versionados neste repositório porque as regras da competição não permitem redistribuí-los.

1. Crie uma conta no Kaggle e aceite as regras da competição na aba **Data** da [página do desafio](https://www.kaggle.com/c/forest-cover-type-prediction/data).
2. Gere um token da API em **Settings → API → Create New Token** e salve o `kaggle.json` em `~/.kaggle/` (Windows: `C:\Users\<usuario>\.kaggle\`).
3. Baixe e extraia os arquivos para a pasta `data/`:

```bash
kaggle competitions download -c forest-cover-type-prediction -p data
unzip data/forest-cover-type-prediction.zip -d data
```

Ao final, a pasta `data/` deve conter `train.csv`, `test.csv` e `sampleSubmission.csv`.

### 3. Executar o notebook

```bash
jupyter notebook forest_cover_classification.ipynb
```

Execute com **Kernel → Restart & Run All**. Todas as etapas aleatórias usam `RANDOM_STATE = 42`.

## Estrutura

```
.
├── data/                                # dados do Kaggle (não versionados)
├── forest_cover_classification.ipynb    # notebook do trabalho
├── requirements.txt
└── README.md
```
