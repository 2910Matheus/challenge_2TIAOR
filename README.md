#  Justificativa do Problema e Descrição da Solução Proposta (E7)

A **YOUVISA**, atuando na otimização de processos de emissão de vistos e serviços consulares, enfrenta o desafio de escalar o atendimento ao cliente, mantendo a qualidade, personalização e segurança dos dados em um ambiente multicanal.  
A alta demanda por informações e a complexidade dos processos consulares exigem uma solução que vá além do atendimento tradicional, integrando **Inteligência Cognitiva** e **Automação Robótica de Processos (RPA)**.

A solução proposta é uma **Plataforma Inteligente de Atendimento Multicanal** baseada em **microsserviços**, com um core de **Processamento de Linguagem Natural (NLP)** e **Visão Computacional**.  
O objetivo é criar uma experiência de usuário fluida, onde o atendimento pode ser iniciado em qualquer canal (WhatsApp, Telegram, Web) e continuado em outro, garantindo a continuidade e consistência da interação.

### A plataforma será capaz de:
-  Automatizar até **80%** das interações iniciais e repetitivas.  
-  Realizar o **reconhecimento e validação de documentos** (passaportes, identidades) via Visão Computacional.  
-  **Personalizar o atendimento** com base no histórico e intenção do usuário.  
-  **Integrar-se a sistemas legados** da YOUVISA para otimização de processos internos (RPA).  

---

##  2.2. Definição das Tecnologias Utilizadas (E8)

A escolha tecnológica visa **escalabilidade, segurança e eficiência** no processamento de dados e linguagem natural.

| Categoria | Tecnologia Sugerida | Justificativa |
|------------|---------------------|----------------|
| **Infraestrutura de Nuvem** | AWS (Amazon Web Services) | Oferece serviços robustos e escaláveis (Lambda, S3, DynamoDB) e é líder em serviços de IA/ML (Amazon Comprehend, Amazon Rekognition). |
| **Processamento de Linguagem Natural (NLP)** | Rasa Open Source | Framework open source para chatbots contextuais e conversacionais, com treinamento local e controle sobre os modelos de NLU. |
| **Visão Computacional (OCR/Validação)** | Amazon Rekognition / Google Vision AI | Serviços especializados em reconhecimento de texto (OCR) e validação de documentos. |
| **Automação de Processos (RPA)** | Python com Selenium / PyAutoGUI | Criação de scripts leves integráveis aos microsserviços para automação de tarefas repetitivas. |
| **Banco de Dados** | Amazon DynamoDB (NoSQL) | Ideal para armazenar logs e perfis de usuários com alta escala e baixa latência. |
| **Canais de Comunicação** | WhatsApp Business API / Telegram Bot API | Integração direta e segura com canais amplamente utilizados, garantindo o multicanal. |

---

##  2.3. Esboço da Arquitetura da Solução (E9)

A arquitetura será baseada em **microsserviços serverless** na **AWS**, garantindo alta disponibilidade e escalabilidade.

1. **Camada de Canais (Front-end):** APIs de WhatsApp, Telegram e Web Widget.  
2. **API Gateway:** Ponto de entrada unificado para todas as requisições.  
3. **Serviço de Chatbot (Rasa/AWS Lambda):** Core de NLP responsável por entender intenções e gerenciar o diálogo.  
4. **Serviço de Visão Computacional (Rekognition):** Processa e valida documentos enviados pelo usuário.  
5. **Serviço de RPA:** Executa automações em sistemas internos (ex: preenchimento automático de formulários consulares).  
6. **Banco de Dados (DynamoDB):** Armazena histórico de conversas e perfis de usuários.  
7. **Serviço de Handoff:** Gerencia a transição para o atendimento humano.  

---

##  2.4. Estratégia de Coleta e Tratamento de Dados (E10)

A coleta de dados é fundamental para a **personalização** e **melhoria contínua** do modelo de NLP.

###  Dados Coletados:
- Histórico completo da conversa.  
- Intenção do usuário (identificada pelo NLP).  
- Métricas de satisfação (feedback).  
- Dados de documentos (com consentimento explícito).  

###  Tratamento e Segurança:
- **Anonimização:** Dados sensíveis criptografados em repouso (S3/DynamoDB) e em trânsito (HTTPS/TLS).  
- **Privacidade:** Conformidade com a **LGPD**, incluindo políticas de retenção de dados e consentimento do usuário.  
- **Análise:** Histórico de conversas usado para **treinar e refinar o modelo NLP** (aprendizado contínuo) e gerar insights preditivos sobre demanda.  

---

##  2.5. Estrutura de Encaminhamento para Atendimento Humano (Handoff) (E6)

O handoff deve ser um processo **transparente e eficiente** para o usuário.

| Critério de Handoff | Ação da Plataforma | Preservação de Contexto |
|----------------------|--------------------|-------------------------|
| **Intenção Não Reconhecida** | Após 2 tentativas de esclarecimento, o chatbot oferece atendimento humano. | Histórico empacotado e enviado ao CRM. |
| **Solicitação Explícita** | O usuário digita “Falar com atendente” ou similar. | Histórico empacotado e enviado ao CRM. |
| **Assuntos Sensíveis/Complexos** | O modelo NLP identifica necessidade de intervenção humana. | Histórico empacotado e enviado ao CRM. |

 O encaminhamento será feito via um **Sistema de Ticketing/CRM** integrado.  
O usuário será notificado sobre o **tempo de espera** e o **canal de continuidade** (ex: “Um atendente responderá seu e-mail em até 2 horas, mantendo o contexto desta conversa”).

---

##  2.6. Plano Inicial de Desenvolvimento e Divisão de Responsabilidades (E11)

### Plano de Desenvolvimento (Sprint 1 - Foco em Documentação)

| Fase | Objetivo | Entregáveis |
|------|-----------|-------------|
| **Sprint 1 (Atual)** | Definição do escopo e arquitetura inicial. | Documentação completa (README.md), Diagramas (UML, Arquitetura, Fluxo). |
| **Sprint 2** | Prova de Conceito (PoC) do Chatbot. | Chatbot funcional (apenas texto) em um canal (Web ou Telegram) com 3 intenções básicas. |
| **Sprint 3** | Integração de canais e handoff. | Integração com WhatsApp API e fluxo de atendimento humano. |
| **Sprint 4** | PoC de Visão Computacional e RPA. | Demonstração da validação de um documento simples e execução de uma tarefa RPA básica. |
