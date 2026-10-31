# Instalação

1. Crie um repositório **público** chamado `amzsants` na sua conta. O nome completo será `amzsants/amzsants`. O README de perfil exige esse nome e visibilidade pública.
2. Envie todo o conteúdo deste pacote para a raiz do repositório, preservando `assets/` e `.github/workflows/snake.yml`. Atenção: `.github` é uma pasta oculta em alguns sistemas.
3. Abra **Actions → Atualizar perfil → Run workflow** na branch padrão. O envio do workflow também inicia uma execução.
4. Depois da execução, confira se as imagens substituíram os avisos iniciais em `assets/`. Não é necessário configurar GitHub Pages ou criar um token pessoal.

O workflow usa o `GITHUB_TOKEN` automático e declara apenas `contents: write`, necessário para salvar os SVGs no próprio repositório. Se a política da conta bloquear escrita ou Actions de terceiros, ajuste as configurações permitidas em **Settings → Actions → General**. Se houver proteção de branch impedindo o bot, a gravação falhará; não é necessário desativar proteção para visualizar os arquivos locais.

Atualização programada: diariamente às **03:23 de São Paulo**, equivalente a `06:23 UTC` na configuração atual. O GitHub pode atrasar execuções. Workflows agendados em repositórios públicos podem ser desativados após 60 dias sem atividade; reative em Actions se necessário.

## Arquivos e manutenção

- `README.md`: conteúdo do perfil.
- `assets/banner.svg`, `typing.svg`, `ia.svg` e `footer.svg`: identidade visual, sem fontes externas, scripts ou serviços de imagem.
- `assets/stats.svg`, `languages.svg`, `streak.svg`, `activity.svg`, `snake-dark.svg` e `snake-light.svg`: imagens atualizadas pelo workflow.
- `assets/languages-empty.svg`: estado de ausência de dados; mantenha esse arquivo.
- `.github/workflows/snake.yml`: gera todas as imagens e grava na branch padrão. Não usa branch `output`.

As imagens iniciais mostram “Aguardando primeira atualização”. Elas não representam estatísticas. Se uma dependência falhar, o workflow mantém a imagem anterior e registra um aviso no log; portanto, confira os avisos mesmo que a execução termine com sucesso. O gráfico exibe sua própria data de atualização. Outras imagens podem conter dados da última geração bem-sucedida.

Os cards extras ficam em uma seção expansível para manter o perfil mais limpo. As imagens têm fundo próprio e texto claro para continuar legíveis tanto no tema claro quanto no escuro. A cobra usa duas paletas. O texto principal acompanha o tema do GitHub. A animação de digitação é SVG local; o navegador pode mostrar apenas o texto estático se não oferecer suporte à animação. Há tratamento de preferência por movimento reduzido na digitação; a animação de cobra depende do comportamento do gerador.

## Dados e limitações

- Confirmado pelo usuário: Amoz Santos; aprendiz na função de auxiliar administrativo; uso de ferramentas de IA em geral; interesse em desenvolvimento, automação de processos e RPA; projetos privados.
- Nenhuma linguagem, marca de IA, competência específica, experiência adicional ou realização foi atribuída ao usuário.
- A API pública retornou zero repositórios públicos no momento da consulta. O card de linguagens mantém um estado neutro até haver dados públicos elegíveis. O próprio repositório de perfil é excluído do cálculo.
- O token automático não concede acesso aos demais repositórios privados da conta. Contribuições privadas anonimizadas podem aparecer no calendário conforme as configurações públicas do perfil; o workflow não publica nomes ou código desses projetos.
- O gráfico usa `contributionCalendar` do GitHub, nos últimos 31 dias incluindo o dia atual; o dia atual é parcial. Ele não equivale a um histórico de eventos nem a um registro de produtividade. O GitHub determina as datas e a elegibilidade das contribuições.
- Estatísticas gerais e linguagens: GitHub Readme Stats Action mantido por `stats-organization`. O projeto original de `anuraghazra` indica descontinuação e recomenda sucessores.
- Sequência: GitHub Readme Streak Stats, gerado localmente no runner. O endpoint público respondeu HTTP 200 durante a verificação; a geração por Action evita depender desse endpoint a cada visita.
- Activity Graph e GitHub Trophies: os endpoints públicos consultados responderam HTTP 402. O gráfico foi substituído por um SVG gerado a partir da API do GitHub. Troféus foram omitidos; a alternativa são os indicadores de atividade reais já incluídos. Não há premiações inventadas.
- O gráfico consulta o GitHub diretamente. Os cards de estatísticas e sequência ainda dependem dos respectivos geradores, dos pacotes que eles instalam e da API do GitHub; podem ocorrer limites de requisições ou falhas.
- As Actions diretas estão fixadas nos commits verificados. Para atualizar versões, revise os commits e altere as referências no workflow.

## Validação realizada

- Sintaxe XML dos SVGs e caminhos de imagem do README conferidos.
- YAML do workflow e sintaxe do Python interno analisados.
- Geração do gráfico executada com dados de teste em três cenários: todos os dias zerados, contagens variadas e falha de rede. Os testes não são dados do perfil nem foram usados nas imagens entregues.
- Banner e SVGs estáticos renderizados localmente; banner inspecionado em larguras de 960 e 360 pixels.
- Perfil público, endpoints consultados e referências das Actions verificados.
- O workflow completo não foi executado no GitHub. Não houve publicação ou alteração na conta. A renderização final pelo GitHub e a execução da cobra dependem da instalação e da primeira execução bem-sucedida.

## Referências

- Perfil README: https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme
- Estatísticas: https://github.com/stats-organization/github-readme-stats-action
- Descontinuação do projeto original: https://github.com/anuraghazra/github-readme-stats
- Sequência: https://github.com/DenverCoder1/github-readme-streak-stats
- Cobra: https://github.com/Platane/snk
- Endpoint de gráfico consultado: https://github-readme-activity-graph.vercel.app/graph?username=amzsants
- Endpoint de troféus consultado: https://github-profile-trophy.vercel.app/?username=amzsants
- Agendamentos: https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule
