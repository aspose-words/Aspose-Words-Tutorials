---
category: general
date: 2026-10-10
description: Applicera fotnoter med rubrikstil i ett Word‑dokument med Aspose.Words
  för Java – en komplett steg‑för‑steg‑guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply heading style footnotes
- footnote separator
- endnote separator
- Aspose.Words for Java
- style identifier
language: sv
lastmod: 2026-10-10
og_description: Använd rubrikstil för fotnoter i ett Word‑dokument med Aspose.Words
  för Java. Lär dig hur du formaterar fotnot‑ och slutnotseparatorer på några minuter.
og_image_alt: Document after applying heading style footnotes to footnote and endnote
  separators
og_title: Använd fotnoter med rubrikstil i Aspose.Words för Java – fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Apply heading style footnotes in a Word document using Aspose.Words
    for Java – a complete step‑by‑step guide.
  headline: Apply heading style footnotes with Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word processing
- Document styling
title: Applicera fotnoter i rubrikstil med Aspose.Words för Java
url: /sv/java/annotations-comments/apply-heading-style-footnotes-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Applicera rubrikstil fotnoter med Aspose.Words för Java

Om du behöver **applicera rubrikstil fotnoter** i ett Word‑dokument, visar den här handledningen exakt hur du gör det med Aspose.Words för Java. Du får se ett komplett, körbart exempel som formaterar både fotnotseparatorn och slutnotseparatorn med inbyggda rubrikstilar.

Formatering av fotnot- och slutnotseparatorer gör dokumenten lättare att läsa och ger dig enhetlig formatering i stora manuskript. Guiden täcker också vanliga fallgropar, såsom att säkerställa att rätt `StyleIdentifier` används och hantera dokument som redan innehåller anpassade separatorer.

## Vad du kommer att lära dig

* Hur du laddar en `.docx`‑fil som innehåller fotnoter och slutnoter.  
* Hur du hämtar **fotnotseparator**‑paragrafen och sätter dess stil till `HEADING_2`.  
* Hur du hämtar **slutnotseparator**‑paragrafen och sätter dess stil till `HEADING_3`.  
* Hur du sparar det modifierade dokumentet och verifierar ändringarna.  

**Förutsättningar**

* Java 17 eller senare.  
* Aspose.Words for Java 23.12 (eller den senaste versionen).  
* Grundläggande kunskap om Word‑bearbetningskoncept (fotnoter, slutnoter, stilar).

---

## Applicera rubrikstil fotnoter – översikt

Kärnidén är att använda Aspose.Words `Document.getFootnoteSeparator()` och `Document.getEndnoteSeparator()`‑metoderna. Båda metoderna returnerar ett `Paragraph`‑objekt som representerar den dolda separatorlinjen mellan huvudtexten och fotnot‑/slutnot‑området. Genom att ändra paragrafens `ParagraphFormat` och tilldela ett `StyleIdentifier` kan du effektivt **applicera rubrikstil fotnoter** utan att manuellt redigera Word‑gränssnittet.

## Steg 1: Ställ in projektet

Create a Maven (or Gradle) project and add the Aspose.Words for Java dependency:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Proffstips:** Använd den senaste versionen för att dra nytta av buggfixar relaterade till `StyleIdentifier`‑enumerationen.

---

## Steg 2: Ladda källdokumentet

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // Load a Word document that already contains footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");
        // From here we will manipulate the footnote and endnote separators.
```

*`Document`‑konstruktorn läser in filen i minnet och ger dig full programmatisk åtkomst.*  

---

## Steg 3: Formatera fotnotseparatorn

```java
        // Retrieve the hidden paragraph that separates footnotes from the main text.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();

        // Apply the built‑in Heading 2 style to this separator.
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);
```

Varför `HEADING_2`? Rubrikstilar ärver teckenstorlek, färg och avstånd, vilket gör separatorn visuellt tydlig samtidigt som den följer dokumentets stilhierarki.

---

## Steg 4: Formatera slutnotseparatorn

```java
        // Retrieve the hidden paragraph that separates endnotes.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();

        // Apply the built‑in Heading 3 style to this separator.
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);
```

Genom att använda `HEADING_3` hålls den visuella vikten lägre än fotnotseparatorn, vilket matchar vanliga akademiska formateringskonventioner.

---

## Steg 5: Spara det modifierade dokumentet

```java
        // Persist the changes to a new file.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

Efter att programmet har körts, öppna `FootnoteStyled.docx` i Microsoft Word. Du kommer att märka:

* Fotnotseparatorn visas nu med formateringen **Heading 2** (större tecken, fet som standard).  
* Slutnotseparatorn återspeglar **Heading 3** (lite mindre, fortfarande fet).  

Dessa ändringar tillämpas automatiskt på varje fotnot och slutnot i dokumentet, även om nya läggs till senare.

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Vad händer om dokumentet redan använder anpassade stilar för separatorer?** | Att skriva över `StyleIdentifier` ersätter den befintliga stilen. Om du behöver bevara anpassad formatering, klona den ursprungliga stilen, modifiera den och tilldela klonens identifierare. |
| **Kan jag använda en anpassad stil istället för en inbyggd rubrik?** | Ja. Skapa den anpassade stilen med `document.getStyles().add(StyleIdentifier.CUSTOM)`, konfigurera dess attribut och tilldela sedan dess identifierare till separator‑paragrafen. |
| **Fungerar detta med `.doc` (binära) filer?** | Absolut. Aspose.Words abstraherar filformatet, så samma kod fungerar för `.doc` och `.docx`. |
| **Finns det någon prestandapåverkan på stora dokument?** | Operationerna är O(1) eftersom de riktar sig mot ett enda dolt stycke; även ett 500‑sidigt dokument bearbetas på några millisekunder. |

## Fullständig källkod (körbar)

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document containing footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2️⃣ Retrieve the footnote separator and apply Heading 2.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);

        // 3️⃣ Retrieve the endnote separator and apply Heading 3.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);

        // 4️⃣ Save the modified document.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

**Förväntad output** (konsol):

```
Document saved with styled footnote and endnote separators.
```

Öppna den sparade filen för att se de formaterade separatorerna.

## Slutsats

Du vet nu hur du **applicerar rubrikstil fotnoter** i ett Word‑dokument med Aspose.Words för Java. Genom att hämta **fotnotseparator**‑ och **slutnotseparator**‑paragraferna och tilldela lämpliga `StyleIdentifier`‑värden får du enhetlig, professionell formatering med bara några rader kod.

Nästa steg du kan överväga:

* Experimentera med anpassade stilar istället för de inbyggda rubrikerna.  
* Automatisera stiländringar över en batch av dokument med samma tillvägagångssätt.  
* Kombinera denna teknik med andra `Document`‑API:er, såsom `getFootnoteOptions()` för finjusterad fotnotnumrering.

Känn dig fri att anpassa koden för dina egna publiceringsflöden, och lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Använda fotnoter och slutnoter i Aspose.Words för Java](/words/english/java/using-document-elements/using-footnotes-and-endnotes/)
- [Spara Word som PDF med Aspose.Words – Steg‑för‑steg Java‑guide](/words/english/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Exportera Word till Markdown – Java‑guide med Aspose.Words](/words/english/java/document-conversion-and-export/export-word-to-markdown-java-guide-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}