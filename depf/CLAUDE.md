# Despachos DEP — CAU/RJ

Gerador de despachos padronizados do DEP (Departamento de Exercício Profissional) para processos de **pessoas físicas**: RRTs, CATs, RDAs e comunicações diversas.

**Repositório:** https://github.com/CAURJ/CAURJ-despachos-dep-main (org CAURJ)
**Produção:** https://caurj.github.io/CAURJ-despachos-dep-main/

## Stack

HTML estático + Bootstrap 4 + Jodit (CDN) + Font Awesome 4.7. Zero backend. GitHub Pages.

Analytics: Google Analytics (G-YSWX6RT94F).

## Categorias de templates

| Prefixo | Categoria | Quantidade |
|---|---|---|
| `index.html` + `rrts-XX` | RRT Extemporâneo (variantes) | 17 |
| `cat-XX` | CAT-A | 17 |
| `rda-XX` | RDA | 4 |
| `protocolos-XX` | Protocolos | 14 |
| `email-XX` | E-mails | 13 |
| `status-XX` | Atualizações de status | 15 |
| `exterior-XX` | RRTs exterior | 12 |
| `derivado-XX` | RRTs derivados | 6 |
| `interrupcao-XX` | Interrupções | 11 |
| `reativacao-XX` | Reativações | 9 |
| `cancelamento-XX` | Cancelamentos | 2 |
| `ativ-tecnica-XX` | Atividade técnica | 2 |

## Layout

3 colunas: sidebar de navegação | área principal com Jodit | sidebar direita. Seleção de variante via radio buttons na sidebar esquerda. Botão "Copiar" formata com tabela HTML e copia para clipboard (colar no SICCAU).

## Convenções

**Navbar:** `#006f78` (verde-azul — diferente do DEPJ/PJ que usa `#14385d` azul)

**Distinção de projetos:** Este projeto (DEP) cobre profissionais PF com RRTs/CATs. O projeto `despachos-depj-main` cobre PJ.

## Deploy

Push para `main` → GitHub Pages atualiza automaticamente.
