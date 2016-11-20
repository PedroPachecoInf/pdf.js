# Arquitetura do software
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

A arquitetura de um software define os componentes da aplicação, as suas relações e as suas dependências externas, em função dos requisitos. Um software bem desenhado facilita a criação dos seus constituintes e permite idealizar padrões para relacionar e reutilizar componentes. 

### Modelo de visualização 4+1

O modelo de visualização 4+1 permite visualizar a arquitetura do software a partir de quatro pontos de vista concorrentes:

- vista de **lógica** (*logical view*);
- vista de **implementação** (*implementation view*);
- vista de **implantação** (*deployment view*);
- vista de **processos** (*process view*).

Estas vistas premitem incluir a perspetivas de todos os *stakeholders* do projeto, sejam eles os próprios *developers*, utilizadores ou *project managers*. 

Há ainda uma quinta perspetiva resultante da conjunção das referidas: a vista de **casos de uso**. Esta vista ilustra o cenário ao qual a arquitetura pode ser aplicada, tendo em conta tudo aquilo que o constitui.

### Padrão de arquitetura do pdf.js

O padrão de arquitetura utilizado pelo pdf.js é o **Asynchronous Module Definition** (AMD). Este padrão tem como objetivo facilitar a abordagem modular em JavaScript, permitindo que tanto o módulo como as suas dependências sejam carregas de forma assíncrona.

O pdf.js recorre à invocação de um conjunto de módulos escritos em UMD ([Universal Module Definition](https://github.com/umdjs/umd)) para o seu funcionamento, que tem o AMD por base, mas é compatível com um maior número de *loaders* de JS. As funcionalides destes módulos incluem o *parsing, render e display* de ficheiros PDF. Este módulos são todos carregados ao mesmo tempo, pelo que a arquitetura do pdf.js deve ter em conta as dependências de cada um.

>"(...) in the PDF.js library we use Promises."
[*Displaying PDF files with PDF.js library*](https://developer.tizen.org/community/tip-tech/displaying-pdf-files-pdf.js-library)

A arquitetura do *pdf.js* sustenta-se no conceito de [*Promises*](https://www.promisejs.org/ "Promise.js HomePage"), que é bastante utilizado em JavaScript para aplicações que utilizam vários recursos e comunicam de forma **assíncrona**. *Promises* facilita a aplicação da comunicação assíncrona em programas de JS, para evitar que uma função bloqueie o resto do código. 

O elemento básico de *Promises* é a "promessa". Uma promessa representa o resultado de uma operação assíncrona e pode estar em três estados diferentes:

- **pendente**: estado inicial da promessa;
- **realizada**: estado que representa uma operação bem-sucedida;
- **rejeitada**: estado que representa uma operação mal-sucedida.

O pdf.js usa estas promessas para carregar todos os módulos sem haver atrasos de espera por ficheiros mais extensos. 

## Implementation view

Numa vista de implementação, é mostrada a forma como o software pode ser decompostos em várias componentes para desenvolvimento, ou seja, aquilo que é efetivamente necessário criar para que o programa funcione.

No pdf.js, as suas componentes são módulos inter-dependentes que, quando carregados de forma bem sucedida, permitem lançar a aplicação. No diagrama seguinte, encontram-se demonstradas as dependências dos módulos "*core*" do pdf.js, que lidam principalmente com o processamento de informação. Este conjunto de componentes é depois interligado com as componenentes "*display*", para que os dados processados sejam imprimidos no ecrã.

<img src=".\Relatório 3 - Esquemas\Development View.png" alt="development view">

## Deployment View

Nesta vista, percebemos onde e como podemos implementar o pdf.js. Verificamos que este tanto pode ser implementado num computador com recurso à clonagem do repositorio e posterior compilação (modo mais usado por developers), ou com recurso à simples adição das dependências e consequente integração no código dum website.

<img src = ".\Relatório 3 - Esquemas\Deployment View.png" alt = "deployment view">


## Contribuição

Todos os membros do grupo contribuiram de forma equitativa para a elaboração deste relatório.

## Referências

https://developer.tizen.org/community/tip-tech/displaying-pdf-files-pdf.js-library - consultado a 17 de Novembro de 2016

https://www.promisejs.org/ - consultado a 17 de Novembro de 2016

### APAGAR
------------------------------------

Links úteis: https://addyosmani.com/resources/essentialjsdesignpatterns/book/

http://www.oreilly.com/programming/free/files/software-architecture-patterns.pdf

https://developer.tizen.org/community/tip-tech/displaying-pdf-files-pdf.js-library

Divisão:

-Vinte: Process View
-Duque: Deployment View
-Pacheco: Logical View
-Aleixo: Development View