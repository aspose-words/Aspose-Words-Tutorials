---
category: general
date: 2026-07-29
description: 'Ställ in knappstorlek Java‑handledning: lär dig hur du infogar en ActiveX‑kommandoknapp
  i ett Word‑dokument med Java och Aspose.Words, samt storleksinställning och skapande
  av ett tomt dokument.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: sv
lastmod: 2026-07-29
og_description: Set button size Java‑guide visar hur man infogar en ActiveX‑kommandoknapp
  i en Word‑fil med Java, justerar dess storlek och sparar dokumentet programatiskt.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Ställ in knappstorlek Java – Lägg till ActiveX‑kommandoknapp i Word med
  Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Ställ in knappstorlek i Java – Infoga ActiveX‑kommandoknapp i Word
url: /sv/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Infoga ActiveX Command Button i Word

Har du någonsin undrat **how to set button size java** när du automatiserar Word-dokument? Kanske bygger du ett rapporteringsverktyg som behöver en klickbar “Submit”-knapp direkt i .docx-filen. I den här handledningen går vi igenom hela processen — skapa ett tomt Word‑dokument, infoga en ActiveX‑kommandoknapp och explicit ange dess bredd och höjd — allt med Java och Aspose.Words.

Vi kommer också att besvara den kvarstående frågan “how to insert activex” som dyker upp för många utvecklare. I slutet har du ett körbart program som skapar en Word‑fil med en perfekt dimensionerad kommandoknapp, redo för vidare anpassning.

---

## Vad du behöver

- **Java Development Kit (JDK) 8 eller nyare** – koden kompileras med vilken recent JDK som helst.
- **Aspose.Words for Java** (den senaste versionen per juli 2026). Hämta JAR‑filen från [Aspose webbplats](https://products.aspose.com/words/java) eller via Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- En IDE eller enkel textredigerare — IntelliJ IDEA, Eclipse eller VS Code räcker.
- En mapp där du vill att den genererade **CommandButton.docx** ska sparas.

Det är allt. Inga extra Office‑interop‑bibliotek, inga COM‑knep, bara ren Java.

## Steg‑för‑steg‑implementation

Vi delar upp lösningen i fem logiska steg. Varje steg har en egen H2‑rubrik; ett av dem innehåller vårt **primary keyword** för att uppfylla SEO.

### 1. Ställ in projektet och importera Aspose.Words

Först, skapa ett nytt Maven‑ (eller Gradle‑)projekt och lägg till Aspose.Words‑beroendet som visas ovan. Importera sedan de nödvändiga klasserna i din Java‑källfil:

```java
import com.aspose.words.*;
```

> **Pro tip:** Om du använder en IDE, låt den automatiskt importera klasserna. Det sparar mycket skrivande och förhindrar stavfel.

### 2. java create blank word Document

Nu skapar vi faktiskt **java create blank word** dokument. Detta är grunden som vi senare **insert command button word** på.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

`Document`‑objektet representerar hela Word‑filen i minnet. Vid detta tillfälle har filen inga sidor, ingen text — bara en ren tom sida.

### 3. Initiera DocumentBuilder och infoga ActiveX‑kontrollen

`DocumentBuilder` är ett verktyg som låter oss lägga till innehåll, stycken, tabeller och, ja, ActiveX‑kontroller. Här svarar vi på **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` är Asposes omslag runt ett OLE‑objekt. Genom att ange `COMMANDBUTTON` säger vi åt Word att bädda in en klassisk ActiveX‑kommandoknapp.

### 4. How to Set Button Size Java – Justera bredd och höjd

Nu kommer hjärtat i handledningen: **how to set button size java**. Kontrollen exponerar flera layout‑egenskaper — `Left`, `Top`, `Width` och `Height`. Att sätta dem direkt styr knappens utseende på sidan.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Varför dessa siffror? I Word motsvarar en punkt 1/72 tum. Så en bredd på `120` punkter blir ungefär 1,67 tum — tillräckligt stor för en läsbar etikett, men inte överväldigande. Justera värdena för att passa ditt layout; samma egenskaper svarar också på frågan **how to set button** som du kan ha.

> **Note:** Om du behöver en annan knapptyp (t.ex. en kryssruta), ersätt `Forms2OleControlType.COMMANDBUTTON` med det lämpliga enum‑värdet.

### 5. Spara dokumentet

Till sist, spara dokumentet till disk:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Ersätt `YOUR_DIRECTORY` med en absolut eller relativ sökväg på din maskin. Efter att programmet har körts, öppna den genererade filen i Microsoft Word. Du kommer att se en knapp med etiketten “Click Me” placerad 100 pts från vänster och 200 pts från toppen, med exakt de dimensioner vi angav.

## Fullt fungerande exempel

Nedan är den kompletta, redo‑till‑kör Java‑klassen. Kopiera‑klistra in den i `CommandButtonActiveX.java`, justera utdatavägen och tryck **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Förväntat resultat:** När du öppnar `CommandButton.docx` i Word visas en enda sida med en klickbar “Click Me”-knapp placerad ungefär i mitten av sidan. Knappens dimensioner matchar de värden du angav, vilket bekräftar att **set button size java** fungerar som avsett.

## Vanliga frågor & specialfall

### Vad händer om knappen inte visas i Word?

- **Kontrollera Word‑versionen.** ActiveX‑kontroller kräver skrivbordsversionen av Word; Word Online tar bort dem.
- **Se till att Aspose.Words‑licensen är tillämpad** (om du använder en betald version). En olicensierad utvärderingsversion kan bädda in ett vattenmärke men visar fortfarande kontrollen.

### Kan jag ändra knappens teckensnitt eller färg?

Ja. Efter att ha infogat kontrollen kan du komma åt dess underliggande OLE‑objekt och manipulera VBA‑egenskaperna. Det är ett mer avancerat ämne — titta på `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` för en röd rubrik, till exempel.

### Hur hanterar jag knappens klick‑händelse?

ActiveX‑kommandoknappar avfyrar en VBA‑`Click`‑händelse. För att göra knappen funktionell måste du bädda in ett makro i samma dokument. Aspose.Words kan lägga till ett makro‑modul via `Document.getMacros()`‑API:t, men makrokoden själv måste skrivas i VBA.

### Vad sägs om olika knapptyper?

Aspose.Words stödjer många `Forms2OleControlType`‑värden: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` osv. Byt ut enum‑konstanten i anropet `insertForms2OleControl` för att experimentera.

## Pro‑tips för produktionsklar kod

1. **Använd konstanter för layout‑värden** – gör framtida justeringar enklare.
2. **Wrapa sparvägen i ett `Path`‑objekt** för att undvika plattforms‑specifika separatorer.
3. **Disposera Document‑objektet** (eller använd try‑with‑resources) om du bearbetar många filer i en loop.
4. **Validera utdatamappen** innan du anropar `save` för att undvika `FileNotFoundException`.

## Slutsats

Du har precis lärt dig **set button size java** genom att skapa en tom Word‑fil, infoga en ActiveX‑kommandoknapp och exakt konfigurera dess dimensioner — allt med några rader Java‑kod. Detta täcker grunden för **how to insert activex**, **how to set button**, **java create blank word** och **insert command button word** i ett enda, självständigt exempel.

Nästa steg? Prova att anpassa knappens rubrik, lägga till ett makro som svarar på klick, eller bädda in flera kontroller på samma sida. Du kan också utforska att konvertera den resulterande .docx‑filen till PDF med Aspose.Words, där knappen bevaras som en statisk bild.

Känn dig fri att experimentera, och om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}