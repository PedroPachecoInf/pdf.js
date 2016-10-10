# Processos de Software
#### Relatório de Engenharia de Software

## Introdução

O projeto open-source escolhido para ser abordado ao longo da cadeira de Engenharia de Software foi o 
[**pdf.js**](https://github.com/mozilla/pdf.js), que a Mozilla alberga.

O PDF.js é um visualizador de Portable Document Format (PDF), construído  em JavaScript sobre o HTML5, com o propósito de criar um standard no que toca às plataformas que visualizam e criam PDFs na Web. Desta forma torna-se muito mais prática e rápida a leitura de PDFs, dado que não é necessário o download do mesmo. 

## Processo de desenvolvimento em open-source

Um projeto open-source parte de uma ideia, que um ou mais programadores implementam, criando uma base de desenvolvimento. Quando esse protótipo é libertado para o público, a comunidade vai maturando-o e aperfeiçoando-o, segundo as necessidades que surgem. Passado um certo período de tempo, a ideia inicial torna-se um projeto robusto, pronto a ser usado com poucos defeitos.

#### Desenvolvimento ágil

Os métodos de desenvolvimento de software podem ter uma abordagem adaptativa ou preditiva. O desenvolvimento ágil foca-se na adaptação a problemas em detrimento da sua previsão. Isto porque anos de experiência levaram as empresas a perceber que é mais complicado prever uma mudança nos requerimentos da aplicação e precaver-se contra ela, do que esperar que ela ocorra e depois desenvolver a partir dela.

<img src = "https://raw.githubusercontent.com/PedroPachecoInf/pdf.js/ESOF/ESOF/Relat%C3%B3rio%201%20-%20Esquemas/Esquema%201%20-%20Agil%20vs%20Planned.png" alt = "Planned vs Agile development" width = "500" height = "450" >

O modelo ágil, por se basear em iterações curtas e em lançamentos de várias versões funcionais, permite que, à medida que se vai desenvolvendo, o *feedback* do cliente contribua para um software adaptado aos seus requerimentos, sem que haja desperdício de recursos em funcionalidades que não interessariam ao cliente, nem em possíveis *bugs*.

Um exemplo de uma metodologia ágil é o **Extreme Programming (XP)**, muito usada em projetos open-source, e que tem como pilares:
- **comunicação**: permitir que os desenvolvedores conheçam a perspetiva do utilizador.
- **simplicidade**: começar pela solução mais simples poupa trabalho.
- **feedback** vindo do utilizador, da equipa ou de testes unitários.
- **coragem** para publicar código e avançar com o projeto.
- **respeito** por aqueles que dedicam o seu esforço.

A sua maior vantagem relativamente a outras metodologias ágeis (como SCRUM) tem a ver com envolver práticas especificas de programação, como por exemplo o facto de ser TDD (*test-driven development*), tendo uma grande componente de revisão de código.

### Controlo de versões e o modelo ágil

A divulgação e o aperfeiçoamento de ferramentas de controlo de versão contribuiu muito para a expansão do open-source.

Atualmente, o Git e, mais particularmente, o *hoster* de repositórios **GitHub**, fornecem as ferramentas necessárias para uma colaboração organizada e simplificada entre programadores. 

Neste plano, em vez de a mudança do software ser imposta por um "cliente", é incentivada pela comunidade online que, ao utilizar e modificar o programa, gera *feedback* suficiente para os *developers* alterarem e melhorarem as funcionalidades.

## Processo de desenvolvimento do *pdf.js*

O pdf.js, como projeto open-source, segue um modelo de desenvolvimento ágil que partilha características com o Extreme Programming. 

Todo o seu código-fonte encontra-se publicado no [repositório](https://github.com/mozilla/pdf.js) GitHub da Mozilla. Sendo a Mozilla uma marca do open-source, os seus projetos atraem uma maior audiência que sente maior confiança no sucesso do projeto. Este em particular conta com mais de 200 colaboradores. 

O repositório tem uma pequena equipa de contribuidores principais que revê as contribuições e aceita-as ou rejeita-as. Estas contribuições têm de passar numa série de testes automatizados de verificação de sintaxe e de obedecer a certas convenções em termos de estilo de escrita, para facilitar a leitura e integração do código no repositório.

Partindo de um código base, que serviu de núcleo da aplicação, foram sendo adicionados pequenos **incrementos** ao projeto, que contribuiam para a sua estabilidade e para a adição de uma ou outra funcionalidade. Estas adições são incentivadas ou realizadas por internautas que clonam o código e decidem modificá-lo ou utilizá-lo.

Quando são implementadas funcionalidades e arranjos suficientes, um dos *main developers* faz *release* de uma nova versão completamente funcional para o repositório. Neste momento, o pdf.js encontra-se relativamente estável, com intervalos de meses entre *releases*.

## Problemas e opiniões

Atualmente o PDF.js funciona de forma estável apenas no Firefox,Chrome e Opera. Apesar de estes browsers serem usados por grande parte das pessoas, usuários, por exemplo, do Safari, não têm acesso a todas as funcionalidades do programa, ou estas têm defeitos. Sendo assim, uma das prioridades no desenvolvimento do projeto seria tornar o PDF.js suportado por praticamente todos os browsers.

Por outro lado, o facto de o PDF.js estar implementado em vários browsers cria diferentes tipos de bugs, dado que cada browser tem as suas especificidades e é necessário adapatar o programa a cada um. Desta forma, o aperfeiçoamento do projeto será mais complicado e demoroso.

Durante o desenvolvimento do projeto, é aconselhado aos programadores que sigam certas convenções em termos de "estilo de escrita". Este estilo define que a indentação é de 2 espaços, as chavetas ficam na mesma linha que o respetivo 'if', 'for' ou 'while'. A definição deste estilo universal permite que o código tenha sempre uma estrutura idêntica, tornando o código mais legível.

##Processos alternativos

Existem diversos processos de desenvolvimento que poderiam ter sido usados para desenvolver este projecto.

O processo "Waterfall" é uma das alternativas possíveis. Baseando-se na divisão do desenvolvimento em fases específicas, em que cada fase depende da terminação da anterior, este processo permite coordenar melhor o desensolvimento. No entanto, este método não seria uma boa escolha pois não permite combater facilmente mudanças relacionadas com as fases já terminadas do projecto. Além disso, sendo este um projecto open-source, esta metedologia dificultaria a introdução de novas ideias e funcionalidades por parte dos contribuidores externos. 
