---
category: general
date: 2026-07-20
description: Ändra fotnotavstånd i DOCX-filer enkelt. Lär dig hur du ställer in avstånd,
  justerar fotnotseparatorn och sätter radavstånd i stycken med Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: sv
lastmod: 2026-07-20
og_description: Ändra fotnotavstånd i DOCX-filer snabbt. Den här guiden visar hur
  du ställer in avstånd, justerar fotnotseparatorn och anpassar radavstånd i stycken
  i Java.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Ändra fotnotavstånd i DOCX – Steg-för-steg-guide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Ändra fotnotavstånd i DOCX – Komplett guide
url: /sv/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ändra fotnotavstånd i DOCX – Komplett guide

Har du någonsin behövt **ändra fotnotavstånd** i ett Word‑dokument men varit osäker på var du ska börja? Du är inte ensam. Oavsett om du putsar på en avhandling eller finjusterar ett kontrakt kan det göra stor skillnad att få fotnotseparatorn precis rätt.  

I den här handledningen går vi igenom **hur man ställer in avstånd**, justerar fotnotseparatorn och **ställer in radavstånd för stycken** med Java‑baserade bibliotek. I slutet har du ett färdigt exempel som du kan lägga in i vilket projekt som helst.

## Vad du behöver

Innan vi dyker ner, se till att du har:

- Java 17 eller nyare (koden använder de moderna språkfunktionerna)
- Maven eller Gradle för beroendehantering
- En DOCX‑fil med minst en fotnot (eller så kan du skapa en manuellt)
- Biblioteket **Aspose.Words for Java** (eller något kompatibelt API; vi använder Aspose i exemplet)

Det är allt—inga tunga ramverk, bara ren Java och ett enda bibliotek.

![Ändra fotnotavstånd i DOCX-exempel](/images/footnote-spacing.png){alt="Ändra fotnotavstånd i DOCX-exempel"}

## Steg 1: Ladda DOCX‑dokumentet (Ändra fotnotavstånd)

Det första du måste göra är att öppna Word‑filen. Detta ger dig ett `Document`‑objekt som du kan manipulera.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Varför detta är viktigt*: Att ladda dokumentet är startpunkten för **ändra fotnotavstånd**. Utan ett `Document`‑instans kan du inte nå fotnotseparatorn eller några styckeformat.

## Steg 2: Hämta och justera fotnotseparatorn (Justera fotnotseparator)

En fotnotseparator är ett dolt stycke som sitter mellan huvudtexten och fotnotlistan. För att ändra dess radavstånd måste du hämta det stycket och justera dess format.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Hur detta löser problemet

- **Hämta fotnotseparatorn** – detta är den del du faktiskt vill modifiera, vilket uppfyller kravet *justera fotnotseparator*.
- **Ställ in radavstånd** – `setLineSpacing(12.0)` svarar direkt på *hur man ställer in avstånd* för det dolda stycket.
- **Hantering av kantfall** – om dokumentet av någon anledning saknar en separator skapar vi en på plats, vilket förhindrar ett `NullPointerException`.

## Steg 3: Verifiera ändringen och spara (Ställ in radavstånd för stycke)

Efter att du har ändrat separatorn vill du försäkra dig om att ändringen sparats. Att öppna den sparade filen i Word visar det nya avståndet, men du kan också kontrollera det programatiskt.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Lägg till ett anrop till `verifySpacing(doc);` precis innan `doc.save(...)` i `main`. När du kör programmet bör du se:

```
Current footnote separator line spacing: 12.0
```

Det bekräftar att operationen **ändra radavstånd i docx** lyckades.

## Vanliga fallgropar & proffstips

- **Fallgrop**: Att använda `setLineSpacing` med ett värde som ser ut som “12” men tolkas som “12 pt” kontra “12 rader”. Aspose förväntar sig punkter, så 12 betyder 12 pt. För dubbelt radavstånd använd `24.0`.
- **Proffstips**: Om du behöver ett enhetligt utseende för alla fotnottyper (separator, fortsättningsseparator osv.) upprepa samma steg för `doc.getFootnoteContinuationSeparator()` och `doc.getFootnoteContinuationNotice()`.
- **Fallgrop**: Glömmer att anropa `save()` efter ändringar. Dokumentet i minnet ändras, men filen på disken förblir densamma.
- **Proffstips**: Kombinera avståndsändringar med stiluppdateringar (`ParagraphStyle`) för en fullt polerad fotnotsektion.

## Fullständigt fungerande exempel (Alla steg i en fil)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Kopiera koden ovan till en ny Java‑klass, lägg till Aspose.Words Maven‑beroendet och kör den. Din `output.docx` kommer nu ha fotnotseparatorns radavstånd inställt på **12 pt**, vilket effektivt **ändrar fotnotavstånd**.

### Maven‑beroende

Lägg till detta kodstycke i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Om du föredrar Gradle är motsvarande:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Slutsats

Du har precis lärt dig hur man **ändrar fotnotavstånd** i en DOCX‑fil med Java. Genom att ladda dokumentet, hämta **fotnotseparatorn** och tillämpa **ställ in radavstånd för stycke**, får du exakt kontroll över hur fotnoterna ser ut.  

Härifrån kan du utforska relaterade justeringar, som att ändra fotnottextens stil, lägga till anpassade separatorer eller till och med automatisera massuppdateringar i flera dokument.  

Har du fler frågor om **justera fotnotseparator** eller andra Word‑automatiseringsuppgifter? Lämna en kommentar, och lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ändra asiatiskt styckeavstånd och indrag i Word-dokument](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ändra asiatiskt styckeavstånd och indrag](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ändra asiatiskt styckeavstånd och indrag](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}