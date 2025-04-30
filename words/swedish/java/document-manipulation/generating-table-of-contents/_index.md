---
"description": "Lär dig hur du genererar och anpassar innehållsförteckningar (TOC) med Aspose.Words för Java. Skapa enkelt organiserade och professionella dokument."
"linktitle": "Generera innehållsförteckning"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Generera innehållsförteckning i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generera innehållsförteckning i Aspose.Words för Java


## Introduktion till att generera innehållsförteckningar i Aspose.Words för Java

den här handledningen går vi igenom processen att generera en innehållsförteckning (TOC) med Aspose.Words för Java. Innehållsförteckningen är en viktig funktion för att skapa organiserade dokument. Vi går igenom hur du anpassar innehållsförteckningens utseende och layout.

## Förkunskapskrav

Innan du börjar, se till att du har Aspose.Words för Java installerat och konfigurerat i ditt Java-projekt.

## Steg 1: Skapa ett nytt dokument

Först, låt oss skapa ett nytt dokument att arbeta med.

```java
Document doc = new Document();
```

## Steg 2: Anpassa innehållsförteckningsstilar

För att anpassa utseendet på din innehållsförteckning kan du ändra de stilar som är kopplade till den. I det här exemplet gör vi innehållsförteckningens poster på första nivån fetstilta.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Steg 3: Lägg till innehåll i ditt dokument

Du kan lägga till ditt innehåll i dokumentet. Detta innehåll kommer att användas för att generera innehållsförteckningen.

## Steg 4: Generera innehållsförteckningen

För att generera innehållsförteckningen, infoga ett innehållsförteckningsfält på önskad plats i dokumentet. Det här fältet fylls automatiskt baserat på rubrikerna och formaten i dokumentet.

```java
// Infoga ett innehållsförteckningsfält på önskad plats i dokumentet.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Steg 5: Spara dokumentet

Spara slutligen dokumentet med innehållsförteckningen.

```java
doc.save("your_output_path_here");
```

## Anpassa tabbstopp i innehållsförteckningen

Du kan också anpassa tabbstoppen i innehållsförteckningen för att styra layouten för sidnummer. Så här ändrar du tabbstopp:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Använd den första tabbtangenten i det här stycket, som justerar sidnumren.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Ta bort den gamla fliken.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Infoga en ny flik på en ändrad position (t.ex. 50 enheter till vänster).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nu har du en anpassad innehållsförteckning i ditt dokument med justerade tabbstopp för sidnummerjustering.


## Slutsats

I den här handledningen har vi utforskat hur man genererar en innehållsförteckning (TOC) med hjälp av Aspose.Words för Java, ett kraftfullt bibliotek för att arbeta med Word-dokument. En välstrukturerad innehållsförteckning är avgörande för att organisera och navigera i långa dokument, och Aspose.Words tillhandahåller verktygen för att enkelt skapa och anpassa innehållsförteckningar.

## Vanliga frågor

### Hur ändrar jag formateringen av innehållsförteckningsposter?

Du kan ändra stilarna som är associerade med innehållsförteckningsnivåer med hjälp av `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, där X är innehållsförteckningsnivån.

### Hur kan jag lägga till fler nivåer i min innehållsförteckning?

För att inkludera fler nivåer i din innehållsförteckning kan du ändra innehållsförteckningsfältet och ange önskat antal nivåer.

### Kan jag ändra tabbstoppspositionerna för specifika innehållsförteckningsposter?

Ja, som visas i kodexemplet ovan kan du ändra tabbstoppspositionerna för specifika innehållsförteckningsposter genom att iterera igenom styckena och modifiera tabbstoppen därefter.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}