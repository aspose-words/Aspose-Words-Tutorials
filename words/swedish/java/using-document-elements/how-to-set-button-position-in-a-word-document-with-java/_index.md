---
category: general
date: 2026-09-24
description: Ställ in knappens position i ett Word‑dokument med Java och Aspose.Words.
  Lär dig hur du infogar en knapp, lägger till en ActiveX‑kontroll och skapar ett
  Word‑dokument i Java‑stil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: sv
lastmod: 2026-09-24
og_description: Ställ in knappens position i ett Word‑dokument med Java. Denna guide
  visar hur du infogar en knapp, lägger till en ActiveX‑kontroll och skapar ett Word‑dokument
  i Java med Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Ställ in knappens position i ett Word‑dokument med Java – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Hur man sätter knappens position i ett Word‑dokument med Java
url: /sv/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ställer in knappens position i ett Word-dokument med Java

Om du behöver **set button position** i en Word-fil, visar den här guiden en komplett, körbar lösning. Oavsett om du bygger en mall som kräver användarinteraktion eller automatiserar ett formulär, kommer du att lära dig exakt **how to insert button** med Aspose.Words för Java och kontrollera dess placering.

Tutorialen täcker allt du behöver för att **add ActiveX control** till ett Word-dokument, förklarar hur man **add button to Word**, och demonstrerar hela processen för **create Word document Java** stil. Inga externa referenser krävs—bara kopiera, kör och verifiera resultatet.

## Förutsättningar

* Java 17 (eller någon Java 8+ runtime) installerad.
* Maven eller Gradle för att hantera beroenden.
* En Aspose.Words för Java-licens (gratisprov fungerar för utvärdering).
* En grundläggande förståelse för Java-syntax.

> **Pro tip:** Förvara dina Aspose.Words JAR-filer i en `libs/`-mapp och lägg till dem i ditt projekts classpath för att undvika versionskonflikter.

## Steg 1: Ställ in Maven-projektet

Skapa ett enkelt Maven-projekt (eller använd Gradle) och lägg till Aspose.Words‑beroendet:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Kör `mvn clean compile` för att ladda ner biblioteket och förbereda byggsökvägen.

## Steg 2: Skapa ett nytt Word-dokument

Den första operationen är att **create Word document java** stil. Du instansierar ett `Document`-objekt och en `DocumentBuilder` som låter dig redigera filen.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`-klassen representerar hela .docx-filen, medan `DocumentBuilder` erbjuder ett flytande API för att infoga innehåll.

## Steg 3: Hur man infogar knapp – add ActiveX control

Aspose.Words exponerar `Forms2OleControl`-klassen för att infoga äldre ActiveX‑kontroller såsom en CommandButton. Detta steg visar det exakta sättet att **how to insert button** i dokumentet.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl`‑metoden returnerar en `Forms2OleControl`‑instans som du kan konfigurera. Detta är kärnan i **add ActiveX control**‑processen.

## Steg 4: Ställ in knappens position

Nu **set button position** faktiskt. Kontrollens `setLeft`- och `setTop`-metoder accepterar värden i punkter (1 pt = 1/72 tum). För att justera knappen med vanliga skärmkoordinater kan du konvertera pixlar till punkter (1 px ≈ 0,75 pt). I exemplet placerar vi knappen 100 px från vänster kant och 150 px från överkant.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Eftersom logiken för **set button position** är kapslad här, kan du återanvända dessa rader när du behöver flytta en kontroll. Justera siffrorna för att passa dina layoutkrav.

## Steg 5: Definiera storlek och rubrik

En knapp utan etikett är förvirrande. Använd `setWidth`, `setHeight` och `setCaption` för att ge den ett synligt utseende.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Storleken uttrycks också i punkter, så vi konverterar från pixlar för konsekvens.

## Steg 6: Spara dokumentet – slutför **create Word document java**‑flödet

Slutligen, skriv filen till disk. Sökvägen kan vara absolut eller relativ till projektets rot.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

När programmet körs skapas `CommandButtonDemo.docx` i `output`‑mappen. När du öppnar filen i Microsoft Word visas en klickbar knapp placerad exakt där du satte den.

### Förväntat resultat

* En `.docx`-fil med namnet **CommandButtonDemo.docx**.
* I dokumentet visas en **CommandButton** med etiketten “Click Me” 100 px från vänstermarginalen och 150 px från övermarginalen.
* Knappen svarar på klick när dokumentet öppnas i Word (den visar ett standard‑ActiveX‑meddelande om du inte bifogar anpassad VBA‑kod).

## Steg 7: Vanliga variationer och kantfall

### Lägga till flera knappar

Om du behöver **add button to Word** mer än en gång, upprepa steg 3‑5 med en ny `Forms2OleControl`‑instans varje gång. Kom ihåg att justera `setTop`‑värdet så att knapparna inte överlappar.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Arbeta utan licens

Aspose.Words lägger till ett vattenmärke när det används utan licens. För produktionskod, köp en licens och tillämpa den i början av `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatibilitet med äldre Office-versioner

ActiveX‑kontroller stöds i `.doc` (Word 97‑2003) formatet. För att skapa en äldre fil, ändra sparformatet:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Fullständig källkod (körbar)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Spara filen som `src/main/java/CommandButtonDemo.java`, kör `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, och öppna det genererade dokumentet för att se resultatet.

## Vanliga frågor

**Q: Fungerar detta med OpenJDK?**  
A: Ja. Aspose.Words är ren Java och körs på alla JDK 8+‑implementationer, inklusive OpenJDK.

**Q: Kan jag ändra knappens teckensnitt eller färg?**  
A: Utseendet på en ActiveX‑knapp styrs av värdapplikationen (Word). Du kan bifoga VBA‑kod för att ändra egenskaper vid körning, men det statiska utseendet är begränsat till standardstilen.

**Q: Vad händer om jag behöver placera knappen i en tabellcell?**  
A: Flytta `DocumentBuilder`‑markören in i cellen innan du anropar `insertForms2OleControl`. Kontrollen ärver cellens layout, och du kan fortfarande använda `setLeft`/`setTop` för finjustering.

## Slutsats

Du vet nu hur du **set button position** i ett Word-dokument med Java, hur du **how to insert button**, hur du **add ActiveX control**, och hur du **add button to Word** samtidigt som du följer bästa praxis för **create Word document java**‑projekt. Det kompletta exemplet demonstrerar hela arbetsflödet—från projektuppsättning till en sparad `.docx`‑fil som innehåller en funktionell CommandButton.

### Nästa steg

* Utforska andra `Forms2OleControl.ControlType`‑värden (t.ex. `CHECKBOX`, `TEXTBOX`) för att bygga rikare formulär.
* Kombinera knappen med VBA‑makron för anpassad klickhantering.
* Använd Aspose.Words‑funktion för sammanslagning av post för att generera personliga dokument som redan innehåller interaktiva kontroller.

Lycka till med kodningen, och njut av att automatisera Word-dokument med Java!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}