## Plano de refatoracao do README

### O que sera mantido
- Estrutura geral do README com hero, botoes, divisor, paineis de perfil e projetos.
- Ideia do hero atual: terminal cyber, nome em destaque, linha de comando e nucleo visual animado girando.
- Os quatro cards de perfil e os quatro projetos ja definidos, sem adicionar informacoes novas.

### O que sera ajustado
- Refinar todos os SVGs para parecerem uma interface tecnica futurista, com menos cara de cards verdes isolados.
- Melhorar espaçamentos, hierarquia visual, contraste e consistencia entre secoes.
- Remover a stack do `profile-panels.svg` e criar/refatorar `tech-stack.svg`.

### Paleta
- Trocar o verde amarelado dominante por uma paleta Matrix/cyber fria:
  `#05070A`, `#0A0F14`, `#0E141B`, `#111820`, `#39FF14`, `#00FF85`, `#0DBF66`, `#F5F7FA`, `#A8B3C2` e `#7E8A98`.
- Evitar `#C8F135` como cor principal; quando existir, sera apenas detalhe minimo ou sera removido.

### Icones
- Padronizar os icones como line icons simples, com traco fino, sem emoji, sem clipart e sem estilos conflitantes.
- Corrigir proporcoes e alinhamento dos icones nos botoes, cards de perfil e cards de projeto.

### Stack
- Criar `assets/readme/tech-stack.svg` como painel separado.
- Organizar os chips em 5 grupos: Frontend & UI, Backend & Dados, ERP & Integracoes, IA & Dev Tools, Qualidade & Processos.
- Manter os chips especificos pedidos, sem substituir ferramentas de IA por termos genericos.

### Animacoes
- Hero: cursor piscando, nucleo girando, glow pulsando, scan line, chuva Matrix discreta, particulas e circuitos sutis.
- Botoes: brilho leve na borda, linha de luz e pulso discreto no icone.
- Divisor: brilho horizontal, pulso central e particulas.
- Paineis, stack e projetos: scan line suave, bordas com brilho controlado, particulas discretas e pulsos alternados.

### Compatibilidade GitHub README
- Usar apenas SVG inline autocontido, sem JavaScript, iframe, imagens externas, badges externos ou CSS externo.
- Manter `viewBox`, `<title>`, `<desc>`, contraste adequado e textos legiveis.
- Deixar apenas LinkedIn e e-mail como links clicaveis no README.
