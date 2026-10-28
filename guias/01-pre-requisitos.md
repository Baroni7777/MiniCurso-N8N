# Pré-requisitos (fazer antes da aula)

## Obrigatório
- **Notebook** com navegador atualizado (Chrome, Edge ou Firefox) e carregador.
- **Conta Google pessoal** (Gmail). Contas institucionais da faculdade costumam bloquear os acessos que vamos usar.
- **Acesso a um n8n**: crie a conta de teste grátis do **n8n Cloud** em https://n8n.io (14 dias) ou use o acesso que o professor passar na aula.
- **Chave do Gemini** (grátis): https://aistudio.google.com/apikey → *Create API key*. Guarde a chave num bloco de notas.
  O Google AI Studio exige **18 anos ou mais**.
  **No n8n Cloud, essa é a única chave que você vai precisar.**

## Por que o n8n Cloud é o caminho mais rápido
- **Google sem configuração:** Sheets, Drive e Gmail já vêm com o login pronto (*Sign in with Google*). Não precisa criar projeto, cliente OAuth nem nada no Google Cloud Console.
- **Memória sem banco de dados:** o agente de IA usa o nó **Simple Memory**, que já vem no n8n.
- Resultado: você só precisa da chave do AI Studio.

## Se for usar n8n instalado no próprio servidor (self-hosted)
- Ative a **verificação em 2 etapas** na conta Google: https://myaccount.google.com/signinoptions/twosv
  Sem isso o Google Cloud mostra *"Google Cloud access blocked"*. Ative com antecedência: às vezes leva alguns minutos para valer.
- Entre uma vez em https://console.cloud.google.com antes da aula e aceite os termos. Conta nova às vezes pede uma verificação extra (celular).
- Vai ser preciso criar o cliente OAuth do Google (veja o [guia de credenciais](02-credenciais.md)).
- Ao conectar o Google aparece **"O Google não verificou este app"**. É esperado: clique em *Avançado → Acessar (não seguro)* e marque todas as permissões.

## Não precisa
- Saber programar.
- Cartão de crédito para os serviços do Google (Sheets, Drive, Gmail, Gemini): são grátis para o que vamos fazer.
- Banco de dados: no n8n Cloud o agente usa a **Simple Memory**.
