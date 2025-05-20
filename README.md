# 🚀 Detecção e Identificação de Motos via Placas

## 📌 Descrição do Problema

Este projeto tem como objetivo identificar motos em imagens e agrupá-las corretamente, utilizando suas placas como critério principal de identificação. A solução envolve a detecção da moto, extração da placa (OCR), validação do formato da placa e agrupamento de motos semelhantes, mesmo quando a leitura da placa não for perfeita.

---

## 🧠 Solução Desenvolvida

A arquitetura geral do projeto envolve três etapas principais:

### 1. 🧭 Detecção de Motos
- **Framework:** YOLOv5 (`ultralytics/yolov5`)
- **Técnica:** Detecção de objetos (object detection)
- **Justificativa:** YOLOv5 é leve, rápido e altamente preciso para detectar objetos em imagens. Aqui, foi utilizado o modelo `yolov5s` por sua performance balanceada.

### 2. 🧾 Leitura da Placa
- **Framework:** EasyOCR
- **Técnica:** OCR (Optical Character Recognition)
- **Justificativa:** EasyOCR fornece ótimos resultados em diferentes tipos de fontes e ângulos, ideal para placas veiculares que podem estar inclinadas ou parcialmente visíveis.

### 3. 🧪 Validação e Agrupamento
- **Técnica usada:** KMeans (não supervisionado)
- **Bibliotecas:** Scikit-learn
- **Features utilizadas:**
  - Tamanho da placa detectada
  - Número de letras e dígitos
  - Área do bounding box da moto
- **Justificativa:** Utilizamos clustering para **tentar agrupar motos com placas similares ou com características compatíveis**, mesmo quando a OCR falha parcialmente.

---

## 🏗️ Arquitetura do Projeto

```text
📦 projeto/
├── main.py                       # Pipeline principal
├── ml_model/
│   ├── kmeans_treino.py         # Código de treinamento do modelo KMeans
│   ├── modelo_kmeans_placas.pkl # Modelo treinado
│   └── scaler.pkl               # Normalizador usado no KMeans
├── data/
│   ├── imagens/                 # Imagens de entrada
│   └── resultado_placas.csv     # Saída com resultados e agrupamento
|
└── README.md                    # Este documento
