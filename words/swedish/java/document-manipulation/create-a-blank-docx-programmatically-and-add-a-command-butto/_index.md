---
category: general
date: 2026-10-20
description: Skapa ett tomt DOCX-programmatiskt och bädda in en kommandoknapp med
  Java. Lär dig den kompletta koden för att skapa ett Word‑dokument, spara Word med
  knappen och sätta kommandoknappens rubrik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: sv
lastmod: 2026-10-20
og_description: Skapa ett tomt DOCX-programmatiskt och bädda in en kommandoknapp.
  Följ den här steg‑för‑steg Java‑guiden för att spara Word med knapp och ange kommandoknappens
  rubrik.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Skapa ett tomt DOCX-programmerat – lägg till en kommandoknapp
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Skapa ett tomt DOCX-programmerat och lägg till en kommandoknapp
url: /sv/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt DOCX-programmässigt och lägg till en kommandoknapp

Om du behöver **skapa ett tomt DOCX programmässigt**, visar den här handledningen hur du bäddar in en kommandoknapp direkt i filen. Du får den kompletta *create word document code* som sparar ett Word‑dokument med en knapp, låter dig **set command button caption**, och fungerar med det senaste Aspose.Words för Java‑biblioteket.

Att bädda in interaktiva kontroller i en DOCX‑fil är användbart när du vill distribuera mallar som triggar makron, startar externa program, eller helt enkelt guidar användare med en klickbar “Click Me”-knapp. Stegen nedan täcker allt från att initiera ett tomt dokument till att spara den slutliga filen på disk.

## Förutsättningar

* Java 17 eller nyare installerat.
* Maven (eller ditt föredragna byggverktyg) för att hantera beroenden.
* Aspose.Words for Java 23.9 eller senare. Lägg till beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* En IDE såsom IntelliJ IDEA eller VS Code (vilken editor som helst som stödjer Java fungerar).

## Skapa ett tomt DOCX programmässigt – steg‑för‑steg

Följande avsnitt delar upp processen i tydliga, numrerade steg. Varje steg förklarar **varför** det behövs, inte bara **vad** du ska skriva.

### Steg 1: Initiera ett nytt tomt dokument

Ett tomt dokument är duken där du placerar kommandoknappen. Aspose.Words tillhandahåller `Document`‑klassen för detta ändamål.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Varför detta är viktigt*: Att börja med ett tomt `Document` säkerställer att ingen dold formatering eller befintliga kontroller stör knappen du lägger till senare.

### Steg 2: Ställ in en `DocumentBuilder`

`DocumentBuilder` är ett verktyg som låter dig infoga innehåll, inklusive OLE‑kontroller, utan att behöva hantera lågnivå‑nodmanipulation.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt*: Byggaren behåller den aktuella markörpositionen, så knappen placeras exakt där du anger.

### Steg 3: Infoga en OLE‑kommandoknapp

Word behandlar interaktiva kontroller som OLE‑objekt (Object Linking and Embedding). Aspose.Words exponerar `Forms2OleControl` för detta.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Varför detta är viktigt*: Att infoga kontrollen skapar en platshållare som du senare kan konfigurera (typ, rubrik, position).

### Steg 4: Konfigurera knappen – typ, rubrik och placering

Du måste definiera kontrollens typ (`COMMANDBUTTON`), ange en användarsynlig rubrik och placera den på sidan.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Varför detta är viktigt*:  
* **Type** talar om för Word att kontrollen beter sig som en klickbar knapp.  
* **Caption** är texten användaren ser; att ändra den är hur du **set command button caption**.  
* **Left** och **Top** styr den exakta placeringen, vilket är avgörande när du **add command button word** dokument som kräver exakt layout.

### Steg 5: Spara dokumentet med den inbäddade knappen

Slutligen skriv filen till disk. Den resulterande filen kan öppnas i Microsoft Word, där knappen kommer att vara fullt funktionell.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Varför detta är viktigt*: Detta steg **saves Word with button** så att kontrollen kvarstår på olika maskiner. Filen kan distribueras som en mall eller användas i automatiserade rapportgenererings‑pipelines.

## Fullt fungerande exempel

Kopiera hela klassen nedan till en fil med namnet `CommandButtonDemo.java`, justera `YOUR_DIRECTORY` till en riktig sökväg, och kör den med `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Förväntat resultat

När du öppnar `CommandButton.docx` i Microsoft Word:

* Dokumentet är helt tomt förutom en knapp med etiketten **Click Me**.
* Att klicka på knappen visar Word:s standardbeteende (den gör inget om inget makro är bifogat), vilket bekräftar att OLE‑kontrollen har bäddats in korrekt.

## Vanliga frågor & edge cases

| Question | Answer |
|----------|--------|
| **Kan jag ändra knappens storlek?** | Ja. Använd `commandButton.setWidth(double)` och `commandButton.setHeight(double)` för att justera dimensionerna i punkter. |
| **Vad händer om jag behöver ett makro kopplat till knappen?** | Knappen i sig är bara en OLE‑kontroll. Du måste lägga till ett VBA‑makro i dokumentet manuellt eller via Aspose.Words `Document`‑API:s `addMacro`‑verktyg. |
| **Fungerar knappen i LibreOffice?** | LibreOffice stödjer begränsade OLE‑kontroller. Knappen visas, men dess klickbeteende kan skilja sig. |
| **Hur lägger man till flera knappar?** | Upprepa Steg 3‑4 med en ny `Forms2OleControl`‑instans. Justera `setLeft`/`setTop` för varje knapp för att undvika överlappning. |
| **Är koden kompatibel med .NET?** | Samma logik gäller, men du skulle använda `Aspose.Words` för .NET‑klasser (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Tips från fältet

* **Proffstips:** Använd `builder.moveToDocumentEnd()` innan du infogar knappen om du vill ha den längst ner i dokumentet, oavsett tidigare innehåll.
* **Var uppmärksam på:** Mycket små `Left`/`Top`‑värden kan placera knappen utanför utskriftsområdet, vilket gör den osynlig i Word:s layoutvy.
* **Prestanda‑notering:** Att infoga många OLE‑kontroller kan öka filstorleken. Om du bara behöver en visuell ledtråd, överväg att använda en enkel `Shape` med en hyperlänk istället.

## Slutsats

Du vet nu hur du **create a blank DOCX programmatically** och bäddar in en fullt funktionell kommandoknapp med Java. Handledningen täckte hela *create word document code*-arbetsflödet, demonstrerade hur du **save Word with button**, visade rätt sätt att **add command button word**‑element, och förklarade hur du **set command button caption**.

Från här kan du:

* Lägg till fler OLE‑kontroller (kryssrutor, kombinationsrutor) för rikare formulär.
* Bifoga VBA‑makron för att låta knappen utföra anpassade åtgärder.
* Kombinera denna teknik med dokument‑mail‑merge för dynamiska, interaktiva mallar.

Känn dig fri att experimentera med knappstilar, positioner och ytterligare kontroller för att matcha dina specifika affärskrav. Lycka till med kodandet


## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa tomt Word‑dokument med en kommandoknapp – steg‑för‑steg‑guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Hur man infogar ActiveX‑knapp i Word – Ställ in knappens rubrik](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Skapa tomt Word‑dokument med Java – Fullständig Aspose.Words‑guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}