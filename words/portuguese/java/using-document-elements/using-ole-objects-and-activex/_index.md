---
"description": "Aprenda a usar objetos OLE e controles ActiveX no Aspose.Words para Java. Crie documentos interativos com facilidade. Comece agora!"
"linktitle": "Usando objetos OLE e controles ActiveX"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Usando objetos OLE e controles ActiveX no Aspose.Words para Java"
"url": "/pt/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando objetos OLE e controles ActiveX no Aspose.Words para Java

Neste tutorial, exploraremos como trabalhar com objetos OLE (Object Linking and Embedding) e controles ActiveX no Aspose.Words para Java. Objetos OLE e controles ActiveX são ferramentas poderosas que permitem aprimorar seus documentos incorporando ou vinculando conteúdo externo, como planilhas, arquivos multimídia ou controles interativos. Acompanhe enquanto nos aprofundamos nos exemplos de código e aprendemos a usar esses recursos de forma eficaz.

### Pré-requisitos

Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:

1. Aspose.Words para Java: Certifique-se de ter a biblioteca Aspose.Words instalada no seu projeto Java. Você pode baixá-la em [aqui](https://releases.aspose.com/words/java/).

2. Ambiente de desenvolvimento Java: você deve ter um ambiente de desenvolvimento Java funcional configurado no seu sistema.

### Inserindo um objeto OLE

Vamos começar inserindo um objeto OLE em um documento do Word. Criaremos um documento simples do Word e, em seguida, inseriremos um objeto OLE representando uma página da web.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", verdadeiro, verdadeiro, nulo);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Neste código, criamos um novo documento e inserimos um objeto OLE que exibe o site Aspose. Você pode substituir a URL pelo conteúdo desejado.

### Inserindo um objeto OLE com OlePackage

A seguir, vamos explorar como inserir um objeto OLE usando um OlePackage. Isso permite que você incorpore arquivos externos como objetos OLE no seu documento.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

Neste exemplo, inserimos um objeto OLE usando um OlePackage, permitindo que você inclua arquivos externos como objetos incorporados.

### Inserindo um objeto OLE como um ícone

Agora, vamos ver como inserir um objeto OLE como um ícone. Isso é útil quando você deseja exibir um ícone representando um arquivo incorporado.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

Neste código, inserimos um objeto OLE como um ícone, fornecendo uma representação visualmente mais atraente do conteúdo incorporado.

### Lendo propriedades de controle ActiveX

Agora, vamos focar nos controles ActiveX. Aprenderemos como ler as propriedades dos controles ActiveX em um documento do Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

Neste código, iteramos pelas formas em um documento do Word, identificamos controles ActiveX e recuperamos suas propriedades.

### Conclusão

Parabéns! Você aprendeu a trabalhar com objetos OLE e controles ActiveX no Aspose.Words para Java. Esses recursos abrem um mundo de possibilidades para a criação de documentos dinâmicos e interativos.

### Perguntas frequentes

### Qual é a finalidade dos objetos OLE em um documento do Word? 
   - Objetos OLE permitem que você incorpore ou vincule conteúdo externo, como arquivos ou páginas da web, dentro de um documento do Word.

### Posso personalizar a aparência de objetos OLE no meu documento? 
   - Sim, você pode personalizar a aparência de objetos OLE, incluindo a configuração de ícones e nomes de arquivos.

### O que são controles ActiveX e como eles podem aprimorar meus documentos? 
   - Os controles ActiveX são elementos interativos que podem adicionar funcionalidade aos seus documentos do Word, como controles de formulário ou players multimídia.

### O Aspose.Words para Java é adequado para automação de documentos em nível empresarial? 
   - Sim, o Aspose.Words para Java é uma biblioteca poderosa para automatizar a geração e manipulação de documentos em aplicativos Java.

### Onde posso obter acesso ao Aspose.Words para Java? 
   - Você pode baixar Aspose.Words para Java em [aqui](https://releases.aspose.com/words/java/).

Comece a usar o Aspose.Words para Java hoje mesmo e libere todo o potencial de automação e personalização de documentos!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}