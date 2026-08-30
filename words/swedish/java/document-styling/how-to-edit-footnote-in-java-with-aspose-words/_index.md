---
category: general
date: 2026-08-07
description: Hur man redigerar fotnot i Java med Aspose.Words – lägg till anpassat
  streck, ändra fotnotslinje och ställ in styckejustering för polerade dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: sv
lastmod: 2026-08-07
og_description: Hur man redigerar fotnot i Java med Aspose.Words. Lär dig att lägga
  till ett anpassat streck, ändra fotnotlinjen och ställa in styckejustering på bara
  några steg.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Hur man redigerar fotnot i Java – lägg till streck, ändra rad, ställ in
  justering
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Hur man redigerar fotnot i Java med Aspose.Words
url: /sv/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man redigerar fotnot i Java med Aspose.Words

Om du behöver **how to edit footnote** i ett Word-dokument med Java, visar den här guiden hela arbetsflödet. Du kommer att lära dig att lägga till ett anpassat streck, ändra fotnotlinjen och ställa in styckejustering så att fotnotseparatorn ser professionell ut.

Att redigera fotnoter är ett vanligt krav när man förbereder juridiska kontrakt, akademiska uppsatser eller marknadsföringsbroschyrer. Stegen nedan täcker allt du behöver – från att ladda dokumentet till att spara den slutliga filen – utan att kräva ytterligare verktyg.

## Förutsättningar

* Java 17 eller nyare installerat.  
* Aspose.Words for Java (senaste version) tillagt i ditt projekts classpath.  
* En DOCX‑fil (`input.docx`) som innehåller minst en fotnot.

Dessa element garanterar att koden körs utan körningsfel.

## Hur man redigerar fotnotseparator och -linje

Fotnotseparatorn är det stycke som visas mellan huvudtexten och listan med fotnoter. Att ändra dess utseende förbättrar läsbarheten och matchar företagets varumärke.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Varför varje rad är viktig

1. **Laddar dokumentet** – `new Document(...)` läser DOCX-filen till minnet och ger dig åtkomst till alla dess noder.  
2. **Hämtar separatorn** – `getFootnoteSeparator()` returnerar det speciella stycket som Aspose.Words behandlar som fotnotlinjen. Detta objekt är den enda platsen där du säkert kan modifiera separatorn.  
3. **Ställer in styckejustering** – `setAlignment(ParagraphAlignment.CENTER)` ändrar linjens justering. Nyckelordet *set paragraph alignment* appliceras direkt på separatorn och säkerställer ett centrerat streck.  
4. **Lägger till anpassat streck** – Genom att rensa befintliga runs och lägga till ett nytt `Run` med em‑dash‑tecknet (`—`) uppnår du *add custom dash*-effekten samtidigt som du *change footnote line* till önskad stil.  
5. **Sparar dokumentet** – `doc.save(...)` skriver tillbaka ändringarna till disk och skapar en utdatafil som reflekterar alla modifieringar.

## Lägg till anpassat streck i fotnotseparatorn

Koden i **Step 4** demonstrerar *add custom dash*-tekniken. Du kan ersätta em‑dash‑tecknet med vilken sträng som helst, exempelvis `"***"` eller `"---"`, för att matcha ditt dokuments visuella språk.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Att använda ett anpassat streck är särskilt hjälpsamt när den standardtunna linjen inte uppfyller varumärkesriktlinjerna.

## Ändra fotnotlinjens stil

Om du föredrar en solid linje istället för ett streck kan du infoga ett Unicode‑tecken för box‑drawing eller ett upprepat understreck.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

*change footnote line*-steget fungerar på samma sätt oavsett vilket tecken du väljer, eftersom separatorstycket bara renderar den text det innehåller.

## Ställ in styckejustering för fotnotseparatorn

*set paragraph alignment*-operationen är inte begränsad till centrerad justering. Du kan justera vänster, höger eller justera (justify) enligt dina layoutbehov.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Att justera separatorn till höger kan vara användbart för dokument som använder högerjusterade fotnoter, exempelvis tvåspråkiga publikationer.

## Fullt, körbart exempel

Nedan är det kompletta programmet som inkorporerar alla koncept – laddning av dokument, redigering av fotnotseparator, tillsats av anpassat streck, ändring av linjestil och inställning av justering.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Förväntad utdata:** `output.docx`‑filen innehåller ett centrerat em‑dash där den ursprungliga tunna linjen tidigare var. Alla fotnoter förblir intakta och dokumentets layout reflekterar den nya separatorstilen.

## Vanliga fallgropar och hur man undviker dem

| Problem | Orsak | Lösning |
|---------|-------|---------|
| Separator ej hittad | Dokumentet har inga fotnoter eller använder en anpassad fotnotstil | Se till att källdokumentet innehåller minst en fotnot innan du anropar `getFootnoteSeparator()` |
| Anpassat streck syns inte | Typsnittet stöder inte det valda tecknet | Använd ett Unicode‑tecken som stöds av dokumentets standardtypsnitt, eller bädda in ett kompatibelt typsnitt |
| Justering verkar oförändrad | Styckeformatet skrivs över senare i koden | Applicera justering **efter** eventuella andra formateringsanrop som kan återställa den |

Att hantera dessa punkter förhindrar körfel och garanterar att *how to edit footnote*-processen fungerar pålitligt.

## Nästa steg

Nu när du vet **how to edit footnote**‑element kan du utforska relaterade uppgifter:

* **Lägg till anpassad fotnotreferensstil** – modifiera `FootnoteReference`‑noder för att ändra numrering eller symboler.  
* **Programmera in nya fotnoter** – använd `DocumentBuilder.insertFootnote()` för dynamiskt innehåll.  
* **Applicera villkorlig formatering** – ändra fotnotens utseende baserat på styckeformat eller innehållslängd.

Varje av dessa utökningar bygger på samma API‑yta som du använde för *add custom dash*, *change footnote line* och *set paragraph alignment*.

---

*Glad kodning! Om handledningen hjälpte dig att bemästra fotnotredigering, överväg att dela den med ditt team eller bidra med en pull‑request för att förbättra exemplet ytterligare.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}