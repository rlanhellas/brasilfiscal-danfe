
# BrasilFiscal - DANFE API

## 1) O que é DANFE ?
Após emitir uma Nota Fiscal é necessário gerar um arquivo chamado DANFE. A DANFE é um arquivo PDF (na maioria dos casos) que contém as informações da nota fiscal emitida, para que possa ser entregue ao cliente e ele possa circular com a mercadoria com uma "Nota Fiscal Física". 

Um exemplo prático é quando você compra algum eletrodoméstico, neste caso você recebe ao final da compra uma Nota Fiscal impressa, essa é a chamada DANFE, pois a Nota Fiscal original é eletrônica e não palpável. 


## 2) Qual objetivo do "BrasilFiscal DANFE-API" ?
Emitir uma DANFE pode ser um processo um pouco complexo, visto que trata-se de um documento com muitos detalhes, formatações, código de barras e etc. Com a DANFE-API você gera este documento com apenas 1 requisição HTTP, ou seja, não importa qual linguagem o seu sistema seja desenvolvido e NÃO PAGA NADA por isso.

## 3) Como usar ? 
Para começar a emitir sua DANFE é muito simples, você só precisa fazer uma chamada HTTP POST para nossa API passando duas informações:
  - Conteúdo do XML da Nota convertido para BASE64 (obrigatório)
    O conteúdo do XML da sua nota é obrigatório e deve ser convertido para BASE64 antes de ser enviado, você pode converter internamente no seu sistema ou converter online, existem diversos sites que realizam essa tarefa, segue um exemplo: https://www.freeformatter.com/base64-encoder.html#ad-output. 

  
  - URL da sua Logomarca (opcional)
    A URL da sua logomarca é opcional, mas quando informada deve ser um endereço de uma imagem válida, ou seja, a página de destino deve ter apenas a imagem e nada mais. Sem conteúdo HTML, javascript e etc. 
    - Exemplo válido: https://http2.mlstatic.com/logomarca-logotipo-logo-criar-logo-marca-profissional-D_NQ_NP_21440-MLB20211035406_122014-F.jpg
    - Exemplo inválido: https://produto.mercadolivre.com.br/MLB-691563721-logomarca-logotipo-logo-criar-logo-marca-profissional-_JM
    
## 4) Dados para emissão
    
|Info  |Valor  |
|--|--|
|  Endereço para Emissão|http://brasilfiscal.querobuy.com.br:7000/brasilfiscal-danfe/v1/  |
|Parâmetro 1| Conteúdo XML em Base64 (obrigatório|
|Parâmetro 2| URL Logomarca (opcional)|
|Tipo Requisição|HTTP POST|
|Content-Type|application/json|
|Conteúdo da Resposta|application/octet-stream|

Note que a resposta sempre será um application/octet-stream, isso nada mais é do que um binário que você poderá converter conforme sua aplicação precisar. 

## 5) Exemplo prático

Você pode executar um exemplo completo e real através do cURL deste link: https://gist.github.com/rlanhellas/891b71f7c057d8b56ab9de9e6902e329. Este possui uma nota fiscal válida que gerará um DANFE válido.
    
 **- Usando cURL**
  
      curl -X POST \
      http://brasilfiscal.querobuy.com.br:7000/brasilfiscal-danfe/v1/ \
      -H 'Cache-Control: no-cache' \
      -H 'Content-Type: application/json' \
      -H 'Postman-Token: 8f842fde-70ee-4856-b126-8fe6b253e03e' \
      -d '{
      "urlLogmarca": "https://http2.mlstatic.com/logomarca-logotipo-logo-criar-logo-marca-profissional-D_NQ_NP_21440-MLB20211035406_122014-F.jpg",
      "xml": "Conteudo do seu XML em BASE64"
    }' >> teste.pdf

 **- Usando PHP** 
 

     <?php
    
    $request = new HttpRequest();
    $request->setUrl('http://brasilfiscal.querobuy.com.br:7000/brasilfiscal-danfe/v1/');
    $request->setMethod(HTTP_METH_POST);
    
    $request->setHeaders(array(
      'Postman-Token' => 'ddcc1f1a-dd26-4f6f-a38b-12498801f4cd',
      'Cache-Control' => 'no-cache',
      'Content-Type' => 'application/json'
    ));
    
    $request->setBody('{
      "urlLogmarca": "https://http2.mlstatic.com/logomarca-logotipo-logo-criar-logo-marca-profissional-D_NQ_NP_21440-MLB20211035406_122014-F.jpg",
      "xml":"Conteudo em BASE64"
    }');
    
    try {
      $response = $request->send();
    
      echo $response->getBody();
    } catch (HttpException $ex) {
      echo $ex;
    }

**- Usando Java**

    HttpResponse<String> response = Unirest.post("http://brasilfiscal.querobuy.com.br:7000/brasilfiscal-danfe/v1/")
      .header("Content-Type", "application/json")
      .header("Cache-Control", "no-cache")
      .header("Postman-Token", "90ba1277-8f8f-4c29-9a6d-bc2cb91cebaf")
      .body("{\n  \"urlLogmarca\": \"https://http2.mlstatic.com/logomarca-logotipo-logo-criar-logo-marca-profissional-D_NQ_NP_21440-MLB20211035406_122014-F.jpg\",\n  \"xml\": \"Conteudo BASE64\"\n}")
      .asString();

**- Usando Swagger**
Se você preferir também poderá acessar nossa API via Web através do endereço: http://brasilfiscal.querobuy.com.br:7000/brasilfiscal-danfe/swagger-ui.html. 
Através deste endereço você poderá realizar a chamar ao DANFE-API sem precisar codificar nada.

# Duvidas ? 
Faça parte do nosso canal no slack: brasilfiscal.slack.com. Lá você terá o canal "danfe-api".
