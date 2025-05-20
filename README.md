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
└── README.md                    # Este documento```

---

## 🛠️ Tecnologias e Bibliotecas
Categoria	Ferramenta / Framework
📦 Detecção de Objetos	YOLOv5 (Ultralytics)
🧾 OCR	EasyOCR
🧪 Machine Learning	Scikit-learn (KMeans, StandardScaler)
🐍 Linguagem	Python 3.10+
📊 Manipulação de dados	Pandas, NumPy
📷 Visualização	Matplotlib

## 🧪 Como Rodar
1. Clone o repositório:
bash
Copiar
Editar
git clone https://github.com/seu-usuario/nome-do-repositorio.git
cd nome-do-repositorio
2. Instale as dependências:
bash
Copiar
Editar
pip install -r requirements.txt
3. Adicione as imagens em data/imagens/.
4. Execute o pipeline principal:
bash
Copiar
Editar
python main.py
📊 Resultados
O sistema detecta motos em imagens e tenta extrair placas com OCR.

As placas são validadas e, quando possíveis, agrupadas por similaridade.

Mesmo placas parcialmente ilegíveis são agrupadas por semelhança (usando KMeans).

📎 Observações Finais
As imagens podem conter placas ilegíveis ou moto com placas ausentes — o sistema tenta identificar padrões em outros atributos (área, formato, quantidade de letras/dígitos).

Visualizações das motos e seus grids estão disponíveis no notebook pitch_visualizacao.ipynb.

O código foi modularizado para facilitar expansão e manutenções futuras.

🧠 Futuras Melhorias
Substituir OCR por uma rede treinada exclusivamente para placas brasileiras

Adicionar validação com regex mais robusta (ex: padrão Mercosul)

Interface Web para uploads e resultados instantâneos

Uso de embeddings ou modelos supervisionados para similaridade entre placas

👨‍💻 Autor
Seu Nome Aqui


