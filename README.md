# Projeto de Transfer Learning: Classificação de Gatos vs Cachorros

Este repositório contém um projeto de **Transfer Learning** utilizando **Python** e **TensorFlow**, com foco na classificação de imagens de **gatos** e **cachorros**. O modelo base utilizado é o **MobileNetV2**, pré-treinado no dataset **ImageNet**, e adaptado para classificação binária (2 classes).

---

## 1. Descrição do Projeto

O objetivo do projeto é demonstrar como:
1. **Descompactar** e **organizar** o dataset `kagglecatsanddogs_5340.zip` no Google Colab.
2. **Preparar** os geradores de dados de treino e validação usando `ImageDataGenerator`.
3. **Construir** e **treinar** um modelo de Transfer Learning, realizando ajustes (fine tuning) em camadas específicas para melhorar a performance.
4. **Avaliar** e **salvar** o modelo resultante.

O notebook completo (`.ipynb`) encontra-se neste repositório, contendo todos os passos de **importação**, **divisão de dados**, **treinamento** e **avaliação**.

---

## 2. Dataset

- **Nome**: [Cats vs Dogs (kagglecatsanddogs_5340.zip)](https://www.microsoft.com/en-us/download/details.aspx?id=54765)  
- **Conteúdo**: Imagens de gatos e cachorros (aproximadamente 25.000 imagens ao total).  
- **Estrutura após extração**:
  - `PetImages/`
    - `Cat/`
    - `Dog/`

Após a descompactação, as imagens são divididas em 80% para **treino** e 20% para **validação**, gerando pastas no formato:

```
cats_vs_dogs_data/
|__ train
|   |__ Cat
|   |__ Dog
|__ validation
    |__ Cat
    |__ Dog
```

---

## 3. Principais Tecnologias

- **Python 3.7+** (ou superior)
- **TensorFlow 2.x** (Keras integrado)
- **NumPy**, **Matplotlib**, **zipfile**, **shutil**, **random**, etc.

---

## 4. Estrutura do Notebook

1. **Bibliotecas e Configurações**  
   Importa as bibliotecas necessárias (TensorFlow, Keras, etc.) e exibe as versões para conferência.

2. **Upload e Descompactação do Dataset**  
   O arquivo `kagglecatsanddogs_5340.zip` é carregado para o Colab e extraído localmente.

3. **Organização das Pastas**  
   Criação das pastas para treino e validação, além da verificação de imagens corrompidas para garantir integridade.

4. **Geradores de Imagens**  
   Uso de `ImageDataGenerator` para normalização e **data augmentation** (zoom, flip, rotate, shift etc.).

5. **Construção do Modelo**  
   - Carregamento do modelo base **MobileNetV2** (pré-treinado no ImageNet).
   - Congelamento das camadas (transfer learning).
   - Adição de camadas densas para classificação binária (`Dense(1, activation='sigmoid')`).

6. **Treinamento Inicial**  
   - Configuração de hiperparâmetros (batch size, epochs).
   - Uso de `model.fit()` para executar o treinamento.

7. **Fine Tuning (opcional)**  
   - Descongelamento de camadas intermediárias/finais do modelo base para refinar o aprendizado.
   - Novo treinamento com taxa de aprendizado reduzida.

8. **Avaliação e Salvamento do Modelo**  
   - Avaliação do conjunto de validação.
   - Armazenamento do modelo em um arquivo H5 (`.h5`).

---

## 5. Como Executar o Projeto

1. **Clone ou baixe** este repositório.
2. **Abra o Google Colab** e faça upload do notebook `.ipynb` (ou abra diretamente pelo GitHub, selecionando “Open in Colab”).
3. **Carregue** o dataset `kagglecatsanddogs_5340.zip` no Colab (upload direto ou via Google Drive).
4. **Execute** as células do notebook na ordem apresentada:
   - Instalação / importação de dependências
   - Descompactação do arquivo `.zip`
   - Organização do dataset em pastas
   - Criação dos geradores de imagens
   - Construção, treinamento e avaliação do modelo
5. **Acompanhe** as métricas (acurácia, loss) e, se necessário, faça ajustes nos hiperparâmetros.
6. **Salve** o modelo final (`.h5`) para uso posterior.

---

## 6. Resultados

No final do treinamento, o notebook exibirá:
- **Acurácia de Validação** do modelo base.
- **Acurácia após Fine Tuning** (se realizada).
- **Curvas** de Acurácia e Perda durante as épocas.

Os resultados podem variar conforme:
- Tamanho do dataset usado (caso parte das imagens sejam removidas).
- Estratégias de data augmentation.
- Número de épocas e taxa de aprendizado.

---

## 7. Contribuição

Fique à vontade para **abrir Issues** ou **enviar Pull Requests** caso queira contribuir com melhorias no código, ajuste de hiperparâmetros, inclusão de métricas adicionais, ou suporte a mais classes de imagens.

---

## 8. Licença

Este projeto está sob a licença [MIT](LICENSE). Você pode usá-lo livremente para estudos e aplicações pessoais, sem qualquer garantia.

---

**Divirta-se aprendendo e desenvolvendo seu modelo de Transfer Learning!**
