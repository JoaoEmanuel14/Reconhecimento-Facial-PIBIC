# Reconhecimento Facial em Câmeras de Segurança aplicado em Cidades Inteligentes e Segurança Pública

# Visão Geral do Projeto

Este repositório contém o código e os resultados de um projeto de iniciação científica que possui como principal objetivo desenvolver, treinar e avaliar algoritmos robustos e eficientes para identificação facial em cenários realistas, utilizando bases de dados representativas e métricas padronizadas, contribuindo para a segurança pública e prevenção de crimes nas cidades inteligentes. 

Neste contexto, o repositório retrata a arquitetura construída para treino e avaliação tendo como base o *dataset* *SCface* (Grgic; Delac; Grgic, 2009). 

O sistema final utiliza uma Rede Adversarial Generativa (GAN), o *CodeFormer*, para realizar a super-resolução e restauração de faces de baixa qualidade antes de submetê-las ao modelo de reconhecimento. O modelo de reconhecimento, por sua vez, é baseado na arquitetura *InceptionResnetV1* (*FaceNet*) e foi fine-tuned com a função de perda *ArcFace* para maximizar a discriminação dos vetores de característricas (*embeddings*) faciais.

O projeto demonstra empiricamente que esta abordagem aumenta a acurácia de identificação em aproximadamente 131% em comparação com um pipeline otimizado sem a etapa de restauração.

> [!IMPORTANT]
> Por limitações do *GitHub*, alguns *widgets* tiveram de ser retirados. Porém, para visualização completa do Notebook, com o código completo e os resultados.
>
> O código-fonte completo está disponível no [Google Colab](https://colab.research.google.com/drive/1mMKZNDrlOwcIngK8Lm1e-cr-dIak2ZnF?usp=sharing).

# Estrutura do modelo

O modelo é composto por um *pipeline* que realiza a detecção facial, extração de características e identificação facial. Cada uma dessas etapas através de tecnologias e métodos que estão, respectivamente, representados abaixo:

- MTCNN (Zhang et al., 2016)
  - Também é responsável pelo pré-processamento das imagens, garantindo que os rostos dos indivíduos estejam alinhados e centralizados.
    
- FaceNet (Schroff; Kalenichenko; Philbin, 2015) e ArcFace (Deng et al., 2021)
  - Responsáveis por transformarem os rostos em *embeddings* (vetores de características).
 
- Comparação de *embeddings*

> [!IMPORTANT]
> O *CodeFormer* faz parte do *pipeline*. Sua função é melhorar a imagem de teste antes que o modelo tente reconhecê-la.

## Como Executar

1. Baixe o *dataset* [*Scface*](https://www.kaggle.com/datasets/yazkarajih/scface) no *Google Drive*

2. **Monte o Google Drive no Colab**:
```python
from google.colab import drive
drive.mount('/content/drive')
```

3. Garanta que o `.zip` do *dataset* *SCface* esteja salvo no *Google Drive* e que os caminhos estejam corretos

4. Execute o *pipeline*

# Autor e Agradecimentos

- **Autor**: João Emanuel Mendonça Apóstolo
- Este projeto foi desenvolvido como parte do Programa Institucional de Bolsas de Iniciação Científica (PIBIC), sendo este remunerado por uma bolsa CNPq, na Universidade Federal de Sergipe, sob orientação do Prof. Dr. Rafael Oliveira Vasconcelos.
