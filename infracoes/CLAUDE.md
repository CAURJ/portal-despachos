# Relato CEP — CAU/RJ

Ferramenta para elaborar **relatos de infração** (fase de autuação) nos processos disciplinares do CAU/RJ, com cálculo automático de penalidades conforme as Resoluções nº 22 e 198.

**Repositório:** https://github.com/CAURJ/relato-main (org CAURJ)
**Produção:** https://caurj.github.io/relato-main/

## Stack

HTML estático + Bootstrap 4 + jQuery + jsPDF 2.5.1. Zero backend. GitHub Pages.

Analytics: Google Analytics (G-7SG2MC2382) + GoatCounter (`causp.goatcounter.com` — ID do CAU/SP, mas o conteúdo é do CAU/RJ).

## Templates disponíveis (~14 arquivos)

**Resolução nº 198:**
- Exercício ilegal da profissão PF e PJ
- Exercício irregular da profissão PF
- Ausência de responsável técnico (para a atividade · PJ)
- Utilização irregular dos termos "Arquitetura" ou "Urbanismo"
- Ausência ou utilização irregular de placa
- Ausência de RRT PF

**Resoluções nº 22 e 198 (combinados):**
- Ausência de registro CAU e CREA PJ
- Ausência de registro CAU PJ
- Ausência de responsável técnico PJ
- Ausência de RRT PF
- Exercício ilegal PF com ausência de responsável para atividade
- Exercício ilegal PF com exploração econômica

## Funcionalidades

- Formulários com campos condicionais (show/hide via checkbox)
- Calculadora de multa: pontos → múltiplo da anuidade (tabela 2012–2026 hardcoded)
- Comparativo automático entre penalidades da Resolução 22 vs 198
- Export para PDF via jsPDF
- Imagens de cabeçalho/rodapé em `img/`

## Atenção

A tabela de anuidades está hardcoded nos HTMLs. Atualizar anualmente.

Este projeto gera os *relatos de infração* (autuação). Para relatórios de *julgamento* no CEP, ver o projeto `relatos-cep`.
