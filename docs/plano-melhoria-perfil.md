# Plano de melhoria do perfil GitHub

Documento de planejamento. Nada aqui foi executado ainda: serve para decidir o que fazer e em que ordem.

## 1. Onde estamos

Levantamento feito em 21/08/2026 sobre `Arthur-Abap/Arthur-Abap` e sobre a conta.

| Item | Situação |
| --- | --- |
| README | 9 imagens SVG empilhadas, nenhum texto markdown |
| Links clicáveis no README | 2 (LinkedIn e e-mail) |
| Repositórios públicos na conta | 1 (o próprio repo de perfil) |
| Pinned repos | vazio |
| Seguidores | 0 |
| Assets | `assets/readme/` e `assets/readme/v2/` byte-idênticos nos 7 arquivos |
| Workflow | snake diário via `Platane/snk`, publicando no branch `output` |

O trabalho visual está bem feito: paleta cyber consistente, 16 animações SMIL no hero, `title`/`desc` preenchidos, SVG autocontido sem dependência externa. O plano descrito em `refactor_plan.md` foi cumprido. Os problemas abaixo são estruturais, não de acabamento.

## 2. Diagnóstico

### 2.1 O README promete projetos que não existem publicamente

`projects.svg` apresenta Oráculo (Central de Demandas), Forge Gym MVP e Projeto IA Agentes. A conta tem um único repositório público, que é o de perfil. Quem se interessa não encontra nada.

Além disso, os cards estão desenhados dentro de um SVG, então não são clicáveis mesmo que os repositórios existissem.

### 2.2 Conteúdo dentro de imagem não é lido por ninguém

- **Busca e SEO.** Termos como SAP ABAP, QA, Omie, Next.js e Prisma estão em SVG. A busca do GitHub e os buscadores não indexam esse conteúdo. Para um recrutador filtrando por tecnologia, o perfil é texto vazio.
- **Mobile.** Os painéis usam `viewBox="0 0 1200 ..."`. Na coluna de aproximadamente 360px de um celular, a escala cai para cerca de 0,30, então o corpo de texto de 15 a 17px renderiza em torno de 5px. É ilegível, e boa parte das visitas a perfil vem de celular.
- **Acessibilidade.** Leitor de tela recebe apenas o atributo `alt`.
- **Manutenção.** Trocar uma tecnologia da stack exige editar o SVG e realinhar coordenadas.

### 2.3 Higiene do repositório

- `assets/readme/v2/` duplica exatamente `assets/readme/` (verificado com `cmp`, os 7 arquivos são idênticos).
- O README mistura os dois caminhos: usa `v2/` na maioria dos blocos e `assets/readme/divider.svg` da v1 em um deles.
- `assets/profile-hero.svg` está órfão, não é referenciado.
- `refactor_plan.md` está na raiz e aparece na listagem do repositório.

### 2.4 Posicionamento e conteúdo

- "Perfil em construção" enfraquece a apresentação. É mais forte afirmar o que já se faz.
- Idioma misturado: painéis em português, "Contribution activity" e o subtítulo do hero em inglês.
- Nenhum resultado concreto nos projetos, apenas descrição do que são.
- O e-mail é clicável mas não selecionável, por estar dentro da imagem.

## 3. Decisões tomadas

- **Formato:** híbrido. O hero permanece em SVG animado; painéis, stack e projetos passam a markdown real.
- **Idioma:** português em todo o perfil, incluindo os textos que hoje estão em inglês dentro dos SVGs.

## 4. Plano por fases

### Fase 1 — Substância

Maior impacto do conjunto e independe de qualquer decisão de design.

- [ ] Publicar o Oráculo como repositório público, com README próprio: o problema que resolve, print ou GIF, stack, como rodar.
- [ ] Publicar o Forge Gym MVP nos mesmos moldes.
- [ ] Publicar o Projeto IA Agentes nos mesmos moldes.
- [ ] Fixar os três como pinned repos. É o bloco que o GitHub renderiza logo abaixo do README e hoje está vazio.
- [ ] Preencher bio, localização e site nas configurações do perfil. A bio é indexada pela busca e aparece no hover card.

Cada README de projeto deve ter pelo menos uma linha de resultado concreto, não só descrição. Exemplo: quantas demandas o Oráculo controla, ou quanto tempo de processo manual ele elimina.

### Fase 2 — README híbrido

- [ ] Manter `hero.svg` no topo, sem alterações estruturais.
- [ ] Converter `profile-panels.svg` em uma seção markdown com os quatro blocos (foco atual, evolução, interesses, objetivo).
- [ ] Converter `tech-stack.svg` em tabela ou lista de badges, mantendo os cinco grupos existentes: Frontend e UI, Backend e Dados, ERP e Integrações, IA e Dev Tools, Qualidade e Processos.
- [ ] Converter `projects.svg` em uma tabela com nome, descrição, stack e link para cada repositório publicado na Fase 1.
- [ ] Manter os botões de LinkedIn e e-mail em SVG, e repetir o e-mail em texto para que possa ser copiado.
- [ ] Manter a seção do snake.
- [ ] Traduzir para português os textos em inglês que permanecerem nos SVGs (`contribution-activity.svg` e o subtítulo do hero).

Alternativa considerada e descartada para os projetos: quebrar `projects.svg` em três imagens, cada uma dentro de um `<a href>`. Resolveria os links, mas manteria os problemas de busca, mobile e acessibilidade.

### Fase 3 — Limpeza

- [ ] Escolher uma pasta única de assets. Promover o conteúdo de `v2/` para `assets/readme/` e apagar `v2/`, já que os arquivos são idênticos.
- [ ] Remover `assets/profile-hero.svg`.
- [ ] Mover `refactor_plan.md` para `docs/`.
- [ ] Unificar todos os caminhos de imagem do README.

### Fase 4 — Polimento

Depende da Fase 1 estar concluída.

- [ ] Reescrever a headline com posicionamento afirmativo, citando as frentes concretas: QA, automações, integrações ERP (SAP ABAP, Omie) e IA aplicada.
- [ ] Avaliar cards de stats dinâmicos. Só faz sentido depois que houver repositórios públicos com histórico, senão os números enfraquecem a página.
- [ ] Avaliar uma versão em inglês (`README.en.md`) se houver interesse em vagas remotas internacionais.

## 5. Esqueleto proposto do README

```
[hero.svg]

[btn-linkedin.svg]  [btn-email.svg]
arthurmedeiros08@gmail.com   (em texto, para copiar)

[divider.svg]

## Sobre
Parágrafo curto, com os termos técnicos em texto pesquisável.

## Foco atual
Quatro itens em lista, vindos do profile-panels.

## Stack
Cinco grupos em tabela ou badges.

## Projetos
Tabela com link real para cada repositório.

[divider.svg]

## Atividade
[snake]
```

## 6. Critérios de conclusão

O trabalho está pronto quando:

- Os três projetos existem como repositórios públicos, fixados no perfil, cada um com README próprio.
- Uma busca no GitHub por uma tecnologia da stack encontra o perfil.
- O README é legível em um celular sem zoom.
- Todo card de projeto no README leva a um repositório.
- Existe uma única pasta de assets, sem arquivos órfãos.
