# Aprimoramento de Imagens em Baixa Luminosidade

## Sobre o projeto

Este projeto tem como objetivo desenvolver e avaliar uma arquitetura de
rede neural para o aprimoramento de imagens capturadas em condições de
baixa luminosidade (*Low-Light Image Enhancement*).

O trabalho surgiu a partir dos estudos realizados no projeto de
iniciação científica PIBIC, que investigou técnicas de aprimoramento de
imagens utilizando aprendizado profundo. A partir dessa experiência, foi
desenvolvida uma arquitetura experimental própria.

## Arquitetura

O modelo utiliza uma estrutura Encoder-Decoder baseada em convoluções,
composta por:

-   **Encoder:** responsável pela extração progressiva de
    características das imagens.
-   **Bottleneck:** incorpora um módulo de autoatenção
    (*Self-Attention*) para ponderar as características extraídas.
-   **Decoder:** realiza a reconstrução da imagem utilizando convoluções
    transpostas.
-   **Skip Connections:** conectam as etapas do Encoder e Decoder,
    auxiliando na preservação de informações espaciais.

## Treinamento 

O treinamento é realizado de forma supervisionada, utilizando pares de
imagens de baixa luminosidade e suas respectivas referências bem
expostas.

## Dataset

Os experimentos utilizam o conjunto de dados **LOL-v1** e **LOL-v2 (Real Captured)**,
organizado em pares de imagens:

-   `Low`: imagens capturadas em baixa luminosidade.
-   `Normal`: imagens de referência com exposição adequada.

## Avaliação

O desempenho do modelo é avaliado por meio de métricas quantitativas:

-   **PSNR (Peak Signal-to-Noise Ratio):** avalia a fidelidade entre a
    imagem aprimorada e a referência.
-   **SSIM (Structural Similarity Index Measure):** avalia a
    similaridade estrutural entre as imagens.

Também são realizadas comparações visuais entre as imagens de entrada,
as imagens aprimoradas e suas respectivas referências.

## Tecnologias

-   Python 3.10
-   TensorFlow / Keras
-   OpenCV
-   NumPy
-   Pandas
-   Scikit-image

## Execução

O projeto é implementado em Jupyter Notebook.

Para configurar o ambiente utilizando Conda:

``` bash
conda create -n modelo_lowlight python=3.10 -y
conda activate modelo_lowlight
pip install tensorflow numpy pandas opencv-python scikit-image matplotlib jupyter ipykernel
```

O modelo treinado pode ser carregado para inferência utilizando
TensorFlow/Keras e o arquivo 'melhor_modelo.h5'