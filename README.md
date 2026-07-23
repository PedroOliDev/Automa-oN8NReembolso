Sistema Inteligente de Gestão de Pedidos de Reembolso com IA
📌 Sobre o projeto

Este projeto é uma automação desenvolvida no n8n que utiliza Inteligência Artificial (Google Gemini) para analisar solicitações de reembolso, consultar informações do cliente em uma base de dados e definir automaticamente o tratamento mais adequado para cada caso.

A solução foi criada para reduzir o trabalho manual da equipe de atendimento, automatizando a análise inicial das solicitações e encaminhando apenas os casos que realmente exigem intervenção humana.

🚀 Como funciona
O cliente preenche um formulário de solicitação de reembolso.
O formulário envia os dados para um Webhook do n8n.
Um agente de IA processa as informações enviadas.
Utilizando o e-mail informado no formulário, a IA consulta uma planilha do Google Sheets para localizar o histórico do cliente.
A IA identifica:
Nome do cliente
Produto solicitado para reembolso
Comentário enviado
Valor total gasto
Data da última compra
A partir dessas informações, o agente:
Calcula quantos dias se passaram desde a última compra;
Realiza uma análise de sentimento do comentário do cliente;
Classifica o cliente conforme as regras de negócio.
O workflow decide automaticamente qual ação executar.
O cliente recebe um e-mail personalizado de acordo com o seu caso.
Quando necessário, a automação envia uma mensagem via Telegram para um responsável da empresa dar continuidade ao atendimento.
🧠 Regras de negócio
Cliente comum
Compra realizada há mais de 7 dias;
Cliente não é VIP;
Comentário não apresenta alto nível de insatisfação.

Ação:

O pedido é recusado automaticamente.
O cliente recebe um e-mail explicando que o prazo legal de reembolso expirou.
Cliente VIP

Quando o cliente possui um alto valor gasto na empresa:

Ação:

O sistema não recusa automaticamente o pedido.
A IA abre uma exceção.
O cliente recebe um e-mail informando que seu caso será analisado pela equipe financeira.
Um colaborador da empresa recebe uma notificação via Telegram para avaliar manualmente o reembolso.
Cliente muito insatisfeito

Quando a análise de sentimento identifica um comentário como muito negativo (ameaças, reclamações graves, Procon, Reclame Aqui etc.):

Ação:

O caso é escalado automaticamente para a gerência.
O cliente recebe uma resposta informando que sua solicitação será tratada com prioridade.
Um membro da equipe recebe um alerta via Telegram contendo os detalhes do caso para continuidade do atendimento.
🛠️ Tecnologias utilizadas
n8n
Google Gemini
Google Sheets
Gmail
Telegram Bot API
📊 Fluxo da automação
Formulário
      │
      ▼
Webhook (n8n)
      │
      ▼
Agente de IA (Google Gemini)
      │
      ▼
Consulta cliente no Google Sheets
      │
      ▼
Análise:
• Histórico do cliente
• Dias desde a compra
• Sentimento
      │
      ▼
Regras de negócio
      │
      ├── Cliente comum
      │      └── Envia e-mail de recusa
      │
      ├── Cliente VIP
      │      ├── Envia e-mail
      │      └── Notifica equipe via Telegram
      │
      └── Cliente muito insatisfeito
             ├── Envia e-mail
             └── Notifica gerente via Telegram
✨ Funcionalidades
Análise automática de solicitações de reembolso.
Consulta de dados do cliente utilizando apenas o e-mail informado.
Integração com Google Sheets.
Análise de sentimento utilizando IA.
Cálculo automático do prazo desde a última compra.
Classificação inteligente dos clientes.
Envio automático de e-mails personalizados.
Escalonamento automático de casos importantes.
Integração com Telegram para notificação da equipe.
🎯 Objetivo

Demonstrar como agentes de IA podem ser integrados a ferramentas de automação para criar fluxos inteligentes de atendimento, capazes de analisar informações, aplicar regras de negócio e tomar decisões de forma autônoma, reduzindo o tempo de resposta e melhorando a experiência do cliente.
