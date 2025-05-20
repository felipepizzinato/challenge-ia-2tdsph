# 🚀 Detecção e Identificação de Motos via Placas

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen)]()
[![Made With](https://img.shields.io/badge/Made%20with-YOLOv5-orange?logo=github)]()
[![OCR](https://img.shields.io/badge/OCR-EasyOCR-yellow)]()
[![ML](https://img.shields.io/badge/ML-KMeans-blueviolet)]()

## 📌 Descrição do Problema

Este projeto tem como objetivo identificar motos em imagens e agrupá-las corretamente, utilizando suas placas como principal critério de identificação. A solução abrange desde a detecção da moto até a extração da placa via OCR, validação do formato e agrupamento de motos semelhantes — mesmo quando a leitura da placa não for perfeita.

---

## 🧠 Solução Desenvolvida

A arquitetura do projeto é composta por três etapas principais:

### 1. 🧭 Detecção de Motos
- **Framework:** YOLOv5 (`ultralytics/yolov5`)
- **Técnica:** Detecção de Objetos (Object Detection)
- **Modelo utilizado:** `yolov5s`
- **Justificativa:** Modelo leve, rápido e com boa precisão, ideal para uso em tempo real ou em ambientes com recursos limitados.

### 2. 🧾 Leitura da Placa
- **Framework:** EasyOCR
- **Técnica:** OCR (Reconhecimento Óptico de Caracteres)
- **Justificativa:** Ótima performance em diferentes fontes, ângulos e condições de visibilidade, ideal para placas veiculares.

### 3. 🧪 Validação e Agrupamento
- **Técnica:** Clustering não supervisionado com KMeans
- **Biblioteca:** Scikit-learn
- **Features utilizadas:**
  - Tamanho da placa detectada
  - Número de letras e dígitos
  - Área do *bounding box* da moto
- **Justificativa:** Agrupamento de motos com placas semelhantes ou características compatíveis, mesmo em casos de OCR parcial ou falho.

---

## 🏗️ Arquitetura do Projeto

```
📦 projeto/
├── main.py # Pipeline principal
├── ml_model/
│ ├── kmeans_treino.py # Treinamento do modelo KMeans
│ ├── modelo_kmeans_placas.pkl # Modelo treinado
│ └── scaler.pkl # Normalizador usado no KMeans
├── data/
│ ├── imagens/ # Imagens de entrada
│ └── resultado_placas.csv # Resultados e agrupamentos
└── README.md # Documentação do projeto

```
---

## 🛠️ Tecnologias e Bibliotecas

| Categoria             | Ferramenta / Framework               |
|-----------------------|--------------------------------------|
| 📦 Detecção de Objetos | YOLOv5 (Ultralytics)                |
| 🧾 OCR                | EasyOCR                              |
| 🧪 Machine Learning   | Scikit-learn (KMeans, StandardScaler)|
| 🐍 Linguagem          | Python 3.10+                         |
| 📊 Dados              | Pandas, NumPy                        |
| 📷 Visualização       | Matplotlib                          |

---

## 📊 Resultados
- O sistema detecta motos em imagens e tenta extrair placas com OCR.

- As placas são validadas e, quando possíveis, agrupadas por similaridade.

- Mesmo placas parcialmente ilegíveis são agrupadas por semelhança (usando KMeans).

## 📎 Observações Finais
- As imagens podem conter placas ilegíveis ou moto com placas ausentes — o sistema tenta identificar padrões em outros atributos (área, formato, quantidade de letras/dígitos).

- Visualizações das motos e seus grids estão disponíveis no notebook pitch_visualizacao.ipynb.

- código foi modularizado para facilitar expansão e manutenções futuras.

## 🧠 Futuras Melhorias 

- Adicionar validação com regex mais robusta (ex: padrão Mercosul)

- Interface Web para uploads e resultados instantâneos

- Uso de embeddings ou modelos supervisionados para similaridade entre placas
