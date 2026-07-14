# Avisos de terceiros

Complemento da [`LICENSE.md`](LICENSE.md). Lista tudo o que está no repositório e **não** é obra do autor — e, portanto, **não** é coberto pela licença dele.

Existe para que ninguém precise adivinhar. O que não está documentado vira dúvida depois.

---

## 1. Fontes tipográficas — referenciadas, não redistribuídas

O aplicativo usa três famílias tipográficas, carregadas em tempo de execução a partir do serviço **Google Fonts** (`Calculadora-Remuneracao-AFRE-RJ.html`, linhas 8-10):

| Família | Titular | Licença |
|---|---|---|
| Bricolage Grotesque | Mathieu Triay e colaboradores | SIL Open Font License 1.1 |
| IBM Plex Sans | IBM Corp. | SIL Open Font License 1.1 |
| IBM Plex Mono | IBM Corp. | SIL Open Font License 1.1 |

**Nenhum arquivo de fonte é embutido ou redistribuído** por este projeto — não há `@font-face`, não há Base64. As famílias são apenas **referenciadas** por `font-family`, com *fallback* para as fontes do sistema. Em consequência, o projeto **não** assume as obrigações de redistribuição da SIL OFL.

> ⚠️ **Se um dia as fontes forem embutidas** (por exemplo, para tornar o aplicativo verdadeiramente offline), a situação muda: passará a haver redistribuição, e será **obrigatório** incluir, junto ao arquivo, o aviso de copyright de cada família e o texto integral da SIL OFL 1.1.

**Consequência de privacidade:** cada carregamento entrega **IP e User-Agent** do usuário ao Google. Está declarado na Cláusula 10 da licença e no rodapé do aplicativo. É a única transmissão de dados a terceiro em todo o projeto.

## 2. `legacy/prototipo-dc/` — FORA da licença

O protótipo original (v0.1.0), no formato Claude Design / React, contém:

- **`support.js`** — *bundle* de um *runtime* de terceiros (`dc-runtime`), gerado por ferramenta. **Não traz aviso de copyright, de licença nem de autoria.** Sua titularidade e sua licença **não foram determinadas**.
- **`prototipo.dc.html`** — carrega **React 18.3.1** e **ReactDOM** em tempo de execução, a partir do CDN `unpkg.com` (com verificação SRI). React é de titularidade da Meta Platforms, Inc., sob licença MIT. O código do React **não** é redistribuído por este projeto.
- **`thumbnail.webp`** — miniatura gerada por ferramenta.

**Nada disso é obra do autor, e nada disso é licenciado por ele.** O autor não reivindica direitos sobre esses arquivos, não autoriza sua redistribuição e **não os publica**.

A pasta permanece no repositório apenas como **memória histórica** do projeto — foi nela que o modelo de cálculo foi validado pela primeira vez contra a planilha. Ela está aposentada desde a v2.0.0.

**Não publique esta pasta.** Ao subir o projeto para qualquer lugar público, exclua `legacy/prototipo-dc/`.

## 3. `fontes/` — legislação e planilhas de trabalho

Ver [`fontes/README.md`](fontes/README.md) para a procedência arquivo a arquivo.

Em resumo: são **atos oficiais** (decretos, leis complementares, resoluções, publicações do Diário Oficial) e planilhas de trabalho usadas para ancorar o modelo de cálculo.

**Atos oficiais não são objeto de proteção autoral** no Brasil — art. 8º, IV, da Lei nº 9.610/1998: *"não são objeto de proteção como direitos autorais (...) os textos de tratados ou convenções, leis, decretos, regulamentos, decisões judiciais e demais atos oficiais"*. Estão no repositório como **fonte de verdade verificável**: quem quiser conferir a conta, confere contra a norma.

Essa pasta **não** é coberta pela licença do autor.

## 4. Ferramentas de desenvolvimento (não distribuídas)

O `skills-lock.json` registra *skills* de terceiros usadas **durante o desenvolvimento**, que **não** integram o produto e não são redistribuídas:

| Skill | Origem |
|---|---|
| `frontend-design` | `anthropics/skills` |
| `tdd` | `mattpocock/skills` |
| `web-design-guidelines` | `vercel-labs/agent-skills` |

Ficam fora do versionamento (`.gitignore`: `.agents/skills/`, `.claude/skills/`).

## 5. Marcas

**SEFAZ-RJ**, **Governo do Estado do Rio de Janeiro**, **RJPrev**, **RioPrev**, **Instagram** e demais nomes e marcas citados pertencem a seus respectivos titulares.

São mencionados em **caráter nominativo e descritivo** — para identificar o objeto do cálculo e o canal de contato do autor —, sem qualquer sugestão de vínculo, patrocínio ou endosso. Ver Cláusula 7 da licença.

O ícone do Instagram no rodapé do aplicativo é um glifo simplificado, redesenhado, usado exclusivamente como marcador do link de atribuição do autor.

---

## O que É obra do autor

Todo o resto: o aplicativo (HTML, CSS, JavaScript e SVG, escritos à mão, sem framework nem biblioteca), o conjunto de verificação em `tests/`, a documentação e as versões anteriores em `legacy/` — exceto `prototipo-dc/`.

Isso é o que a [`LICENSE.md`](LICENSE.md) cobre.
