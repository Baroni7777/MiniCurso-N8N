# Como importar os workflows

1. Baixe o repositório (**Code → Download ZIP**) e descompacte.
2. No n8n, crie um workflow novo → menu **⋯** (canto superior direito) → **Import from file** → escolha o `.json`.
3. Abra cada nó que mostra ⚠️ e selecione a **sua** credencial (Google Sheets, Drive, Gmail, Gemini...).
4. Nos nós do Google Sheets, troque `COLE_AQUI_O_ID_DA_SUA_PLANILHA` pelo ID da sua planilha
   (o trecho da URL entre `/d/` e `/edit`).
5. Nos nós do Gmail, troque `seu-email@gmail.com` pelo seu e-mail.
6. Clique em **Execute workflow** para testar. Formulários: use a **Test URL** no editor; a **Production URL** só funciona com o workflow publicado.

## Os exemplos

| Arquivo | O que faz | Precisa de |
|---|---|---|
| `00_preparacao_criar_planilha.json` | Cria a planilha "Minicurso n8n - Exemplos" com as abas `Inscricoes`, `Arquivos` e `Contatos` (rode uma vez) | Google Sheets |
| `01_aprovado_ou_reprovado.json` | Nota ≥ 6 → Aprovado, senão Reprovado. Troque a nota e execute de novo | nada |
| `02_formulario_planilha_email.json` | Formulário de inscrição → salva na planilha → manda e-mail de confirmação | Sheets + Gmail |
| `03_upload_drive_planilha.json` | Formulário com arquivo → salva no Drive → registra o link na planilha | Drive + Sheets |
| `04_robo_cotacao_dolar.json` | Todo dia às 8h busca a cotação do dólar numa API e manda por e-mail | Gmail |
| `05_ia_classifica_mensagens.json` | IA lê a mensagem, classifica (reclamação, elogio...) e alerta se for reclamação | Gemini + Sheets + Gmail |

Depois de rodar o **00**, copie o ID da planilha criada e cole nos exemplos 02, 03 e 05. Não precisa criar cabeçalho: ele nasce sozinho na primeira execução.

Em cada exemplo, pergunte: **quanto tempo isso economiza?** Em *Settings → Estimated time saved* você informa os minutos por execução e o painel *Overview* soma tudo.
