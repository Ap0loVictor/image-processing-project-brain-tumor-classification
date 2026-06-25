# Classificação de Tumores Cerebrais em Imagens de Ressonância Magnética utilizando CNNs

## Descrição do Problema

O diagnóstico precoce de tumores cerebrais é fundamental para aumentar as chances de tratamento e sobrevivência dos pacientes. Entretanto, a análise manual de imagens de ressonância magnética (MRI) pode ser demorada e sujeita a erros humanos.

Este projeto investiga o impacto de diferentes técnicas de pré-processamento de imagens no desempenho de Redes Neurais Convolucionais (CNNs) para classificação de tumores cerebrais. O objetivo é comparar abordagens de realce e remoção de ruído em imagens MRI antes de sua utilização por um modelo de aprendizado profundo.

Foram utilizadas imagens do dataset **Brain Tumor MRI Dataset**, contendo quatro classes:

- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

O trabalho compara dois pipelines de pré-processamento e avalia sua capacidade de melhorar a qualidade visual das imagens e potencialmente auxiliar a classificação automática de tumores cerebrais.

# Técnicas Utilizadas

## 1. Pré-processamento das Imagens

Inicialmente, as imagens são ajustadas para uma proporção 1:1, removendo artefatos e padronizando as entradas para a rede neural.

### Experimento 1 – NLM + Equalização Global

Pipeline baseado em Mussalam et al. (2022):

1. Corte central da imagem.
2. Aplicação do filtro **Non-Local Means (NLM)** para redução de ruído.
3. Equalização global do histograma para aumento do contraste.

### Experimento 2 – Gauss + CLAHE

Pipeline baseado em Rasheed et al. (2023):

1. Aplicação de filtro Gaussiano.
2. Combinação da imagem original com a imagem borrada.
3. Aplicação do método **CLAHE (Contrast Limited Adaptive Histogram Equalization)** para realce local de contraste.

## 2. Modelo de Classificação

Foi utilizada uma **Rede Neural Convolucional (CNN)** para classificação das imagens nas quatro categorias do dataset. A mesma arquitetura foi utilizada para avaliar os diferentes métodos de pré-processamento.

## 3. Métricas de Avaliação

Para avaliar a qualidade das imagens processadas foram utilizadas:

- **MSE (Mean Squared Error)**
- **PSNR (Peak Signal-to-Noise Ratio)**
- **BRISQUE (Blind/Referenceless Image Spatial Quality Evaluator)**

Essas métricas permitem analisar a preservação da informação visual e a naturalidade das imagens após o pré-processamento.

## Tecnologias Utilizadas

- Python 3
- TensorFlow / Keras
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Scikit-Learn

## Instruções de Execução

### 3.1. Clonar o Repositório

```bash
git clone <https://github.com/Ap0loVictor/image-processing-project-brain-tumor-classification.git>
cd image-processing-project-brain-tumor-classification
```

### 3.2. Criar Ambiente Virtual (Opcional)

Crie um ambiente virtual para isolar as dependências do projeto:

```bash
python -m venv venv
```

#### Ativar o ambiente virtual

**Linux/MacOS**

```bash
source venv/bin/activate
```

**Windows**

```bash
venv\Scripts\activate
```

### 3.3. Instalar Dependências

Instale as bibliotecas necessárias para executar os notebooks:

```bash
pip install tensorflow opencv-python numpy pandas matplotlib scikit-learn kagglehub tqdm seaborn
```

---

## 4. Baixar o Dataset

O projeto utiliza o dataset **Brain Tumor MRI Dataset**, disponível em:

https://www.kaggle.com/datasets/tombackert/brain-tumor-mri-data

Os notebooks utilizam a biblioteca `kagglehub` para realizar o download automático do conjunto de dados.

## 5. Executar os Experimentos

Após instalar as dependências, execute os notebooks na seguinte ordem:

### Modelo Base

```text
modelo_base_cnn.ipynb
```

### Experimento 1 – NLM + Equalização Global

```text
experiment-1/NLM.ipynb
```

### Experimento 2 – Gauss + CLAHE

```text
Experimento2_PI (1).ipynb
```

Os notebooks podem ser executados através do Jupyter Notebook ou do Visual Studio Code.

---

## 6. Resultados

Os resultados gerados são armazenados nas seguintes pastas:

```text
resultados_modelo_base/
resultados_modelo_exp1/
resultados_modelo_exp2/
```

Nelas é possível encontrar:

- Relatórios de classificação;
- Matrizes de confusão;
- Curvas de treinamento;
- Modelos treinados (`.keras`).
