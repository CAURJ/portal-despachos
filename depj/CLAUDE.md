# Despachos DEPJ — CAU/RJ

Gerador de despachos para processos de registro de **pessoas jurídicas** no SICCAU. Atende o DEPJ (Departamento de Exercício Profissional Jurídico) do CAU/RJ.

**Repositório:** https://github.com/CAURJ/despachos-depj-main (org CAURJ)
**Produção:** https://caurj.github.io/despachos-depj-main/

## Stack

HTML estático + Bootstrap 4 + jQuery + Jodit (embutido localmente como `jodit.js`/`jodit.css`). Zero backend. Hospedado no GitHub Pages.

## Desenvolvimento local

```bash
python3 -m http.server 8080
```

Necessário por CORS — a consulta CNPJ via API Minha Receita não funciona em `file://`.

## Fluxo de uso

1. Usuário acessa um módulo de despacho pelo `index.html`
2. Marca checkboxes das pendências do processo
3. Clica em **Atualizar** → texto composto no editor Jodit
4. Clica em **Copiar** → cola no SICCAU

## Estrutura

~50 arquivos HTML, cada um para um tipo de processo. Pasta `arquivos/` guarda versões antigas (não publicadas).

Módulos principais: solicitação de registro, alteração cadastral, baixa (registro e de ofício), interrupção, inclusão/baixa de responsável técnico, inclusão de e-mail, desconto de anuidade, CRQPJ, visto prévio, despachos gerais. Também: consulta CNAE, calculadoras de piso salarial.

Ferramentas de dev internas (prefixo `_`): `_gerador_de_variaveis.html`, `_gerador_de_modais.html`.

## Convenções

**IDs de checkboxes:** 1000–8999 seções gerais · 9000+ RRT · 10000+ CNPJ · 11000+ docs · 13000+ prazo · 14000+ encerramento · 15000+ deferimento

**Cores:** navbar `#14385d` · ícone edição `#005abb` · ícone info `rgba(235,153,1,0.884)`

## Deploy

Push para `main` → GitHub Pages atualiza automaticamente.

SSH configurado via `Host github-caurj` → `IdentityFile ~/.ssh/id_ed25519_ticaurj`.

## Integrações externas

- **SICCAU** — destino final dos despachos (colagem manual)
- **Minha Receita** — busca de CNPJ/CNAE via `fetch` no navegador
