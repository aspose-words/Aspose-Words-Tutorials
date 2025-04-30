---
"description": "Lär dig hur du jämför dokument för att hitta skillnader med Aspose.Words i Java. Vår steg-för-steg-guide säkerställer korrekt dokumenthantering."
"linktitle": "Jämföra dokument för att hitta skillnader"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Jämföra dokument för att hitta skillnader"
"url": "/sv/java/document-merging/comparing-documents-for-differences/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jämföra dokument för att hitta skillnader

## Introduktion

Har du någonsin undrat hur man hittar alla skillnader mellan två Word-dokument? Kanske reviderar du ett dokument eller försöker hitta ändringar som gjorts av en samarbetspartner. Manuella jämförelser kan vara tråkiga och felbenägna, men med Aspose.Words för Java är det hur enkelt som helst! Det här biblioteket låter dig automatisera dokumentjämförelser, markera revisioner och sammanfoga ändringar utan ansträngning.

## Förkunskapskrav

Innan du börjar med koden, se till att du har följande redo:  
1. Java Development Kit (JDK) installerat på ditt system.  
2. Aspose.Words för Java-biblioteket. Du kan [ladda ner den här](https://releases.aspose.com/words/java/).  
3. En utvecklingsmiljö som IntelliJ IDEA eller Eclipse.  
4. Grundläggande kunskaper i Java-programmering.  
5. En giltig Aspose-licens. Om du inte har en, skaffa en [tillfällig licens här](https://purchase.aspose.com/temporary-license/).

## Importera paket

För att använda Aspose.Words behöver du importera de nödvändiga klasserna. Nedan följer de importerade klasserna:

```java
import com.aspose.words.*;
import java.util.Date;
```

Se till att dessa paket är korrekt tillagda till dina projektberoenden.


I det här avsnittet kommer vi att dela upp processen i enkla steg.


## Steg 1: Konfigurera dina dokument

Till att börja med behöver du två dokument: ett som representerar originalet och det andra som representerar den redigerade versionen. Så här skapar du dem:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

Detta skapar två dokument i minnet med grundläggande innehåll. Du kan också ladda befintliga Word-dokument med hjälp av `new Document("path/to/document.docx")`.


## Steg 2: Kontrollera befintliga revisioner

Revisioner i Word-dokument representerar spårade ändringar. Innan du jämför, se till att inget av dokumenten innehåller befintliga revisioner:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Om det finns ändringar kanske du vill acceptera eller avvisa dem innan du fortsätter.


## Steg 3: Jämför dokumenten

Använd `compare` metod för att hitta skillnader. Denna metod jämför måldokumentet (`doc2`) med källdokumentet (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Här:
- AuthorName är namnet på den person som gör ändringarna.
- Datum är jämförelsens tidsstämpel.


## Steg 4: Processrevisioner

När Aspose.Words har jämförts genererar de revideringar i källdokumentet (`doc1`Låt oss analysera dessa revisioner:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Denna loop ger detaljerad information om varje revision, såsom typ av ändring och den berörda texten.


## Steg 5: Godkänn alla revisioner

Om du vill ha källdokumentet (`doc1`) för att matcha måldokumentet (`doc2`), acceptera alla ändringar:

```java
doc1.getRevisions().acceptAll();
```

Denna uppdatering `doc1` för att återspegla alla förändringar som gjorts i `doc2`.


## Steg 6: Spara det uppdaterade dokumentet

Slutligen, spara det uppdaterade dokumentet till disk:

```java
doc1.save("Document.Compare.docx");
```

För att bekräfta ändringarna, ladda om dokumentet och kontrollera att det inte finns några kvarvarande revisioner:

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

Om texterna matchar, grattis – du har jämfört och synkroniserat dokumenten!


## Slutsats

Att jämföra dokument är inte längre ett besvär tack vare Aspose.Words för Java. Med bara några få rader kod kan du identifiera skillnader, bearbeta revideringar och säkerställa dokumentkonsekvens. Oavsett om du hanterar ett gemensamt skrivprojekt eller granskar juridiska dokument är den här funktionen banbrytande.

## Vanliga frågor

### Kan jag jämföra dokument med bilder och tabeller?  
Ja, Aspose.Words stöder jämförelse av komplexa dokument, inklusive de med bilder, tabeller och formatering.

### Behöver jag en licens för att använda den här funktionen?  
Ja, en licens krävs för full funktionalitet. Skaffa en [tillfällig licens här](https://purchase.aspose.com/temporary-license/).

### Vad händer om det finns befintliga revisioner?  
Du måste acceptera eller avvisa dem innan du jämför dokument för att undvika konflikter.

### Kan jag markera ändringarna i dokumentet?  
Ja, Aspose.Words låter dig anpassa hur revisioner visas, till exempel markera ändringar.

### Finns den här funktionen i andra programmeringsspråk?  
Ja, Aspose.Words stöder flera språk, inklusive .NET och Python.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}