# azure-credit-card-insight
Utiliza o serviço Azure Document Intelligence para identificar se uma imagem é um cartão de crédito e extrair automaticamente seus principais campos

Projeto desenvolvido como entrega final do curso de Azure AI. Utiliza o serviço Azure Document Intelligence para identificar se uma imagem é um cartão de crédito e extrair automaticamente seus principais campos (número, nome, validade, etc).

# 💳 Azure Credit Card Insight

**Azure Credit Card Insight** é um projeto desenvolvido como entrega final do curso de **Azure AI Services**.  
O objetivo é demonstrar o uso do **Azure Document Intelligence (anteriormente Form Recognizer)** para **identificar automaticamente se uma imagem contém um cartão de crédito** e **extrair seus principais campos**, como número, nome do titular e data de validade.


## 🚀 Objetivo

O projeto mostra na prática como aplicar **Inteligência Artificial baseada em visão computacional e processamento de documentos** do Azure para resolver um problema real de **validação e extração de dados de imagens de cartões**.

## 🧩 Funcionalidades

- ✅ Verifica se a imagem enviada é (ou não) um cartão de crédito  
- 🔍 Extrai automaticamente os campos principais:
  - Número do cartão  
  - Nome do titular  
  - Data de validade  
  - Bandeira (Visa, MasterCard, etc) *(se disponível)*  
- 📦 Retorna os dados estruturados em formato JSON  

## 🧠 Tecnologias Utilizadas

- **Azure Document Intelligence (Document Identification Service)**
- **Python 3.10+**
- **Azure SDK for Python**
- **FastAPI** *(para a criação da API de demonstração)*

## 📂 Estrutura do Projeto

```
azure-credit-card-insight/
│
├── app/
│   ├── main.py              # API principal (FastAPI)
│   ├── azure_client.py      # Integração com Azure Document Intelligence
│   ├── utils.py             # Funções auxiliares
│   └── examples/            # Imagens de exemplo
│
├── requirements.txt         # Dependências do projeto
├── .env.example             # Exemplo de variáveis de ambiente
└── README.md

````


## ⚙️ Configuração do Ambiente

### 1️⃣ Clonar o repositório
```bash
git clone https://github.com/<seu-usuario>/azure-credit-card-insight.git
cd azure-credit-card-insight
````

### 2️⃣ Instalar dependências

```bash
pip install -r requirements.txt
```

### 3️⃣ Configurar as credenciais do Azure

Crie um arquivo `.env` na raiz do projeto com suas credenciais:

```
AZURE_DOCUMENT_ENDPOINT=<seu-endpoint>
AZURE_DOCUMENT_KEY=<sua-chave>
AZURE_MODEL_ID=prebuilt-document
```

### 4️⃣ Executar a API

```bash
uvicorn app.main:app --reload
```

Acesse em:
👉 `http://127.0.0.1:8000/docs`


## 🧪 Exemplo de Uso (via API)

**POST /analyze**

Envie uma imagem (JPEG/PNG) contendo um cartão de crédito:

```bash
curl -X POST "http://127.0.0.1:8000/analyze" \
     -F "file=@exemplo_cartao.jpg"
```

**Resposta:**

```json
{
  "is_credit_card": true,
  "fields": {
    "card_number": "1234 5678 9012 3456",
    "cardholder_name": "JOAO DA SILVA",
    "expiration_date": "12/28",
    "brand": "Visa"
  }
}
```

## 🎓 Sobre o Projeto

Este projeto foi desenvolvido como **entrega final do curso de Azure AI**, com o objetivo de aplicar conceitos de **Visão Computacional e Reconhecimento de Documentos** em um caso prático.
Ele demonstra como é possível combinar **serviços cognitivos da Microsoft** para **automatizar a identificação e extração de informações de documentos complexos**.

## 📜 Licença

Este projeto é distribuído sob a licença **MIT**.
Sinta-se à vontade para usar, modificar e contribuir!
