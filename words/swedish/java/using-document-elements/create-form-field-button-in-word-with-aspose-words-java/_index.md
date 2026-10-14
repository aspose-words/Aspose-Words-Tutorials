---
category: general
date: 2026-10-13
description: Skapa formulärfältknapp i Word med Aspose.Words för Java. Lär dig hur
  du infogar kommandoknapp‑formulärfält och sätter kommandoknappens rubrik i några
  enkla steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: sv
lastmod: 2026-10-13
og_description: Skapa formulärfältknapp i Word med Aspose.Words för Java. Den här
  handledningen visar hur du snabbt infogar kommandoknappfält i Word och sätter kommandoknappens
  bildtext.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Skapa formulärfältknapp i Word – Aspose.Words Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa formulärfältknapp i Word med Aspose.Words Java
url: /sv/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa formulärfältknapp i Word med Aspose.Words Java

Om du behöver **skapa formulärfältknapp** i ett Word‑dokument, guidar den här guiden dig genom hela processen med Aspose.Words för Java. Oavsett om du bygger en ifyllnadsmall för formulär eller lägger till interaktiva kontroller i en rapport, får du lära dig hur du **infogar command button word**‑formulärfält och **sätter command button caption** med minimal kod.

Tutorialen täcker allt från Maven‑inställning till ett fullt körbart exempel, så att du kan kopiera‑klistra koden, köra den och se en `.docx`‑fil som innehåller en klickbar knapp redo för vidare anpassning.

## Förutsättningar

Innan du börjar, se till att du har:

- Java 17 (eller nyare) installerat och konfigurerat på din maskin.
- Maven 3.6+ för beroendehantering.
- En IDE eller textredigerare du föredrar (t.ex. IntelliJ IDEA, VS Code).
- En giltig Aspose.Words för Java‑licens (gratis provversion fungerar för utvärdering).

## Steg 1: Lägg till Aspose.Words i ditt Maven‑projekt

Skapa en `pom.xml` (eller redigera den befintliga) och inkludera Aspose.Words‑beroendet:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Proffstips:** Håll versionsnumret uppdaterat. Nya releaser lägger till stöd för de senaste Word‑funktionerna och förbättrar prestandan.

## Steg 2: Initiera ett tomt dokument och en `DocumentBuilder`

Klassen `DocumentBuilder` erbjuder ett flytande API för att redigera ett Word‑dokument. I detta steg skapar vi ett tomt `Document` och kopplar en builder till det.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Att skapa dokumentet är grunden för **skapa formulärfältknapp**‑objekt senare i tutorialen.

## Steg 3: Infoga ett command button‑formulärfält

Aspose.Words exponerar klassen `Forms2OleControl` för OLE‑formulärkontroller. För att **infoga command button word**‑formulärfält, anropa `insertForms2OleControl` med enum‑värdet `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoden returnerar en `Forms2OleControl`‑instans som vi kan konfigurera innan vi sparar.

## Steg 4: Definiera storlek och position för knappen

En command button kräver explicita dimensioner och placering på sidan. Justera bredd, höjd och koordinater så att de passar ditt layout‑behov.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Finjustering av dessa värden säkerställer att knappen visas exakt där du vill ha den i det slutgiltiga dokumentet.

## Steg 5: **Sätt command button caption**

Den synliga texten på knappen styrs av metoden `setCaption`. Här **sätter vi command button caption** för att vägleda användaren.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Du kan ersätta `"Click Me"` med vilken etikett som helst som matchar ditt formulärs syfte, t.ex. `"Submit"` eller `"Approve"`.

## Steg 6: Spara dokumentet

Till sist skriver vi dokumentet till disk. Den resulterande filen innehåller den interaktiva knappen och kan öppnas i Microsoft Word eller LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

När programmet körs får du `CommandButtonDemo.docx`. Att öppna den i Word visar en knapp med etiketten **Click Me** placerad 50 pt från vänster och 100 pt från toppen av sidan.

### Förväntat resultat

- En `.docx`‑fil med namnet `CommandButtonDemo.docx`.
- Dokumentet innehåller en enda sida med ett command button‑formulärfält.
- Knappen visar den caption du har angett (t.ex. **Click Me**).

## Vanliga variationer och kantfall

| Situation | Hur du anpassar |
|-----------|-----------------|
| **Flera knappar** | Anropa `insertForms2OleControl` upprepade gånger och justera `setLeft`/`setTop` för varje ny knapp. |
| **Olika caption per knapp** | Använd `setCaption` med en unik sträng efter varje infogning. |
| **Knapp i en tabellcell** | Flytta markören till önskad cell med `builder.moveTo(cell.getFirstParagraph())` innan du infogar kontrollen. |
| **Legacy Word‑format (.doc)** | Spara med `doc.save("Demo.doc", SaveFormat.DOC);` – command button bevaras. |
| **Read‑only‑formulär** | Efter infogning, sätt `commandButton.setEnabled(false);` för att förhindra användarinteraktion. |

## Tips för en robust implementation

- **Validera dimensioner**: Extremt stora bredder kan göra att knappen går utanför sidmarginalen.
- **Licenshantering**: Utan en giltig licens lägger Aspose.Words till ett vattenstämpel i det genererade dokumentet. Applicera din licens tidigt med `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testning**: Öppna den genererade filen i Word och slå på **Design Mode** (Developer → Design Mode) för att se knappens egenskaper.

## Fullständig källkodssammanfattning

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Kopiera koden till en fil med namnet `InsertCommandButtonDemo.java`, kompilera med Maven (`mvn compile`) och kör (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Det genererade dokumentet kommer att ligga i projektets rotmapp.

## Slutsats

Du vet nu hur du **skapar formulärfältknapp** i Word med Aspose.Words för Java, hur du **infogar command button word**‑formulärfält, och hur du **sätter command button caption** programatiskt. Detta end‑to‑end‑exempel ger dig en solid grund för att bygga rikare, interaktiva Word‑dokument—oavsett om du behöver en enda submit‑knapp eller en hel svit av formulärkontroller.

### Vad blir nästa?

- Utforska andra formulärkontroller såsom kryssrutor (`Forms2OleControlType.CHECKBOX`) och textrutor (`Forms2OleControlType.TEXTBOX`).
- Kombinera formulärfält med mail‑merge för att generera personliga frågeformulär.
- Använd Aspose.Words `FormField`‑API för att läsa användarinmatade data efter att dokumentet fyllts i.

Känn dig fri att experimentera med olika storlekar, captions och placeringar. När du bemästrar command buttons blir det enkelt att lägga till fullständiga formulär i dina Word‑automatiseringspipeline. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande tutorials täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}