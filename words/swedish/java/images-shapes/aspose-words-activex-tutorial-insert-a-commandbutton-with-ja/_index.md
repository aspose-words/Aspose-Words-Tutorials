---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX-handledning visar hur du lägger till en CommandButton‑kontroll
  i ett Word‑dokument med Java. Lär dig hela koden, konfigurationen och sparstegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: sv
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX-handledning förklarar hur du bäddar in en CommandButton
  ActiveX‑kontroll i ett Word‑dokument med Java. Följ det kompletta exemplet för att
  skapa, konfigurera och spara dokumentet.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX-handledning – Java steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX-handledning – infoga en CommandButton med Java
url: /sv/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX‑handledning – infoga en CommandButton med Java

Om du behöver bädda in en ActiveX‑kontroll i en Word‑fil, guidar dig den här **Aspose.Words ActiveX‑handledningen** genom hela processen. Du får se hur du skapar ett tomt dokument, infogar en CommandButton, ställer in dess egenskaper och sparar resultatet – allt med vanlig Java‑kod.

Exemplet använder Aspose.Words for Java‑API:t, vilket eliminerar behovet av Microsoft Office på byggservern. I slutet av den här guiden kan du generera .docx‑filer som innehåller fullt funktionella CommandButton‑kontroller redo att användas i Windows‑miljöer.

## Förutsättningar

- Java Development Kit (JDK) 8 eller nyare installerat.
- Maven eller ett annat byggverktyg för att hantera beroenden.
- En Aspose.Words for Java‑licens (eller en tillfällig utvärderingsnyckel) för att undvika vattenstämplar i utvärderingsversionen.
- Grundläggande kunskap om Java‑syntax och objekt‑orienterad programmering.

> **Proffstips:** Lägg till Aspose.Words Maven‑beroendet i din `pom.xml` så att IDE:n automatiskt kan lösa klasser.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Steg 1: Skapa ett nytt tomt dokument och en `DocumentBuilder`

`Document`‑klassen representerar Word‑filen i minnet, medan `DocumentBuilder` erbjuder ett flytande API för att redigera dokumentet. Att initiera båda objekten förbereder dokumentet för vidare ändringar.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:**  
`DocumentBuilder` spårar den aktuella markörpositionen, så varje efterföljande infogningsoperation – som att lägga till en kontroll – visas exakt där du avser.

## Steg 2: Infoga en CommandButton ActiveX‑kontroll

Aspose.Words exponerar `Forms2OleControl` för ActiveX‑objekt. Metoden `insertForms2OleControl` kräver kontrolltypen, som du anger via uppräkningen `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Förklaring:**  
Den infogade kontrollen är ett COM‑baserat objekt som Word renderar som en klickbar knapp när dokumentet öppnas i en Windows‑miljö.

## Steg 3: Konfigurera knappens egenskaper

Efter infogning kan du justera knappens namn, rubrik, storlek och position. Dessa egenskaper påverkar hur kontrollen ser ut och beter sig i Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Varför dessa inställningar är viktiga:**  

- **Name** – Gör det möjligt för VBA‑makron att referera till kontrollen (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Bestämmer den synliga etiketten som användarna klickar på.
- **Left / Top** – Styr placeringen relativt sidmarginalerna.
- **Width / Height** – Säkerställer en konsekvent visuell storlek över olika skärmupplösningar.

## Steg 4: Spara dokumentet

Genom att anropa `save` skrivs den minnesbaserade representationen till en fysisk fil. Du kan välja vilket som helst av de stödjade formaten (`.docx`, `.doc`, `.pdf`, etc.). I den här handledningen behåller vi det ursprungliga Word‑formatet.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Resultat:**  
När du öppnar `ActiveXDemo.docx` i Microsoft Word visas en CommandButton med etiketten **Submit** placerad på de angivna koordinaterna. Att klicka på knappen utlöser standardbeteendet (ingen VBA‑kod är bifogad som standard).

## Fullständig källkod

När vi sätter ihop delarna ser det kompletta, körbara programmet ut så här:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Förväntat resultat

- En fil med namnet **ActiveXDemo.docx** i mappen `output`.
- När den öppnas i Microsoft Word (Windows) visar dokumentet en klickbar **Submit**‑knapp på den definierade positionen.
- Knappen kan väljas, flyttas eller länkas till VBA‑kod via Word‑gränssnittet (Developer → Properties).

## Hantera vanliga variationer

| Scenario | Adjustment |
|----------|------------|
| **Spara som .doc** (legacy‑format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Lägg till en händelsehanterare** | Word exponerar inte ActiveX‑händelser via Aspose.Words. Du måste lägga till VBA‑kod manuellt efter att dokumentet har genererats. |
| **Flera kontroller** | Upprepa infognings‑/konfigurationsblocket med olika `setName`‑ och `setCaption`‑värden. |
| **Olika kontrolltyp (t.ex. CheckBox)** | Använd `Forms2OleControlType.CHECKBOX` i anropet till `insertForms2OleControl`. |
| **Icke‑Windows‑plattformar** | ActiveX‑kontroller renderas endast i Windows‑Word. För plattformsoberoende lösningar, överväg innehållskontroller (`StructuredDocumentTag`). |

## Bästa praxis och fallgropar

- **Licensiera tidigt** – Registrera din Aspose.Words‑licens innan du skapar `Document` för att undvika utvärderingsmeddelanden.
- **Koordinatsystem** – Positioner mäts i punkter (1 pt = 1/72 tum). Konvertera från pixlar eller centimeter om ditt UI‑design använder dessa enheter.
- **Filsökvägar** – Använd absoluta sökvägar eller Javas `Paths`‑API för att undvika `FileNotFoundException` när mål‑katalogen saknas.
- **Trådsäkerhet** – `Document` och `DocumentBuilder` är inte trådsäkra. Skapa separata instanser per tråd om du genererar dokument parallellt.
- **Testning** – Verifiera det genererade dokumentet på den mål‑Word‑versionen (t.ex. Word 2016, Word 365) eftersom äldre versioner kan visa ActiveX‑kontroller annorlunda.

## Slutsats

Denna **Aspose.Words ActiveX‑handledning** visar hur du programatiskt lägger till en CommandButton‑kontroll i ett Word‑dokument med Java. Du har lärt dig hur du:

1. Initierar ett `Document` och en `DocumentBuilder`.
2. Infogar ett `Forms2OleControl` av typen `COMMAND_BUTTON`.
3. Ställer in knappens namn, rubrik, storlek och position.
4. Sparar dokumentet som en .docx‑fil som innehåller ActiveX‑kontrollen.

Härifrån kan du utforska ytterligare kontrolltyper, automatisera VBA‑makro‑injektion eller kombinera ActiveX‑kontroller med andra Aspose.Words‑funktioner såsom kopplad utskrift och innehållskontroller. Experimentera med olika layouter och integrera de genererade dokumenten i din större Java‑baserade rapporteringspipeline.

---


## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Använda OLE‑objekt och ActiveX‑kontroller i Aspose.Words för Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Konvertera Word till RTF med Aspose.Words för Java‑handledning](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}