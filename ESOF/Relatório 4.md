# Verificação e Validação
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

Neste relatório, vamos fazer uma análise aos testes de software no PDF.js.Testar o software significa correr testes específicos para cada parte do programa, e observar se ele se comporta da forma esperada, ou se não, foi decoberto um bug.Sendo assim, vamos avaliar a qualidade e a quantidade dos testes de software,testes estes que são disponibilizados pelos *developers* do projeto.
A verificação e validação permitem-nos compreender se o projeto está a ser construído corretamente e se tem as funcionalidades corretas.Faremos então umas estatísticas relativas aos testes e depois apresentaremos uma possível solução para um dos bugs do programa.

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
..- *primitives* (33)
..- *CFFParser* (20)
..- *CFFCompiler* (2)
..- *Type1Parser* (10)
..- *Fonts* (1)
..- *unicode* (11)
..- *function* (79)
..- *crypto* (33)
..- *CipherTransformFactory* (15)
..- *evaluator* (17)
..- *stream* (8)
..- *parser* (12)
..- *api* (53)
..- *metadata* (2)
..- *ui_utils* (11)
..- *util* (20)
..- *cmap* (12)
..- *Annotation layer* (55)
..- *network* (3)
..- *dom_utils* (4)

### Quantidade de testes

Ainda é preciso, tendo em conta a lista acima???
Provavelmente era mais fácil completar a lista acima

### Cobertura dos testes

### "Flaky Tests"

Ao longo das várias vezes que corremos a framework de testes, os resultados destes foram consistentes, e portanto não encontramos nenhum *flaky test*.

## Identificação e correção de um bug

[TO DO]



## Contribuição

BOTA TRABALHAR PESSOAL!

## Referências

