## Definição geral de Versionamento Semântico (SemVer)

> Versionamento Semântico, em inglês  *“Semantic Versioning”* , é um padrão de regras para manter um acompanhamento de versões no desenvolvimento de códigos. Um modelo geral que todas as pessoas usuárias podem entender e utilizar.

Se você já lida com instalações de pacotes, frameworks e softwares de forma geral, já observou que existe uma sequência numérica que se refere à última versão atualizada.


![Captura de tela colorida em recorte, que mostra a tela inicial do site oficial do Express. Na parte superior direita da tela encontra-se uma barra de navegação com os links “Home”, “Getting Started”, “Guide”, “API reference”, “Advanced topics”. Em destaque, dentro de um quadrado vermelho, está a aba “API reference” com as opções: “5.x (beta)”, “4.x”, “3.x (deprecated)”, “2.x(deprecated)”. Abaixo da aba temos um fundo branco e a seguinte frase na cor preta:“Express 4.18.1”. Na linha abaixo a frase na cor cinza temos os seguinte texto: “Fast, unopionionated, minimalist web framework for Node.js”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem2.jpg)

Na imagem acima, temos o framework Express.js e, na aba *API reference* temos suas diferentes versões.

Cada versão possui um número diferente que, ao clicar em cada uma das versões, vemos melhorias e demais mudanças que podem diferir bastante uma das outras, maior número representa a versão mais atual - no caso 5.x (beta). O *x* indica que podemos ter qualquer número ali, o que importa é o primeiro número da sequência; já o beta está ligado ao momento de lançamento desse software (não se preocupe, veremos isso no próximo tópico).

Aqui na Alura procuramos destacar em nossas videoaulas a versão utilizada nas instalações para evitar qualquer tipo de problemas com incompatibilidade de versões e seu código não quebrar no desenvolvimento do projeto.

Esse cuidado deve fazer parte da rotina de uma pessoa desenvolvedora. [Versionar seu código](https://www.alura.com.br/artigos/comecando-com-git-aprendendo-versionar) é uma forma de acompanhar etapas e comunicar mudanças no projeto, já que constantemente estamos compartilhando códigos através de repositórios públicos e até mesmo privados.

## Ciclo de vida de lançamento de um software

Você provavelmente já se deparou com algum anúncio de determinado produto ou jogo que lançou uma versão **beta** para os usuários testarem.

E além da versão beta, nos deparamos com outros nomes ligados ao ciclo de vida de lançamento de um software, que, de forma resumida, estão ligados a determinados momentos (desde seus primeiros dias de vida até o seu lançamento) em que o software se encontra.

Podemos dividir esses “momentos” em 3 partes principais:

![Figura colorida que mostra o ciclo simples de um software. A imagem possui três retângulos de fundo azul ligados por setas azuis com os seguintes textos em branco: “Alpha”, “Beta”, “Release Candidate” respectivamente, um em cada retângulo.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem3.jpg)

* **Alpha** : Além de ser a primeira letra do alfabeto grego, para nosso contexto, essa versão é a primeira a ser testada **pelos times de desenvolvimento** . Essa versão normalmente não é publicada, ou seja, enquanto usuários e usuárias nós ainda não temos acesso às funcionalidades do software, apenas o time interno que fará uma série de testes visando principalmente a estabilidade.
* **Beta** : A segunda letra do alfabeto e que corresponde à versão posterior à alpha. A versão beta se inicia quando as funcionalidades previstas para o software foram implementadas. Essa é a primeira versão pública, onde usuários e usuárias possuem o papel fundamental de testar o software, assim a empresa saberá como está a usabilidade de seu produto e como reduzir impactos negativos relacionados a ele.

É muito comum que *beta testers* (users que testam a versão beta) recebam recompensas, como descontos ou até receber o software gratuitamente (no caso de produtos pagos).

* **RC (Release Candidate)** : Uma tradução seria “candidato a lançamento”, ou seja, trata-se da versão com potencial de ser o produto final, aquele que foi testado em uma versão beta, se mostrou estável, suas funcionalidades estão bem especificadas e o software está pronto para ser lançado (a menos que algum bug mais severo se perceba a tempo).

Bom! Até aqui já entendemos como funciona o lançamento de um software. Mas assim como o exemplo do Express, após seu lançamento, o software recebe desde pequenas correções como mudanças grandes no seu comportamento.E, para cada mudança, uma nova versão é lançada.

Para termos um versionamento semântico, não faz sentido que um software mude da versão 1 para versão 2 tanto para mudanças pequenas quanto grandes. Isso acaba não sendo significativo para nós, pois você não conseguirá diferenciar se foi apenas uma pequena correção que você não precisa se preocupar ou uma grande mudança que terá efeitos mais problemáticos para o seu software.

E, pensando nisso, existe um formato para uma versão: basta apenas olhar sua estrutura e podemos identificar que tipo e o impacto de uma mudança foi feita de uma versão para outra.

## Formato do Versionamento Semântico

O padrão do versionamento é uma sequência numérica separada em três posições:

![Figura colorida que mostra o formato de uma versão. Ao fundo há a cor sólida azul, e no primeiro plano temos um texto escrito na cor branca “1.0.0”. Abaixo temos as palavras “MAJOR, “MINOR”, “PATCH” que são relacionadas a  cada número 1.0.0  por  meio de uma seta. Ou seja, “1” e “MAJOR” estão ligados por uma seta, bem como “0” e “MINOR” e “0” e “PATCH”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem4.jpg)

### MAJOR (Maior)

O primeiro dígito informa a versão de compatibilidade e é alterado caso o software ou biblioteca sofra mudanças que a torne incompatível com outras versões. São as chamadas  *breaking changes* , atualizações que possuem o potencial de “quebrar” códigos que utilizam versões anteriores.

Exemplo: você está usando uma função de uma biblioteca X, porém foi lançada uma nova versão da biblioteca onde essa função tem outro nome ou outra assinatura. Se tentarmos executar o código usando a versão nova da biblioteca, a função não executará corretamente.

Versão 1.0.0 → Agora é 2.0.0

### MINOR (Menor)

O segundo dígito informa a versão da funcionalidade, onde uma nova função ou melhoria substancial é adicionada e não há problemas de incompatibilidade com outras versões.

Exemplo: A biblioteca que você costuma usar tem agora uma nova funcionalidade e é compatível com outras versões, necessita apenas de atualização local.

Versão 2.0.0 → Agora é 2.1.0

### PATCH (Correção)

O terceiro dígito informa a versão da correção de bugs, melhorias de desempenho ou alterações similares que não alteram as funcionalidades atuais e nem introduzem novas.

Exemplo: A biblioteca que você costuma usar tem um bug que gera uma vulnerabilidade no código. Esse bug foi corrigido em uma nova versão.

Versão 2.1.0 → Agora é 2.1.1

## Regras de publicação do software

O versionamento semântico traz algumas especificações visando manter uma comunicação clara entre os softwares, para que você, ao olhar o formato de uma versão, tenha o mesmo entendimento que qualquer outra pessoa ao redor do mundo. Algumas regras são:

* Um número de versão tem o formato X.Y.Z, onde X, Y e Z são inteiros não negativos e não devem conter zeros à esquerda. X é a versão major (maior, em português), Y é a versão minor (menor, em português) e Z é a versão patch (correção, em português).
* Cada número da versão deve aumentar numericamente; ou seja, não podemos ter uma versão 1.0.0 e uma versão 3.0.0 sem que exista uma versão 2.0.0.
* Quando um pacote for lançado (released), o conteúdo dessa versão não deve ser modificado! Se houver modificações, uma nova versão deve ser lançada.
* Uma versão de pré-lançamento (como vimos anteriormente: alpha, beta, rc) pode ser identificada quando adicionado um hífen após a versão de Correção (o Z do nosso formato) e uma série de identificadores separados por ponto. O identificador deve incluir apenas caracteres alfanuméricos e hífen [0-9A-Za-z-] e não deve ser vazio. Exemplos: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7.
* No início do desenvolvimento, a versão Maior deve ser zero (0.y.z).
* A versão 1.0.0 define a API como pública (aquela que foi lançada e está disponível para o público). A maneira como o número de versão é incrementado após este lançamento é dependente da API pública e como ela muda.

Caso queira entender outras regras acerca do versionamento semântico, você pode consultar a documentação oficial [clicando aqui](https://semver.org/lang/pt-BR/).

## Controlando versões no Git/Github

Sabemos que o Git nos permite fazer o controle das versões do nosso código (caso esse assunto seja novo para você, recomendo fortemente que leia [esse artigo sobre Git e Github](https://www.alura.com.br/artigos/o-que-e-git-github) para entender do que estou falando aqui).

Porém, além dos commits que indicam as mudanças feitas no nosso código, podemos unir um conjunto de funcionalidades através das [tags](https://git-scm.com/book/pt-br/v2/Fundamentos-de-Git-Criando-Tags) e [releases](https://docs.github.com/pt/repositories/releasing-projects-on-github/managing-releases-in-a-repository) (em inglês).

Basicamente, as tags representam os trechos de código de uma versão e através dos releases nós podemos descrever para o público do que se trata essa versão.

Assim, você pode indicar nos seus projetos (tanto para seu time quanto para o público externo) qual a versão atual do projeto na totalidade, tanto para quando estiver começando o desenvolvimento, quanto seus códigos estiverem com as funcionalidades implementadas para uma primeira versão de lançamento.

Mostrando na prática: eu criei um repositório no Github chamado  *versionamento-semantico* , fiz o clone no editor que estou usando (no caso, Visual Studio Code) e já realizei o commit de um trecho de código (a inicialização de um servidor em Node.js). Através do Github, esse é o nosso ponto de partida:

![Captura de tela colorida em recorte. Trecho de um projeto do Github como título no canto superior esquerdo escrito: “EmersonLaranja/ versionamento semântico”. Na parte inferior da tela, temos dois arquivoschamados “index.js” e “package.json” e à direita temos uma coluna chamada “Releases” com a seguinte informação abaixo: “No releases published”, acompanhada de um link em azul escrito: “Create a new release”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem5.jpg)

> Novamente, caso sinta dificuldade com algum desses passos, recomendo, além da leitura do [artigo](https://www.alura.com.br/artigos/comecando-com-git-aprendendo-versionar), o curso [Git e Github: Controle de versão](https://www.alura.com.br/curso-online-git-github-controle-de-versao) para por em prática esses conceitos.

E para criarmos nossa primeira tag, em nosso terminal aberto no projeto, digitamos o seguinte comando:

```
git tag -a <NUMERO_DA_TAG> -m “<MENSAGEM_DA_TAG>”
```

Assim, para indicar que estamos começando o desenvolvimento do projeto, criando nossa primeira versão (0.1.0, por exemplo), podemos digitar:

```
git tag -a 0.1.0 -m “começando o desenvolvimento do projeto”
```

E para enviar as tags para nosso repositório remoto, digitamos o comando:

```
git push --tags
```

Agora, ao atualizar a página do nosso projeto no Github, vemos que o campo *Releases* recebeu uma alteração, conforme é mostrado a seguir:

![Tela do projeto criado no Github sobre versionamento semântico. A tela traz informações sobre os arquivos do projeto, autor (EmersonLaranja), quantidades de branches e quantidades de tags. Na parte inferior direita da tela, há um uma coluna destacada em vermelho com nome “Releases” em que temos dentro da coluna um ícone de etiqueta acompanhada da frase “1 tags”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem6.jpg)

Ao clicar em “1 tags” vemos a tag que criamos, bem como a mensagem de descrição e a possibilidade de fazer o download desta versão, conforme a sequência abaixo:

![Captura de tela do projeto criado no Github sobre versionamento semântico. A tela traz uma aba de navegação com os links “Code”, “Issues”, “Pull requests”, “Actions”, “Projects”, “Wiki”, “Security”, “Insights” e “Settings”. Em destaque temos o campo “Tags” selecionado em um botão de fundo azul e letras brancas. Destacado por um retângulo de bordas vermelhas está a versão com texto “0.1.0” as formas de download “zip” e “tar.gz”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem7.jpg)

Por fim, ao acessar a aba “Releases”, podemos criar uma versão de lançamento, para que as pessoas consigam visualizar do que se trata essa primeira versão, clicando em “Create a new release”. Confira este passo na tela a seguir:

![Captura de tela do projeto criado no Github sobre versionamento semântico. A tela traz uma aba de navegação com os links “Code”, “Issues”, “Pull requests”, “Actions”, “Projects”, “Wiki”, “Security”, “Insights” e “Settings”. Em destaque tempos o campo “Release”, que estáselecionado em um botão de fundo azul e letras brancas. No canto inferior direito há um botão de cor azul “Create a new release”, destacado por um retângulo vermelho. . Acima do botão está o ícone de etiqueta e o seguinte texto na linha inferior ao ícone: “There aren’t any releases here.You can create a release to package software, along with release notes and links to binary files, for other people to use. Learn more about releases in our docs”, em português: “Não há nenhuma versão aqui. Você pode criar uma versão para empacotar software, juntamente com notas de versão e links para arquivos binários, para outras pessoas usarem. Saiba mais sobre lançamentos em nossos documentos”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem8.jpg)

Após isso, basta selecionar a tag que se refere essa release (no caso, 0.1.0), preencher com um título (é comum usar uma estrutura que indique a data e a versão da release, adicionei também o usuário responsável) e uma descrição.

Você pode também selecionar a opção “Set as a pre-release” caso essa ainda não seja uma versão de lançamento (no caso, eu optei por marcar , pois é apenas o começo do nosso desenvolvimento do projeto).

Confira na tela a seguir:

![Captura de tela do projeto criado no Github sobre versionamento semântico. Em destaque temos a aba  “Release”, na cor azul, no canto superior esquerdo. . Abaixo do botão há  um formulário, sendo que o primeiro campo traz a tag selecionada “0.1.0” com um ícone de etiqueta à esquerda. Abaixo temos o título “2022-11-24, versão 0.1.0, @EmersonLaranja”. Abaixo temos o campo de descrição com o texto “Criei a inicialização de um servidor com o Node.js”. Abaixo temos um campo de upload escrito “Attach binaries by dropping them here or selecting there.” com uma seta apontada para baixo no começo do texto. Na sequência, abaixo,  temos um botão de opção com o texto “Set as a pre-release” e subtexto “This release will be labeled as non-production ready”. E logo no canto inferior esquerdo  temos os botões “Publish release”,  e “Save draft”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem9.jpg)

Após isso, clicando em “Publish release”, veremos a seguinte tela:

![Captura de tela do projeto criado no Github sobre versionamento semântico. A tela traz uma aba de navegação com os links “Code”, “Issues”, “Pull requests”, “Actions”, “Projects”, “Wiki”, “Security”, “Insights” e “Settings”. Em destaque temos o campo “Releases” selecionado em um botão de fundo azul e letras brancas. Destacado por um retângulo de bordas vermelhas está o texto “Pre-releases”, de cor laranja. À esquerda do retângulo está o título principal “2022-11-24, versão 0.1.0, @EmersonLaranja”. Abaixo está a descrição “Criei a inicialização de um servidor com o Node.js”. Abaixo existe o campo “Assets” com duas linhas que são links de cor azul, o primeiro escrito “Source code (zip)” e o segundo “Source code (tar.gz)”.](https://www.alura.com.br/artigos/assets/versionamento-semantico-breve-introducao/imagem10.jpg)

Pronto! Temos nossa primeira release publicada e qualquer pessoa que acessar nosso projeto saberá como está o andamento do projeto (no caso, “prerelease”, como indicado na imagem acima), bem como as funcionalidades desta versão.

Um exemplo mais elaborado de detalhes é a [release da última versão do Node.js](https://github.com/nodejs/node/releases/tag/v19.1.0), na qual vemos a descrição das novas funcionalidades, commits relacionados e o código referente a esta versão.

## Conclusão

Neste artigo vimos o que é o versionamento semântico, como identificar de forma rápida o seu formato (graças às regras de padronização das versões), além de usá-lo de forma prática, por exemplo, nos seus projetos do Git.

Esse conhecimento será essencial para tomar decisões de quando atualizar seus projetos, bem como versioná-lo. Mas para que esses conceitos se tornem um aprendizado, além de entender mais detalhes na [documentação oficial](https://semver.org/lang/pt-BR/), é necessário que você pratique!

Aqui na Alura você pode praticar com diversos projetos, como [sua primeira biblioteca usando Node.js](https://www.alura.com.br/curso-online-nodejs-criando-primeira-biblioteca), onde você também poderá lançar sua biblioteca no npm, praticando mais do versionamento semântico.
