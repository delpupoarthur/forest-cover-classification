# Forest Cover Type Classification

Trabalho final da disciplina de Reconhecimento de Padrões (PPCOMP/IFES).

O objetivo é prever o tipo de cobertura florestal predominante (7 espécies de árvores) em áreas de 30×30 m da Roosevelt National Forest (Colorado, EUA), usando apenas variáveis cartográficas, como elevação, inclinação, distância até a água e tipo de solo.

- **Desafio Kaggle:** [Forest Cover Type Prediction](https://www.kaggle.com/c/forest-cover-type-prediction)
- **Notebook principal:** [`forest_cover_classification.ipynb`](forest_cover_classification.ipynb)

## Resultados

| Avaliação | Resultado |
|---|---|
| Modelo final | Extra Trees com features de distância e elevação criadas no trabalho |
| Validação cruzada (5 folds, 80% do treino) | 89,5% de acurácia |
| Teste guardado (20% do treino, usado uma única vez) | 89,9% de acurácia, F1 macro 0,897, AUC-ROC 0,990 |
| Kaggle (late submission) | 0,80579 (público e privado) |

A diferença entre o teste guardado e a nota do Kaggle vem da distribuição das classes: o treino é balanceado, e o teste do Kaggle segue a distribuição real da floresta. A seção 7.6 do notebook explica e estima essa diferença.

## Como reproduzir

### 1. Clonar o repositório e criar o ambiente

Pré-requisito: **Python 3.11 ou superior** (a CLI do Kaggle exige essa versão). O notebook foi executado com Python 3.12.9.

```bash
git clone https://github.com/delpupoarthur/forest-cover-classification.git
cd forest-cover-classification
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

O `requirements.txt` fixa as versões exatas usadas, para que os resultados sejam idênticos.

### 2. Baixar os dados

Os dados não são versionados neste repositório porque as regras da competição não permitem redistribuí-los.

1. Crie uma conta no Kaggle e aceite as regras da competição na aba **Data** da [página do desafio](https://www.kaggle.com/c/forest-cover-type-prediction/data).
2. Em **Settings → API**, gere um token de API e salve o valor no arquivo `~/.kaggle/access_token` (Windows: `C:\Users\<usuario>\.kaggle\access_token`).
3. Baixe e extraia os arquivos para a pasta `data/`:

```bash
kaggle competitions download -c forest-cover-type-prediction -p data
unzip data/forest-cover-type-prediction.zip -d data
```

Ao final, a pasta `data/` deve conter `train.csv`, `test.csv` e `sampleSubmission.csv`.

### 3. Executar o notebook

Abra o notebook no Jupyter ou no VSCode, selecione o kernel do ambiente `.venv` e execute **Kernel → Restart & Run All**:

```bash
jupyter notebook forest_cover_classification.ipynb
```

A execução completa leva cerca de 4 a 5 minutos. Todas as etapas aleatórias usam `RANDOM_STATE = 42`, então os resultados são sempre os mesmos.

### 4. (Opcional) Enviar a submissão ao Kaggle

O notebook gera o arquivo `submission.csv` na raiz do projeto. Para enviá-lo:

```bash
kaggle competitions submit -c forest-cover-type-prediction -f submission.csv -m "mensagem"
```

## Estrutura

```
.
├── data/                                # dados do Kaggle (não versionados)
├── forest_cover_classification.ipynb    # notebook do trabalho
├── requirements.txt                     # dependências com versões fixas
├── README.md
└── submission.csv                       # gerado pelo notebook (não versionado)
```
