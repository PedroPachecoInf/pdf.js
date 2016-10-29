# Elicitação de requisitos
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

### Requisitos principais

> "Like many before us, we were wondering why nobody had implemented a PDF reader in HTML5/JavaScript. The kinds of operations a PDF reader needs to be fast at –render text, draw lines, blit images– need to be fast in browsers too, so browsers are already highly optimized for them. (...) Displaying PDFs directly in the browser would definitely improve the user’s experience."
>_**Andreas Gal** - criador do pdf.js_

Um _software_ é desenvolvido a partir dos seus requisitos. Estes requisitos definem aquilo que deve ser possível concretizar ao utilizar a aplicação. 

Andreas Gal, ao criar o **pdf.js**, queria tornar realidade um leitor de PDF que fosse rápido e que pudesse ser incorporado nos browsers. Desta forma, uma pessoa poderia ler diretamente o PDF no browser, em vez de ter o esforço extra de o baixar e ler num programa próprio.

Os requisitos do pdf.js não se limitam apenas ao utilizador que lê PDF, mas também ao programador que o hospeda na sua página Web. Por ser escrito em JavaScript, o pdf.js permite ao *host* de um website integrar PDFs na sua página como se se tratassem de um outro qualquer elemento HTML e possibilita interações entre o PDF e o resto do site.

### Âmbito 
O âmbito de um projeto é o conjunto de todos os processos que devem ser executados para satisfazer os requisitos propostos. Quando se define o âmbito, definem-se os limites do projeto. 

Da mesma forma que um construtor civil constrói uma cerca em redor da sua área de construção para saber aquilo que está dentro e fora do seu comando, um engenheiro de software deve declarar os métodos que estão incluídos no desenvolvimento de uma aplicação e os que não estão. Desta forma verifica-se se todos os processos necessários foram concluídos e se não se perde tempo em esforços inúteis.

O âmbito do pdf.js é muito restrito, pois trata-se de um leitor de um tipo específico de ficheiros. O âmbito global deste *webviewer* pode ser subdividido em âmbitos menores, que têm como objetivo final preencher um requisito, por exemplo:

| Requisito | Âmbito |
| --- | --- |
| Ler um ficheiro PDF | Processos necessários para fazer o *input* da informação do ficheiro para o programa e interpretá-la.|
| Incorporar um browser HTML5 | Criar um conjunto de normas escritas no standard HTML5, que permitam utilizar as funções de leitura de ficheiros de forma a fazer o *display* do PDF num browser atual.|

## Implementação de funcionalidades
O desenvolvimento deste projeto, para além da equipa inicial, depende muito da comunidade, dado que esta pode intervir ativamente neste processo.

Atualmente, as pessoas intervenientes no desenvolvimento do PDF.js trabalham para implementar novas funcionalidades e corrigir os vários *issues* existentes, de forma a tornar este projeto num grande sucesso.

A equipa de desenvolvimento fornece um guião em que explica de forma detalhada como é possível contribuir e sugerir novas ideias. Para além disso, é também fornecida uma lista com os vários bugs detetados, e esta pode sempre aumentar se alguém eventualmente descobrir novos problemas no programa.

Quando uma pessoa pretende contribuir com uma nova ideia ou mesmo corrigir bugs deve fazer o seguinte:

1. Fork: Primeiro deve criar uma conta no GitHub e fazer fork do projeto.
2. Criar uma branch: Depois de fazer fork, deve criar uma branch, idealmente com o nome da nova funcionalidade que pretende adicionar ou mesmo do bug que vai corrigir e trabalhar nesta.
3. Editar: Após a criação da branch, o contribuidor deve fazer as alterações que entende de acordo com *"coding style"* exigido.
4. Correr os testes: São fornecidos alguns testes, que devem ser usados para verificar se está tudo em ordem.
5. Criar o Pull Request: Se tudo até este ponto estiver funcional, a pessoa pode criar o Pull Request e esperar que o código seja analisado.

Para além desta forma de contribuição, existem encontros semanais para a discussão do desenvolvimento do projeto. Qualquer pessoa pode aparecer no meeting e dar o seu ponto de vista sobre o projeto, sugerir novas ideias ou até mesmo apontar novos bugs.

### Requisitos funcionais

Em Engenharia de Software, os requisitos funcionais de um programa são as capacidades que este deve ter e são definidas pelo cliente ou utilizador. O cliente do pdf.js é um qualquer internauta que deseje abrir um PDF no seu browser. Por exemplo, qualquer utilizador do Mozilla Firefox torna-se um cliente "forçado" do pdf.js ao abrir um PDF nesse browser. Como tal, os requisitos funcionais mais importantes do pdf.js são:

- Ler qualquer ficheiro PDF
- Fazer o *render* e *display* do PDF da forma mais rápida e otimizada possível
- Permitir a inclusão de anotações no PDF
- Poder ser incorporado numa página web
- Poder ser corrido a partir de qualquer browser que compile HTML5

### Requisitos não-funcionais

Os requisitos não-funcionais influenciam a forma como os requisitos funcionais são atingidos. São, sobretudo, requisitos a nível da qualidade do produto, que regem a forma como os processos de desenvolvimento são executados.

As qualidades -ou seja, os requisitos não-funcionais- do pdf.js podem ser divididas em três categorias: 

1. **Qualidades de desenvolvimento**, que são aplicadas na criação do programa. Ex.: linguagem e standards utilizados no código.
2. **Qualidades de execução**, que são observadas em *runtime*. Ex.: segurança e usabilidade.
3. **Qualidades de evolução**, que permitem alterar a estrutura do sistema de software. Ex.: testabilidade, extensibilidade e escalabilidade.

Sendo o pdf.js um programa utilizado por defeito no Mozilla Firefox, é essencial que o seu patamar de qualidade seja elevado, para não denegrir a fama do browser e afastar milhões de utilizadores. As suas **qualidades de desenvolvimento** foram influenciadas pelas linguagens mais populares para *web development* dos dias de hoje, que são as que permitirão ao pdf.js ser compatível com a maior parte dos sistemas:

- Deve ser codificado em JavaScript.
- Deve obedecer às normas HTML5.

Em termos de **requisitos não-funcionais** de execução, o pdf.js deve:

- Ter uma interface simples e auto-explicativa.
- Possuir uma camada de segurança bem estabelecida, para que não haja injeção de código através do PDF.

Já as suas **qualidades de evolução** são:

- Facilitar **testes de execução**, disponibilizando uma série de testes automáticos.
- Ter uma estutura propensa à **extensibilidade**, para que seja possível adicionar novas funcionalidades.
- Permitir a **escalabilidade** do seu núcleo de código, para que possa acompanhar a evolução dos standards usados, nomeadamente do HTML5 e do JavaScript.


## Casos de uso

### Sistema

### Atores

### Casos de uso e relações

## Análise de domínio

Para facilitar a compreensão do das mecânicas básicas do PDF.js, criou-se um modelo de dominio (*domain model*) que abrange as 3 camadas fundamentais do mesmo, incluindo algum do funcionamento interno respetivo de cada camada.

<img src = ".\Relatorio 2 - Esquemas\domain model.png" alt = "domain model">

## Contribuições

## Referências

https://andreasgal.com/2011/06/15/pdf-js/ - Consultado a 25 de outubro

http://www.pmexamsmartnotes.com/difference-between-requirements-and-scope/ - Consultado a 27 de outubro

https://en.wikipedia.org/wiki/Scope_(project_management) - Consultado a 27 de outubro

https://en.wikipedia.org/wiki/Non-functional_requirement -  Consultado a 28 de outubro

