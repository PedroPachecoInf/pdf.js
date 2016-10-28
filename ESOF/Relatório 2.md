# Elicitação de requisitos
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

| Requerimento | Âmbito |
| --- | --- |
| Ler um ficheiro PDF | Processos necessários para fazer o *input* da informação do ficheiro para o programa e interpretá-la.|
| Incorporar um browser HTML5 | Criar um conjunto de normas escritas no standard HTML5, que permitam utilizar as funções de leitura de ficheiros de forma a fazer o *display* do PDF num browser atual.|

## Requisitos específicos e funcionalides
O desenvolvimento deste projeto, para além da equipa inicial, depende muito da comunidade, dado que esta pode intervir ativamente neste processo.

Atualmente, as pessoas intervenientes no desenvolvimento do PDF.js trabalham para implementar novas funcionalidades e corrigir os vários issues existentes, de forma a tornar este projeto num grande sucesso.

A equipa de desenvolvimento fornece um guião em que explica de forma detalhada como é possível contribuir e sugerir novas ideias. Para além disso, é também fornecida uma lista com os vários bugs detetados, e esta pode sempre aumentar se alguém eventualmente descobrir novos problemas no programa.

Quando uma pessoa pretende contribuir com uma nova ideia ou mesmo corrigir bugs deve fazer o seguinte:
    1.Fork: Primeiro deve criar uma conta no GitHub e fazer fork do projeto.
    2.Criar uma branch: Depois de fazer fork, deve criar uma branch, idealmente com o nome da nova funcionalidade que pretende adicionar ou mesmo do bug que vai corrigir e trabalhar nesta.
    3.Editar: Após a criação da branch, o contribuidor deve fazer as alterações que entende de acordo com "coding style" exigido.
    4.Correr os testes: São fornecidos alguns testes, que devem ser usados para verificar se está tudo em ordem.
    5.Criar o Pull Request: Se tudo até este ponto estiver funcional, a pessoa pode criar o Pull Request e esperar que o código seja analisado.

Para além desta forma de contribuição, existem encontros semanais para a discussão do desenvolvimento do projeto. Qualquer pessoa pode aparecer no meeting e dar o seu ponto de vista sobre o projeto, sugerir novas ideias ou até mesmo apontar novos bugs.

Um dos principais requisitos é a possibilidade de usar o PDF.js em qualquer browser existente.


### Requerimentos funcionais

### Requerimentos não-funcionais

### Funcionalides

## Casos de uso

### Sistema

### Atores

### Casos de uso e relações

## Análise de domínio

## Contribuições

## Referências

https://andreasgal.com/2011/06/15/pdf-js/ - Consultado a 25 de outubro

