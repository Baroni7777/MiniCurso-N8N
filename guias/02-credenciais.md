# As chaves (credenciais)

Antes de montar qualquer fluxo, o n8n precisa de permissão para usar os seus serviços.

## ⚡ Caminho rápido: n8n Cloud (recomendado)

No **n8n Cloud** você **não precisa configurar nada no Google Cloud Console**: o login do Google já vem pronto (*Managed OAuth*).
E a memória do agente pode ser a **Simple Memory**, que fica dentro do próprio n8n (sem banco de dados).

**A única chave que você vai precisar é a do Google AI Studio (Gemini).**

| Serviço | No n8n Cloud |
|---|---|
| Google Sheets, Drive, Gmail | *Create credential* → escolha o serviço → **Sign in with Google** → marque todas as permissões. Pronto. |
| Gemini (IA) | Chave de API do AI Studio: https://aistudio.google.com/apikey → *Create API key* → no n8n: *Create credential → Google Gemini (PaLM) API* |
| Memória do agente | Nó **Simple Memory** ligado no AI Agent (não precisa de credencial) |

> A Simple Memory guarda só as últimas mensagens de cada conversa e é ótima para aprender. Para um projeto de verdade, que precisa lembrar por muito tempo, use Postgres (seção mais abaixo).

---

## Caminho completo: n8n instalado no próprio servidor (self-hosted)

No self-hosted o login do Google não vem pronto: é preciso criar o cliente OAuth no Google Cloud (passo a passo abaixo).

| Serviço | Tipo de credencial | Onde se cria |
|---|---|---|
| Google Sheets, Drive, Gmail | OAuth2 (Client ID + Client Secret) | Google Cloud Console (console.cloud.google.com) |
| Gemini (exemplos simples) | Chave de API | Google AI Studio (aistudio.google.com/apikey) |
| IA do agente FinBot | Chave de API OpenRouter | openrouter.ai → Keys (defina um limite de gasto) |
| Memória do agente | Postgres (host, banco, usuário, senha) | neon.tech → projeto → Connect |

> **Atenção:** Sheets, Drive e Gmail **não** usam "chave de API". Só a IA usa chave.
> OpenRouter e Neon são opcionais: só para quem quiser o FinBot com outro modelo ou memória permanente.

## Passo a passo do Google Cloud

1. Ative a verificação em 2 etapas na conta Google (myaccount.google.com → Segurança).
2. Abra https://console.cloud.google.com → **New Project** → nome "Minicurso n8n" → **Create**. Confira se o projeto está selecionado no topo.
3. **APIs e serviços → Biblioteca** → ative **Google Sheets API**, **Google Drive API** e **Gmail API**.
4. **Google Auth Platform → Branding**: nome do app e e-mail de suporte.
   **Público**: *Externo*; adicione o seu e-mail em **Usuários de teste**; clique em **Publicar app** (senão o login expira em 7 dias).
5. **Clientes → Criar cliente OAuth → Aplicativo da Web**. Em **URIs de redirecionamento autorizados**, cole a *OAuth Redirect URL* que aparece na credencial do n8n
   (ex.: `https://SEU-N8N/rest/oauth2-credential/callback`).
6. Copie o **Client ID** e o **Client Secret** (o Secret só aparece inteiro nessa hora).
7. No n8n: **Create credential → Google Sheets OAuth2 API** → cole ID e Secret → **Sign in with Google** → aceite o aviso de app não verificado (*Avançado → continuar*) → marque todas as permissões → deve aparecer **"Account connected"**.
   Repita para **Google Drive OAuth2 API** e **Gmail OAuth2** usando o mesmo cliente.

## Gemini
1. https://aistudio.google.com/apikey → **Create API key**.
2. No n8n: **Create credential → Google Gemini (PaLM) API** → cole a chave.

## OpenRouter (agente FinBot)
1. https://openrouter.ai → crie a conta → **Keys → Create key** (defina um limite de gasto).
2. No n8n: **Create credential → OpenRouter** → cole a chave. Modelo usado: `google/gemini-3.5-flash`.

## Neon / Postgres (memória do FinBot)
1. https://neon.tech → crie um projeto → **Connect**.
2. No n8n: **Create credential → Postgres** → preencha host, banco, usuário e senha; marque SSL.

## Erros comuns

| Mensagem | Causa | Solução |
|---|---|---|
| Google Cloud access blocked | Conta sem verificação em 2 etapas | Ativar 2SV, esperar alguns minutos e recarregar |
| redirect_uri_mismatch | URL de redirecionamento diferente da do n8n | Copiar a *OAuth Redirect URL* do n8n e colar igual (https, sem espaço) |
| access_denied / app não verificado | E-mail não está em Usuários de teste | Adicionar o e-mail em Público → Usuários de teste |
| invalid_client / Client authentication failed | Client ID/Secret errado ou cliente apagado | Copiar de novo do Cloud Console; recriar o cliente se preciso |
| Para de funcionar depois de 7 dias | App em modo Teste | Publicar o app e reconectar a credencial |
| 429 Too Many Requests (Gemini) | Limite grátis (~5 pedidos/min) | Esperar 1 minuto |
