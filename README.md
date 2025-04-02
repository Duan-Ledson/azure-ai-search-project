# Azure AI Search - Indexação e Consulta de Dados com Cognitive Search

## ✨ Sobre o Projeto
Este projeto demonstra como utilizar o **Azure Cognitive Search** para indexar e consultar dados de maneira eficiente utilizando recursos de **AI Search**. O objetivo é construir uma solução de busca inteligente que possa ser aplicada em diversos cenários, como e-commerce, pesquisa em documentos e buscas semânticas.

## 📝 Tecnologias Utilizadas
- **Azure Cognitive Search**
- **Microsoft Azure**
- **Python (para indexação e consultas)**
- **REST API do Azure Search**
- **Azure Blob Storage (para armazenamento de dados)**
- **SQL Server (opcional, para fontes de dados estruturadas)**

---
## ⚡ Configuração do Projeto

### 1. Criando o Serviço no Azure
1. Acesse o portal do Azure ([https://portal.azure.com](https://portal.azure.com)).
2. Pesquise por **"Azure Cognitive Search"** e clique em **Criar**.
3. Escolha um **Resource Group** ou crie um novo.
4. Defina um nome para o seu serviço de busca.
5. Escolha o plano **"Free"** para testes ou um plano pago conforme a necessidade.
6. Clique em **Revisar + Criar** e finalize a criação.

### 2. Configurando a Indexação de Dados

#### Criando um Index no Azure Search
1. No portal do Azure, acesse o serviço **Cognitive Search** criado.
2. Clique em **Index** e selecione **Criar um novo index**.
3. Defina os campos do seu index (exemplo para um e-commerce):
   ```json
   {
       "name": "products-index",
       "fields": [
           { "name": "id", "type": "Edm.String", "key": true },
           { "name": "name", "type": "Edm.String", "searchable": true },
           { "name": "description", "type": "Edm.String", "searchable": true },
           { "name": "price", "type": "Edm.Double" }
       ]
   }
   ```
4. Clique em **Criar**.

### 3. Indexando Dados via API
Para enviar dados ao Azure Search, podemos utilizar a API REST. Exemplo em Python:
```python
import requests
import json

SERVICE_NAME = "seu-servico"
API_KEY = "sua-api-key"
INDEX_NAME = "products-index"

url = f"https://{SERVICE_NAME}.search.windows.net/indexes/{INDEX_NAME}/docs/index?api-version=2020-06-30"
headers = {
    "Content-Type": "application/json",
    "api-key": API_KEY
}

dados = {
    "value": [
        {"id": "1", "name": "Smartphone X", "description": "Celular com câmera de 48MP", "price": 1999.99},
        {"id": "2", "name": "Notebook Pro", "description": "Laptop de alta performance", "price": 4999.99}
    ]
}

response = requests.post(url, headers=headers, json=dados)
print(response.json())
```

### 4. Consultando Dados Indexados
Para buscar dados indexados, utilizamos a API de **search**:
```python
query = "Smartphone"
search_url = f"https://{SERVICE_NAME}.search.windows.net/indexes/{INDEX_NAME}/docs?api-version=2020-06-30&search={query}"

response = requests.get(search_url, headers=headers)
print(response.json())
```

---
## 🔍 Possibilidades de Uso
- **E-commerce**: Busca avançada por produtos utilizando IA.
- **Bibliotecas Digitais**: Indexação de livros e documentos.
- **Chatbots e Assistentes Virtuais**: Para melhorar buscas e respostas.
- **Empresas e Arquivos Internos**: Busca de informações corporativas.

---
## 💡 Aprendizados e Insights
- O **Azure Cognitive Search** permite enriquecer os dados indexados com IA (OCR, tradução, NLP).
- Com a **busca semântica**, é possível entender melhor a intenção do usuário.
- O uso de **Python + API REST** facilita a indexação e consulta de dados de forma programática.

---
## ✅ Como Executar o Projeto
1. Clone este repositório:
   ```sh
   git clone https://github.com/seu-usuario/azure-ai-search-project.git
   cd azure-ai-search-project
   ```
2. Instale as dependências:
   ```sh
   pip install requests
   ```
3. Edite as variáveis `SERVICE_NAME` e `API_KEY` no código Python.
4. Execute os scripts para indexação e consulta:
   ```sh
   python indexar_dados.py
   python consultar_dados.py
   ```

---
## 🔗 Links e Referências
- [Documentação Oficial do Azure Cognitive Search](https://learn.microsoft.com/pt-br/azure/search/)
- [API REST do Azure Search](https://learn.microsoft.com/en-us/rest/api/searchservice/)

---
**Desenvolvido por [Seu Nome]** | 2025

