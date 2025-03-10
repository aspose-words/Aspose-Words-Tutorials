---
title: Generera innehållsförteckning i Aspose.Words för Java
linktitle: Generera innehållsförteckning
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du genererar och anpassar innehållsförteckningen (TOC) med Aspose.Words för Java. Skapa organiserade och professionella dokument utan ansträngning.
weight: 21
url: /sv/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generera innehållsförteckning i Aspose.Words för Java


## Introduktion till generering av innehållsförteckning i Aspose.Words för Java

I den här handledningen går vi igenom processen att skapa en innehållsförteckning (TOC) med Aspose.Words för Java. TOC är en avgörande funktion för att skapa organiserade dokument. Vi tar upp hur man anpassar innehållsförteckningens utseende och layout.

## Förutsättningar

Innan du börjar, se till att du har Aspose.Words för Java installerat och konfigurerat i ditt Java-projekt.

## Steg 1: Skapa ett nytt dokument

Låt oss först skapa ett nytt dokument att arbeta med.

```java
Document doc = new Document();
```

## Steg 2: Anpassa innehållsförteckningsstilar

För att anpassa utseendet på din innehållsförteckning kan du ändra stilarna som är kopplade till den. I det här exemplet kommer vi att göra TOC-posterna på första nivån fetstilta.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Steg 3: Lägg till innehåll i ditt dokument

Du kan lägga till ditt innehåll i dokumentet. Detta innehåll kommer att användas för att generera innehållsförteckningen.

## Steg 4: Skapa innehållsförteckningen

För att generera innehållsförteckningen, infoga ett innehållsförteckningsfält på önskad plats i ditt dokument. Det här fältet kommer att fyllas i automatiskt baserat på rubrikerna och stilarna i ditt dokument.

```java
// Infoga ett innehållsförteckningsfält på önskad plats i ditt dokument.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Steg 5: Spara dokumentet

Slutligen, spara dokumentet med innehållsförteckningen.

```java
doc.save("your_output_path_here");
```

## Anpassa tabbstopp i TOC

Du kan också anpassa tabbstoppen i din innehållsförteckning för att styra layouten på sidnummer. Så här kan du ändra tabbstopp:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Få den första fliken som används i det här stycket, som justerar sidnumren.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Ta bort den gamla fliken.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Sätt in en ny flik vid en modifierad position (t.ex. 50 enheter till vänster).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nu har du en anpassad innehållsförteckning i ditt dokument med justerade tabbstopp för sidnummerjustering.


## Slutsats

I den här handledningen har vi utforskat hur man genererar en innehållsförteckning (TOC) med Aspose.Words för Java, ett kraftfullt bibliotek för att arbeta med Word-dokument. En välstrukturerad innehållsförteckning är avgörande för att organisera och navigera i långa dokument, och Aspose.Words tillhandahåller verktygen för att skapa och anpassa innehållsförteckningar utan ansträngning.

## FAQ's

### Hur ändrar jag formateringen av TOC-poster?

 Du kan ändra stilarna som är associerade med innehållsförteckningsnivåer med hjälp av`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, där X är TOC-nivån.

### Hur kan jag lägga till fler nivåer till min innehållsförteckning?

För att inkludera fler nivåer i din innehållsförteckning kan du ändra innehållsförteckningsfältet och ange önskat antal nivåer.

### Kan jag ändra tabbstopppositionerna för specifika TOC-poster?

Ja, som visas i kodexemplet ovan kan du ändra tabbstoppspositionerna för specifika TOC-poster genom att iterera genom styckena och ändra tabbstoppen därefter.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
