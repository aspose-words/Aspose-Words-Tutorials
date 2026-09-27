---
category: general
date: 2026-09-27
description: Skapa docx som innehåller ActiveX i Java med Aspose.Words. Lär dig att
  infoga en ActiveX‑kommandoknapp steg för steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: sv
lastmod: 2026-09-27
og_description: Skapa docx med ActiveX i Java med Aspose.Words. Följ den här guiden
  för att infoga en ActiveX‑kommandoknapp och spara dokumentet.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Skapa docx med ActiveX i Java – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Hur man skapar docx som innehåller ActiveX med Java och Aspose.Words
url: /sv/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här skapar du docx som innehåller ActiveX med Java och Aspose.Words

Om du behöver **skapa docx som innehåller ActiveX**, visar den här guiden en komplett lösning. Du kommer att lära dig hur du **infogar en ActiveX‑kommandoknapp** i en Word‑fil med Aspose.Words för Java, och sedan sparar resultatet som en .docx som kan öppnas i Microsoft Word.

Att generera ett Word‑dokument programatiskt sparar dig från manuellt redigerande och garanterar konsekvens över rapporter, kontrakt eller formulärmallar. Stegen nedan täcker allt från projektuppsättning till hantering av vanliga fallgropar, så att du kan integrera tekniken i vilken Java‑applikation som helst.

## Förutsättningar

Innan du börjar, se till att du har:

* Java Development Kit (JDK) 8 eller senare installerat.
* Maven 3.6+ (eller ett annat byggverktyg du föredrar).
* En licensfil för Aspose.Words for Java (den kostnadsfria utvärderingen fungerar för testning).
* Microsoft Word installerat på målmaskinen om du vill verifiera ActiveX‑kontrollen visuellt.

Dessa objekt krävs eftersom Aspose.Words tillhandahåller API‑et som skapar dokumentet, medan Word behövs för att rendera ActiveX‑kontrollen.

## Steg 1: Ställ in Maven‑projektet

Skapa ett nytt Maven‑projekt eller lägg till Aspose.Words‑beroendet i en befintlig `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Proffstips:** Håll Aspose.Words‑versionen i synk med de officiella versionsnoterna för att dra nytta av buggfixar och nya ActiveX‑funktioner.

## Steg 2: Skriv Java‑koden som skapar dokumentet

Skapa en klass med namnet `ActiveXDocxCreator`. Koden nedan innehåller alla nödvändiga imports, en `main`‑metod och detaljerade kommentarer som förklarar varje operation.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Varför varje rad är viktig

* `Document` är behållaren för allt Word‑innehåll. Att skapa en ny instans ger dig en ren canvas.
* `DocumentBuilder` tillhandahåller ett flytande API för att infoga element; det spårar automatiskt infogningspunkten.
* `insertForms2OleControl()` skapar en generisk OLE‑kontrollplatshållare. Aspose.Words behandlar den som en ActiveX‑behållare.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` talar om för Word att platshållaren ska renderas som en CommandButton.
* `setCaption("Click Me")` definierar texten som visas på knappen.
* `setLeft` och `setTop` placerar knappen relativt till sidmarginalerna. Justera dessa värden för att passa din layout.
* `setWidth` och `setHeight` är valfria men förbättrar knappens utseende, särskilt när standardstorleken är för liten.
* `doc.save` skriver den minnesbaserade strukturen till en fysisk .docx‑fil som Word kan öppna.

## Steg 3: Verifiera det genererade dokumentet

Öppna `output/ActiveXCommandButton.docx` i Microsoft Word:

1. Dokumentet ska visa en enda sida med en knapp märkt **Click Me** placerad nära övre‑vänstra hörnet.
2. Om knappen inte visas, kontrollera att **ActiveX‑kontroller är aktiverade** i Words Trust Center (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. Knappen fungerar endast i Windows‑versioner av Word som stödjer ActiveX. På macOS eller webb‑baserad Word visas kontrollen som en statisk bild.

## Steg 4: Hantera vanliga kantfall

| Situation | Orsak | Rekommenderad åtgärd |
|-----------|-------|----------------------|
| Knappen saknas efter att filen öppnats | Words säkerhetsinställningar blockerar ActiveX | Aktivera “Run all controls without restrictions” för betrodda platser. |
| Den genererade .docx‑filen kan inte öppnas | Inkompatibel Aspose.Words‑version | Uppgradera till den senaste Aspose.Words‑utgåvan; äldre versioner kan misslyckas med att bädda in de nödvändiga OLE‑delarna korrekt. |
| Du behöver att knappen kör ett makro | ActiveX ensam innehåller ingen makrokod | Kombinera ActiveX‑kontrollen med ett VBA‑makro som hanterar `Click`‑händelsen. Använd `DocumentBuilder.insertOleObject`‑metoden för att bädda in en makro‑aktiverad mall. |
| Layouten blir fel på olika sidstorlekar | Koordinaterna är absoluta punkter | Använd `builder.getPageSetup().setPageWidth` och `setPageHeight` för att standardisera sidstorleken innan kontrollen placeras. |

## Steg 5: Utöka lösningen

Du kan infoga andra ActiveX‑kontroller genom att ändra `ControlType`‑enumen:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words stödjer också att infoga **ActiveX‑textrutor**, **listboxar** och **comboboxar**. Samma placeringsmetoder (`setLeft`, `setTop`, `setWidth`, `setHeight`) gäller.

Om du behöver placera flera kontroller, anropa `builder.insertForms2OleControl()` upprepade gånger och justera varje kontrolls koordinater därefter.

## Komplett källkodfil

Nedan är hela `ActiveXDocxCreator.java`‑filen klar för kopiering och inklistring:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Att köra detta program producerar ett **docx som innehåller ActiveX** som du kan distribuera till slutanvändare som behöver interaktiva formulär.

## Slutsats

Du vet nu hur du **skapar docx som innehåller ActiveX** med Java och Aspose.Words, och hur du **infogar en ActiveX‑kommandoknapp** programatiskt. Handledningen täckte projektuppsättning, fullständig källkod, verifieringssteg och strategier för att hantera typiska problem.

Från här kan du utforska:

* Lägga till VBA‑makron för att svara på knapptryckning.
* Bädda in andra ActiveX‑kontroller såsom kryssrutor eller kombinationsrutor.
* Automatisera genereringen av flersidiga formulär med dynamisk data.

Experimentera med olika koordinater, storlekar och kontrolltyper för att passa just ditt dokumentlayout. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Använda OLE‑objekt och ActiveX‑kontroller i Aspose.Words för Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Skapa rektangel‑form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}