# **🔍 Recomendação de Produtos por Similaridade de Imagem**

Este projeto implementa um **sistema de recomendação de produtos** baseado na **similaridade de imagens**. Utilizamos **redes neurais convolucionais (CNNs)** para extrair características visuais dos produtos e um i**ndexador vetorial (Annoy) ** para buscar os itens mais semelhantes.

## **🛠️ Tecnologias Utilizadas**
* Python 3
* TensorFlow/Keras
* MobileNetV2 (Transfer Learning)
* Annoy (Approximate Nearest Neighbors)
* Streamlit (Interface Web)
* Flask (API REST)
* Google Colab
* Kaggle Dataset
* Pyngrok/Cloudflare Tunnel (Deploy Temporário)
  
## **📁 Estrutura do Repositório**
```graphql
📦 MeuProjeto
 ┣ 📂 notebooks           # Jupyter Notebook com o código principal
 ┃ ┣ 📜 recomendacao.ipynb  # Notebook completo do projeto
 ┣ 📂 datasets            # Dataset de produtos (imagens, metadados, etc.)
 ┣ 📂 models              # Modelo treinado salvo (.keras)
 ┣ 📂 api                 # Código das APIs em Flask e Streamlit
 ┃ ┣ 📜 app.py           # Interface visual com Streamlit
 ┃ ┣ 📜 flask_app.py     # API REST para recomendação via POST
 ┃ ┣ 📜 utils.py         # Utilitários para carregar modelo e indexador
 ┣ 📜 requirements.txt   # Dependências do projeto
 ┣ 📜 README.md          # Documentação do projeto
 ┗ 📜 .gitignore         # Arquivos a serem ignorados no Git
```

## **📌 Passos do Projeto**

## 1️⃣ Coleta de Dados
O dataset foi obtido do Kaggle Fashion Product Images e contém milhares de imagens de produtos categorizados.

## 2️⃣ Treinamento do Modelo
* Utilizamos MobileNetV2 para extração de características.
* Treinamos o modelo com imagens do Kaggle, categorizando produtos por sua aparência.
* O modelo foi salvo no formato .keras para uso posterior.

## 3️⃣ Indexação das Imagens
* Extraímos os vetores de características de cada imagem.
* Utilizamos o Annoy para construir um indexador eficiente para busca de similaridade.

## 4️⃣ Implementação das APIs
✅ Streamlit → Interface Web para upload de imagens e recomendação de produtos.

✅ Flask API → API REST para enviar imagens e receber recomendações via código.

## **🚀 Como Executar o Projeto**

### 📌 1️⃣ Clonar o repositório
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```
### 📌 2️⃣ Criar um ambiente virtual (opcional, mas recomendado)
```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate      # Windows
```
### 📌 3️⃣ Instalar dependências
```bash
pip install -r requirements.txt
```
### 📌 4️⃣ Executar a Interface Web (Streamlit)
```bash
streamlit run api/app.py
```
Acesse a aplicação em: **http://localhost:8501**

### 📌 5️⃣ Executar a API REST (Flask)
```bash
python api/flask_app.py
```
A API estará disponível em: **http://localhost:5000/fashion**

Para testar via **Postman** ou código Python, envie uma imagem via **POST**.

## 🖼️ Exemplo de Uso
### 🔹 Interface Web (Streamlit)
1️⃣ O usuário faz upload de uma imagem.
2️⃣ O modelo processa e retorna os produtos mais semelhantes.

📸 Imagem Enviada

🔍 Recomendações

**🔹 Testando a API REST com Python**
```python
import requests
import base64
from PIL import Image
from io import BytesIO

url = "http://localhost:5000/fashion"
files = {"image": open("test_image.jpg", "rb")}

response = requests.post(url, files=files)

if response.status_code == 200:
    result = response.json()
    for i, img_base64 in result.items():
        img_data = base64.b64decode(img_base64)
        img = Image.open(BytesIO(img_data))
        img.show()
```
## 📌 Melhorias Futuras
* Implementar AWS Elastic Beanstalk para deploy da API REST.
* Testar outros modelos como ResNet e EfficientNet.
* Melhorar a eficiência do indexador para grandes volumes de dados.

## 📜 Licença
Este projeto é de código aberto e segue a licença MIT. Sinta-se à vontade para modificar e contribuir!

### 📢 Dúvidas ou sugestões?
Entre em contato ou abra uma issue no repositório! 🚀

🔗 Repositório no GitHub

📩 Contato: rafaeldnbr@hotmail.com

