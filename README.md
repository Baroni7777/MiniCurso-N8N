# Minicurso n8n: do primeiro workflow à automação com IA

Material do minicurso da **Semana Nacional de Informática** (29/10/2026).
Aqui está tudo o que você precisa para acompanhar a aula e refazer os exemplos em casa.

## 📂 O que tem aqui

| Pasta / arquivo | O que é |
|---|---|
| [`slides/Minicurso_n8n_Apresentacao.pdf`](slides/Minicurso_n8n_Apresentacao.pdf) | Os slides da aula |
| [`guias/01-pre-requisitos.md`](guias/01-pre-requisitos.md) | O que trazer e preparar **antes** da aula |
| [`guias/02-credenciais.md`](guias/02-credenciais.md) | Passo a passo das chaves (Google, Gemini, OpenRouter, Postgres) e erros comuns |
| [`guias/03-como-importar.md`](guias/03-como-importar.md) | Como importar os workflows no seu n8n |
| [`guias/04-finbot.md`](guias/04-finbot.md) | Como montar o projeto principal (FinBot) |
| [`guias/05-ideias-e-desafio.md`](guias/05-ideias-e-desafio.md) | Banco de ideias e o desafio final |
| [`workflows/exemplos/`](workflows/exemplos) | Exemplos 00 a 05, prontos para importar |
| [`workflows/finbot/`](workflows/finbot) | Os workflows do FinBot (versão n8n Cloud e versão self-hosted) |
| [`planilhas/`](planilhas) | Modelo da planilha do FinBot (a dos exemplos é criada pelo workflow 00) |

## 🗺️ Roteiro da aula

1. **O que é o n8n**: gatilho, nó, conexão, item/JSON, execução, teste × produção
2. **As chaves**: credenciais do Google e da IA
3. **Exemplo 01**: Aprovado ou Reprovado (lógica, If, expressões `{{ }}`)
4. **Exemplo 02**: Formulário → Planilha → E-mail
5. **Exemplo 04**: Robô agendado da cotação do dólar (API)
6. **Exemplo 03**: Upload de arquivo → Google Drive → Planilha
7. **Exemplo 05**: IA classifica mensagens (Gemini)
8. **Projeto FinBot**: agente de IA com memória e ferramentas
9. **Potencial**: ideias, tempo economizado e o desafio

## 🚀 Começo rápido

> ⚡ **Use o n8n Cloud** (teste grátis em https://n8n.io): o login do Google já vem pronto (sem configurar o Google Cloud) e o agente usa a **Simple Memory** (sem banco de dados).
> **A única chave que você vai precisar é a do Google AI Studio:** https://aistudio.google.com/apikey

1. Faça o [pré-requisito](guias/01-pre-requisitos.md): conta Google pessoal, conta no n8n Cloud e chave do AI Studio.
2. Baixe este repositório: botão verde **Code → Download ZIP**.
3. No n8n: **⋯ → Import from file** e escolha um arquivo de `workflows/exemplos/`.
4. Em cada nó com ⚠️, escolha a **sua** credencial (*Sign in with Google*) e troque `COLE_AQUI_O_ID_DA_SUA_PLANILHA` pelo ID da sua planilha.
5. Para o projeto principal, use `workflows/finbot/1b_FinBot_agente_n8n_cloud.json` (Gemini + Simple Memory). Veja o [guia do FinBot](guias/04-finbot.md).

> Os arquivos **não têm nenhuma credencial**: cada um usa as próprias chaves. Os e-mails de destino estão como `seu-email@gmail.com`; troque pelo seu.

## 🔗 Links úteis

- n8n Cloud (teste grátis): https://n8n.io
- Documentação do n8n: https://docs.n8n.io
- Chave do Gemini: https://aistudio.google.com/apikey
- Google Cloud Console: https://console.cloud.google.com
- OpenRouter: https://openrouter.ai
- Neon (Postgres grátis): https://neon.tech
