# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização na Maya AI |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores e identificar reincidência de fraudes ou problemas recorrentes|
| `perfil_investidor.json` | JSON | Personalizar recomendações e alertas conforme o perfil e preferências do cliente |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil,incluindo opções de proteção antifraude e segurança |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente,detectar transações suspeitas e gerar alertas de risco |
| `dispositivo_cliente.json` | JSON | Monitorar dispositivos conectados,identificar acessos suspeitos e reforçar segurança digital |


---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Durante o desenvolvimento do agente, os dados mockados foram modificados e expandidos para atender ao caso de uso de fraudes e segurança. As principais adaptações foram:

📌transacoes.csv

- Expandido com novas colunas: localizacao, meio_pagamento, dispositivo, status, risco.

- Inclusão de transações suspeitas (ex.: compras internacionais, saques noturnos, valores elevados).

- Permite simular detecção de anomalias e geração de alertas.

📌historico_atendimento.csv

- Adicionado registros de fraudes relatadas (cartão clonado, phishing, transações internacionais não autorizadas).

- Inclui casos resolvidos e pendentes, simulando fluxo real de investigação.

📌perfil_investidor.json

- Expandido com seção preferencias_seguranca (alertas desejados, canal preferido, seguro antifraude).

- Inclusão de historico fraudes para contextualizar riscos anteriores.

- Mantém metas financeiras, mas agora vinculadas à proteção da reserva de emergência.

📌produtos_financeiros.json

- Além dos investimentos tradicionais, foram adicionados produtos de segurança:

- Seguro Antifraude

- Monitoramento de Transações

- Plano de Segurança Digital

= Permite que o agente sugira soluções de proteção quando detectar risco.

📌dispositivos_cliente.json 

- Criado para registrar dispositivos cadastrados e acessos suspeitos.

- Campos incluem: tipo, sistema_operacional, localizacao_registrada, ultimo_acesso, status.

- Permite identificar logins em dispositivos não reconhecidos ou em locais incomuns.

📌 Essas adaptações garantem que o agente:

- Responda apenas com base nos dados fornecidos.

- Tenha insumos para detectar fraudes e comportamentos suspeitos.

- Reforce as estratégias de segurança e anti-alucinação definidas.

---

## Estratégia de Integração

### Como os dados são carregados?
- Os arquivos da pasta data são carregados em Python no início da sessão do agente.

- Os CSV são lidos com a biblioteca pandas.

- Os JSON são lidos com a biblioteca nativa json.

- Após o carregamento, os dados ficam disponíveis no contexto do agente, garantindo que todas as respostas sejam baseadas exclusivamente na base de conhecimento mockada.

📂 Exemplo de código em Python
```
import json 
import pandas as pd

perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')
produtos = json.load(open('./data/produtos_financeiros.json'))
dispositivo = json.load(open('./data/dispositivo_cliente.json'))


````
⚖️ Estratégia de integração
- O agente não consulta fontes externas: todas as respostas vêm dos arquivos mockados.

- As respostas passam por validação interna para evitar alucinações.

- O agente cruza informações entre arquivos (ex.: transações + dispositivos + histórico de atendimento) para gerar alertas de fraude contextualizados.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

- Os arquivos CSV e JSON não são inseridos diretamente no system prompt.

- Em vez disso, eles são carregados em memória pelo código Python e consultados dinamicamente durante a interação.

- Quando o cliente faz uma pergunta, o agente busca nos arquivos relevantes (ex: transações, histórico, perfil, dispositivos) e utiliza esses resultados para compor a resposta.

- Isso garante que o agente não dependa de um prompt fixo e estático, mas sim de dados estruturados que podem ser atualizados ou expandidos.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente

 Nome: João Silva

 Perfil: Moderado

 Saldo disponível: R$ 5.000

Últimas Transações (transacoes.csv)

 01/11: Supermercado – R$ 450 (risco: baixo)

 03/11: Streaming – R$ 55 (risco: baixo)

 05/11: Saque em caixa eletrônico – R$ 1.200 (risco: médio)

 07/11: Compra internacional – R$ 2.000 (risco: alto)

Histórico de Atendimento (historico_atendimento.csv)

 15/10: Reclamação de cartão clonado – resolvido

 20/10: Suspeita de phishing – em investigação

Perfil do Investidor (perfil_investidor.json)

 Perfil: Moderado

 Preferências de segurança:

  Alertas em tempo real: ativo

  Canal preferido: SMS

  Seguro antifraude: contratado

Produtos Disponíveis (produtos_financeiros.json)

 Tesouro Selic (renda fixa, risco baixo)

 Fundo Multimercado (risco médio)
 
 Seguro Antifraude (proteção contra transações não autorizadas)

 Monitoramento de Transações (alertas em tempo real)

Dispositivos Cadastrados (dispositivos_cliente.json)

 Celular Android – São Paulo – ativo

 Desktop Windows – São Paulo – ativo

 iPhone – Miami – status: suspeito
...
```
