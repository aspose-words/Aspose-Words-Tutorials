---
"description": "Lär dig använda OLE-objekt och ActiveX-kontroller i Aspose.Words för Java. Skapa interaktiva dokument enkelt. Kom igång nu!"
"linktitle": "Använda OLE-objekt och ActiveX-kontroller"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda OLE-objekt och ActiveX-kontroller i Aspose.Words för Java"
"url": "/sv/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda OLE-objekt och ActiveX-kontroller i Aspose.Words för Java

den här handledningen utforskar vi hur man arbetar med OLE-objekt (Object Linking and Embedding) och ActiveX-kontroller i Aspose.Words för Java. OLE-objekt och ActiveX-kontroller är kraftfulla verktyg som låter dig förbättra dina dokument genom att bädda in eller länka externt innehåll, till exempel kalkylblad, multimediafiler eller interaktiva kontroller. Följ med när vi fördjupar oss i kodexemplen och lär dig hur du använder dessa funktioner effektivt.

### Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar på plats:

1. Aspose.Words för Java: Se till att du har Aspose.Words-biblioteket installerat i ditt Java-projekt. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).

2. Java-utvecklingsmiljö: Du bör ha en fungerande Java-utvecklingsmiljö installerad på ditt system.

### Infoga ett OLE-objekt

Låt oss börja med att infoga ett OLE-objekt i ett Word-dokument. Vi skapar ett enkelt Word-dokument och infogar sedan ett OLE-objekt som representerar en webbsida.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://"www.aspose.com", "html-fil", sant, sant, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

I den här koden skapar vi ett nytt dokument och infogar ett OLE-objekt som visar Aspose-webbplatsen. Du kan ersätta URL:en med önskat innehåll.

### Infoga ett OLE-objekt med OlePackage

Nu ska vi utforska hur man infogar ett OLE-objekt med hjälp av ett OlePackage. Detta gör att du kan bädda in externa filer som OLE-objekt i ditt dokument.

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

I det här exemplet infogar vi ett OLE-objekt med hjälp av ett OlePackage, vilket gör att du kan inkludera externa filer som inbäddade objekt.

### Infoga ett OLE-objekt som en ikon

Nu ska vi se hur man infogar ett OLE-objekt som en ikon. Detta är användbart när du vill visa en ikon som representerar en inbäddad fil.

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

I den här koden infogar vi ett OLE-objekt som en ikon, vilket ger en mer visuellt tilltalande representation av det inbäddade innehållet.

### Läser egenskaper för ActiveX-kontroller

Nu ska vi fokusera på ActiveX-kontroller. Vi ska lära oss hur man läser egenskaperna för ActiveX-kontroller i ett Word-dokument.

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

I den här koden itererar vi igenom formerna i ett Word-dokument, identifierar ActiveX-kontroller och hämtar deras egenskaper.

### Slutsats

Grattis! Du har lärt dig hur man arbetar med OLE-objekt och ActiveX-kontroller i Aspose.Words för Java. Dessa funktioner öppnar upp en värld av möjligheter för att skapa dynamiska och interaktiva dokument.

### Vanliga frågor

### Vad är syftet med OLE-objekt i ett Word-dokument? 
   - Med OLE-objekt kan du bädda in eller länka externt innehåll, till exempel filer eller webbsidor, i ett Word-dokument.

### Kan jag anpassa utseendet på OLE-objekt i mitt dokument? 
   - Ja, du kan anpassa utseendet på OLE-objekt, inklusive att ange ikoner och filnamn.

### Vad är ActiveX-kontroller, och hur kan de förbättra mina dokument? 
   - ActiveX-kontroller är interaktiva element som kan lägga till funktioner i dina Word-dokument, till exempel formulärkontroller eller multimediaspelare.

### Är Aspose.Words för Java lämpligt för dokumentautomation på företagsnivå? 
   - Ja, Aspose.Words för Java är ett kraftfullt bibliotek för att automatisera dokumentgenerering och manipulation i Java-applikationer.

### Var kan jag få tillgång till Aspose.Words för Java? 
   - Du kan ladda ner Aspose.Words för Java från [här](https://releases.aspose.com/words/java/).

Kom igång med Aspose.Words för Java idag och lås upp den fulla potentialen av dokumentautomation och anpassning!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}