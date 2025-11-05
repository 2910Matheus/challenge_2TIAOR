#  Justificativa do Problema e Descrição da Solução Proposta

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

##  Definição das Tecnologias Utilizadas

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

##  Esboço da Arquitetura da Solução

A arquitetura será baseada em **microsserviços serverless** na **AWS**, garantindo alta disponibilidade e escalabilidade.

1. **Camada de Canais (Front-end):** APIs de WhatsApp, Telegram e Web Widget.  
2. **API Gateway:** Ponto de entrada unificado para todas as requisições.  
3. **Serviço de Chatbot (Rasa/AWS Lambda):** Core de NLP responsável por entender intenções e gerenciar o diálogo.  
4. **Serviço de Visão Computacional (Rekognition):** Processa e valida documentos enviados pelo usuário.  
5. **Serviço de RPA:** Executa automações em sistemas internos (ex: preenchimento automático de formulários consulares).  
6. **Banco de Dados (DynamoDB):** Armazena histórico de conversas e perfis de usuários.  
7. **Serviço de Handoff:** Gerencia a transição para o atendimento humano.  

---

##  Estratégia de Coleta e Tratamento de Dados

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

##  Estrutura de Encaminhamento para Atendimento Humano (Handoff)

O handoff deve ser um processo **transparente e eficiente** para o usuário.

| Critério de Handoff | Ação da Plataforma | Preservação de Contexto |
|----------------------|--------------------|-------------------------|
| **Intenção Não Reconhecida** | Após 2 tentativas de esclarecimento, o chatbot oferece atendimento humano. | Histórico empacotado e enviado ao CRM. |
| **Solicitação Explícita** | O usuário digita “Falar com atendente” ou similar. | Histórico empacotado e enviado ao CRM. |
| **Assuntos Sensíveis/Complexos** | O modelo NLP identifica necessidade de intervenção humana. | Histórico empacotado e enviado ao CRM. |

 O encaminhamento será feito via um **Sistema de Ticketing/CRM** integrado.  
O usuário será notificado sobre o **tempo de espera** e o **canal de continuidade** (ex: “Um atendente responderá seu e-mail em até 2 horas, mantendo o contexto desta conversa”).

---

##  Plano de Desenvolvimento (Sprint 1 - Foco em Documentação)

O plano de desenvolvimento foi estruturado para garantir uma **base sólida de documentação e arquitetura**, servindo como ponto de partida para as próximas etapas de implementação e validação técnica.

| Fase | Objetivo | Entregáveis |
|------|-----------|-------------|
| **Sprint 1 (Atual)** | Definição do Escopo e Arquitetura Inicial. | Documentação completa (`README.md`), diagramas de **UML**, **Arquitetura** e **Fluxo**. |
| **Próximas Fases** | Implementação e Prova de Conceito (PoC). | Desenvolvimento gradual das funcionalidades: **PoC do Chatbot**, **Integração de Canais**, **Handoff** e **PoC de Visão Computacional/RPA**. O número e a duração das sprints serão definidos conforme o progresso do projeto. |

---

##  Divisão de Responsabilidades (Equipe Individual)

Considerando que o projeto está sendo desenvolvido por **um único membro**, todas as responsabilidades **técnicas e de gestão** estão **centralizadas**.

| Papel | Foco Principal |
|--------|----------------|
| **Desenvolvedor(a) FullStack / Arquiteto(a)** | Responsável pela concepção da arquitetura, escolha tecnológica, desenvolvimento do core de **NLP/IA**, integração de canais e automação de processos. |
| **Documentador(a) / Analista de Requisitos** | Responsável pela elaboração da **Justificativa**, **Estratégia de Dados**, **Plano de Desenvolvimento**, **Handoff** e pela estrutura e clareza do `README.md`. |

---

 **Resumo:**  
O projeto adota uma abordagem **incremental e iterativa**, priorizando inicialmente a **documentação e arquitetura** para garantir alinhamento técnico. As próximas etapas focarão na **prototipação**, **integração de canais de comunicação** e **validação das automações**, de forma adaptável ao ritmo de evolução do desenvolvimento.

