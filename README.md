
# BrasilFiscal - DANFE API

## 1) O que é DANFE ?
Após emitir uma Nota Fiscal é necessário gerar um arquivo chamado DANFE. A DANFE é um arquivo PDF (na maioria dos casos) que contém as informações da nota fiscal emitida, para que possa ser entregue ao cliente e ele possa circular com a mercadoria com uma "Nota Fiscal Física". 

Um exemplo prático é quando você compra algum eletrodoméstico, neste caso você recebe ao final da compra uma Nota Fiscal impressa, essa é a chamada DANFE, pois a Nota Fiscal original é eletrônica e não palpável. 


## 2) Qual objetivo do "BrasilFiscal DANFE-API" ?
Emitir uma DANFE pode ser um processo um pouco complexo, visto que trata-se de um documento com muitos detalhes, formatações, código de barras e etc. Com a DANFE-API você gera este documento com apenas 1 requisição HTTP, ou seja, não importa qual linguagem o seu sistema seja desenvolvido e NÃO PAGA NADA por isso.

## 3) Como usar ? 
Para usar é muito simples, você só precisa fazer uma requisição HTTP para nossa API, os exemplos podem ser encontrados e testados através do Swagger na seguinte URL: http://brasilfiscal.querobuy.com.br:8762/brasilfiscal-danfe/swagger-ui.html#/danfe-resource. 

Importante:
1) O envio do XML deve ser feito em BASE64
2) A resposta do serviço com o PDF gerado também será em BASE64

# Duvidas ? 
Faça parte do nosso canal no slack: brasilfiscal.slack.com. 
