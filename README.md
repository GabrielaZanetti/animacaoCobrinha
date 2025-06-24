# Animação Cobrinha
esse é o passo a passo de como fazer a animação da cobrinha que come os commits.
<br>
<p>Iniciamos no repositorio do perfil, em Actions</p>
<img src="img/actions.png" title="Actions GitHub" max-width="100%">
<br>
<p>Criamos um Workflows</p>
<img src="img/newWorkflows.png" title="New Workflows" max-width="100%">
<br>
<p>Após criar selecionamos o Simple workflow, onde configuramos ele para carregar a animação da cobrinha.</p>
<img src="img/configure.png" title="Configuração" max-width="100%">
<br>
<p>Logo em seguida escolhemos o nome e adicionamos o código</p>
<img src="img/code.png" title="new actions" max-width="100%">

```
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

<p>No código adicionamos exclusivamente o username do GitHub</p>
<img src="img/code-1.png" title="Código" max-width="100%">
<br>
<p>Em seguida clique em start commit e commita o arquivo para adicionar o arquivo no main</p>
<p>Selecione novamente o Actions e em Generate Datas estara selecionado o arquivo da cobrinha.yml</p>
<img src="img/generateDatas.png" title="Gerar Dados" max-width="100%">
<br>
<p>Cloque em run woekflow e aguarde o carregamento.</p>
<img src="img/carregando.png" title="Carregando" max-width="100%">
<img src="img/concluido.png" title="Concluído" max-width="100%">
<br>
<p>E por fim adicione no readme a seguinte linha de código:</p>
<br>
<p>![Snake animation](https://github.com/GabrielaZanetti/GabrielaZanetti/blob/output/github-contribution-grid-snake.svg)</p>
<br>
<p>Apenas mudando seu username.</p>
