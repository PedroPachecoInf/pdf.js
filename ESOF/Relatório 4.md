# Verificação e Validação
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

Neste relatório, vamos fazer uma análise aos testes de software no PDF.js.Testar o software significa correr testes específicos para cada parte do programa, e observar se ele se comporta da forma esperada, ou se não, foi decoberto um *bug*.

Sendo assim, vamos avaliar a qualidade e a quantidade dos testes de software,testes estes que são disponibilizados pelos *developers* do projeto.

A verificação e validação permitem-nos compreender se o projeto está a ser construído corretamente e se tem as funcionalidades corretas.

Faremos então umas estatísticas relativas aos testes e depois apresentaremos uma possível solução para um dos *bugs* do programa.

## Testabilidade e revisão de software

O pdf.js possui uma suite de testes no seu respositório que é atualizada ao longo do seu desenvolvimento. Os testes avaliam todas as componentes do pdf.js: o *render*, *display* e a interface gráfica, sendo mais focados no *render*. É essencial para o pdf.js que o seu grau de testabilidade seja elevado, pois apesar de estar maturo, o programa continua a precisar de updates. Para facilitar este processo de evolução, as ferramentas de testes devem permitir que qualquer erro seja detetado facilmente.

### Controlabilidade

A controlabilidade determina o trabalho necessário para testar os casos de utilização de uma CUT (*Component Under Test*), ou seja, o quão fácil é obter o input necessário para replicar o funcionamento da CUT. No caso do pdf.js é algo bastante simples, visto que o input necessário para testar **todas** as suas funcionalidades é um simples ficheiro de PDF. Para testar componentes individualmente basta isolar um pedaço de um PDF (uma stream de informação) e usá-la como argumento desse módulo. A controlabilidade diminui com o grau de dependência do módulo que está a ser testado, no entanto no pdf.js não há módulos com dependências tão complexas que aumentem significativamente a sua controlabilidade.

### Observabilidade

O grau de observabilidade de um software é maior quanto maior for a facilidade em verificar os resultados de um teste. A suite de testes do pdf.js é toda automaticamente corrida a partir do comando "gulp test", mostrando em tempo de execução os testes que passam e que falham, pelo que é extremamente fácil observar o resultado de testes incluídos no projeto. 

Além disso, caso se queira correr apenas testes unitários, o pdf.js utiliza a ferramenta Jasmine que, através do browser, mostra os testes unitários realizados, assim como o resultado de cada teste.

### Isolabilidade

Sendo a arquitetura do pdf.js modular, a sua isolabilidade vai depender de módulo para módulo, tal como a controlabilidade. Quantas mais dependências um módulo tiver, mais difícil é isolar os seus testes, pois sofre influências de várias partes. Por exemplo, se um determinado módulo necessitar de funções de 5 outros módulos para executar uma função sua, ao testar essa função é difícil perceber se um erro que surja advém do próprio módulo ou de um módulo exterior.

### Separação de tarefas

Por estar desenhado por módulos, a separação de tarefas do pdf.js está muito bem definida. Tanto os nomes dos ficheiros de JavaScript como os nomes das funções contribuem para o entendimento daquilo que aquela secção de código faz. Tarefas que sejam mais complexas são divididas em tarefas menores, de forma a delinear ainda mais a arquitetura modular. Por exemplo, a função do ficheiro "stream.js", que lê uma imagem e faz o seu *decode* chama, consoante o tipo de imagem, funções diferentes, para retornar o resultado. Essas funções, por sua vez, são divididas em outras menos complexas, que lêem separadamente o cabeçalho e o corpo da imagem.

### Percetibilidade

O pdf.js peca em termos de documentação, visto que não há uma definição explícita daquilo que cada módulo e função faz. 

No entanto, graças à sua eficiente separação de tarefas e nomenclatura de funções/módulos, é possível perceber o que o código faz simplesmente lendo-o. A sua sintaxe é bem estruturada e alguns comentários guiam o leitor por partes mais complicadas de código.

### Heterogeneidade

A heterogeneidade do pdf.js é baixa, pois não há grande diversidade nas ferramentas que usa. Não inclui nenhuma framework nem biblioteca de funções. Apenas faz uso das funcionalidades de um browser, mas por ser escrito em JavaScript, isto não tem impacto na heterogeneidade. Por isso mesmo, apenas é necessário um tipo de ferramenta para cada forma de teste:

- Testes unitários: [Jasmine](https://jasmine.github.io/) e [JS Test Driver](https://code.google.com/archive/p/js-test-driver/) para display em HTML dos testes;
- Teste de regressão: NodeJS para criar um servidor capaz de hospedar o pdf.js

## Estatisticas e Análises dos Testes

Para verificarmos a validade do software, um dos métodos por excelência são os testes.
Assim sendo, procurámos ao máximo analizar as várias capacidades destes testes e também onde estão as suas limitações.

Os testes estão divididos em 5 categorias que testam diferentes aspetos:

- **load**: verifica se o PDF é carregado sem crashar

- **eq**: verifica detalhes relacionados com a renderização

- **text**: verifica detalhes relacionados com a *textLayer*

- **annotations**: verifica detalhes relacionados com a *annotationLayer* (e a página subjacente)

- **fbf**: um teste *forward-back-forward*

- **unit tests**: 378 testes unitários *Jasmine* (corridos separadamente dos acima), também divididos em categorias de acordo com os aspetos a testar:
  - *primitives* (33)
  - *CFFParser* (20)
  - *CFFCompiler* (2)
  - *Type1Parser* (10)
  - *Fonts* (1)
  - *unicode* (11)
  - *function* (79)
  - *crypto* (33)
  - *CipherTransformFactory* (15)
  - *evaluator* (17)
  - *stream* (8)
  - *parser* (12)
  - *api* (53)
  - *metadata* (2)
  - *ui_utils* (11)
  - *util* (20)
  - *cmap* (12)
  - *Annotation layer* (55)
  - *network* (3)
  - *dom_utils* (4)

### Testes *eq*

Os testes "eq" (equal) são utilizados para verificar se o código alterado traz alguma **regressão**, isto é, se alterou outros aspetos que diminuam a qualidade do programa. 

A Mozilla utiliza *snapshots* de PDFs que se sabe estarem corretamente renderizados e compara-os com os PDFs gerados com o novo código. Se os resultados forem iguais, o código não traz nenhuma regressão em relação ao render desses ficheiros.

### Quantidade de testes

A suite completa de testes fornecida pelo pdf.js é corrida utilizando o comando "gulp test", que cria um processo no browser que executa todos o ficheiros do diretório "test".

Há 378 testes unitários, como já foi referido, assim como 436 *snapshots* de PDF para testar regressões e 6 ficheiros de testes relativos a fontes de texto. Tudo isto demora cerca de 15 minutos a executar.

Podemos assumir que, pela integridade da Mozilla, os testes são todos necessários e testam partes independentes. Como o pdf.js é um sofwtare relativamente simples, podemos afirmar que é bem robusto a nível de testabilidade.

### Cobertura dos testes

De modo a analizar a qualidade dos testes foi utilizada a ferramenta JSCover. Após a sua utilização obteve-se uma percentagem de cobertura total de apenas 59%, o que encontra abaixo das espetativas.

  <img src=".\Relatório 4\coverage1.png" alt="coverage1">
  <img src=".\Relatório 4\coverage2.png" alt="coverage2">

### "Flaky Tests"

Ao longo das várias vezes que corremos a framework de testes, os resultados destes foram consistentes, e portanto não encontramos nenhum *flaky test*.

## Identificação e correção de um bug

O *pdf.js* é uma ferramenta suportada pelo Mozilla, que se define como uma fonte de open-source de qualidade, e é utilizado no próprio Firefox, pelo que a quantidade de *bugs* que existe no código acaba por ser mínima. Muitos têm a ver com *tweaks* que a interface possa ter e alguns com problemas de compatibilidade.

Seria muito complicado testar o pdf.js para problemas de compatibilidade, pois o nosso grupo não tem acesso a terminais com características variadas. Assim, a nossa abordagem para a descoberta de bugs foi testar o *reader* para verificar se ele funcionava para diversos tipos de PDF.

Um dos ficheiros que testámos foi o seguinte: [PDF-TIFF-1-bit-depth.pdf](.\Relatório 4\PDF-TIFF-1-bit-depth.pdf), que é um PDF que inclui uma imagem em formato TIFF com apenas 1 bit de profundidade de cor. 

A forma que o pdf.js tem de ler uma imagem é determinar o formato de imagem e depois invocar a função apropriada para ler o bloco de bytes. No caso do TIFF, essa função é a readBlockTiff() que se encontra no ficheiro src/stream.js, especificamente nas linhas 742-752:

```javascript
    if (bits === 1) {
      for (i = 0; i < rowBytes; ++i) {
        var c = rawBytes[i];
        inbuf = (inbuf << 8) | c;
        // bitwise addition is exclusive or
        // first shift inbuf and then add
        buffer[pos++] = (c ^ (inbuf >> colors)) & 0xFF;
        // truncate inbuf (assumes colors < 16)
        inbuf &= 0xFFFF;
      }
    }
```

O que acontece é que a imagem é lida com defeitos a nível de resolução e com as cores invertidas (*background* preto e letras brancas):

<img src=".\Relatório 4\PDF-Bugged.png" alt="bugged PDF">

Ao lermos a especificação do formato TIFF, percebemos que a leitura dos bytes da imagem estava a ser feita de forma incorreta. No código original, lê-se um byte inteiro, e faz-se a soma das componentes de cada cor através do XOR. 

No entanto, a forma correta de interpretar é lendo a informação **bit a bit**. Sempre que aparecer um bit a 1 num determinado byte original, o bit *decoded* altera-se para o oposto ao bit anterior. Se for 0, continua igual.

Por exemplo, em TIFF, a cor preta com 1 bit de profundidade é representada pelo decimal 128, que é 1000 0000 em binário. No código errado, o byte resultante seria 1100 0000 que equivale a 192 e todos os bits daí em diante são 0, pelo que apareceria um pixel a um tom mais branco (192) e os restantes a preto (0), que resulta nas letras brancas e background preto. Além disso, por se estar a ler o byte por inteiro, perde-se resolução.

A nossa reformulação de código tem isto em conta e soluciona o problema:

```javascript
if (bits === 1) {
      var complement = 0;
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

Esta implementação é mais custosa em processamento, pois lê cada bit separadamente, poussindo 8 vezes mais iterações que a original. No entanto é apenas 50% mais lenta e resolve o problema da resolução e da cor, mostrando o pdf como é suposto:

 <img src=".\Relatório 4\PDF-fixed.png" alt="fixed PDF">

No momento da escrita deste relatório, o nosso grupo encontrava-se em comunicação com os responsáveis pelo pdf.js para a possível incorporação deste *fix* no projeto original, via IRC. Se obtivermos luz verde, avançamos com o *pull request*. 

## Contribuição

Todos os membros contribuiram de forma igual para a elaboração do relatório.

## Referências

https://en.wikipedia.org/wiki/Software_testability -  consultado a 2 de Dezembro de 2016
http://robertvbinder.com/software-testability-part-2-controllability-and-observability/ - consultado a 3 de Dezembro de 2016

https://moodle-arquivo.ciencias.ulisboa.pt/1415/pluginfile.php/108074/mod_resource/content/1/vvs-slides-13.pdf - consultado a 3 de Dezembro de 2016