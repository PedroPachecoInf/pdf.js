# Processos de Software
#### Relatório de Engenharia de Software

## Introdução

O projeto open-source escolhido para ser abordado ao longo da cadeira de Engenharia de Software foi o 
[**pdf.js**](https://github.com/mozilla/pdf.js), que a Mozilla alberga.

O PDF.js é um visualizador de Portable Document Format (PDF), construído sobre o HTML5, com o propósito de criar um standard no que toca às plataformas que visualizam e criam PDFs na Web. Desta forma torna-se muito mais prática e rápida a leitura de PDFs, dado que não é necessário o download do mesmo.

## Processo de desenvolvimento

### Software open-source

Um projeto open-source parte de uma ideia, que um ou mais programadores implementam, criando uma base de desenvolvimento. Quando esse protótipo é libertado para o público, a comunidade vai maturando-o e aperfeiçoando-o, segundo as necessidades que surgem. Passado um certo período de tempo, a ideia inicial torna-se um projeto robusto, pronto a ser usado sem problemas.

A utilização de sistemas de controlo de versão como o Git, permitiu que a colaboração em open-source fosse facilitada e atraísse uma audiência mais alargada, que, consequentemente, precisa de maior controlo nas suas contribuições.

Assim, para a grande maioria dos projetos open-source é aplicada a metodologia do desenvolvimento ágil (*agile development*) de software.

#### Desenvolvimento ágil

Os métodos de desenvolvimento de software podem ter uma abordagem adaptativa ou preditiva. O desenvolvimento ágil foca-se na adaptação a problemas em detrimento da previsão. Isto porque anos de experiência levaram as empresas a perceber que é mais complicado prever uma mudança nos requerimentos da aplicação e precaver-se contra ela, do que esperar que ela ocorra e depois desenvolver a partir dela.

O modelo ágil 

#### Programação Extrema

Esta metodologia ágil muito usada em projetos open-source tem como pilares:
- comunicação
- simplicidade
- feedback
- coragem
- respeito

A sua maior vantagem relativamente a outras metodologias ágeis (como SCRUM) tem a ver com envolver práticas especificas de programação, como por exemplo o facto de ser TDD (*test-driven development*), ou de ter uma grande componente de revisão de código


### PDF.js




## Problemas/Opiniões

Atualmente o PDF.js funciona de forma estável apenas no Firefox,Chrome e Opera. Apesar de estes browsers serem usados por grande parte das pessoas, usuários, por exemplo, do Safari, não têm acesso a todas as funcionalidades do programa, ou estas têm defeitos. Sendo assim, uma das prioridades no desenvolvimento do projeto seria tornar o PDF.js suportado por praticamente todos os browsers.

Por outro lado, o facto de o PDF.js estar implementado em vários browsers cria diferentes tipos de bugs, dado que cada browser tem as suas especificidades e é necessário adapatar o programa a cada um. Desta forma, o aperfeiçoamento do projeto será mais complicado e demoroso.

Durante o desenvolvimento do projeto, é aconselhado aos programadores que sigam certas convenções em termos de "estilo de escrita". Este estilo define que a indentação é de 2 espaços, as chavetas ficam na mesma linha que o respetivo 'if', 'for' ou 'while'. A definição deste estilo universal permite que o código tenha sempre uma estrutura idêntica, tornando o código mais legível.

##Processos Alternativos

Existem diversos processos de desenvolvimento que poderiam ter sido usados para desenvolver este projecto.

O processo "Waterfall" é uma das alternativas possíveis. Baseando-se na divisão do desenvolvimento em fases específicas, em que cada fase depende da terminação da anterior, este processo permite coordenar melhor o desensolvimento. No entanto, este método não seria uma boa escolha pois não permite combater facilmente mudanças relacionadas com as fases já terminadas do projecto. Além disso, sendo este um projecto open-source, esta metedologia dificultaria a introdução de novas ideias e funcionalidades por parte dos contribuidores externos. 
