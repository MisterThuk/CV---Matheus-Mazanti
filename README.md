# Classificação de Qualidade de Carnes com Transfer Learning (Deep Learning)

Este repositório contém o código fonte de um projeto acadêmico focado na classificação automática de qualidade de carnes. O objetivo é utilizar Redes Neurais Convolucionais (CNNs) para distinguir imagens de carne em dois estados: **Fresca (Fresh)** e **Estragada (Spoiled)**.

## Sobre o Projeto

A solução foi desenvolvida utilizando a técnica de **Transfer Learning** com a arquitetura **MobileNetV2**. O projeto aborda desde o pré-processamento de dados até o ajuste fino (fine-tuning) do modelo, com foco na correção de vieses estatísticos durante a etapa de validação.

### Principais Funcionalidades:
* **Pipeline de Dados Robusto:** Implementação manual de carregamento e pré-processamento de imagens.
* **Divisão Estratificada (Stratified Split):** Solução implementada via Scikit-Learn para corrigir um problema estrutural de balanceamento entre as classes de treino e validação.
* **Treinamento em Duas Fases:**
    1.  **Warm-up:** Treinamento apenas do classificador (camadas densas).
    2.  **Fine-tuning:** Descongelamento parcial do backbone (MobileNetV2) para refino de características.

## Tecnologias Utilizadas

* **Python 3.x**
* **TensorFlow / Keras** (Deep Learning)
* **Scikit-Learn** (Métricas e Split de dados)
* **Matplotlib & Seaborn** (Visualização de dados e matriz de confusão)
* **Pathlib** (Manipulação de arquivos)

## Estrutura do Dataset

> **Nota:** O dataset de imagens não está incluído neste repositório devido ao seu tamanho. O link para download foi fornecido separadamente na entrega do projeto.

Para executar o código, o script espera que o dataset esteja organizado na seguinte estrutura de diretórios:

```text
meat_dataset/
├── Fresh/
│   ├── imagem_01.jpg
│   ├── imagem_02.jpg
│   └── ...
└── Spoiled/
    ├── imagem_01.jpg
    ├── imagem_02.jpg
    └── ...
```

## Metodologia
O código executa os seguintes passos:

Diagnóstico: Verifica a integridade dos diretórios e conta as imagens.

Split Estratificado: Garante que 20% das imagens de cada classe sejam separadas para validação, evitando viés.

Construção do Modelo: Adiciona camadas de GlobalAveragePooling, Dense (com ReLU) e Dropout ao topo da MobileNetV2.

Treinamento: Executa o treinamento monitorando a val_loss com EarlyStopping para evitar overfitting.

Avaliação: Gera a matriz de confusão e relatório de métricas.

## Resultados Obtidos
O modelo final alcançou métricas consistentes na classificação das duas classes:

Acurácia Global: 97.37%

Comportamento: A matriz de confusão demonstra que o modelo é capaz de generalizar bem, com baixas taxas de falso-positivos e falso-negativos para ambas as categorias.

## Autor
Matheus Mazanti - Desenvolvimento e Implementação
Este projeto foi desenvolvido como parte da avaliação da disciplina de Processamento de Imagens
