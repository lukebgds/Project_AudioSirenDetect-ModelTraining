# Project_AudioSirenDetect-ModelTraining

## Introdução

Este repositório contém um notebook Jupyter que descreve de forma minuciosa o processo de **criação, treinamento e avaliação** de um classificador de imagens baseado em Rede Neural Convolucional (CNN), treinado do zero para distinguir espectrogramas Mel em duas categorias: **`no_siren`** (sem sirene) e **`yes_siren`** (com sirene).

A seguir, uma visão geral das principais etapas do projeto, apresentada de forma sucinta:

## 1. Pré-processamento do Dataset

- **Bibliotecas utilizadas:**
  - TensorFlow / Keras (modelo e treino)
  - NumPy (manipulação de dados)
  - Matplotlib (visualizações)

- **Parâmetros principais:**
  - Tamanho da imagem: **128×128**
  - Batch size: **32**
  - Épocas máximas: **15**
  - Divisão dos dados: **80% treino / 20% validação**

- **Preparação dos dados:**
  - As imagens estão organizadas em subpastas que representam as classes (**`no_siren` e `yes_siren`**)
  - Uso do **`ImageDataGenerator`** para normalizar as Imagens para o Intervalo [0,1]
  - **`flow_from_directory`**: carrega imagens, redimensiona, cria lotes, divide em treino (com shuffle) e validação (sem shuffle).

## 2. Criação e Treinamento do Modelo CNN

- **Arquitetura do modelo:**
  - 4 blocos com camadas **`Conv2D`** seguidas de **`MaxPooling2D`**
  - Camada **`Flatten`**
  - Camada **Dense(128) + Dropout(0.5)**  
  - Camada final **`Dense(2)`** com **`Softmax`** (duas classes)

- **Configuração e callbacks:**
  - Otimizador: `Adam`  
  - Função de perda: `categorical_crossentropy`  
  - Métrica: `accuracy`  
  - **EarlyStopping** (paciência 6)  
  - **ReduceLROnPlateau** (fator 0.7, paciência 2)

- **Treinamento:**
  - Até 15 épocas
  - Monitoramento de desempenho em treino e validação
  - Callbacks ajustam automaticamente a taxa de aprendizado e evitam overfitting

## 3. Avaliação

- Visualização de gráficos de acurácia e perda
- Análise visual para verificar estabilidade e aprendizado adequado

## 4. Salvamento do Modelo

- Modelo final (melhores pesos) salvo em `.h5`

## Conclusão

Este projeto apresenta uma implementação prática e bem estruturada de uma **Rede Neural Convolucional (CNN) construída do zero** para a classificação de espectrogramas Mel, com foco na detecção de sirenes em ambientes urbanos. Todo o fluxo — desde o pré-processamento dos dados até o salvamento do modelo final — foi desenvolvido de forma clara e progressiva, com cada etapa explicada e documentada diretamente no notebook, facilitando o entendimento e a reprodutibilidade.

---

### Autor

**Lucas Benício Gusmão da Silva**

Idealizador e desenvolvedor do projeto.

`Todos os Direitos Reservados`
