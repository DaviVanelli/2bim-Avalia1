# Desenho Assinado

Aplicação que recebe um número inteiro entre 1 e 100 e gera um SVG assinado com o e-mail da conta Google autenticada.

## Funcionamento

O login usa Google Identity Services. O navegador envia o número para POST /api/desenho e o ID token no cabeçalho Authorization: Bearer.

O servidor verifica o token no Google, confere o público (aud) e a verificação do e-mail. A assinatura é obtida do token validado.

A geração do SVG ocorre no servidor, usando a implementação original preservada em lib/desenho.js.

## Estrutura

- public/: HTML, CSS e JavaScript do navegador.
- lib/desenho.js: implementação original do desenho.
- functions/api/desenho.js: validação e geração do SVG.
- functions/api/config.js: fornece o Client ID público ao navegador.
- evidencias/exemplo.svg: desenho gerado no site com o número 75.

## Respostas da API

- 405: método diferente de POST.
- 400: JSON ou número inválido.
- 401: autenticação ausente ou inválida.
- 200: SVG com Content-Type image/svg+xml.

## Publicação

Cloudflare Pages conectado à branch main do GitHub.

Framework preset: None.
Build command: vazio.
Build output directory: public.

A variável GOOGLE_CLIENT_ID está configurada no ambiente de produção do Cloudflare.

## Identificação

Nome: Davi Cunha Mayer Vanelli

RA: 2026108175

URL: https://2bim-avalia1-f3r.pages.dev
