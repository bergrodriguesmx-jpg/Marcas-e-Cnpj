# Dashboard — Marcas, CNPJ e Responsáveis

Painel de acompanhamento e atribuição de responsáveis para uma base de 546 marcas,
organizadas em três setores: **Área** (396), **Informática** (93) e **Coffe Break** (57).

## O que a aplicação faz

- **Indicadores** — total de marcas, quantas já têm responsável (com percentual),
  quantas estão pendentes e quantos responsáveis distintos existem.
- **Gráficos** — marcas por responsável e distribuição por setor, recalculados a cada edição.
- **Tabela editável** — o campo *Responsável* e o campo *Situação*
  (Pendente / Em andamento / Concluído) são editados direto na linha e salvos na hora.
- **Busca e filtros** — busca livre por marca, CNPJ, setor ou responsável, mais filtros
  por setor, responsável (incluindo "sem responsável") e situação.
- **Importar planilha** — seleção de arquivo ou arraste de `.xlsx`, `.xls` ou `.csv` para
  qualquer ponto da tela. As colunas são detectadas pelo cabeçalho (aceita variações como
  *marca/nome/empresa*, *cnpj/documento*, *setor/segmento*, *responsavel/resp*, *situacao/status*),
  com pré-visualização e escolha entre acrescentar aos dados atuais ou substituir tudo.
- **Exportar CSV** — exporta exatamente o que está visível na tela, respeitando os filtros
  ativos, com BOM UTF-8 para abrir corretamente no Excel.
- **Restaurar padrão** — volta à base original de 546 marcas, descartando as edições.

## Tecnologias

- HTML, CSS e JavaScript sem framework nem etapa de build — uma única página estática.
- [SheetJS](https://sheetjs.com) (via CDN) para leitura de arquivos Excel; há um parser
  de CSV próprio como alternativa.
- `localStorage` para guardar as edições.
- Hospedagem estática na Netlify (`public/` publicado direto, sem build).

## Onde ficam os dados

As edições são gravadas no navegador de quem as fez, sob a chave
`dash-cnpj-responsaveis-v3`. Isso mantém a aplicação instantânea e sem login, mas
significa que cada pessoa vê a sua própria cópia — as atribuições não são compartilhadas
entre computadores ou navegadores. Para circular o resultado hoje, use **Exportar CSV**.

## Acesso à Aplicação

A aplicação é um site estático e roda diretamente no navegador, sem necessidade de instalação ou servidor local.

- **Link do site em direto:** [marcasecnpj.netlify.app](https://marcasecnpj.netlify.app)
- **Como testar localmente:** Basta dar dois cliques no ficheiro `index.html` para abri-lo em qualquer navegador.


## Possível evolução

Transformar as atribuições em dados compartilhados por toda a equipe — uma base
Postgres da Netlify com uma function de leitura e gravação no lugar do `localStorage`,
mantendo a mesma tela. A partir daí, histórico de alterações e filtro por pessoa
logada passam a ser viáveis.
