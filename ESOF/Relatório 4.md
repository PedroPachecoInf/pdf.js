# Verificação e Validação
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

Neste relatório, vamos fazer uma análise aos testes de software no PDF.js.Testar o software significa correr testes específicos para cada parte do programa, e observar se ele se comporta da forma esperada, ou se não, foi decoberto um *bug*.
Sendo assim, vamos avaliar a qualidade e a quantidade dos testes de software,testes estes que são disponibilizados pelos *developers* do projeto.
A verificação e validação permitem-nos compreender se o projeto está a ser construído corretamente e se tem as funcionalidades corretas.
Faremos então umas estatísticas relativas aos testes e depois apresentaremos uma possível solução para um dos *bugs* do programa.

## ???

[TO DO]
[Tb tem de se dizer que, depois de um pull request, sao executados testes automaticos e fazem-se reviews]


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
  - *Type1Parser* (10)# Verificação e Validação

## Introdução

Neste relatório, vamos fazer uma análise aos testes de software no PDF.js.Testar o software significa correr testes específicos para cada parte do programa, e observar se ele se comporta da forma esperada, ou se não, foi decoberto um *bug*.
Sendo assim, vamos avaliar a qualidade e a quantidade dos testes de software,testes estes que são disponibilizados pelos *developers* do projeto.
A verificação e validação permitem-nos compreender se o projeto está a ser construído corretamente e se tem as funcionalidades corretas.
Faremos então umas estatísticas relativas aos testes e depois apresentaremos uma possível solução para um dos *bugs* do programa.

## ???

[TO DO]
[Tb tem de se dizer que, depois de um pull request, sao executados testes automaticos e fazem-se reviews]


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

### Quantidade de testes

[Comentario]

Ainda é preciso, tendo em conta a lista acima???

Provavelmente era mais fácil completar a lista acima. Digam o que acham

### Cobertura dos testes

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

<img src=".\Relatório 4\PDF-bugged.png" alt="bugged PDF">

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

Esta implementação é mais custosa em processamento, pois lê cada bit separadamente, poussindo 8 vezes mais iterações que a original. No entanto é apenas 50% mais lenta e resolve o problema da resolução e dar cor, mostrando o pdf como é suposto:

 <img src=".\Relatório 4\PDF-fixed.png" alt="fixed PDF">

No momento da escrita deste relatório, o nosso grupo encontrava-se em comunicação com os responsáveis pelo pdf.js para a possível incorporação deste *fix* no projeto original, via IRC. Se obtivermos luz verde, avançamos com o *pull request*. 

## Contribuição

BOTA TRABALHAR PESSOAL!

## Referências


  -
