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

## Elicitação de requisitos
Na elicitação de requisitos, ou seja, no levantamento das funcionalidades que o software necessita ter, é imperativa a interação com a parte que tem interesse direto no sucesso do produto, sejam eles investidores ou clientes. As partes com este papel denominam-se *stakerholders*.

Para que a elicitação seja bem efetuada, a equipa de desenvolvimento deve ir entrevistando e debatendo protóripos com os *stakeholders*,  de forma a que não hajam grandes alterações de requisitos numa fase posterior do projeto.

Sendo o pdf.js open-source, depende muito da comunidade online, que ganha o papel de *stakeholder*.

Atualmente, as pessoas intervenientes no desenvolvimento do PDF.js trabalham para implementar novas funcionalidades e corrigir os vários *issues* existentes, de forma a tornar este projeto num grande sucesso, pelo que desempenham tanto a função de *stakeholder* como de contribuidor.

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

Sendo o pdf.js um programa utilizado por defeito no Mozilla Firefox, é essencial que o seu patamar de qualidade seja elevado, para não denegrir a fama do browser e afastar milhões de utilizadores. 

**Requistos não-funcionais de desenvolvimento** 

- Ser codificado em JavaScript.
- Obedecer às normas HTML5.

**Requisitos não-funcionais de execução**:

- Ter uma interface simples e auto-explicativa.
- Possuir uma camada de segurança bem estabelecida, para que não haja injeção de código através do PDF.

**Requisitos não-funcionais de evolução**:

- Facilitar **testes de execução**, disponibilizando uma série de testes automáticos.
- Ter uma estutura propensa à **extensibilidade**, para que seja possível adicionar novas funcionalidades.
- Permitir a **escalabilidade** do seu núcleo de código, para que possa acompanhar a evolução dos standards usados, nomeadamente do HTML5 e do JavaScript.


## Casos de uso

### Diagrama

<img src = ".\Relatorio 2 - Esquemas\use case diagram.png" alt = "use case model">

### Atores
Os atores que intervém no sistema são apenas dois: a página web na qual o pdf.js é corrido (WebSite) e o ficheiro PDF a ser lido(PDF File).

- O Website corre o PDF.js e posteriormente comunica com ele através de várias funções especificadas no programa. O Website é o único ator que desencadeia os casos de uso, e assim sendo o único que espera algo em retorno.

- O PDF File funciona quase como uma base de dados, pelo que não desencadeia nenhum caso de uso. No entanto, é um elemento sempre presente pois é fonte dos dados que são tratados pelo pdf.js.

Existem outras entidades que poderiam de certa forma parecer atores, mas no entanto não o são. Estas entidades como o utilizador comum do website ou programador do website, não interagem com o pdf.js mas sim com o website em si, pelo que não são consideradas atores.

### Descrição Casos de uso
**Nome**: Mostrar um ficheiro PDF

**Atores**: Website, PDF File

**Objectivo**: Mostrar um determinado ficheiro pdf no website

**Referência aos Requerimentos**: ...

**Pré-condições**:

- O website está aberto sem nenhum outro problema
- O ficheiro pdf  existe e é válido

**Descrição**:

1. O Website corre o pdf.js
2. O Website fornece o endereço do ficheiro pdf e pede ao pdf.js o documento
3. O PDF.js lê os dados contidos no ficheiro pdf indicado
4. O Website solicita uma determinada página do documento
5. O PDF.js prepara a página indicada para posteriores operações
6. O Website solicita o *rendering* da página como descrito no caso de uso "*Render a Page*”

**Pós-condições**:

O Website consegue mostrar um ficheiro pdf

**Variações**:

6a. O documento têm mais de uma página
	6a1. O Website solicita o *rendering* da página como descrito no caso de uso "*Render a Page*”
	6a2. O processo continua para o item 2.
	
**Exceções**:

2a. O ficheiro pdf não existe.
	2a1. O PDF.js retorna uma mensagem de erro.


Nome: Render a Page
Atores: Website
Objectivo: *Renderizar* uma página do ficheiro pdf
Referência aos Requerimentos:...
Pré-condições:
	Curso normal do caso de uso "*Display a PDF File*" completado
	Uma página foi escolhida com sucesso
Descrição:
	1. O Website solicita o *rendering* da página
	2. O PDF.js trata os dados referentes à página e gera a imagem correspondente
Pós-condições:
	A página é *renderizada*
Variações:
	...
Exceções:
	2a. O page têm algum problema.
		2a1. O PDF.js retorna uma mensagem de erro.

## Análise de domínio

Para facilitar a compreensão das mecânicas básicas do PDF.js, criou-se um modelo de dominio (*domain model*) que abrange as 3 camadas fundamentais do mesmo, incluindo algum do funcionamento interno respetivo de cada camada.

<img src = ".\Relatorio 2 - Esquemas\domain model.png" alt = "domain model">

## Contribuições

Todos os membros contribuiram de igual forma para a elaboração deste relatório.

## Referências

https://andreasgal.com/2011/06/15/pdf-js/ - Consultado a 25 de outubro

http://www.pmexamsmartnotes.com/difference-between-requirements-and-scope/ - Consultado a 27 de outubro

https://en.wikipedia.org/wiki/Scope_(project_management) - Consultado a 27 de outubro

https://en.wikipedia.org/wiki/Non-functional_requirement -  Consultado a 28 de outubro

