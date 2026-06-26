# Relatos CEP — CAU/RJ

Gerador do **Relatório do Conselheiro** para julgamento de Autos de Infração na Comissão de Exercício Profissional (CEP) do CAU/RJ.

**Repositório:** git@github.com:CAURJ/relatos-cep.git (SSH, org CAURJ)
**Produção:** https://caurj.github.io/relatos-cep/

## Stack

HTML estático + Bootstrap 4 + Jodit (CDN). Zero backend. GitHub Pages.

## Arquivos

- `index.html` — menu inicial com cards de tipos de relato
- `relatorio-ai.html` — Relatório do Conselheiro: Julgamento de AI com Fatores Atenuantes (Res. 198)
- `img/cabecalho.jpg` e `img/rodape.jpg` — imagens do documento oficial

## Fluxo do relatorio-ai.html

1. Preencher dados do processo (protocolo, auto de infração, autuado, conselheiro relator)
2. Preencher histórico, análise e voto
3. Marcar fatores atenuantes aplicáveis (lógica condicional de exibição)
4. Preview do documento ao lado do formulário (Jodit, toolbar simplificada)

A lista de conselheiros titulares e suplentes está hardcoded no `<select>` — atualizar a cada mandato.

## Atenção

Este projeto gera os *relatórios de julgamento* (fase CEP). Para os *relatos de infração* (fase de autuação), ver o projeto `relato-main`.

## Deploy

Push para `main` → GitHub Pages atualiza automaticamente.
