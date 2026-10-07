# 🌱 Agrotech — Sistema de Irrigação Inteligente

> Sistema inteligente e acessível de irrigação automatizada para pequenos agricultores, integrando hardware IoT, previsão do tempo e controle remoto via web e mobile.

## 📑 Sumário

* [Sobre o Projeto](#-sobre-o-projeto)

* [Problema vs. Solução](#-problema-vs-solução)

* [Principais Funcionalidades](#-principais-funcionalidades)

* [Arquitetura e Fluxo de Dados](#-arquitetura-e-fluxo-de-dados)

* [Requisitos do Sistema](#-requisitos-do-sistema)

* [Perfis de Usuário](#-perfis-de-usuário)

* [Critérios de Aceite (BDD/Gherkin)](#-critérios-de-aceite-bddgherkin)

* [Tecnologias Envolvidas](#-tecnologias-envolvidas)

* [Autores e Créditos](#-autores-e-créditos)

## 💡 Sobre o Projeto

O **Agrotech** elimina a tomada de decisão baseada no "achismo" e em previsões meteorológicas genéricas na agricultura familiar. Através da leitura em tempo real de umidade e temperatura do solo via sensores IoT, o sistema calcula a necessidade exata de irrigação por cultura (ex.: tomate, milho, alface), acionando ou recomendando o acionamento de aspersores e bombas de forma precisa.

### 🎯 Objetivo Geral

Otimizar o manejo de água na agricultura familiar, reduzindo desperdícios de água e energia, preservando os nutrientes do solo e maximizando a produtividade da safra.

## 🛑 Problema vs. 🟢 Solução

| Cenário Atual (Problema) | Solução com Agrotech | 
| ----- | ----- | 
| Decisão de irrigação por "achismo" ou olhômetro. | Leituras precisas de umidade do solo em tempo real via IoT. | 
| Excesso de água gera desperdício energético e lava nutrientes. | Cálculo automático da necessidade exata de lâmina d'água em mm/litros. | 
| Perda de safra por falta de irrigação em momentos críticos. | Alertas instantâneos no celular indicando solo seco. | 
| Deslocamento físico constante para ligar/desligar bombas. | Acionamento e desligamento remoto via App Mobile ou Web. | 

## ✨ Principais Funcionalidades

* **📋 Gestão de Talhões:** Cadastro das áreas da propriedade especificando a cultura cultivada (ex.: tomate, milho).

* **📊 Monitoramento IoT em Tempo Real:** Dashboard intuitivo exibindo umidade e temperatura do solo.

* **☀️ Integração Meteorológica:** Cruzamento de dados de sensores com APIs de previsão do tempo.

* **🎮 Controle Remoto de Irrigação:** Acionamento e desligamento manual ou automático de aspersores e bombas.

* **🔔 Sistema de Alertas:** Notificações push informando momento ideal de irrigação ou falhas na rede.

* **📈 Relatórios e Métricas de Consumo:** Histórico visual de volume de água utilizado e horas de irrigação por safra.





## ⚙️ Requisitos do Sistema

### Requisitos Funcionais (RF)

| Código | Descrição | 
| ----- | ----- | 
| **RF01** | Permitir o cadastro de talhões especificando a cultura. | 
| **RF02** | Registrar medições manuais e automáticas de umidade e temperatura do solo. | 
| **RF03** | Calcular a necessidade diária de irrigação (mm ou L) com base em cultura e clima. | 
| **RF04** | Emitir alertas/notificações sobre o momento ideal de acionamento/desligamento. | 
| **RF05** | Gerar relatórios de consumo de água e histórico por safra. | 
| **RF06** | Permitir controle remoto (manual/automático) de aspersores via App e Web. | 
| **RF07** | Gerenciamento de acessos (Perfis: Agricultor e Técnico de Suporte). | 
| **RF08** | Integrar-se com APIs meteorológicas para otimização do cálculo de irrigação. | 

### Requisitos Não Funcionais (RNF)

| Código | Categoria | Descrição | 
| ----- | ----- | ----- | 
| **RNF01** | **Usabilidade** | Interface simples e adaptada para produtores rurais com pouca familiaridade técnica. | 
| **RNF02** | **Desempenho** | Notificações críticas entregues em até **2 minutos** após o evento. | 
| **RNF03** | **Disponibilidade** | Backend em nuvem com SLA de no mínimo **99%** de uptime. | 
| **RNF04** | **Segurança** | Dados cadastrais e acessos armazenados com **criptografia**. | 

## 👥 Perfis de Usuário

1. **🌾 Pequeno Agricultor (Usuário Final):**

   * Cadastra talhões e culturas.

   * Acompanha o dashboard de umidade e alertas.

   * Aciona irrigadores e visualiza histórico de consumo de água.

2. **🛠 Técnico de Suporte / Instalador:**

   * Gerencia e calibra dispositivos IoT na propriedade.

   * Acessa logs de conectividade e painel de diagnóstico de hardware.

## 🧪 Critérios de Aceite (Exemplos BDD)

### US-01 — Cadastro de Talhões

* **Dado** que o agricultor possui os dados válidos do talhão (nome e tipo de cultura), **Quando** o usuário confirmar o cadastro do talhão, **Então** o sistema registra o talhão e o exibe na lista de áreas da propriedade (*Prioridade: Essencial*).

* **Dado** que existem campos obrigatórios não preenchidos, **Quando** o usuário tentar concluir o cadastro, **Então** o sistema impede a conclusão e exibe um aviso de erro (*Prioridade: Complementar*).

### US-02 — Monitoramento de Umidade do Solo

* **Dado** que os sensores de campo estão ativos e enviando dados, **Quando** o agricultor acessar o dashboard, **Então** o sistema exibe os níveis atuais de umidade e temperatura do solo em tempo real (*Prioridade: Essencial*).

* **Dado** que o sinal de conexão com os sensores estiver indisponível, **Quando** o usuário consultar o painel, **Então** o sistema informa que os dados estão desatualizados (*Prioridade: Complementar*).

### US-05 — Controle Remoto dos Aspersores

* **Dado** que o talhão e os aspersores estão conectados, **Quando** o agricultor acionar o comando de ligar/desligar no aplicativo, **Então** o sistema envia a instrução para o hardware e atualiza o status para "Ligado" ou "Desligado" (*Prioridade: Essencial*).

## 🛠 Tecnologias Envolvidas (Sugeridas)

* **Plataforma Mobile & Web:** React Native / React.js ou Flutter / Web

* **Backend:** Node.js / Python (FastAPI)

* **Hardware/IoT:** ESP32, Sensores de Umidade de Solo (Capacitivos), Módulos Relé

* **Protocolos:** MQTT / HTTP REST APIs

* **Banco de Dados:** PostgreSQL / MongoDB

## 👤 Autores e Créditos

* **Responsável do Projeto:** Evanildo de Jesus Silva

* **Cliente / Stakeholder:** Joaquim Rodrigues da Silva

* **Data da Documentação:** 27/09/2026

