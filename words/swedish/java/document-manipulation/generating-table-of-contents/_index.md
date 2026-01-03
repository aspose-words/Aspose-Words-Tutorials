---
date: 2026-01-03
description: Lär dig hur du justerar sidnummer när du infogar en innehållsförteckning
  med Aspose.Words för Java. Anpassa TOC‑stilar och skapa dokument utan ansträngning.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Justera sidnummer och generera innehållsförteckning med Aspose.Words för Java
url: /sv/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Justera sidnummer och generera innehållsförteckning i Aspose.Words för Java

I den här handledningen får du lära dig hur du **justerar sidnummer** och **infogar en innehållsförteckning** (TOC) med Aspose.Words för Java. En välstrukturerad TOC gör långa dokument lätta att navigera, och finjustering av sidnummerjusteringen ger dina läsare en professionell upplevelse. Vi går igenom hur du skapar ett dokument, anpassar TOC‑stilar och justerar tabbstopp så att sidnumren hamnar exakt där du vill ha dem.

## Snabba svar
- **Vad betyder “justera sidnummer”?** Att ändra tabbstopp som justerar sidnummer i en TOC.  
- **Kan jag infoga en innehållsförteckning automatiskt?** Ja – använd klassen `FieldToc`.  
- **Behöver jag en licens för att köra koden?** En gratis provversion fungerar för utveckling; en licens krävs för produktion.  
- **Vilken Aspose‑version stöds?** Exemplen fungerar med den senaste versionen av Aspose.Words för Java.  
- **Är det möjligt att anpassa TOC‑stilar?** Absolut – du kan ändra teckensnitt, fetstil och mer.

## Vad är en innehållsförteckning i Aspose.Words?
En TOC är ett fält som skannar dokumentet efter rubrikstilar (t.ex. Heading 1, Heading 2) och genererar en lista med poster och sidnummer. Aspose.Words låter dig infoga detta fält programatiskt och ha full kontroll över dess utseende.

## Varför justera sidnummer i en TOC?
Att justera tabbstopp ger dig exakt kontroll över var sidnumren visas, vilket är viktigt för:

- Att upprätthålla en ren, kolumn‑justerad layout.  
- Att följa företagets stilguide.  
- Att förbättra läsbarheten i både utskrivna och digitala dokument.

## Förutsättningar
- Aspose.Words för Java har lagts till i ditt projekt (Maven/Gradle).  
- Grundläggande kunskap om Java‑syntax.  

## Steg‑för‑steg‑guide

### Steg 1: Skapa ett nytt dokument
Först skapar du ett tomt `Document`‑objekt som kommer att innehålla ditt innehåll och din TOC.

```java
Document doc = new Document();
```

### Steg 2: Anpassa TOC‑stilar
Du kan ändra utseendet för varje TOC‑nivå. I det här exemplet gör vi poster på första nivån fetstil, vilket är en vanlig formateringsbegäran.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Steg 3: Lägg till innehåll i ditt dokument
Infoga rubriker (t.ex. `Heading1`, `Heading2`) och vanliga stycken. TOC‑fältet kommer senare att plocka upp dessa rubriker automatiskt. *(Kod utelämnad för korthet – fokus ligger på TOC‑generering.)*

### Steg 4: Infoga TOC‑fältet
Placera TOC‑fältet där du vill ha det – vanligtvis i början av dokumentet.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Steg 5: Spara dokumentet
Spara dokumentet till disk. Du kan välja vilket som helst av de stödjade formaten, såsom DOCX, PDF eller HTML.

```java
doc.save("your_output_path_here");
```

## Anpassa tabbstopp i TOC (justera sidnummer)
Om standard‑tabbstoppet inte justerar sidnumren som du önskar kan du iterera igenom alla TOC‑stycken och ändra deras tabbpositioner.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nu visar TOC‑poster sidnummer exakt där du vill ha dem, vilket ger ditt dokument ett polerat utseende.

## Vanliga problem & tips
- **Saknade rubriker i TOC:** Säkerställ att dina rubriker använder inbyggda stilar (`Heading1`, `Heading2` osv.) eller mappa anpassade stilar till TOC‑nivåer.  
- **Tabbstoppet tillämpas inte:** Verifiera att stycket faktiskt tillhör en TOC‑stil (`TOC_1`‑`TOC_9`).  
- **Prestanda i stora dokument:** Anropa `doc.updateFields()` efter att du har infogat TOC för att uppdatera posterna i ett enda pass.

## Vanliga frågor

**Q: Hur ändrar jag formateringen av TOC‑poster?**  
A: Använd `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` där *X* är nivån (1‑9) och modifiera dess teckensnitt, färg eller styckeinställningar.

**Q: Hur kan jag lägga till fler nivåer i min TOC?**  
A: Justera `FieldToc`‑parametern `\o "1-3"` (t.ex.) för att inkludera ytterligare rubriknivåer, och uppdatera sedan motsvarande `TOC_X`‑stilar.

**Q: Kan jag ändra tabbstopp‑positionerna för specifika TOC‑poster?**  
A: Ja – iterera genom styckena som visas i avsnittet “Anpassa tabbstopp” och ändra varje tabbstopp individuellt.

**Q: Är det möjligt att generera en TOC i PDF‑utdata?**  
A: Absolut. Spara dokumentet som PDF (`doc.save("output.pdf")`) efter att TOC har genererats; fältet renderas automatiskt.

**Q: Måste jag anropa `updateFields()` manuellt?**  
A: När du infogar ett `FieldToc` uppdaterar Aspose.Words det vid sparning, men att anropa `doc.updateFields()` ger omedelbara resultat för felsökning.

## Slutsats
Du har nu lärt dig hur du **justerar sidnummer**, **infogar en innehållsförteckning** och **anpassar TOC‑stilar** med Aspose.Words för Java. Dessa tekniker låter dig skapa rena, navigerbara och professionellt formaterade dokument som uppfyller alla publiceringsstandarder.

---  

**Senast uppdaterad:** 2026-01-03  
**Testad med:** Aspose.Words för Java (senaste version)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}