---
name: template-relatorio-numerologia-astrologia
description: Gera um dossiê pessoal em HTML (formato A4, pronto pra imprimir/exportar como PDF) combinando numerologia cabalística (mapa essencial, ciclos, desafios, triângulos e arcanos, numerologia de marca/empresa, laboratório de nomes) e astrologia (mapa astral natal e revolução solar), com um design autoral "matcha moderno" — cream, verde matcha, argila, tipografia editorial (Fraunces + Inter + Space Mono), toques artesanais de washi tape e selo. Use esta skill sempre que o usuário pedir um relatório, dossiê, laudo ou leitura de numerologia e/ou astrologia para uma pessoa (ou para o nome de uma marca/empresa), mesmo que ele não mencione "template" ou "HTML" explicitamente — por exemplo "faça a numerologia do nome dela", "analisa esse mapa astral", "monta um relatório de revolução solar", "preciso de um laudo numerológico completo".
---
 
# Relatório de Numerologia + Astrologia
 
Gera um dossiê autoral, em HTML de 15 páginas A4, cruzando numerologia cabalística e astrologia
(mapa natal + revolução solar) para uma pessoa — com opção de incluir a numerologia de uma marca/empresa
dela e um laboratório de testes de nome.
 
## Quando usar
 
Use sempre que o pedido envolver **calcular ou interpretar** números numerológicos (motivação, impressão,
expressão, destino, missão, arcanos, ciclos, desafios) e/ou **interpretar um mapa astral** (natal e/ou
revolução solar) para entregar como um documento/relatório visual — não apenas responder em texto corrido no
chat. Também use quando o usuário pedir para "testar nomes", "achar o melhor nome pra marca" com base em
numerologia, ou pedir a leitura de uma revolução solar.
 
Se o usuário pedir só uma resposta rápida e conversacional (ex: "o que significa o número 7?"), **não** use
esta skill — responda direto no chat. Reserve a skill para quando o pedido pede um documento completo, com
cara de dossiê, pra guardar ou compartilhar.
 
## Arquivo base
 
`assets/template.html` — o template completo, com o CSS já pronto (não precisa reescrever) e 15 `<div class="page">`,
cada uma com tokens `{{ASSIM}}` no lugar dos dados reais e comentários indicando o que vai em cada um.
 
**Fluxo de trabalho:**
 
1. Copie `assets/template.html` para a área de trabalho (`/home/claude/`) com um nome novo por cliente.
2. Reúna os dados necessários (ver checklist abaixo). Se faltar algo essencial (nome completo, data de
   nascimento, hora e cidade de nascimento para o mapa astral), pergunte antes de calcular — não invente
   posições planetárias.
3. Calcule os números de numerologia cabalística e, se o usuário já forneceu as posições planetárias
   (ex: exportadas do astro-seek ou similar), converta graus para casas comparando com as cúspides fornecidas.
   Se o usuário não forneceu o mapa astral, você pode calculá-lo você mesma se tiver os dados de nascimento
   completos (data, hora exata, cidade) — ou pedir que ela cole os dados de um app/site de mapa astral.
4. Substitua **todos** os tokens `{{...}}` pelo conteúdo real, com interpretações escritas por você (tom de
   "amiga que estuda numerologia e astrologia há décadas" — caloroso, direto, sem jargão desnecessário).
   Nunca deixe um token sem substituir no arquivo final.
5. Páginas 7, 8 e 9 (numerologia de marca, laboratório de nomes, identidade recomendada) são **opcionais** —
   remova as três `<div class="page">` inteiras se o cliente não tiver marca/empresa ou não estiver testando
   nomes. Renumere `.pagenum` das páginas seguintes se remover alguma.
6. Salve o arquivo final em `/mnt/user-data/outputs/` e entregue com `present_files`.
## Checklist de dados necessários
 
**Sempre:**
- Nome completo de nascimento + apelidos/variações relevantes
- Data de nascimento
- Cálculos numerológicos: motivação, impressão, expressão, destino, missão, talento oculto, número
  psíquico, arcano atual (+ vigência), ano/mês/dia pessoal, dias favoráveis, ciclos de vida, momentos
  decisivos, desafios (1º, 2º, principal), lições e dívidas cármicas, tendências ocultas, resposta
  subconsciente, harmonia conjugal, números harmônicos, os 4 triângulos (pessoal, vida, social, destino)
  com seus arcanos.
**Se houver mapa astral:**
- Data, hora exata e cidade de nascimento
- Posições de todos os planetas/pontos (signo + grau) e cúspides das 6 primeiras casas (as outras 6 se
  deduzem por oposição/espelhamento, salvo Placidus com muita distorção latitudinal — nesse caso peça a
  lista completa das 12)
- Para a revolução solar: mesma lista de planetas/pontos + ASC + MC do ano em questão
**Se houver marca/empresa:**
- Razão social completa e nome fantasia
- Cálculos de motivação/impressão/expressão para ambos, destino, ciclo de vida atual, desafio e momento
  decisivo da empresa
**Se houver laboratório de nomes:**
- Cada variação testada (nome civil, apelidos, assinaturas, grafias alternativas) com seus respectivos
  motivação/impressão/expressão e arcano
## Como interpretar (não só listar números)
 
Para cada bloco, não se limite a definir o número — conecte com o restante do mapa:
- Aponte quando o mesmo tema aparece em múltiplos lugares (ex: destino numerológico e um planeta natal
  contando a mesma história) — isso é o tipo de "achado" que dá peso ao relatório (ver `.callout` no
  template, feito exatamente pra esses insights de conexão).
- Nas casas astrológicas, sempre dê **potencial e dificuldade** juntos — nunca só o lado bonito.
- Na revolução solar, leia por *cluster de casas* (quais casas concentram mais planetas), não planeta a
  planeta isoladamente — é isso que torna a leitura "profissional" em vez de uma lista de posições.
- Feche a página 15 amarrando numerologia + astrologia num único fio narrativo, não dois resumos separados.
## Como trocar a paleta (se pedirem outra estética)
 
Todas as cores vivem em `:root` no topo do `<style>`. Para uma variação da mesma estética "matcha moderno",
ajuste só os valores das variáveis (`--matcha-500`, `--clay`, `--gold`, `--lilac` etc.) — a estrutura de
cards, tabelas e tipografia (Fraunces/Inter/Space Mono/Caveat) não precisa mudar. Para uma estética
totalmente diferente, é melhor recriar o CSS do zero em vez de forçar o sistema atual.
 
## Coisas a não fazer
 
- Não invente posições planetárias ou números numerológicos — sempre calcule a partir dos dados fornecidos
  ou peça o que faltar.
- Não inclua informações sobre terceiros (família, amigos, vínculos alheios ao cliente) nas interpretações
  a menos que o próprio cliente as tenha trazido para o contexto da leitura.
- Não deixe tokens `{{...}}` sem preencher no HTML final.
- Não remova o aviso de rodapé lembrando que os mapas são espelhos simbólicos, não roteiros fechados —
  é uma boa prática ética manter esse disclaimer em qualquer leitura de numerologia/astrologia.
