---
category: general
date: 2026-11-22
description: Skapa makronknapp i ett Word‑dokument med Java. Lär dig att infoga en
  kommandoknapp, ange knapptext och länka makro till knappen för interaktiva dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: sv
lastmod: 2026-11-22
og_description: Skapa makronknapp i ett Word-dokument med Java. Den här handledningen
  visar hur du infogar en kommandoknapp, ställer in knapptexten och länkar makrot
  till knappen för full interaktivitet.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Skapa en makronknapp i ett Word‑dokument med Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Hur man skapar en makroknapp i ett Word‑dokument med Aspose.Words för Java
url: /sv/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du makroknapp i ett Word‑dokument med Aspose.Words för Java

Om du behöver **skapa makroknapp** i en Word‑fil, visar den här guiden exakt vilka steg som krävs. Du lär dig hur du **infogar kommandoknapp**, **sätter knapptext** och **länkar makro till knappen** så att dokumentet blir helt interaktivt.

Utvecklare bäddar ofta in OLE‑kontroller för att trigga VBA‑makron från ett dokument. Denna tutorial täcker hela arbetsflödet, från projektuppsättning till ett körbart Java‑exempel som lägger till en **interaktiv knapp** i en .docx‑fil. Inga externa skript behövs – allt körs i Java‑processen.

## Förutsättningar

Innan du börjar, se till att du har:

* JDK 17 eller senare installerat.  
* Maven 3.8+ (eller Gradle) för beroendehantering.  
* Aspose.Words for Java 23.9 eller nyare – biblioteket tillhandahåller `DocumentBuilder` och OLE‑kontroll‑API:er.  
* Grundläggande kunskap om Java och VBA‑makron.

Om någon av dessa komponenter saknas, installera dem först; resten av tutorialen förutsätter att de är tillgängliga.

## Så skapar du makroknapp med Aspose.Words för Java

Kärnan i lösningen består av fyra åtgärder:

1. **Infoga kommandoknapp**‑OLE‑kontroll i dokumentet.  
2. **Sätt knapptext** (caption) som användaren ser.  
3. **Länka makro till knappen** så att ett klick kör den önskade VBA‑rutinen.  
4. **Spara dokumentet** med det inbäddade makrot.

Varje åtgärd förklaras i sin egen sektion nedan.

### Steg 1: Infoga kommandoknapp i dokumentet

`DocumentBuilder.insertForms2OleControl` skapar en OLE‑kontroll av den angivna typen. Konstanten `Forms2OleControlType.COMMAND_BUTTON` talar om för Aspose.Words att generera en kommandoknapp som kan hysa ett makro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Varför detta är viktigt:** OLE‑kontrollen fungerar som en behållare för makrot. Utan att infoga den finns ingen visuell komponent för användaren att klicka på.

### Steg 2: Sätt knapptext (caption)

Caption är den synliga etiketten på knappen. Använd `setCaption` för att definiera vad användaren ser.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Varför detta är viktigt:** Tydlig knapptext förbättrar användbarheten. Metoden `setCaption` uppdaterar OLE‑kontrollens `Caption`‑egenskap, som Word renderar som knappens etikett.

### Steg 3: Länka makro till knappen

Ett makro identifieras med sitt namn, till exempel `MyMacro`. Metoden `setOnClick` lagrar detta namn i knappens `OnClick`‑händelsehanterare.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Varför detta är viktigt:** Att länka ett makro skapar den interaktiva beteendet. När användaren klickar på knappen i Word körs den associerade VBA‑rutinen.

### Steg 4: Lägg till interaktiv knapp i ett Word‑dokument

Efter att OLE‑kontrollen har konfigurerats kan du vilja placera den, ändra storlek eller lägga till omgivande text. `DocumentBuilder` fortsätter att arbeta på dokumentet, så du kan infoga stycken före eller efter knappen.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Varför detta är viktigt:** Att spara som `.docm` bevarar makrokoden. Om du sparar som `.docx` förloras makroreferensen.

## Fullt körbart exempel

Nedan är det kompletta Java‑programmet, inklusive imports, felhantering och kommentarer som förklarar varje steg. Kopiera koden till ett Maven‑projekt med Aspose.Words‑beroendet och kör det.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Förväntad output

När programmet körs genereras `MacroButtonDemo.docm`. När du öppnar filen i Microsoft Word visas:

* Ett stycke med texten *“Press the button to execute the macro:”*.
* En knapp med etiketten **Run Report** direkt under stycket.
* När du klickar på knappen försöker Word köra makrot `MyMacro`. (Du måste manuellt lägga till den faktiska VBA‑koden i dokumentet eller via ett annat automatiseringssteg.)

Om makrot inte finns visar Word en säkerhetsvarning, vilket är standardbeteende för makro‑aktiverade dokument.

## Vanliga variationer och kantfall

| Scenario | Hur du anpassar koden |
|----------|-----------------------|
| **Olika knappcaption** | Ändra strängen som skickas till `setCaption`. |
| **Flera knappar** | Anropa `insertForms2OleControl` upprepade gånger, varje gång med egen `setCaption` och `setOnClick`. |
| **Anpassade makronamn** | Ersätt `"MyMacro"` med vilket giltigt VBA‑procedurnamn som helst, t.ex. `"ExportToExcel"`. |
| **Knappstorleksbegränsningar** | Justera värdena för `setWidth` och `setHeight`; Word respekterar de punkter du anger. |
| **Bädda in makrot programatiskt** | Använd `Document.getBuiltInDocumentProperties().add("Macros", …)` eller ett separat VBA‑injiceringssteg; Aspose.Words skriver inte själva VBA‑kod. |

**Proffstips:** Testa alltid den genererade `.docm`‑filen på en maskin med makrosäkerhet satt till *Enable all macros* under utveckling. I produktion, signera makrot med ett betrott certifikat för att undvika säkerhetspromptar.

## Felsökningschecklista

* **Knappen visas inte** – Kontrollera att dokumentet sparas som `.docm` och öppnas i en Word‑version som stödjer OLE‑kontroller.  
* **Makrot körs inte** – Säkerställ att makronamnet matchar exakt, inklusive skiftläge, och att makrot finns i dokumentets VBA‑projekt.  
* **Knappcaptionen kapas** – Öka knappens bredd med `setWidth` för att rymma längre text.  
* **Oväntad layoutförskjutning** – Använd `builder.moveTo` för att placera markören exakt innan du infogar kontrollen.

## Slutsats

Du vet nu hur du **skapar makroknapp** i ett Word‑dokument med Java, **infogar kommandoknapp**, **sätter knapptext** och **länkar makro till knappen** för full interaktivitet. Det kompletta exemplet demonstrerar varje nödvändigt API‑anrop, förklarar varför varje steg är viktigt och ger vägledning för vanliga variationer.

Nästa steg kan vara att utforska:

* **Lägg till interaktiv knapp** i befintliga mallar istället för ett nytt dokument.  
* **Programatiskt injicera VBA‑kod** med Open XML SDK eller ett sekundärt automatiseringsverktyg.  
* **Kombinera flera OLE‑kontroller** (kryssrutor, listboxar) för att bygga rika formulär.

Experimentera med olika captions, makronamn och knappstorlekar för att passa just ditt användningsområde. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande handledningarna behandlar närliggande ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}