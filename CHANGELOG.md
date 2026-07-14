# Histórico de versões

Versionamento [SemVer](https://semver.org/lang/pt-BR/) (`MAJOR.MINOR.PATCH`). Entradas mais recentes no topo.

A regra de incremento neste projeto tem uma particularidade: **MAJOR** vale tanto para mudança que altera resultados quanto para redesenho completo da interface. **O número do líquido é sagrado** — o motor (bruto, previdências e IRPF) reproduz a planilha-fonte com diferença de R$ 0,00 nos 4 cenários padrão, e nenhuma versão pode quebrar isso sem que a mudança seja intencional, documentada e revalidada.

Uma precisão importante, porque a frase "paridade R$ 0,00" circulava sem ela: a paridade vale no **motor**, até a linha "total antes das indenizatórias" (R$ 18.767,77 no cenário 1). Ela **não** vale no líquido final. A planilha fecha o cenário 1 em R$ 27.498,54; o app mostra R$ 30.072,38. A diferença de R$ 2.573,84 é a reindexação de alimentação e transporte à UFIR-RJ pela Res. SEFAZ 895/2026 — a planilha é anterior à norma. Desde a v3.0.1 isso é uma asserção executável (`tests/oracle.js`), não uma promessa em prosa.

---

## v3.1.1 — 14/07/2026 · *atual*

**Licenciamento, avisos legais e uma errata que já durava três versões.**

Nenhuma mudança no cálculo. Os 4 cenários seguem em R$ 30.072,38 / 33.711,78 / 32.175,95 / 36.236,07.

**Licença**
- ⚖️ **`LICENSE.md`** — o projeto não tinha licença. Agora tem: licença proprietária de código à vista, em português, ancorada na Lei nº 9.609/1998. Concede uso educacional e redistribuição do arquivo **íntegro e inalterado**; veda derivados, remoção de créditos e uso comercial. Traz o que faltava e mais importava: **exclusão de garantia**, **limitação de responsabilidade** (a ferramenta influencia a decisão de aderir ou não ao RPC — e quem decide é o usuário), **negativa de vínculo institucional** e **cláusula de privacidade**.
- 📄 **`NOTICE.md`** — avisos de terceiros. `legacy/prototipo-dc/` fica **expressamente fora** da licença: o `support.js` é um *runtime* empacotado de terceiros, sem aviso de copyright ou licença, cuja titularidade não foi determinada. Não deve ser publicado.
- 📁 **`fontes/README.md`** — procedência de cada norma e de cada planilha. Registra que a "planilha-fonte" **não é documento oficial da SEFAZ-RJ**, e alerta que o `.docx` de normativos carrega, nos metadados, o nome de quem o redigiu.

**Errata — a alegação de "zero dependências" era falsa**
- 🐛 O app carrega **Google Fonts de CDN** (3 requisições a cada abertura, entregando IP e User-Agent do usuário ao Google). Mesmo assim, o README (`:45`, `:257`) e o `docs/RESUMO-PROJETO.md` (`:23`) afirmavam "sem dependências" / "zero dependências"; a entrada da v2.0.0 deste changelog diz "sem frameworks nem CDN". A afirmação nasceu verdadeira na v2.0.0 e deixou de ser na v3.0.0, quando a tipografia nova entrou — e ninguém percebeu.
- ✅ Corrigido no README e no RESUMO-PROJETO. **A entrada histórica da v2.0.0 fica como está**: changelog é registro, não se reescreve. Esta errata é o conserto.
- 🔒 A `LICENSE.md` declara a transmissão ao Google de forma expressa, em vez de prometer uma privacidade que o código não entrega. Uma licença que afirma o falso não blinda: expõe.

**Aplicativo**
- ⚖️ **Rodapé ganhou a negativa de vínculo** — "não é produto da SEFAZ-RJ, não tem endosso de órgão público" —, a promessa de privacidade (com a ressalva do Google Fonts) e o link para a licença. É a superfície que o usuário de fato lê; o aviso pertence a ela, não só a um `.md`.
- 🐛 O tutorial chamava a base de dados de "planilha **oficial**" — única expressão do app que insinuava origem institucional, e falsa: a planilha é de trabalho. Agora diz "planilha-fonte", como o resto da documentação sempre disse.

---

## v3.1.0 — 14/07/2026

**Gratificação de presença por participação em órgão de deliberação coletiva (Decreto 50.369/2026).**

Nenhuma mudança no líquido padrão: a verba nasce desligada, e os 4 cenários seguem em R$ 30.072,38 / 33.711,78 / 32.175,95 / 36.236,07. Os 55 cenários da v3.0.1 foram comparados **id a id** contra o baseline guardado antes da mudança — **zero diferenças**.

**Nova verba**
- ➕ Novo parâmetro **"Órgão de deliberação coletiva"**: **Conselho de Contribuintes / Representantes da Fazenda** (250 UFIR-RJ por sessão realizada, até **14 sessões/mês** → R$ 1.240,10 por sessão, R$ 17.361,40 no teto) e **Junta de Revisão Fiscal** (100 UFIR-RJ, até **12/mês** → R$ 496,04 por sessão, R$ 5.952,48 no teto). O Decreto 50.369/2026 deu redação nova ao caput do art. 1º do Decreto 12.936/1989 e ao do Decreto 41.904/2009.
- 🎖️ **Acréscimo de representação** por cargo no colegiado (parágrafo único de cada decreto, **não revogado**): no Conselho, Presidente +40%, Presidentes de Câmara e Representante Geral da Fazenda +20%, Secretário-Geral +10%, Secretários de Câmara +5%; na Junta, Presidente de Turma +20% e Secretário de Turma +5%.
- 🧾 **Indenizatória**, como a função gratificada: entra no líquido **depois do IR**, sem previdência, fora do abate-teto e da base de 13º/férias.
- ⚙️ Os valores por sessão (250 e 100 UFIR) viraram **variáveis globais editáveis** no drawer, como a moradia — um decreto novo muda o número sem tocar no código.

**Modelagem**
- ⚖️ A vedação do **art. 170 do Estatuto** (participar de mais de um órgão de deliberação coletiva) é enforçada **pelo modelo de dados**, não por validação: o órgão é um `<select>` com enum, e não há estado capaz de representar dois colegiados ao mesmo tempo. Não há regra a esquecer. É o mesmo idioma da função gratificada, que também é "só uma por vez".
- 🤝 O **art. 171** (acumulável com quaisquer outras vantagens) não pede código nenhum — mas ganhou teste: Conselho + função Tipo I somam, sem trava.
- 🔒 O clamp de sessões mora **dentro do `calc()`** (como o de dependentes do auxílio-educação), nunca escrevendo de volta no `state`. Normalizar no `refresh()` faria o link `#s=` divergir do estado persistido — e o canário de semeadura do harness existe justamente para pegar isso.

**Testes**
- 🎯 Nova suíte de motor com os valores **calculados à mão a partir do decreto** (o oráculo e o `unit.js` não podem tirar número nenhum do app). Varredura de invariantes ampliada para **41.472 combinações**, com duas monotonicidades novas: mais sessões nunca reduz o líquido, e o teto do órgão satura; cargo com representação nunca paga menos que o membro.
- 🧪 **19 cenários novos** (74 no total), incluindo os clamps, o cargo órfão (um "Presidente do Conselho" com a Junta selecionada) e o órgão fora da tabela.
- 🔒 Duas sabotagens novas no auto-teste (adulterar o valor da sessão e o teto da Junta) — ambas passam pelo contrato forjado e só o oráculo pega.
- 🐛 **Correção latente no auto-teste**: a mutação `chart-sem-position` casava com um CSS que não existia mais desde a v3.0.0. Ela só continuava "funcionando" porque o golden era a v2.2.0; na promoção, teria virado um auto-teste inválido silencioso.
- 📌 **Golden promovido da v2.2.0 para a v3.1.0.** Foi a primeira alteração intencional do motor desde que ele foi congelado — o redesenho da v3.0.0 passou porque não tocou numa vírgula do `calc()`. A ordem seguida: escrever a Camada 0 **antes** do app (ela afere contra a lei, não contra o golden), implementar, e só então promover, provando o zero-diff nos 55 cenários antigos.

---

## v3.0.1 — 13/07/2026

**Validação do cálculo contra as fontes, e o primeiro teste que pode reprovar uma fórmula errada.**

Nenhuma mudança no líquido: os 4 cenários seguem em R$ 30.072,38 / 33.711,78 / 32.175,95 / 36.236,07.

**Testes — nova Camada 0 (motor, sem browser, ~200ms)**
- 🎯 `tests/oracle.js` — os 4 cenários ancorados nas **células da planilha** e nas normas, transcritos à mão. Até agora nenhum teste lia `fontes/`: o baseline dos 55 cenários foi gerado rodando o próprio código, então provava imutabilidade, nunca correção. Uma fórmula errada desde o início passaria verde para sempre.
- 🎯 `tests/unit.js` — 160 asserções em ponto flutuante sobre o motor (IRRF nas 5 fronteiras de faixa, triênio contra a tabela de lookup da planilha, previdência nos 4 ramos, abate-teto, auxílios e seus limites, PPE, função gratificada, `fvSchedule` contra a fórmula fechada da anuidade). O harness só comparava strings já arredondadas do DOM — um erro de centavos se escondia no `toLocaleString`.
- 🎯 `tests/invariants.js` — 6.912 combinações varridas: o bruto nunca passa do teto do STF, o IR nunca excede a base, nenhuma rubrica fica negativa, mais tempo de serviço nunca reduz o líquido.
- 🔒 `tests/self-test.js` — 5 sabotagens novas que corrompem o app **e regeram o golden junto**. O contrato forjado passa; só o oráculo pega. É a prova de que a Camada 0 não é redundante com o congelamento.
- 🧰 `tests/lib/engine.js` — extrai o núcleo da IIFE via `sliceSymbol` e roda em `node:vm`. Dá acesso ao float, sem browser e sem tocar no arquivo do app.

**Correção**
- 🐛 **Auxílio negativo descontava do contracheque.** `saudeUfir`, `educUfir` e `ppeValue` não tinham piso zero (só `educDeps` tinha). Inalcançável pelos sliders (`min="0"`), mas alcançável por link `#s=` montado à mão e por `localStorage` — que é justamente por onde o `state` entra. Um link hostil exibia "auxílio-saúde: −R$ 496,04". Saneado na fronteira (`sanitizeState()`, logo após `loadState()`), sem tocar em nenhum símbolo do núcleo congelado.

**Documentação**
- 📝 A frase "paridade R$ 0,00 com a planilha" era **falsa como estava escrita** — ver a nota no topo deste arquivo. Corrigida no README, no CHANGELOG e na saída do `run-all.js`.

---

## v3.0.0 — 13/07/2026 🎉

**Redesenho completo da interface, modo escuro e paleta reancorada na identidade original.**

Nenhuma mudança no cálculo. Os 4 cenários padrão continuam idênticos à planilha no motor (**diferença R$ 0,00** até "total antes das indenizatórias"), revalidados pelo harness de testes.

**Interface**
- 🎛️ **Régua dos tetos no hero** — mostra onde o bruto do cargo cai entre o teto do RGPS (onde o RPPS para) e o teto do STF (onde o abate começa). Nenhuma tela do app mostrava isso antes.
- 📊 **Cascata horizontal** ("do bruto ao líquido") — com o eixo deitado, cada rubrica cabe por extenso e a leitura vira a da folha de pagamento.
- 🌙 **Modo escuro**, seguindo o sistema (`prefers-color-scheme`) e alternável no cabeçalho. A preferência é guardada em `localStorage` (`afre_theme`), separada do estado do cálculo.
- 📱 **Acordeão de parâmetros no mobile**, mantendo o líquido à vista enquanto se mexe nos controles.
- 🔤 Tipografia nova: **Bricolage Grotesque** (títulos) + **IBM Plex Sans** (corpo) + **IBM Plex Mono** (números, tabulares).
- 📐 Sistema de tokens completo (cor, espaçamento, tipografia, raio, sombra) — antes só havia tokens de cor.

**Cor**
- 🎨 **Paleta reancorada no original**: navy `#0A2E57` + verde `#0E7A4E`. O verde continua sendo a cor de ação (chip de cenário ativo, Exportar PDF, sublinhado da aba, slider) *e* a cor do "positivo" — no original ele acumula os dois papéis, e isso é a identidade.
- 🔵 Azul `#1769C4` reservado para a série **bruto** dos gráficos: com o verde significando ação e positivo, o bruto precisava de matiz própria para não virar mais uma barra verde.
- ♿ **Correção de contraste**: texto branco sobre o acento claro do modo escuro dava 3,3:1 (o mínimo é 4,5:1). Novo token `--on-brand` inverte a tinta no escuro — 6,1:1.
- 🎯 Séries dos gráficos validadas nos dois temas contra as seis checagens de paleta (banda de luminosidade, croma, separação para daltonismo e contraste com a superfície).

**Gráficos**
- 📉 **Deduções ao longo do tempo** — a área empilhada cobria a grade (preenchimento em 88%). Agora em 55%, com filete de superfície entre as camadas: quem carrega a leitura é o traço do topo, não o bloco de cor.
- 📈 **Ganho com triênios** deixou de degenerar quando o toggle está desligado (a curva achatava no zero e o eixo passava a medir de R$ 0 a R$ 1). Agora exibe um estado vazio que nomeia a ação: *"Ligue Triênios / ADF no painel para ver o ganho acumulado."*
- ⚡ A revelação dos gráficos passou a animar `transform` em vez de `width`.

**Projeto**
- 🧪 **Harness de testes** (`tests/`) — três camadas: contrato estático (ids, ganchos `data-*`, núcleo de cálculo congelado), paridade de motor (55 cenários em Chrome headless, tolerância zero) e fiação (aciona os 54 controles e detecta chave-fantasma). Zero dependências.
- 📦 **Controle de versão** (git) e reorganização da pasta: `legacy/`, `docs/`, `fontes/`.

---

## v2.2.0 — 10/07/2026

**UFIR-RJ como variável global, auxílios saúde e educação (Res. SEFAZ 895/2026) e reindexação das verbas indenizatórias.**
- ➕ Nova **variável global UFIR-RJ** (2026 = **R$ 4,9604**, Res. SEFAZ nº 849/2025), editável no drawer, que passa a indexar as verbas.
- 🩺 Novo **Auxílio-Saúde** (Res. SEFAZ nº 895/2026): reembolso de até **300 UFIR-RJ/mês** (≈ R$ 1.488,12), **global** (independe de dependentes), ajustável por comprovação — padrão no teto. Indenizatório, extra-teto, sem IR nem previdência.
- 🎓 Novo **Auxílio-Educação** (Res. SEFAZ nº 895/2026): reembolso de até **500 UFIR-RJ por dependente/mês** (≈ R$ 2.480,20), limitado a **3 dependentes**, ajustável por comprovação — padrão no teto. Mesma natureza indenizatória.
- 🔄 **Alimentação, transporte e moradia reindexados à UFIR-RJ**: alimentação **450 UFIR** (R$ 2.232,18), transporte **650 UFIR** (R$ 3.224,26) e moradia **1.500 UFIR** (R$ 7.440,60). Mudar a UFIR recalcula todas de uma vez. *(Isso eleva o líquido dos 4 cenários padrão em +R$ 2.573,84 vs. a v2.1.0 — atualização legal, não regressão.)*
- 🧾 **Nota didática do ADF**: para o novo auditor (ingresso após 06/10/2021), o triênio tradicional foi extinto pela LC 194/2021 e substituído pelo **Adicional de Desenvolvimento Funcional — ADF** (LC 230/2026 + Decreto 50.356/2026), com o **mesmo cálculo** já modelado (1º +10%, demais +5%, teto 60%), porém condicionado a desempenho/capacitação/disciplina. Sem mudança no cálculo.
- ✅ **Sem regressão no núcleo**: os auxílios entram como acréscimo indenizatório no fim da cascata (como a função gratificada), sem tocar em IR, previdência, abate-teto nem na base de 13º/férias.

## v2.1.0 — 30/06/2026

**Função gratificada de chefia/assessoramento/direção (Resolução SEFAZ 874/2026).**
- ➕ Novo parâmetro **"Função de chefia / assessoramento / direção"** no painel: seletor dos **4 tipos** da Resolução SEFAZ nº 874/2026 (regulamenta o art. 8º da LC nº 226/2025), cada um aplicando seu percentual do teto do STF — **I 30%, II 27%, III 23,5%, IV 20%**.
- 🧾 Modelada como parcela **extra-teto e indenizatória** (sem IR, sem previdência, fora do abate-teto) e **não acumulável** entre si.
- ✅ **Sem regressão**: os 4 cenários padrão continuam idênticos à planilha-fonte (diferença R$ 0,00).

## v2.0.0 — 30/06/2026

**Reescrita como app standalone e correção do modelo previdenciário.**
- ♻️ **Reescrita completa** para um app **standalone de 1 arquivo** (HTML + JavaScript puro + SVG), **sem frameworks nem CDN** — abre offline por duplo clique e é publicável em qualquer lugar.
- 🛠️ **Correção do modelo RPPS/RPC**: o RPPS passa a ser **sempre limitado ao teto do RGPS** (aderindo ou não ao RPC), conforme a EC 103/2019. Aderir ao RPC agora **reduz** o líquido de hoje (contribuição complementar com contrapartida), em vez de aumentá-lo. O comportamento antigo da planilha ficou preservado como *toggle* avançado.
- ✨ **Camada de polish**: animação de contagem no valor principal, acentos e *hover* nos cartões/KPIs, brilho no cabeçalho.
- 📱 **Painel de parâmetros colapsável no celular**, priorizando o resultado na tela.
- 📊 Gráfico de saturação passa a mostrar **bruto efetivo + nominal + teto**, evidenciando o abate-teto.

## v1.1.0

**Premissas revisáveis e comparações mais realistas.**
- 🔀 Premissas discutíveis viram ***toggles*** (triênio sobre produtividade, PPE tributada), com padrão igual à planilha — sem correção silenciosa.
- 🏠 **Auxílio moradia unificado** em um único controle (antes havia dois controles que se anulavam).
- 📈 **Comparação RPC × conta própria** simulada **mês a mês**, com contribuição que cresce ao longo da carreira.

## v1.0.0

**Primeiro app standalone.**
- 🚀 Primeira versão em arquivo único (HTML + JS puro + SVG) com as abas **Calculadora**, **Projeção no tempo**, **Comparações** e **Como usar**.
- 🎯 **4 cenários padrão**, validados contra a planilha-fonte (diferença R$ 0,00).
- 💾 Persistência no navegador, link de compartilhamento e exportação em PDF.

## v0.1.0 — *protótipo*

- 🧪 Protótipo inicial da calculadora (formato Claude Design / React), usado para validar o modelo de cálculo contra a planilha. Preservado em `legacy/prototipo-dc/`, não mais em uso.

---

## Para mantenedores

Ao lançar uma versão:

1. **Rode o harness** — `node tests/run-all.js "Calculadora-Remuneracao-AFRE-RJ.html"`. Exit 0 é obrigatório. Se a paridade mudar de propósito (atualização legal, como na v2.2.0), diga isso **explicitamente** na entrada do changelog, com o delta em reais.
2. **Arquive a versão anterior** em `legacy/vX.Y.Z-<nome>.html` antes de sobrescrever o app.
3. **Incremente o número**: correção → PATCH · novidade compatível → MINOR · mudança de resultado ou redesenho completo → MAJOR.
4. Adicione a entrada no topo e mova o marcador *atual*.

### Se a mudança tocar o núcleo de cálculo

`tests/golden/original.html` congela o texto de `DEFAULTS`, `DEFAULT_STATE`, `calc`, `buildParams`, `detectPreset` e `applyPreset`. Mexer em qualquer um deles reprova a checagem C5 do contrato, e o único jeito de destravar é **promover o golden** — que é exatamente o ataque que o `tests/README.md` descreve: "corrompi o app e regerei o golden junto". A promoção é legítima, mas só nesta ordem:

1. **Escreva a Camada 0 primeiro** (`oracle.js`/`unit.js`/`invariants.js`), com os números tirados da norma e da planilha, **nunca do app**. Ela é a única camada que não depende do golden — é ela que impede a promoção de congelar um erro. Se ela não ficar verde, **pare**.
2. `cp tests/golden/baseline.json <algum lugar seguro>` — o baseline vigente é a única testemunha de que nada regrediu.
3. `cp <app> tests/golden/original.html` e recalcule `tests/golden/source.sha256`.
4. `node tests/contract.js <app> --update` e depois `node tests/gen-baseline.js`.
5. **Prove o zero-diff**: compare, cenário a cenário e id a id, o baseline novo contra o guardado. Os textos didáticos (`glos`, `premissas`, `tutSteps`, `chartGuide`) são prosa e podem mudar; **qualquer outro dígito que se mexa é regressão**. Uma verba nova, desligada por padrão, tem de sair com zero diferenças.
6. `node tests/self-test.js` — e confira que as mutações ainda *aplicam* no golden novo (elas casam com texto literal do arquivo; um CSS reescrito as transforma em no-op silencioso).
