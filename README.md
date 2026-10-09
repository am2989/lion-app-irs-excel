# 🦁 Lion App – Agregador de Dados para a Declaração de IRS (Excel)

Projeto desenvolvido no âmbito de um desafio da [DIO](https://www.dio.me/): construir, inteiramente em Excel, uma ferramenta que ajude a **organizar e reunir a informação essencial para a declaração de impostos sobre o rendimento**, com navegação por menus, validações automáticas e ligações rápidas.

> ⚠️ Todos os dados que constam do ficheiro (nome, NIF, morada, contactos, bancos e valores) são **fictícios** e servem apenas de exemplo.

---

## 🇵🇹 Adaptação a Portugal

O enunciado original fala em *imposto de renda*, o termo usado no Brasil. Como vivo e trabalho em Portugal, **optei por adaptar o projeto à realidade portuguesa**, usando a terminologia e os formatos que se utilizam cá:

| Conceito no enunciado (Brasil) | Adaptação neste projeto (Portugal) |
|---|---|
| Imposto de renda | **IRS** (Imposto sobre o Rendimento das Pessoas Singulares) |
| CPF | **NIF** (Número de Identificação Fiscal), formatado como `000.000.000` |
| CEP | **Código postal** no formato `0000-000` |
| Celular | **Telemóvel**, com indicativo `+351` |
| Moeda em R$ | **Euro (€)** |
| Pessoa física | **Pessoa singular** |
| Informes de rendimentos | Informação de rendimentos / valores por instituição bancária |
| Residente do exterior | Indicação de residência fora do país |
| Trabalho dependente / independente / rendas | Correspondem, respetivamente, aos rendimentos de trabalho por conta de outrem, trabalho independente e rendas de prédios |

O objetivo foi que a ferramenta fosse realmente útil a quem prepara o IRS em Portugal, e não apenas uma cópia do exemplo das aulas.

---

## 🎯 Objetivo

Criar um **agregador de dados** onde o utilizador consegue:

- registar os seus dados pessoais;
- registar os rendimentos/saldos por instituição bancária;
- registar as entradas de dinheiro mês a mês, por categoria;
- fazê-lo de forma **guiada e validada**, reduzindo erros de preenchimento.

---

## 🗂️ Estrutura do ficheiro (`lion_app_alda.xlsx`)

| Folha | Conteúdo |
|---|---|
| **1. Titular** | Dados da pessoa singular: nome, NIF, data de nascimento, cônjuge, morada, código postal, telefone, telemóvel, e-mail e três indicações SIM/NÃO (alterações face à entrega anterior, dependente cônjuge, residente no exterior). |
| **2. Informes** | Até 3 bancos, cada um com **banco**, **valor atual** e **anexo** (nome do extrato). Mostra o **TOTAL** automaticamente. |
| **3. Notas** | Tabela de entradas (transferências/extrato) com **data**, **categoria** e **valor**, até 29 linhas. |
| **tabelas** *(oculta)* | Lista de bancos que alimenta a lista pendente da folha *Informes*. |

---

## ⚙️ Funcionalidades

### 🧭 Menu de navegação
Cada folha tem um menu com botões (formas do Excel com hiperligações) que levam diretamente às outras folhas, mais setas de navegação e um atalho para o meu LinkedIn. Em cada folha o utilizador sabe sempre onde está e para onde pode ir.

### ✅ Validações automáticas
- **Listas pendentes SIM/NÃO** nos campos de resposta fechada da folha *Titular*.
- **Lista de bancos** na folha *Informes*, alimentada pela folha oculta `tabelas`, com mensagem de ajuda (*"Informe um banco vinculado ao seu NIF"*) e mensagem de erro (*"Banco não encontrado"*).
- **Lista de categorias** na folha *Notas*: Trabalho Independente, Trabalho Dependente e Rendas.

### 🔗 Ligações rápidas
- Navegação interna entre folhas.
- Ligação `mailto:` no campo de e-mail do titular, que abre uma mensagem pré-preenchida.
- Ligação externa para o LinkedIn.

### 🧮 Fórmulas e formatação
- **Total dos bancos:** `=SUM(D11,D16,D21)` na folha *Informes*.
- Formatos personalizados: NIF (`000.000.000`), código postal (`0000-000`), telefones com `+351`, valores em `€` e datas no formato mês-ano nas notas.
- **Tabela do Excel** (`Tabela7`) na folha *Notas*, com estilo e filtros.

### 🔒 Proteção das folhas
As folhas estão protegidas e **só as células de preenchimento estão desbloqueadas**, para o utilizador não estragar títulos, fórmulas ou o layout por engano. (A proteção não tem palavra-passe, para ser fácil de alterar.)

---

## 🖼️ Capturas de ecrã

| Titular | Informes | Notas |
|---|---|---|
| ![Titular](images/titular.png) | ![Informes](images/informes.png) | ![Notas](images/notas.png) |

---

## ▶️ Como usar

1. Descarregue o ficheiro `lion_app_alda.xlsx`.
2. Abra-o no Excel e, se aparecer o aviso, clique em **Ativar edição**.
3. Preencha apenas as células desbloqueadas (as dos campos de resposta).
4. Use o menu no topo de cada folha para navegar.
5. Na folha *Notas*, registe cada entrada com data, categoria e valor.

---

## 📚 O que aprendi

- Construir **menus de navegação** com formas e hiperligações internas.
- Criar **validação de dados** com listas fixas e com listas vindas de outra folha (folha oculta).
- Usar **mensagens de entrada e de erro** para guiar o utilizador.
- Aplicar **formatos numéricos personalizados** (NIF, código postal, telefone).
- **Proteger folhas** deixando só as células de entrada editáveis.
- Documentar um projeto técnico em **Markdown** e partilhá-lo no **GitHub**.

---

## 🚧 Limitações e melhorias futuras

- Acrescentar mais validações: NIF com 9 dígitos, e-mail válido, datas válidas e valores numéricos não negativos.
- Rever alguns termos e listas que ainda vêm do exemplo original (por exemplo, o campo *Título de Eleitor* e a lista de bancos, que tem códigos de bancos brasileiros) e substituí-los por equivalentes portugueses.
- Transformar o campo *Anexo* num verdadeiro **link** para o ficheiro do extrato.
- Acrescentar **totais por categoria** na folha *Notas* (por exemplo, com `SUMIF`).
- Permitir mais de 3 bancos e mais de 29 entradas.

---

## 👩‍💻 Autora

**Alda Benta** · [LinkedIn](https://www.linkedin.com/in/alda-benta/)

Projeto realizado para fins de aprendizagem na DIO.
