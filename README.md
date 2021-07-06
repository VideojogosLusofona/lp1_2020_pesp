# Projeto de Época Especial de Linguagens de Programação 2020/2021

## Introdução

Os grupos devem implementar o jogo **18 Ghosts** na forma de uma aplicação de
consola .NET Core. O jogo deve ser PvP (_Player vs Player_), sem qualquer
tipo de inteligência artificial.

As regras do jogo estão explicadas
[neste ficheiro](https://secure.grupolusofona.pt/ulht/moodle/pluginfile.php/1011340/mod_assign/introattachment/0/18GHOSTS_EN_r1.pdf?forcedownload=1). Para este projeto existem
duas simplificações a estas regras:

* A primeira fase do jogo consiste em colocar os fantasmas no tabuleiro (no
  manual do jogo é a secção que diz "PLACING THE GHOSTS ON THE BOARD"). Em vez
  de colocação dos fantasmas um a um por parte dos jogadores, a vossa aplicação
  pode colocar os fantasmas automaticamente e aleatoriamente no tabuleiro, sem
  que a nota fique prejudicada.
* O jogo pode terminar assim que um jogador consiga retirar três fantasmas do
  castelo, independentemente da cor dos mesmos, tal como descrito no final do
  manual do jogo, na secção "VARIANT FOR SHORTER PLAY".

É muito importante criarem o jogo fisicamente, incluindo tabuleiro e peças
jogáveis, bem como realizar alguns jogos. Esta abordagem inicial permite
desenvolver uma melhor noção do jogo, facilitando o posterior planeamento e
implementação em C#.

## Funcionamento da Aplicação

O funcionamento exato da aplicação é da responsabilidade de cada grupo. No
entanto, quando a aplicação começa, **deve ser claro como cada jogador joga**,
ou seja, o jogo deve ter instruções muito claras sobre que teclas fazem o quê.
Por outras palavras, os grupos devem ter em conta as regras importantes do
_game design_, pois serão tidas em conta na avaliação do projeto.

A aplicação deve funcionar em Windows, macOS e Linux. A melhor estratégia para
garantir que assim seja é testar o jogo em Linux (e.g., numa máquina virtual).
Algumas instruções incompatíveis com macOS e Linux são, por exemplo:

* [Console.Beep()](https://docs.microsoft.com/dotnet/api/system.console.beep)
* [Console.SetBufferSize()](https://docs.microsoft.com/dotnet/api/system.console.setbuffersize)
* [Console.SetWindowPosition()](https://docs.microsoft.com/dotnet/api/system.console.setwindowposition)
* [Console.SetWindowSize()](https://docs.microsoft.com/dotnet/api/system.console.setwindowsize)
* Entre outras.

As instruções que só funcionam em Windows têm a seguinte indicação na sua
documentação:

![The current operating system is not Windows.](img/notsupported.png "The current operating system is not Windows.")

### Organização do código e estrutura de classes

O projeto deve estar devidamente organizado usando a abordagem MVC discutida nas
aulas, fazendo uso de classes, _structs_ e enumerações. Cada classe, _struct_ ou
enumeração deve ser colocada num ficheiro com o mesmo nome. Por exemplo, uma
classe chamada `Ghost` deve ser colocada no ficheiro `Ghost.cs`. A estrutura de
classes deve ser bem pensada usando a abordagem MVC, e [cada classe deve ter
uma responsabilidade específica e bem definida][SRP].

## Objetivos e critério de avaliação

Este projeto tem os seguintes objetivos:

* **O1** - Programa deve funcionar como especificado e deve ter em conta as
  regras básicas do _game design_.
* **O2** - Projeto e código bem organizados, nomeadamente:
  * Estrutura de classes bem pensada (ver secção [Organização do código e
    estrutura de classes](#organizacao-do-codigo-e-estrutura-de-classes)).
  * Código devidamente comentado e indentado.
  * Inexistência de código "morto", que não faz nada, como por exemplo
    variáveis, propriedades ou métodos nunca usados.
  * Projeto compila e executa sem erros e/ou *warnings*.
* **O3** - Projeto adequadamente documentado com [comentários de documentação
  XML][XML]. A documentação gerada em formato HTML em [Doxygen] ou [DocFX],
  deve estar incluída no `zip` do projeto, mas **não** integrada no repositório
  Git.
* **O4** - Repositório Git deve refletir boa utilização do mesmo, nomeadamente:
  * Devem existir *commits* de todos os elementos do grupo, _commits_ esses
    com mensagens que sigam as melhores práticas para o efeito (como indicado
    [aqui](https://chris.beams.io/posts/git-commit/),
    [aqui](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53),
    [aqui](https://github.com/erlang/otp/wiki/writing-good-commit-messages) e
    [aqui](https://stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)).
  * Ficheiros binários não necessários, como por exemplo todos os que são
    criados nas pastas `bin` e `obj`, bem como os ficheiros de configuração
    do Visual Studio (na pasta `.vs` ou `.vscode`), não devem estar no
    repositório. Ou seja, devem ser ignorados ao nível do ficheiro
    `.gitignore`.
  * *Assets* binários necessários, como é o caso da imagem do diagrama UML,
    devem ser integrados no repositório em modo Git LFS.
* **O5** - Relatório em formato [Markdown] (ficheiro `README.md`),
  organizado da seguinte forma:
  * Título do projeto.
  * Autoria:
    * Nome dos autores (primeiro e último) e respetivos números de aluno.
    * Informação de quem fez o quê no projeto. Esta informação é
      **obrigatória** e deve refletir os *commits* feitos no Git.
    * Indicação do repositório Git utilizado. Esta indicação é
      opcional, pois podem preferir manter o repositório privado após a
      entrega.
  * Arquitetura da solução:
    * Descrição da solução, com breve explicação de como o código foi
      organizado, bem como dos algoritmos não triviais que tenham sido
      implementados.
    * Um diagrama UML de classes simples (i.e., sem indicação dos
      membros da classe) descrevendo a estrutura de classes.
  * Referências, incluindo trocas de ideias com colegas, código aberto
    reutilizado (e.g., do StackOverflow) e bibliotecas de terceiros
    utilizadas. Devem ser o mais detalhados possível.
  * **Nota:** o relatório deve ser simples e breve, com informação mínima e
    suficiente para que seja possível ter uma boa ideia do que foi feito.
    Atenção aos erros ortográficos e à correta formatação [Markdown], pois
    ambos serão tidos em conta na nota final.

O projeto tem um peso de 10 valores na nota final da disciplina e será avaliado
de forma qualitativa. Isto significa que todos os objetivos têm de ser
parcialmente ou totalmente cumpridos. A cada objetivo, O1 a O5, será atribuída
uma nota entre 0 e 1. A nota do projeto será dada pela seguinte fórmula:

*N = 10 x O1 x O2 x O3 x O4 x O5 x D*

Em que *D* corresponde à nota da discussão e percentagem equitativa de
realização do projeto, também entre 0 e 1. Isto significa que se os alunos
ignorarem completamente um dos objetivos, não tenham feito nada no projeto ou
não comparecerem na discussão, a nota final será zero.

## Entrega

O projeto deve ser entregue por **grupos de 1 a 3 alunos** via Moodle até às
23h de **29 de agosto de 2021**. Um (e apenas um) dos elementos do grupo deve
ser submeter um ficheiro `zip` com a solução completa, nomeadamente:

* Pasta escondida `.git` com o repositório Git local do projeto.
* Documentação HTML gerada com [Doxygen] ou [DocFX]. Esta documentação
  **não** deve ser incluída no repositório Git, pelo que a respetiva pasta deve
  estar explicitamente ignorada a nível do ficheiro `.gitignore`.
* Ficheiro da solução (`.sln`).
* Pasta do projeto, contendo os ficheiros `.cs` e o ficheiro do projeto
  (`.csproj`).
* Ficheiro `README.md` contendo o relatório do projeto em formato [Markdown].
* Ficheiro de imagem contendo o diagrama UML. Este ficheiro deve ser incluído
  no repositório em modo Git LFS.
* Outros ficheiros de configuração, como por exemplo `.gitignore`,
  `.gitattributes`, `Doxyfile` ou `docfx.json`.

Não serão avaliados projetos sem estes elementos e que não sejam entregues
através do Moodle.

Discussões do projeto irão realizar-se presencialmente no dia **1 de setembro de
2021, às 9h30**.

## Honestidade académica

Nesta disciplina, espera-se que cada aluno siga os mais altos padrões de
honestidade académica. Isto significa que cada ideia que não seja do
aluno deve ser claramente indicada, com devida referência ao respetivo
autor. O não cumprimento desta regra constitui plágio.

O plágio inclui a utilização de ideias, código ou conjuntos de soluções
de outros alunos ou indivíduos, ou quaisquer outras fontes para além
dos textos de apoio à disciplina, sem dar o respetivo crédito a essas
fontes. Os alunos são encorajados a discutir os problemas com outros
alunos e devem mencionar essa discussão quando submetem os projetos.
Essa menção **não** influenciará a nota. Os alunos não deverão, no
entanto, copiar códigos, documentação e relatórios de outros alunos, ou dar os
seus próprios códigos, documentação e relatórios a outros em qualquer
circunstância. De facto, não devem sequer deixar códigos, documentação e
relatórios em computadores de uso partilhado, e muito menos usar
repositórios Git públicos (embora os mesmos possam ser tornados públicos
12h após a data limite de submissão).

Nesta disciplina, a desonestidade académica é considerada fraude, com
todas as consequências legais que daí advêm. Qualquer fraude terá como
consequência imediata a anulação dos projetos de todos os alunos envolvidos
(incluindo os que possibilitaram a ocorrência). Qualquer suspeita de
desonestidade académica será relatada aos órgãos superiores da escola
para possível instauração de um processo disciplinar. Este poderá
resultar em reprovação à disciplina, reprovação de ano ou mesmo suspensão
temporária ou definitiva da ULHT.

*Texto adaptado da disciplina de [Algoritmos e
Estruturas de Dados][aed] do [Instituto Superior Técnico][ist]*

## Referências

* \[1\] **18 Ghosts** (2010). Retrieved from
  <https://boardgamegeek.com/boardgame/70116/18-ghosts>.
* \[2\] Whitaker, R. B. (2016). **The C# Player's Guide** (3rd Edition).
  Starbound Software.
* \[3\] Albahari, J. (2017). **C# 7.0 in a Nutshell**. O’Reilly Media.
* \[4\] Dorsey, T. (2017). **Doing Visual Studio and .NET Code Documentation
  Right**. Visual Studio Magazine. Retrieved from
  <https://visualstudiomagazine.com/articles/2017/02/21/vs-dotnet-code-documentation-tools-roundup.aspx>.

## Licenças

* Este enunciado é disponibilizado através da licença [CC BY-NC-SA 4.0].

## Metadados

* Autores: [Phil Lopes] e [Nuno Fachada]
* Curso:  [Licenciatura em Videojogos][lamv]
* Instituição: [Universidade Lusófona de Humanidades e Tecnologias][ULHT]

[CC BY-NC-SA 4.0]:https://creativecommons.org/licenses/by-nc-sa/4.0/
[lamv]:https://www.ulusofona.pt/licenciatura/videojogos
[Phil Lopes]:https://github.com/worshipcookies
[Nuno Fachada]:https://github.com/fakenmc
[ULHT]:https://www.ulusofona.pt/
[aed]:https://fenix.tecnico.ulisboa.pt/disciplinas/AED-2/2009-2010/2-semestre/honestidade-academica
[ist]:https://tecnico.ulisboa.pt/pt/
[Markdown]:https://guides.github.com/features/mastering-markdown/
[Doxygen]:https://www.stack.nl/~dimitri/doxygen/
[DocFX]:https://dotnet.github.io/docfx/
[KISS]:https://en.wikipedia.org/wiki/KISS_principle
[XML]:https://docs.microsoft.com/dotnet/csharp/codedoc
[SRP]:https://en.wikipedia.org/wiki/Single_responsibility_principle
[2º projeto de LP1 2018/19]:https://github.com/VideojogosLusofona/lp1_2018_p2_solucao
