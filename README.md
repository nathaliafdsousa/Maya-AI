# 🤖 DIO LAB - BIA DO FUTURO

Projeto desenvolvido como parte do laboratório da DIO para construção de uma assistente virtual inteligente voltada ao setor financeiro, utilizando dados simulados de clientes, produtos e transações.

## 📘 Descrição

**Maya AI** é uma agente financeira especializada em **antifraude** e **segurança digital**, capaz de analisar perfis de investidores, sugerir produtos financeiros e interpretar dados de atendimento e transações. A aplicação é construída com Python e Streamlit, utilizando arquivos JSON e CSV como base de conhecimento.

🔗 [Template da documentação do agente](https://github.com/nathaliafdsousa/dio-lab-bia-do-futuro/blob/main/docs/01-documentacao-agente.md)

## 📁 Estrutura do Projeto

```bash
DIO-LAB-BIA-DO-FUTURO/
├── assets/                  
├── data/                   
│   ├── dispositivo_cliente.json
│   ├── historico_atendimento.csv
│   ├── perfil_investidor.json
│   ├── produtos_financeiros.json
│   └── transacoes.csv
├── docs/                   
│   ├── 01-documentacao-agente.md
│   ├── 02-base-conhecimento.md
│   ├── 03-prompts.md
│   ├── 04-metricas.md
│   
├── examples/               
├── src/                    
│   ├── app.py
│   └── requirements.txt
└── README.md               
🚀 Tecnologias Utilizadas
Python 3.9+

Streamlit para interface web

Pandas para manipulação de dados

Ollama para execução local de modelos de linguagem

JSON/CSV como fontes de dados simulados

⚙️ Como Executar
Clone o repositório:

  git clone https://github.com/nathaliafdsousa/dio-lab-bia-do-futuro.git
  cd dio-lab-bia-do-futuro/src

Instale as dependências do Python:
  pip install -r requirements.txt

Instale o Ollama (necessário para rodar localmente):
  Download Ollama

Após instalar, verifique se está funcionando:
  ollama --version

Execute a aplicação:
  streamlit run .\src\app.py
````


👩‍💻 Autoria
Projeto desenvolvido por Nathalia F. D. Sousa com base no laboratório da Digital Innovation One.
