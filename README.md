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
<br>
<p>name: Generate Datas</p>
<br>
<p>on:</p>
<p>   schedule: # execute every 12 hours</p>
<p>     - cron: "* */12 * * *"</p>
<p>   workflow_dispatch:</p>
<p>jobs:</p>
<p>   build:</p>
<p>     name: Jobs to update datas</p>
<p>     runs-on: ubuntu-latest</p>
<p>     steps:</p>
<p>       # Snake Animation</p>
<p>       - uses: Platane/snk@master</p>
<p>         id: snake-gif</p>
<p>         with:</p>
<p>         github_user_name: GabrielaZanetti</p>
<p>         svg_out_path: dist/github-contribution-grid-snake.svg</p>
<br>
<p>       - uses: crazy-max/ghaction-github-pages@v2.1.3</p>
<p>       with:</p>
<p>         target_branch: output</p>
<p>         build_dir: dist</p>
<p>       env:</p>
<p>       GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}</p>
<br>
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
