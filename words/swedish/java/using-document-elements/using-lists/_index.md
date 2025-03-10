---
title: Använda listor i Aspose.Words för Java
linktitle: Använda listor
second_title: Aspose.Words Java Document Processing API
description: Lär dig att använda listor i Aspose.Words för Java med denna steg-för-steg handledning. Organisera och formatera dina dokument effektivt.
weight: 18
url: /sv/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använda listor i Aspose.Words för Java


den här omfattande självstudien kommer vi att utforska hur man effektivt använder listor i Aspose.Words för Java, ett kraftfullt API för att arbeta med Microsoft Word-dokument programmatiskt. Listor är viktiga för att strukturera och organisera innehåll i dina dokument. Vi kommer att täcka två viktiga aspekter av att arbeta med listor: att starta om listor vid varje avsnitt och ange listnivåer. Låt oss dyka in!

## Introduktion till Aspose.Words för Java

Innan vi börjar arbeta med listor, låt oss bekanta oss med Aspose.Words för Java. Detta API ger utvecklare verktyg för att skapa, ändra och manipulera Word-dokument i en Java-miljö. Det är en mångsidig lösning för uppgifter som sträcker sig från enkel dokumentgenerering till komplex formatering och innehållshantering.

### Ställa in din miljö

 För att börja, se till att du har Aspose.Words för Java installerat och konfigurerat i din utvecklingsmiljö. Du kan ladda ner den[här](https://releases.aspose.com/words/java/). 

## Startar om listor vid varje avsnitt

många scenarier kan du behöva starta om listor vid varje avsnitt av ditt dokument. Detta kan vara användbart för att skapa strukturerade dokument med flera avsnitt, såsom rapporter, manualer eller akademiska uppsatser.

Här är en steg-för-steg-guide om hur du uppnår detta med Aspose.Words för Java:

### Initiera ditt dokument: 
Börja med att skapa ett nytt dokumentobjekt.

```java
Document doc = new Document();
```

### Lägg till en numrerad lista: 
Lägg till en numrerad lista till ditt dokument. Vi använder standardnumreringsstilen.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Konfigurera listinställningar: 
\Aktivera listan för att starta om vid varje avsnitt.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder-inställningar: 
Skapa en DocumentBuilder för att lägga till innehåll i ditt dokument.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Lägg till listobjekt: 
Använd en slinga för att lägga till listobjekt till ditt dokument. Vi infogar en avsnittsbrytning efter den 15:e posten.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Spara ditt dokument: 
Spara dokumentet med önskade alternativ.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Genom att följa dessa steg kan du skapa dokument med listor som startar om vid varje avsnitt och bibehålla en tydlig och organiserad innehållsstruktur.

## Ange listnivåer

Aspose.Words för Java låter dig ange listnivåer, vilket är särskilt användbart när du behöver olika listformat i ditt dokument. Låt oss utforska hur du gör detta:

### Initiera ditt dokument: 
Skapa ett nytt dokumentobjekt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Skapa en numrerad lista: 
Använd en numrerad listmall från Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Ange listnivåer: 
Iterera genom olika listnivåer och lägg till innehåll.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Skapa en punktlista: 
Låt oss nu skapa en punktlista.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Ange nivåer för punktlista: 
I likhet med den numrerade listan, ange nivåer och lägg till innehåll.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Stoplistformatering: 
För att stoppa listformateringen, ställ in listan på null.

```java
builder.getListFormat().setList(null);
```

### Spara ditt dokument: 
Spara dokumentet.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Genom att följa dessa steg kan du skapa dokument med anpassade listnivåer, så att du kan styra formateringen av listor i dina dokument.

## Komplett källkod
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection kommer endast att skrivas om efterlevnaden är högre än OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Skapa en numrerad lista baserad på en av Microsoft Word-listmallarna
        //och tillämpa den på dokumentbyggarens nuvarande stycke.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Det finns nio nivåer i den här listan, låt oss prova dem alla.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Skapa en punktlista baserad på en av Microsoft Word-listmallarna
        //och tillämpa den på dokumentbyggarens nuvarande stycke.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Detta är ett sätt att stoppa listformatering.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Skapa en lista baserad på en mall.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // För att återanvända den första listan måste vi starta om numreringen genom att skapa en kopia av den ursprungliga listformateringen.
        List list2 = doc.getLists().addCopy(list1);
        // Vi kan ändra den nya listan på vilket sätt som helst, inklusive att ställa in ett nytt startnummer.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Slutsats

Grattis! Du har lärt dig hur du arbetar med listor i Aspose.Words för Java effektivt. Listor är avgörande för att organisera och presentera innehåll i dina dokument. Oavsett om du behöver starta om listor vid varje avsnitt eller ange listnivåer, tillhandahåller Aspose.Words för Java de verktyg du behöver för att skapa professionella dokument.

Nu kan du med säkerhet använda dessa funktioner för att förbättra dina dokumentgenererings- och formateringsuppgifter. Om du har några frågor eller behöver ytterligare hjälp, tveka inte att kontakta oss[Aspose community forum](https://forum.aspose.com/) för stöd.

## Vanliga frågor

### Hur installerar jag Aspose.Words för Java?
 Du kan ladda ner Aspose.Words för Java från[här](https://releases.aspose.com/words/java/) och följ installationsinstruktionerna i dokumentationen.

### Kan jag anpassa numreringsformatet för listor?
Ja, Aspose.Words för Java erbjuder omfattande alternativ för att anpassa listnumreringsformat. Du kan se API-dokumentationen för detaljer.

### Är Aspose.Words för Java kompatibelt med de senaste Word-dokumentstandarderna?
Ja, du kan konfigurera Aspose.Words för Java för att följa olika Word-dokumentstandarder, inklusive ISO 29500.

### Kan jag skapa komplexa dokument med tabeller och bilder med Aspose.Words för Java?
Absolut! Aspose.Words för Java stöder avancerad dokumentformatering, inklusive tabeller, bilder och mer. Se dokumentationen för exempel.

### Var kan jag få en tillfällig licens för Aspose.Words för Java?
Du kan få en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
