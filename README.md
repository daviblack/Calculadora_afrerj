# 💰 Calculadora de Remuneração — Auditor Fiscal SEFAZ-RJ

> **App web de apoio à decisão para o novo Auditor Fiscal da Receita Estadual (AFRE) da SEFAZ-RJ** — concurso organizado pela **Cebraspe (2025)**, base remuneratória **2026**.

Uma ferramenta interativa, **gratuita e offline**, que estima a **remuneração líquida** do auditor fiscal e ajuda o futuro servidor a visualizar projeções de carreira, o impacto de cada verba e decisões importantes — como **aderir ou não à previdência complementar (RPC/RJPrev)**.

<p align="center">
  <b>Desenvolvido por Davi Teixeira</b> · 📸 <a href="https://instagram.com/daviteixeira.concursos">@daviteixeira.concursos</a>
</p>

---

## ⚠️ Aviso importante — leia antes de usar

**Esta calculadora é uma estimativa de caráter meramente ilustrativo e educacional. Não substitui o contracheque oficial, a legislação vigente nem orientação profissional (contábil, jurídica ou financeira).**

Para que a ferramenta fosse **viável, simples e didática**, foram adotadas premissas e simplificações (detalhadas na seção [Premissas adotadas](#-premissas-e-simplificações-adotadas)). Entre elas:

- **Não considera inflação** — todos os valores são **nominais** (não corrigidos no tempo).
- **Imposto de Renda** incide apenas sobre **bases pré-definidas** (bruto menos previdências), pela tabela progressiva mensal de 2026, **sem dependentes** e sem desconto simplificado.
- **Não modela composição de carteiras de investimento** — a comparação "RPC × conta própria" usa uma **taxa de retorno única anual**, sem alocação por ativos nem tributação sobre os rendimentos do investimento próprio.
- Verbas indenizatórias e o Prêmio de Produtividade (PPE) são **estimativas**.

A ferramenta foi idealizada **com a melhor das intenções**, para servir de apoio ao estudo e ao planejamento dos candidatos. **Sempre confirme os valores no contracheque oficial e na legislação aplicável.**

---

## 📑 Índice

- [O que a ferramenta faz](#-o-que-a-ferramenta-faz)
- [Como acessar / abrir](#-como-acessar--abrir)
- [Tutorial completo de uso](#-tutorial-completo-de-uso)
- [Como funciona o cálculo](#-como-funciona-o-cálculo-resumo)
- [Premissas e simplificações adotadas](#-premissas-e-simplificações-adotadas)
- [Histórico de versões (Changelog)](#-histórico-de-versões-changelog)
- [Roadmap — próximos passos](#-roadmap--próximos-passos)
- [Estrutura do repositório](#-estrutura-do-repositório)
- [Como contribuir / sugerir melhorias](#-como-contribuir--sugerir-melhorias)
- [Autoria e licença](#-autoria-e-licença)

---

## 🚀 O que a ferramenta faz

A calculadora é um **aplicativo web standalone** (um único arquivo HTML, sem dependências, sem instalação) organizado em **4 abas**:

| Aba | O que mostra |
|---|---|
| **Calculadora** | O líquido mensal estimado, o gráfico "do bruto ao líquido" (cascata), o detalhamento de cada verba e desconto, KPIs (carga tributária, % que sobra, alíquota efetiva de IR) e uma "visão do futuro" com a progressão de classe em 3 e 6 anos. |
| **Projeção no tempo** | A evolução da remuneração ao longo da carreira, o **ponto de saturação no teto do STF**, as deduções (previdência + IR) ano a ano, o ganho acumulado com triênios e o patrimônio de carreira (líquido acumulado). |
| **Comparações** | A decisão **aderir ao RPC × investir por conta própria** (com ponto de empate), o líquido por classe e o **impacto marginal** de cada parâmetro no seu líquido. |
| **Como usar** | Tutorial passo a passo, glossário e explicação das premissas — embutidos no próprio app. |

### Principais recursos

- ✅ **4 cenários padrão** prontos (com/sem reajuste de 11,56%, com/sem triênios).
- ✅ **Painel de parâmetros** totalmente personalizável (classe, RPC e alíquota, triênios, PPE, auxílio moradia, ajudas de custo).
- ✅ **Premissas avançadas** ajustáveis por *toggles* (ex.: triênio sobre produtividade, PPE tributada) — nunca alteradas silenciosamente.
- ✅ **Variáveis globais editáveis** (tetos, alíquotas, reajuste) para o caso de a legislação mudar.
- ✅ **Gráficos interativos** (SVG, com *hover*) e caixas **"Como ler"** em cada um.
- ✅ **Compartilhar** o cenário por link e **Exportar PDF**.
- ✅ Salva seus parâmetros no navegador (localStorage), funciona **offline** e é **responsivo** (celular e desktop), com cuidados de **acessibilidade**.

---

## 🔌 Como acessar / abrir

A ferramenta é **um único arquivo HTML** — não precisa instalar nada.

**Opção 1 — abrir localmente (mais simples):**
1. Baixe o arquivo [`Calculadora-Remuneracao-AFRE-RJ.html`](Calculadora-Remuneracao-AFRE-RJ.html).
2. Dê **duplo clique** nele. Abre em qualquer navegador (Chrome, Edge, Firefox, Safari), inclusive **sem internet**.

**Opção 2 — publicar na web (GitHub Pages):**
1. Suba o arquivo `.html` para um repositório.
2. Em **Settings → Pages**, ative o GitHub Pages na branch principal.
3. Acesse pelo link gerado (ex.: `https://seu-usuario.github.io/repo/Calculadora-Remuneracao-AFRE-RJ.html`).

> 💡 As fontes vêm do Google Fonts, mas há *fallback* do sistema — se estiver offline, o app continua funcionando com fontes locais.

---

## 📖 Tutorial completo de uso

Este é um guia detalhado para tirar o máximo da ferramenta. (O app também traz uma versão resumida na aba **"Como usar"**.)

### Passo 1 — Comece por um cenário padrão

No topo da página, há quatro botões em **"Cenários padrão"**:

1. **Base, sem reajuste** — o líquido de hoje, do auditor entrante (3ª classe), sem reajuste e sem triênios.
2. **Sem reajuste + triênios** — acrescenta 3 triênios (9 anos de serviço público anterior que contam).
3. **Reajuste 11,56%** — aplica o reajuste prometido para 2026.
4. **Reajuste + triênios** — combina os dois.

👉 Clique em um deles para ver os números na hora. Eles são o **ponto de partida** e reproduzem a planilha-fonte do projeto. A etiqueta ao lado mostra qual cenário está ativo ("Cenário padrão 1", etc.) ou "Cenário personalizado" se você alterar algo.

### Passo 2 — Personalize para o seu caso

No **painel da esquerda** ("Parâmetros do seu caso" — no celular, toque para expandir):

- **Classe na carreira** — 3ª (entrada), 2ª ou 1ª (topo).
- **Reajuste de 11,56% (2026)** — ligue/desligue o reajuste previsto.
- **Adesão à previdência complementar (RPC)** — ligue para simular a adesão ao RJPrev e ajuste a **alíquota** (de 5,5% a 8,5%) no controle deslizante.
- **Triênios** — ligue e informe seus **anos de serviço público anterior**; escolha se esse tempo **conta** ou **não conta** para triênios.
- **PPE — Prêmio de Produtividade** — ligue/desligue e ajuste o valor médio mensal.
- **Auxílio Moradia (barreira fiscal)** — ative apenas se sua lotação for em barreira fiscal.
- **Ajudas de custo** — alimentação e transporte.

> 🔧 **Premissas avançadas** (no fim do painel, em "Premissas avançadas do modelo"): controles para quem quer revisar o modelo — *triênio incide sobre a produtividade*, *PPE tributada* e *RPPS sobre todo o bruto sem adesão*. Por padrão, eles reproduzem exatamente a planilha-fonte; mexa apenas se souber o que está testando.

### Passo 3 — Leia o resultado (aba Calculadora)

- O **cartão grande no topo** mostra o **líquido mensal estimado**, o valor anual (×12) e uma estimativa com **13º + ⅓ de férias**.
- Se a remuneração ultrapassar o **teto do STF**, aparece um aviso de **abate-teto**.
- O gráfico **"Do bruto ao líquido"** (cascata) mostra, passo a passo: começa no **bruto** (azul), as barras **vermelhas descem** (previdência e IR descontam) e as **verdes sobem** (ajudas e PPE acrescentam) até o **líquido** final.
- O painel **"Detalhamento"** lista cada item em reais.
- Os **KPIs** resumem: bruto do cargo, total de deduções, **quanto sobra** (%), alíquota efetiva de IR e carga previdenciária.
- **"Visão do futuro"** projeta seu líquido em **3 e 6 anos**, quando você progride de classe.

### Passo 4 — Olhe para o futuro (aba Projeção no tempo)

- Ajuste o **horizonte** (5 a 35 anos) no controle deslizante.
- **Ponto de saturação**: compara o bruto "de direito" (linha tracejada) com o **efetivamente pago** após o abate-teto (linha cheia). Quando elas se separam, você **bateu o teto do STF** e ganhos extras (como triênios) param de aumentar o líquido.
- **Deduções no tempo**: área empilhada de previdência + IR. Conforme o salário sobe, a fatia do IR cresce mais rápido (progressividade).
- **Ganho acumulado com triênios** e **Patrimônio de carreira** (líquido somado ano a ano) dimensionam o tamanho financeiro da carreira.

### Passo 5 — Compare decisões (aba Comparações)

- **Aderir ao RPC × conta própria**: simula o patrimônio acumulado nos dois caminhos. O RPC recebe **contrapartida do Estado**; por conta própria você fica só com a sua parte. Ajuste o rendimento do fundo, o rendimento próprio, a contrapartida e o horizonte. A ferramenta calcula a **taxa que você precisaria render sozinho para empatar** com o RPC.
- **Líquido mensal: adesão × não adesão** — mostra que **aderir reduz o líquido de hoje** (a contribuição vira fundo), com o custo mensal explicitado.
- **Líquido por classe** e **Impacto marginal** de cada parâmetro (quanto cada item soma ou retira do seu líquido).

### Passo 6 — Salve e compartilhe

- **🔗 Compartilhar** gera um link que carrega exatamente o seu cenário.
- **↧ Exportar PDF** abre a impressão (salve como PDF).
- **⚙ Variáveis globais** permite editar tetos, alíquotas e reajuste, caso a legislação mude.
- **↺ Resetar** volta aos valores padrão. Seus parâmetros ficam salvos no navegador entre as visitas.

---

## 🧮 Como funciona o cálculo (resumo)

A remuneração líquida é montada nesta ordem (a "cascata"):

1. **Bruto** = (Vencimento Base + Produtividade) × fator de reajuste × fator de triênio
2. **Abate-teto** = excedente acima do teto do STF (subtraído do bruto)
3. **RPPS (RioPrev)** = 14% sobre o bruto, **limitado ao teto do RGPS** (para o novo entrante, conforme a EC 103/2019 — aderindo ou não ao RPC)
4. **RPC (RJPrev)** = alíquota (5,5%–8,5%) sobre o que **excede** o teto do RGPS, **apenas se houver adesão**
5. **Base de IR** = bruto − previdências (+ PPE, se marcada como tributada)
6. **IRPF** = tabela progressiva mensal de 2026 (método da parcela a deduzir)
7. **Líquido** = bruto − previdências − IR + alimentação + transporte + PPE + moradia

**Triênios:** 1º triênio +10%, demais +5% cada, com teto de 60%.

> Os valores-base (vencimento, produtividade por classe), tetos, alíquotas e a tabela do IRRF estão documentados no app (aba "Como usar" → "Premissas & fórmulas") e na planilha-fonte do projeto.

---

## 📋 Premissas e simplificações adotadas

Para manter a ferramenta **simples, viável e didática**, foram adotadas as seguintes premissas. Elas são **escolhas conscientes de modelagem**, não erros — mas você precisa conhecê-las ao interpretar os números:

| Tema | Premissa adotada |
|---|---|
| **Inflação** | **Desconsiderada.** Todos os valores são nominais; não há correção monetária ao longo do tempo nas projeções. |
| **Imposto de Renda** | Incide sobre a base **bruto − previdências**, pela **tabela progressiva mensal de 2026** (parcela a deduzir). **Sem dependentes** e sem o desconto simplificado. A PPE, por padrão, **não** entra na base (ajustável). |
| **Previdência (RPPS)** | Contribuição de **14% limitada ao teto do RGPS** para o novo entrante (EC 103/2019), aderindo ou não ao RPC. O modelo antigo (14% sobre todo o bruto sem adesão) fica disponível como *toggle* avançado. |
| **Previdência complementar (RPC)** | Modelada como contribuição opcional sobre o que excede o teto do RGPS, com contrapartida do Estado. |
| **Investimentos (RPC × conta própria)** | Usa uma **taxa de retorno anual única**. **Não modela composição de carteira**, alocação por ativos, liquidez, risco, nem tributação sobre os rendimentos do investimento por conta própria. |
| **Verbas indenizatórias e PPE** | Tratadas como **estimativas**; valores médios mensais editáveis. Não sofrem IR nem previdência e não entram no teto. |
| **Triênios** | Modelados como 1º +10%, demais +5%, teto de 60%. Progressão de classe assumida a cada 3 anos nas projeções. |
| **13º e férias** | Aparecem como **estimativa aproximada** (≈ líquido ×12 + 13º + ⅓ de férias), não como cálculo mês a mês detalhado. |
| **Caráter geral** | É uma **estimativa de apoio à decisão**. **Não substitui** o contracheque oficial nem a legislação vigente. |

---

## 🗒️ Histórico de versões (Changelog)

O versionamento segue o padrão **[SemVer](https://semver.org/lang/pt-BR/)** (`MAJOR.MINOR.PATCH`). As entradas mais recentes ficam no topo.

### v2.0.0 — 30/06/2026 · *atual* 🎉
**Reescrita como app standalone e correção do modelo previdenciário.**
- ♻️ **Reescrita completa** para um app **standalone de 1 arquivo** (HTML + JavaScript puro + SVG), **sem frameworks nem CDN** — abre offline por duplo clique e é publicável em qualquer lugar.
- 🛠️ **Correção do modelo RPPS/RPC**: o RPPS passa a ser **sempre limitado ao teto do RGPS** (aderindo ou não ao RPC), conforme a EC 103/2019. Aderir ao RPC agora **reduz** o líquido de hoje (contribuição complementar com contrapartida), em vez de aumentá-lo. O comportamento antigo da planilha ficou preservado como *toggle* avançado.
- ✨ **Camada de polish**: animação de contagem no valor principal, acentos e *hover* nos cartões/KPIs, brilho no cabeçalho.
- 📱 **Painel de parâmetros colapsável no celular**, priorizando o resultado na tela.
- 📊 Gráfico de saturação passa a mostrar **bruto efetivo + nominal + teto**, evidenciando o abate-teto.

### v1.1.0
**Premissas revisáveis e comparações mais realistas.**
- 🔀 Premissas discutíveis viram ***toggles*** (triênio sobre produtividade, PPE tributada), com padrão igual à planilha — sem correção silenciosa.
- 🏠 **Auxílio moradia unificado** em um único controle (antes havia dois controles que se anulavam).
- 📈 **Comparação RPC × conta própria** simulada **mês a mês**, com contribuição que cresce ao longo da carreira.

### v1.0.0
**Primeiro app standalone.**
- 🚀 Primeira versão em arquivo único (HTML + JS puro + SVG) com as abas **Calculadora**, **Projeção no tempo**, **Comparações** e **Como usar**.
- 🎯 **4 cenários padrão**, validados contra a planilha-fonte (diferença R$ 0,00).
- 💾 Persistência no navegador, link de compartilhamento e exportação em PDF.

### v0.1.0 — *protótipo*
- 🧪 Protótipo inicial da calculadora (formato Claude Design / React), usado para validar o modelo de cálculo contra a planilha. Preservado no histórico, não mais em uso.

> **Para mantenedores:** ao lançar uma nova versão, adicione uma entrada no topo desta seção, incremente o número conforme o SemVer (correção → PATCH, novidade compatível → MINOR, mudança que altera resultados/comportamento → MAJOR) e descreva o que mudou.

---

## 🧭 Roadmap — próximos passos

Ideias mapeadas para versões futuras (sujeitas a prioridade):

- [ ] **Renda na aposentadoria** estimada (converter o saldo do RPC em renda mensal).
- [ ] **VPL** da decisão do RPC (trazer valores a valor presente, descontando uma taxa real).
- [ ] **"Custo do teto"** acumulado como KPI dedicado.
- [ ] **Dependentes** e **desconto simplificado** no cálculo do IR.
- [ ] **Comparação entre carreiras/órgãos** (ex.: AFRE-RJ × Receita Federal).

Tem uma sugestão? Veja [como contribuir](#-como-contribuir--sugerir-melhorias). 🙌

---

## 📂 Estrutura do repositório

| Arquivo | Descrição |
|---|---|
| **`Calculadora-Remuneracao-AFRE-RJ.html`** | **A ferramenta.** App standalone — é o único arquivo necessário para usar. |
| `RESUMO-PROJETO.md` | Documento técnico de contexto: modelo de cálculo, validações e log de decisões. |
| `Remuneracao_AFRE-RJ.xlsx` | Planilha-fonte que serviu de "verdade" do modelo. |
| `README.md` | Este arquivo. |

---

## 🤝 Como contribuir / sugerir melhorias

Encontrou um valor que não bate, um cenário não previsto, ou tem uma ideia para melhorar a ferramenta?

> **Mande sua sugestão ou correção pelo Instagram: [📸 @daviteixeira.concursos](https://instagram.com/daviteixeira.concursos)**

Toda crítica construtiva é bem-vinda — a ferramenta foi idealizada com a melhor das intenções e melhora com a colaboração de quem a usa. 💙

---

## 👤 Autoria e licença

**Desenvolvido por Davi Teixeira** — criador de conteúdo para concursos · 📸 [@daviteixeira.concursos](https://instagram.com/daviteixeira.concursos)

© 2026 Davi Teixeira. **Uso livre para fins educacionais e de estudo**, desde que **mantidos os créditos ao autor e o link do Instagram**. Para **reuso, adaptação ou redistribuição** (especialmente com fins comerciais), entre em contato pelo Instagram acima.

---

<p align="center">
  <sub>⚠️ Estimativa de apoio à decisão · base 2026 · não substitui o contracheque oficial nem a legislação vigente.<br>
  Feito com 💙 para os futuros Auditores Fiscais da SEFAZ-RJ.</sub>
</p>
