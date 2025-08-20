# Reconhecimento Facial em Câmeras de Segurança aplicado em Cidades Inteligentes e Segurança Pública (Português)

# Visão Geral do Projeto

Este repositório contém os códigos e resultados de um projeto de iniciação científica que possui como principal objetivo desenvolver, treinar e avaliar algoritmos robustos e eficientes para identificação facial em cenários realistas, utilizando bases de dados representativas e métricas padronizadas, contribuindo para a segurança pública e prevenção de crimes nas cidades inteligentes. 

Neste contexto, o repositório retrata as arquiteturas construídas para treino e avaliação tendo como base os *datasets* *SCface* (Grgic; Delac; Grgic, 2009) e QMUL-SurvFace (Cheng; Zhu; Gong, 2018). 

O sistema final, que possui as melhores métricas, utiliza uma Rede Adversarial Generativa (GAN), o *CodeFormer*, para realizar a super-resolução e restauração de faces de baixa qualidade antes de submetê-las ao modelo de reconhecimento. O modelo de reconhecimento, por sua vez, é baseado na arquitetura *InceptionResnetV1* (*FaceNet*) e foi fine-tuned com a função de perda *ArcFace* para maximizar a discriminação dos vetores de característricas (*embeddings*) faciais.

O projeto demonstra empiricamente que esta abordagem aumenta a acurácia de identificação em aproximadamente **131%** em comparação com um pipeline otimizado sem a etapa de restauração.

> [!NOTE]
> Os arquivos ".pth" de cada uma das redes neurais está disponível no [*Google Drive*](https://drive.google.com/drive/folders/1WisWVGKdmpVIb90wThpv8gj8dMPViKw9?usp=sharing)

> [!IMPORTANT]
> Por limitações do *GitHub*, alguns *widgets* tiveram de ser retirados. Porém, para visualização completa do Notebook, com o código completo e os resultados.
>
> O código-fonte completo do modelo utilizado no *SCface* está disponível no [*Google Colab*](https://colab.research.google.com/drive/1mMKZNDrlOwcIngK8Lm1e-cr-dIak2ZnF?usp=sharing).
> O código-fonte completo do modelo utilizado no *QMUL-SurvFace* está disponível no [*Google Colab*](https://colab.research.google.com/drive/15YkwYVnydM8La_1anMMMaMY6IvmCKDyZ?usp=sharing).

# Estrutura do modelo

Os modelos são compostos por um *pipeline* que realiza a detecção facial, extração de características e identificação facial. Cada uma dessas etapas através de tecnologias e métodos que estão, respectivamente, representados abaixo:

- MTCNN (Zhang et al., 2016)
  - Também é responsável pelo pré-processamento das imagens, garantindo que os rostos dos indivíduos estejam alinhados e centralizados.
    
- FaceNet (Schroff; Kalenichenko; Philbin, 2015) e ArcFace (Deng et al., 2021)
  - Responsáveis por transformarem os rostos em *embeddings* (vetores de características).
 
- Comparação de *embeddings*

> [!NOTE]
> Foi estabelecido que a etapa de identificação do rosto seria desconsiderada para a arquitetura do *QMUL-SurvFace*.

> [!IMPORTANT]
> O *CodeFormer* faz parte do *pipeline* da arquitetura voltada para o *SCface*. Sua função é melhorar a imagem de teste antes que o modelo tente reconhecê-la.

## Como Executar

1. Baixe o *dataset* [*Scface*](https://www.kaggle.com/datasets/yazkarajih/scface) ou [*QMUL-SurvFace*](https://qmul-survface.github.io) no *Google Drive*

2. Monte o Google Drive no Colab:
```python
from google.colab import drive
drive.mount('/content/drive')
```

3. Garanta que o `.zip` do *dataset* *SCface* ou do *QMUL-SurvFace* esteja salvo no *Google Drive* e que os caminhos estejam corretos

4. Execute o *pipeline*

# Autor e Agradecimentos

- **Autor**: João Emanuel Mendonça Apóstolo (joao.apostolo@dcomp.ufs.br).
- Este projeto foi desenvolvido como parte do Programa Institucional de Bolsas de Iniciação Científica (PIBIC), sendo este remunerado por uma bolsa CNPq, na Universidade Federal de Sergipe, sob orientação do Prof. Dr. Rafael Oliveira Vasconcelos (rafael@dcomp.ufs.br).


# Facial Recognition in Security Cameras Applied to Smart Cities and Public Safety (English)

# Project Overview

This repository contains the code and results of a scientific initiation project whose main objective is to develop, train, and evaluate robust and efficient algorithms for facial identification in realistic scenarios, using representative datasets and standardized metrics, contributing to public safety and crime prevention in smart cities.

In this context, the repository presents the architectures built for training and evaluation based on the SCface dataset (Grgic; Delac; Grgic, 2009) and the QMUL-SurvFace dataset (Cheng; Zhu; Gong, 2018).

The final system, which achieved the best performance metrics, uses a Generative Adversarial Network (GAN), CodeFormer, to perform super-resolution and restoration of low-quality faces before submitting them to the recognition model. The recognition model itself is based on the InceptionResnetV1 (FaceNet) architecture and was fine-tuned with the ArcFace loss function to maximize the discrimination of facial feature vectors (embeddings).

The project empirically demonstrates that this approach increases identification accuracy by approximately **131%** compared to an optimized pipeline without the restoration step.

> [!NOTE]
> The ".pth" files of each neural network are available on [*Google Drive*](https://drive.google.com/drive/folders/1WisWVGKdmpVIb90wThpv8gj8dMPViKw9?usp=sharing)

> [!IMPORTANT]
> Due to GitHub limitations, some widgets had to be removed. However, for full notebook visualization with complete code and results:
>
> The full source code is available on [Google Colab](https://colab.research.google.com/drive/1mMKZNDrlOwcIngK8Lm1e-cr-dIak2ZnF?usp=sharing).
> The full source code of the model used with QMUL-SurvFace is available on [Google Colab](https://colab.research.google.com/drive/15YkwYVnydM8La_1anMMMaMY6IvmCKDyZ?usp=sharing).

# Model Structure

The models consist of a pipeline that performs face detection, feature extraction, and face identification. Each of these steps uses technologies and methods that are, respectively, represented below:

- MTCNN (Zhang et al., 2016)
  - Also responsible for image preprocessing, ensuring that individuals’ faces are aligned and centered.
    
- FaceNet (Schroff; Kalenichenko; Philbin, 2015) and ArcFace (Deng et al., 2021)
  - Responsible for transforming faces into embeddings (feature vectors).
 
- Embedding Comparison

> [!NOTE]
> It was established that the face identification step would be disregarded for the QMUL-SurvFace architecture.

> [!IMPORTANT]
> CodeFormer is part of the pipeline for the SCface architecture. Its role is to enhance the test image before the model attempts to recognize it.

## How to Run

1. Download [Scface dataset](https://www.kaggle.com/datasets/yazkarajih/scface) or [QMUL-SurvFace dataset](https://qmul-survface.github.io) to your Google Drive

2. Mount Google Drive in Colab:
```python
from google.colab import drive
drive.mount('/content/drive')
```

3. Ensure that the `.zip` of the SCface or QMUL-SurvFace dataset is saved in Google Drive and that the paths are correct.

4. Run the *pipeline*

# Author and Acknowledgments

- **Author**: João Emanuel Mendonça Apóstolo (joao.apostolo@dcomp.ufs.br).
- This project was developed as part of the Programa Institucional de Bolsas de Iniciação Científica (PIBIC), funded by a CNPq scholarship, at the Federal University of Sergipe, under the supervision of Prof. Dr. Rafael Oliveira Vasconcelos (rafael@dcomp.ufs.br).
