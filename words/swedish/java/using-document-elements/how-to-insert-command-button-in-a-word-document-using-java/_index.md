---
category: general
date: 2026-08-23
description: Lär dig hur du infogar en kommandoknapp i ett Word‑dokument med Java
  och Aspose.Words. Denna guide visar hur du lägger till en formulärkontroll, sätter
  knappens namn och bäddar in en ActiveX‑knapp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: sv
lastmod: 2026-08-23
og_description: Infoga en kommandoknapp i ett Word‑dokument med Java. Följ den här
  guiden för att lägga till en formulärkontroll, ange knappnamn och bädda in en ActiveX‑knapp
  med Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Infoga kommandoknapp i Word med Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man infogar en kommandoknapp i ett Word‑dokument med Java
url: /sv/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar command button i ett Word-dokument med Java

Om du behöver **insert command button** i en Word‑fil, visar den här handledningen en komplett lösning med Aspose.Words for Java. Du kommer att se hur du lägger till ett formulärkontroll, konfigurerar dess rubrik och sätter knappens namn utan att lämna din IDE.

Guiden täcker allt du behöver för att skapa en `.docx` som innehåller en ActiveX‑knapp klar för användning i Microsoft Word. Ingen extra verktyg behövs, och exemplet körs på Java 8+.

## Vad du kommer att lära dig

* Hur man lägger till ett formulärkontroll av typen **CommandButton** i ett Word‑dokument.  
* De exakta stegen för att **set button name** och **add activex button** egenskaper.  
* Hur man sparar dokumentet så att knappen visas korrekt när det öppnas i Word.  

Du bör ha en grundläggande Java‑utvecklingsmiljö och ett Maven‑ eller Gradle‑projekt som kan importera Aspose.Words‑biblioteket.

## Förutsättningar

| Krav | Orsak |
|------|-------|
| Java 8 eller nyare | Aspose.Words for Java körs på Java 8+. |
| Maven‑ eller Gradle‑byggverktyg | Förenklar att lägga till Aspose.Words‑beroendet. |
| Aspose.Words for Java‑licens (eller gratis provversion) | Krävs för full funktionalitet; API‑et fungerar i utvärderingsläge. |
| En IDE såsom IntelliJ IDEA eller Eclipse | Gör det enklare att redigera och köra exemplet. |

## Steg 1: Lägg till Aspose.Words i ditt projekt

Om du använder Maven, lägg till följande beroende i `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

För Gradle, placera den här raden i `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

När beroendet har lösts kan du importera biblioteksklasserna i din Java‑källfil.

## Steg 2: Infoga command button – kärnkoden

Skapa en ny Java‑klass som heter `InsertCommandButtonDemo`. Koden nedan utför alla fyra åtgärder som krävs för att **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Varför varje rad är viktig

* **Document & DocumentBuilder** – De tillhandahåller en in‑memory‑representation av en Word‑fil och API‑et för att ändra dess innehåll.  
* **insertForms2OleControl** – Denna metod **adds form control** av typen `COMMAND_BUTTON`. Det returnerade `Forms2OleControl`‑objektet representerar ActiveX‑kontrollen.  
* **setName** – Tilldelar en programmatisk identifierare (`btnSubmit`). Word‑makron eller VBA kan referera till detta namn senare.  
* **setCaption** – Definierar den text som användaren ser på knappen, vilket svarar på frågan “hur man lägger till en knapp”.  
* **save** – Skriver `.docx`‑filen till disk och bevarar den inbäddade ActiveX‑knappen.

När programmet körs skapas `CommandButtonDemo.docx` i arbetskatalogen. När du öppnar filen i Microsoft Word visas en knapp med etiketten **Submit** som du kan klicka på (den visar en standard‑ActiveX‑dialog i utvärderingsläge).

## Steg 3: Verifiera den infogade knappen i Word

1. Öppna `CommandButtonDemo.docx` med Microsoft Word (2016 eller senare).  
2. Knappen **Submit** visas där markören var placerad under infogningen.  
3. Högerklicka på knappen och välj **Properties** för att se att fältet **Name** innehåller `btnSubmit`.  

Om knappen inte visas, kontrollera att **ActiveX controls** är aktiverade i Word:s Trust Center‑inställningar.

## Steg 4: Anpassa knappen (valfritt)

Du kan ytterligare anpassa knappen genom att justera dess storlek, position eller lägga till ett VBA‑makro. Klassen `Forms2OleControl` exponerar ytterligare egenskaper såsom `setWidth`, `setHeight` och `setLeft`. Nedan är ett exempel som gör knappen större:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Dessa rader kan placeras efter anropet `setCaption`. De demonstrerar **add activex button**‑anpassning utöver den grundläggande infogningen.

## Vanliga fallgropar och hur man undviker dem

| Symptom | Orsak | Åtgärd |
|---------|-------|--------|
| Knappen visas inte i Word | Dokumentet sparades innan kontrollen lades till | Se till att `insertForms2OleControl` anropas innan `doc.save`. |
| Knappens rubrik är tom | `setCaption` har inte anropats eller anropats med en tom sträng | Ange en icke‑tom sträng, t.ex. `"Submit"`. |
| VBA kan inte hitta knappen | Namnmatchning mellan VBA‑kod och värdet i `setName` | Håll namnet konsekvent; använd `setName("btnSubmit")` och referera till `btnSubmit` i VBA. |
| Säkerhetsvarning vid öppning av filen | Word:s makrosäkerhet blockerar ActiveX‑kontroller | Justera Trust Center > Macro Settings, eller signera dokumentet med ett betrott certifikat. |

## Fullt, körbart exempel

Nedan är den kompletta källfilen, klar för kopiering och inklistring i din IDE. Den innehåller import‑satserna, felhantering och ett kommentarsblock som förklarar varje huvudsteg.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Förväntat resultat:** Efter att programmet har körts innehåller `CommandButtonDemo.docx` en enda **Submit**‑knapp. När du öppnar filen i Word visas knappen exakt där `DocumentBuilder`‑markören befann sig.

## Nästa steg

* **Add more form controls** – Använd `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` eller `TEXT_BOX` för att bygga kompletta Word‑formulär.  
* **Combine with mail merge** – Infoga knappar i ett mail‑merge‑dokument för att skapa personliga interaktiva formulär.  
* **Attach VBA macros** – Programmera in VBA som reagerar på knappens `Click`‑händelse för avancerad automatisering.  

Dessa ämnen bygger naturligt på **add form control**‑tekniken du just har lärt dig.

---

### Sammanfattning

Du vet nu hur man **insert command button** i ett Word‑dokument med Java, hur man **add form control**, hur man **set button name**, och hur man **add activex button**‑anpassningar. Det kompletta exemplet körs direkt, och du kan anpassa det för att passa vilket dokument‑genereringsflöde som helst. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Combo Box Form Field in Word Document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}