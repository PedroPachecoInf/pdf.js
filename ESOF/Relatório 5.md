# Evolução de Software
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

O pdf.js é uma aplicação que, como temos vindo a referir, já se encontra bem maturada. Com um período de desenvolvimento de mais de 4 anos e um âmbito de funcionalidades muito restrito, são muito poucos os *features* que podem ser adicionados a este leitor. No entanto, o projeto continua aberto ao desenvolvimento de novas funcionalidades, que são sobretudo pressionadas pela evolução das plataformas suportadas pelo leitor.

## Manutenção do pdf.js

[TODO: falar da importância da manutenção no pdf.js (por ex., estar sempre a par com as evoluções do Mozilla Firefox). Comentar que por causa de o método usado ser o Agile, o software já está preparado para a evolução/mudança.]

### Implementação de alterações

[TODO: ver slides 10 e 11 da evolução de software e falar do processo de implementação de alterações]

### Análise métrica do *Better Code Hub*

![Write Short Units of Code](./Relatório 5/BCH-ShortUnits.png)


![Write Simple Units of Code](./Relatório 5/BCH-SimpleUnits.png)


![Write Code Once](./Relatório 5/BCH-CodeOnce.png)


![Keep Unit Interfaces Small](./Relatório 5/BCH-InterfacesSmall.png)


![Separate Concerns in Modules](./Relatório 5/BCH-SeparateConcerns.png)


![Couple Architecture Components Loosely](./Relatório 5/BCH-CompsLoosely.png)


![Keep Architecture Components Balanced](./Relatório 5/BCH-CompsBalanced.png)


![Keep Your Codebase Small](./Relatório 5/BCH-CodebaseSmall.png)


![Automate Tests](./Relatório 5/BCH-AutomateTests.png)


![Write Clean Code](./Relatório 5/BCH-CleanCode.png)



[TODO: correr o repositório no Better Code Hub e meter prints dos resultados, assim como comentá-los e como se poderia melhorar o que está mal (muito breve)]


## Identificação da nova funcionalidade

Apesar de raros, ainda há certos tipos de PDF que o pdf.js é incapaz de ler corretamente. No nosso relatório anterior, corrigimos um *bug* relacionado com a leitura de um formato muito específico de imagens, que se encontrava defeituoso. 

Ao interpretar o código dedicado à interpretação dessas imagens, descobrimos que o pdf.js não está preparado para ler um outro tipo de *bitmaps*, intimamente ligado àquele que era incorretamente renderizado. Este comportamento poderia ser considerado um *bug*, no entanto, é um caso particular que não está em parte alguma previsto pelo pdf.js. Desta forma, consideramo-lo uma adição ao projeto, ou seja, uma *feature*.

### Descrição detalhada da funcionalidade

> "A bilevel image contains two colors—black and white. TIFF allows an application to write out bilevel data in either a white-is-zero or black-is-zero format. The field that records this information is called PhotometricInterpretation."

> *TIFF specification 6.0*

Como tal, a forma como o pdf.js lê um bit depende da tag *PhotmetricInterpretation*, que quando tem o valor igual a 0 dita que um bit a 0 representa a cor branca e que quando tem o valor igual a 1 dita que um bit a 0 tem a cor preta.

O problema com que nos deparámos para implementar esta funcionalidade foi a falta de recursos para testar: não encontrámos nem conseguimos criar nenhuns PDFs com valores de *PhotmetricInterpretation* diferentes. Para implementar a nossa funcionalidade testámo-la invertendo as cores do PDF utilizado para corrigir o *bug*.

Black-is-zero           |  White-is-zero
:-------------------------:|:-------------------------:
![](./Relatório 4/PDF-fixed.png)  |  ![](./Relatório 5/inverted-colors.png)

Prevemos que um PDF com *white-is-zero* esteja codificado de forma a que as cores apareçam de forma correta e não invertidas, visto que aquilo que é necessário é apenas alterar a forma como se lê o bit.

### Implementação da funcionalidade

O bloco de código que implementa a *feature* é o mesmo que estudámos para a reparação do *bug*. A alteração que é efetuada altera o valor da variável "complement" de acordo com a tag *PhotometricInterpretation* da imagem TIFF:

```javascript
if (bits === 1) {
   if(PhotometricInterpretation == black-is-zero){
      var complement = 0;
   }
   else{
      var complement = 1;
   }
    var bitOrder = 0;

   for(i=0; i < rowBytes; ++i) {

      inbuf = (inbuf << 8) | (rawBytes[i] & 0xFF);

      for(bitOrder=7; bitOrder>=0; --bitOrder) {
          complement = (complement + (inbuf >> bitOrder)) & 0x1;
          outbuf = (outbuf << 1) | complement;
      }
      buffer[pos++] = (outbuf & 0xFF);
    }
}
```

Este código não está implementado, de momento, ainda não arranjámos forma de obter a *tag* a partir do PDF. No entanto, é ilustrativo do que faremos com esse valor assim que o obtivermos.

## Submissão da funcionalidade

Como a resolução do *bug* e a *feature* estão intimamente ligados, a sua sugestão foi feita no mesmo [*pull request*](https://github.com/mozilla/pdf.js/pull/7869), sendo que estamos em comunicação com a equipa do pdf.js não só através do GitHub, mas também através do seu canal IRC, para discutir melhoramentos em termos de eficiência de processamento e como obter a informação que resta para implementar a funcionalidade.

## Contribuição

Todos os elementos do grupo contribuíram de forma equivalente para a produção deste relatório.

