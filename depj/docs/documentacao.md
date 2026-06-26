# Despachos DEPJ — Documentação do Sistema

## Visão Geral

O **Despachos DEPJ** é uma ferramenta web para geração de despachos oficiais do **CAU/RJ** (Conselho de Arquitetura e Urbanismo do Rio de Janeiro), voltada ao **Departamento de Exercício Profissional Jurídico (DEPJ)**. Seu objetivo é padronizar e agilizar a elaboração de despachos para os processos de registro de Pessoas Jurídicas no sistema **SICCAU**.

A aplicação é 100% client-side (sem backend), podendo ser executada localmente ou hospedada como site estático.

- **Repositório:** https://github.com/CAURJ/despachos-depj-main
- **Produção:** https://caurj.github.io/despachos-depj-main/

---

## Como Executar Localmente

Requisito: Python 3 instalado.

```bash
cd ~/despachos-depj-main
python3 -m http.server 8080
```

Acesse no navegador: http://localhost:8080

> Não abra os arquivos `.html` diretamente pelo navegador (`file://`), pois as chamadas de API (consulta CNAE) serão bloqueadas por restrições de CORS.

---

## Stack Tecnológica

| Tecnologia | Versão | Uso |
|---|---|---|
| Bootstrap | 4.1.3 | Layout responsivo e componentes UI |
| jQuery | 3.3.1 | Manipulação de DOM e eventos |
| Popper.js | 1.14.3 | Posicionamento de dropdowns/tooltips |
| Font Awesome | 6.5.0 | Ícones |
| Jodit | — | Editor de rich text (WYSIWYG) |
| Google Analytics | — | Telemetria (ID: G-WG7WBKELRJ) |

---

## Estrutura de Arquivos

```
despachos-depj-main/
├── index.html                          # Página inicial / navegação
├── despacho_solicitacao_novo.html      # Solicitação de Registro de Empresa (principal)
├── alteracao-cadastral.html            # Alteração Cadastral
├── baixa-registro-empresa.html         # Baixa de Registro de Empresa
├── baixa-registro-empresa-oficio.html  # Baixa de Registro por Ofício
├── interrupcao-registro-empresa.html   # Interrupção de Registro de Empresa
├── inclusao-responsavel-tecnico.html   # Inclusão de Responsável Técnico
├── baixa-responsavel-tecnico.html      # Baixa de Responsável Técnico
├── inclusao-email.html                 # Inclusão de E-mail
├── desconto-anuidade.html              # Desconto de Anuidade
├── crq-pj.html                         # CRQPJ
├── visto-previo.html                   # Visto Prévio
├── despachos-gerais.html               # Despachos Gerais
├── consulta_cnae.html                  # Consulta de CNAE
├── consulta_cnae_protocolo.html        # Consulta CNAE por Protocolo
├── piso-semanal.html                   # Calculadora de piso salarial semanal
├── piso-diario.html                    # Calculadora de piso salarial diário
├── cau.png                             # Logo CAU/RJ
├── logo_novo.png                       # Logo alternativo
├── jodit.js                            # Biblioteca Jodit (embutida)
├── jodit.css                           # Estilos do Jodit (embutidos)
├── arquivos/                           # Versões antigas/arquivadas
└── docs/                               # Documentação
```

### Arquivos internos (desenvolvimento)

| Arquivo | Finalidade |
|---|---|
| `_gerador_de_variaveis.html` | Ferramenta auxiliar para gerar variáveis de template |
| `_gerador_de_modais.html` | Ferramenta auxiliar para gerar modais |
| `jodit_com_edicao.html` | Teste do editor Jodit com edição |
| `jodit_sem_edicao_no_final.html` | Teste do editor Jodit sem edição no final |

### Pasta `arquivos/`

Contém versões anteriores dos módulos, mantidas como histórico e referência. Não são utilizadas pela aplicação em produção.

---

## Como Funciona

### Fluxo de uso

1. O usuário acessa um módulo de despacho pelo `index.html`
2. Marca os **checkboxes** correspondentes às pendências ou situações do processo
3. Cada checkbox possui um texto de despacho pré-escrito, editável via ícone de lápis
4. Clica em **Atualizar** para compor o despacho final no editor Jodit
5. Clica em **Copiar** para copiar o conteúdo formatado
6. Cola o texto no sistema **SICCAU**

### Estrutura de um item de despacho

Cada opção de despacho segue este padrão HTML:

```html
<div class="form-check">
  <input type="checkbox" id="despacho1000" data-text="[texto do template]">
  <label>Descrição da pendência</label>
  <i class="edit-icon" data-target="#editModal1000"></i>   <!-- abre modal de edição -->
  <i class="info-icon" data-target="#infoModal1000"></i>   <!-- exibe informação adicional -->
</div>

<!-- Modal de edição -->
<div class="modal" id="editModal1000">
  <textarea id="editTextModal1000">[texto editável]</textarea>
</div>
```

### Convenção de numeração de IDs

Os IDs dos checkboxes seguem uma hierarquia numérica:

| Faixa | Uso |
|---|---|
| 1000–8999 | Seções e subseções gerais |
| 9000+ | RRT |
| 10000+ | CNPJ |
| 11000+ | Documentação |
| 12000+ | Informações complementares |
| 13000+ | Prazo |
| 14000+ | Encerramento |
| 15000+ | Mensagens de deferimento |

---

## Integração Externa

### SICCAU
Sistema oficial do CAU/BR onde os despachos gerados são inseridos manualmente após cópia.
- URL: https://acesso.caubr.gov.br/

### Minha Receita (API pública)
Utilizada na página `consulta_cnae_protocolo.html` para buscar dados de CNPJ e CNAE.
- Chamada via `fetch` no navegador

---

## Deploy

O site é hospedado via **GitHub Pages** a partir da branch `main`.

Para publicar alterações:

```bash
git add <arquivo>
git commit -m "Descrição da alteração"
git push
```

O GitHub Pages atualiza automaticamente após o push.

### Configuração de SSH (repositório da organização CAURJ)

O repositório pertence à organização `CAURJ` no GitHub. Para fazer push, é necessário usar uma chave SSH associada a uma conta com permissão de escrita no repositório.

Caso utilize múltiplas contas GitHub na mesma máquina, configure `~/.ssh/config`:

```
Host github-caurj
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_ticaurj
```

E configure o remote do projeto para usar esse host:

```bash
git remote set-url origin git@github-caurj:CAURJ/despachos-depj-main.git
```

---

## Padrões Visuais

| Elemento | Cor |
|---|---|
| Navbar | `#14385d` (azul escuro) |
| Ícone de edição | `#005abb` (azul) |
| Ícone de informação | `rgba(235, 153, 1, 0.884)` (laranja) |
