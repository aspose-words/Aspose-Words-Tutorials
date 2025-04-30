---
"description": "Otimize o gerenciamento de documentos com o Aspose.Words para Java. Aprenda a trabalhar com propriedades de documentos, adicionar metadados personalizados e muito mais neste tutorial abrangente."
"linktitle": "Usando propriedades do documento"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Usando propriedades de documento no Aspose.Words para Java"
"url": "/pt/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando propriedades de documento no Aspose.Words para Java


## Introdução às Propriedades do Documento

As propriedades do documento são uma parte vital de qualquer documento. Elas fornecem informações adicionais sobre o próprio documento, como título, autor, assunto, palavras-chave e muito mais. No Aspose.Words para Java, você pode manipular propriedades de documento integradas e personalizadas.

## Enumerando Propriedades do Documento

### Propriedades integradas

Para recuperar e trabalhar com propriedades de documentos integradas, você pode usar o seguinte trecho de código:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Este código exibirá o nome do documento e as propriedades internas, incluindo propriedades como "Título", "Autor" e "Palavras-chave".

### Propriedades personalizadas

Para trabalhar com propriedades de documentos personalizadas, você pode usar o seguinte trecho de código:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Este trecho de código demonstra como adicionar propriedades de documento personalizadas, incluindo um valor booleano, uma string, uma data, um número de revisão e um valor numérico.

## Removendo Propriedades do Documento

Para remover propriedades específicas do documento, você pode usar o seguinte código:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Este código remove a propriedade personalizada "Data de autorização" do documento.

## Configurando Link para Conteúdo

Em alguns casos, você pode querer criar links dentro do seu documento. Veja como fazer isso:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Adicionar vinculado à propriedade de conteúdo.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Este trecho de código demonstra como criar um marcador no seu documento e adicionar uma propriedade de documento personalizada que vincula esse marcador.

## Conversão entre unidades de medida

No Aspose.Words para Java, você pode converter unidades de medida facilmente. Veja um exemplo de como fazer isso:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Defina margens em polegadas.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Este trecho de código define várias margens e distâncias em polegadas, convertendo-as em pontos.

## Usando caracteres de controle

Caracteres de controle podem ser úteis ao lidar com texto. Veja como substituir um caractere de controle no seu texto:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Substitua o caractere de controle "\r" por "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Neste exemplo, substituímos o retorno de carro (`\r`) com um retorno de carro seguido por uma quebra de linha (`\r\n`).

## Conclusão

As propriedades do documento desempenham um papel significativo no gerenciamento e organização eficazes dos seus documentos no Aspose.Words para Java. Seja trabalhando com propriedades integradas, propriedades personalizadas ou usando caracteres de controle, você tem uma variedade de ferramentas à sua disposição para aprimorar seus recursos de gerenciamento de documentos.

## Perguntas frequentes

### Como posso acessar as propriedades integradas do documento?

Para acessar as propriedades do documento integradas no Aspose.Words para Java, você pode usar o `getBuiltInDocumentProperties` método sobre o `Document` objeto. Este método retorna uma coleção de propriedades internas que você pode iterar.

### Posso adicionar propriedades personalizadas a um documento?

Sim, você pode adicionar propriedades de documento personalizadas a um documento usando o `CustomDocumentProperties` coleção. Você pode definir propriedades personalizadas com vários tipos de dados, incluindo strings, booleanos, datas e valores numéricos.

### Como posso remover uma propriedade de documento personalizada específica?

Para remover uma propriedade específica de documento personalizado, você pode usar o `remove` método sobre o `CustomDocumentProperties` coleção, passando como parâmetro o nome da propriedade que você deseja remover.

### Qual é o propósito de criar um link para o conteúdo dentro de um documento?

Criar links para o conteúdo de um documento permite criar referências dinâmicas para partes específicas do documento. Isso pode ser útil para criar documentos interativos ou referências cruzadas entre seções.

### Como posso converter entre diferentes unidades de medida no Aspose.Words para Java?

Você pode converter entre diferentes unidades de medida no Aspose.Words para Java usando o `ConvertUtil` classe. Ela fornece métodos para converter unidades como polegadas para pontos, pontos para centímetros e muito mais.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}