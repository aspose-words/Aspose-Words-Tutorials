---
title: Jämföra dokument för skillnader
linktitle: Jämföra dokument för skillnader
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du jämför dokument för skillnader med Aspose.Words i Java. Vår steg-för-steg-guide säkerställer korrekt dokumenthantering.
weight: 12
url: /sv/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jämföra dokument för skillnader

## Introduktion

Har du någonsin undrat hur man ser varje skillnad mellan två Word-dokument? Du kanske reviderar ett dokument eller försöker hitta ändringar som gjorts av en samarbetspartner. Manuella jämförelser kan vara tråkiga och felbenägna, men med Aspose.Words för Java är det enkelt! Det här biblioteket låter dig automatisera dokumentjämförelse, markera revisioner och slå samman ändringar utan ansträngning.

## Förutsättningar

Innan du hoppar in i koden, se till att du har följande redo:  
1. Java Development Kit (JDK) installerat på ditt system.  
2.  Aspose.Words för Java-bibliotek. Du kan[ladda ner den här](https://releases.aspose.com/words/java/).  
3. En utvecklingsmiljö som IntelliJ IDEA eller Eclipse.  
4. Grundläggande förtrogenhet med Java-programmering.  
5.  En giltig Aspose-licens. Om du inte har en, skaffa en[tillfällig licens här](https://purchase.aspose.com/temporary-license/).

## Importera paket

För att använda Aspose.Words måste du importera de nödvändiga klasserna. Nedan följer nödvändiga importer:

```java
import com.aspose.words.*;
import java.util.Date;
```

Se till att dessa paket läggs till korrekt i dina projektberoenden.


I det här avsnittet delar vi upp processen i enkla steg.


## Steg 1: Konfigurera dina dokument

För att börja behöver du två dokument: ett som representerar originalet och det andra som representerar den redigerade versionen. Så här skapar du dem:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Detta skapar två dokument i minnet med grundläggande innehåll. Du kan också ladda befintliga Word-dokument med`new Document("path/to/document.docx")`.


## Steg 2: Kontrollera om det finns befintliga versioner

Revisioner i Word-dokument representerar spårade ändringar. Innan du jämför, se till att inget av dokumenten innehåller redan existerande revisioner:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Om revisioner finns, kanske du vill acceptera eller avvisa dem innan du fortsätter.


## Steg 3: Jämför dokumenten

 Använd`compare` metod för att hitta skillnader. Denna metod jämför måldokumentet (`doc2`) med källdokumentet (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Här:
- AuthorName är namnet på den person som gör ändringarna.
- Datum är jämförelsens tidsstämpel.


## Steg 4: Processrevisioner

En gång jämfört kommer Aspose.Words att generera revisioner i källdokumentet (`doc1`). Låt oss analysera dessa ändringar:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Denna loop ger detaljerad information om varje revision, såsom typ av ändring och den berörda texten.


## Steg 5: Acceptera alla versioner

Om du vill ha källdokumentet (`doc1`) för att matcha måldokumentet (`doc2`), acceptera alla ändringar:

```java
doc1.getRevisions().acceptAll();
```

 Detta uppdateras`doc1` för att återspegla alla ändringar som gjorts i`doc2`.


## Steg 6: Spara det uppdaterade dokumentet

Slutligen sparar du det uppdaterade dokumentet på disken:

```java
doc1.save("Document.Compare.docx");
```

För att bekräfta ändringarna, ladda om dokumentet och verifiera att det inte finns några återstående revisioner:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Steg 7: Verifiera dokumentlikhet

För att säkerställa att dokumenten är identiska, jämför deras text:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Om texterna matchar, grattis – du har framgångsrikt jämfört och synkroniserat dokumenten!


## Slutsats

Dokumentjämförelse är inte längre ett jobb, tack vare Aspose.Words för Java. Med bara några rader kod kan du lokalisera skillnader, bearbeta revisioner och säkerställa dokumentkonsistens. Oavsett om du hanterar ett samarbetsprojekt eller granskar juridiska dokument, är den här funktionen en spelomvandlare.

## FAQ's

### Kan jag jämföra dokument med bilder och tabeller?  
Ja, Aspose.Words stöder jämförelse av komplexa dokument, inklusive de med bilder, tabeller och formatering.

### Behöver jag en licens för att använda den här funktionen?  
 Ja, en licens krävs för full funktionalitet. Skaffa en[tillfällig licens här](https://purchase.aspose.com/temporary-license/).

### Vad händer om det finns redan befintliga revisioner?  
Du måste acceptera eller avvisa dem innan du jämför dokument för att undvika konflikter.

### Kan jag markera ändringarna i dokumentet?  
Ja, Aspose.Words låter dig anpassa hur revisioner visas, som att markera ändringar.

### Är den här funktionen tillgänglig på andra programmeringsspråk?  
Ja, Aspose.Words stöder flera språk, inklusive .NET och Python.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
