# Evolução de Software
<img src="http://www.junifeup.pt/wp-content/uploads/2016/01/feup.png" alt="Logo FEUP" width = "600" height ="200"/>
#### Relatório de Engenharia de Software

## Introdução

O pdf.js é uma aplicação que, como temos vindo a referir, já se encontra bem maturada. Com um período de desenvolvimento de mais de 4 anos e um âmbito de funcionalidades muito restrito, são muito poucos os *features* que podem ser adicionados a este leitor. No entanto, o projeto continua aberto ao desenvolvimento de novas funcionalidades, que são sobretudo pressionadas pelo aparecimento de uma nova plataforma que utilize o leitor.

## Identificação da nova funcionalidade

Apesar de raros, ainda há certos tipos de PDF que o pdf.js é incapaz de ler corretamente. No nosso relatório anterior, corrigimos um *bug* relacionado com a leitura de um formato muito específico de imagens, que se encontrava defeituoso. 

Ao interpretar o código dedicado à interpretação dessas imagens, descobrimos que o pdf.js não está preparado para ler um outro tipo de *bitmaps*, intimamente ligado àquele que era incorretamente renderizado. Este comportamento poderia ser considerado um *bug*, no entanto, é um caso particular que não está em parte alguma previsto pelo pdf.js. Desta forma, consideramo-lo uma adição ao projeto, ou seja, uma *feature*.

### Descrição detalhada da feature



