# Aulyn Student Market Survey

Questionário independente para validar necessidades reais de estudantes do ensino superior antes de fechar o produto Aulyn.

## Estrutura

- `index.html` — questionário público
- `privacy.html` — informação de privacidade
- `dashboard.html` — dashboard privado; pede uma admin key em runtime
- `netlify.toml` — configuração estática para Netlify

## Backend

As respostas são enviadas para uma Supabase Edge Function:

`https://niymlnyfoxjbhijpmpag.supabase.co/functions/v1/submit-student-market-survey`

e guardadas na tabela privada `student_market_survey_responses`.

O dashboard usa uma segunda Edge Function protegida por uma chave que **não está neste repositório**.

## Deploy no Netlify

1. Importa este repositório no Netlify.
2. Build command: vazio.
3. Publish directory: `.`
4. Faz deploy.

O questionário ficará em `/` e o dashboard em `/dashboard.html`.

## Tracking da origem

Podes distribuir links como:

- `/?src=whatsapp`
- `/?src=instagram`
- `/?src=reddit`
- `/?src=utad`

A origem fica guardada na resposta para comparar canais.

## Segurança

- A tabela tem RLS ativo e não tem políticas públicas.
- O formulário não contém uma service-role key.
- A Edge Function pública faz a inserção server-side.
- O dashboard não contém a admin key no código.
- Não comites a admin key no GitHub.
