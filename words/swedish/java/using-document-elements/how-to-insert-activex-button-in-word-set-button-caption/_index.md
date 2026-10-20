---
category: general
date: 2026-07-26
description: Hur man infogar en ActiveX‑knapp i ett Word‑dokument med Aspose.Words
  – lär dig att ange knappens rubrik, position och storlek på bara några rader.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: sv
lastmod: 2026-07-26
og_description: Hur man infogar en ActiveX‑knapp i ett Word‑dokument med Aspose.Words.
  Följ den här steg‑för‑steg‑handledningen för att ange knappens rubrik, position
  och storlek.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Hur man infogar en ActiveX‑knapp i Word – Snabbguide
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Hur man infogar en ActiveX‑knapp i Word – Ställ in knapptext
url: /sv/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar en ActiveX‑knapp i Word – Ange knapptext

Har du någonsin undrat **hur man infogar ActiveX**‑kontroller i en Word‑fil utan att öppna UI‑gränssnittet? Du är inte ensam. I många företagsapplikationer behöver du en klickbar knapp som kör ett makro, och att göra det programatiskt sparar timmar. Den här guiden visar dig exakt **hur man infogar ActiveX** CommandButton med Aspose.Words för Java, och—ja—hur man **ställer in knapptext** så att användaren vet vad som ska klickas på.

Vi går igenom hela processen: från att sätta upp biblioteket, skapa ett nytt dokument, lägga till knappen, justera dess storlek och placering, ge den en vänlig rubrik, och slutligen spara filen. När du är klar har du en körbar `.docx` som öppnas i Word med en fullt fungerande ActiveX‑knapp redo att köra ditt makro.

---

## Vad du kommer att lära dig

- Installera och referera Aspose.Words i ett Java‑projekt.  
- Skapa ett nytt `Document` och `DocumentBuilder`.  
- **Infoga ActiveX** CommandButton‑kontroll med en enda kodrad.  
- **Ställ in knapptext**, justera dess position och definiera dess dimensioner.  
- Spara dokumentet och öppna det i Word för att se resultatet.

Ingen förkunskap om ActiveX krävs; bara grundläggande Java‑kunskaper och en kopia av Aspose.Words.

---

## Förutsättningar

- Java 8 eller nyare installerat på din maskin.  
- Maven eller Gradle för beroendehantering (vi visar Maven‑exemplet).  
- En licensierad eller utvärderingskopi av **Aspose.Words for Java** (gratis provversion fungerar bra för denna demo).  
- Microsoft Word (någon nyare version) för att testa den genererade filen.

---

## Steg 1: Ställ in Aspose.Words i ditt projekt

Först och främst—lägg till Aspose.Words‑beroendet. Om du använder Maven, lägg in följande i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle‑användare kan lägga till:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Efter ett snabbt `mvn clean install` (eller `gradle build`) kommer biblioteket att finnas på din classpath och du är redo att koda.

---

## Steg 2: Skapa ett nytt dokument och en builder

Ett `Document` representerar hela Word‑filen, medan `DocumentBuilder` låter dig redigera den. Tänk på buildern som en penna som ritar på en tom duk.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Varför börja med ett tomt dokument? Det garanterar att du har full kontroll över varje element du lägger till, och det finns ingen dold formatering som kan överraska dig senare.

---

## Steg 3: Infoga ActiveX CommandButton‑kontrollen

Nu till stjärnan i showen. Aspose.Words exponerar `insertForms2OleControl` som kan placera vilken ActiveX‑kontroll du än specificerar. Här begär vi en **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoden returnerar ett `Forms2OleControl`‑objekt, vilket ger dig programmatisk åtkomst till knappens egenskaper. Här blir **hur man infogar activex** en enradare—utan att rota med lågnivå‑COM‑API:er.

---

## Steg 4: Position, storlek och ange knapptext

En knapp som svävar i mitten av sidan är inte särskilt användbar. Du vill placera den där användarna förväntar sig den, ge den en rimlig storlek, och—framför allt—**ställa in knapptext** så att de vet vad ett klick gör.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Varför dessa siffror?** Word använder punkter (1 pt ≈ 1/72 tum). `100 pt` ≈ 1,4 tum från vänster, `150 pt` ≈ 2,1 tum från toppen—ungefär mitten av en standard‑A4‑sida. Justera dem efter ditt layoutbehov.

Att ange rubriken är avgörande; utan den ser knappen ut som en tom rektangel. Metoden `setCaption` accepterar vilken sträng som helst, så du kan lokalisera den senare om så önskas.

---

## Steg 5: Spara dokumentet

Slutligen, skriv dokumentet till disk. Du kan välja vilken mapp du vill; se bara till att sökvägen finns.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

När du öppnar `ActiveXButton.docx` i Word ser du en välplacerad knapp med etiketten **“Click Me.”** Om du dubbelklickar på den kommer Word att be dig aktivera makron (eftersom ActiveX‑kontroller betraktas som makro‑aktiverade). Därefter kan du binda en VBA‑rutin till knappens `Click`‑händelse.

---

## Edge Cases & Tips du kan missa

- **Macro‑Enabled Format**: Word inaktiverar ActiveX‑kontroller i vanliga `.docx`‑filer om inte användaren aktiverar makron. Om du behöver att knappen ska fungera direkt, överväg att spara som `.docm` (macro‑enabled) genom att använda `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibility**: Äldre versioner av Word (före 2007) använder det binära `.doc`‑formatet. Aspose.Words kan spara till det formatet, men kontrollens egenskaper kan renderas något annorlunda.
- **Security Settings**: Vissa företagsmiljöer låser ner ActiveX. Om din knapp inte visas, kontrollera Word → Trust Center → ActiveX Settings.
- **Multiple Buttons**: Vill du ha fler än en? Upprepa bara anropet `insertForms2OleControl` och justera varje knapps `Left`/`Top`‑värden. Håll koll på de returnerade objekten så att du kan sätta individuella rubriker.
- **Styling the Caption**: Rubriken ärver standardfonten. För att ändra den måste du redigera den underliggande XML‑en eller applicera en Word‑stil efter infogning—utanför räckvidden för den här snabba guiden, men möjligt med Aspose.Words `ParagraphFormat`‑API.

---

## Fullt fungerande exempel

Nedan är den kompletta, körklara Java‑klassen. Kopiera‑klistra in den i din IDE, justera utsökvägen och tryck **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Förväntad utskrift**: Efter körning skriver konsolen ut sparplatsen. När du öppnar den genererade filen i Word visas en knapp placerad ungefär i mitten av sidan, märkt “Click Me”. Ett klick på den utlöser standard‑ActiveX‑klick‑händelsen (du måste bifoga ett VBA‑makro för att svara).

---

## Slutsats

Du vet nu **hur man infogar ActiveX** CommandButton‑kontroller i ett Word‑dokument programatiskt med Aspose.Words, och du har sett exakt hur man **ställer in knapptext**, position och storlek på kontrollen. Detta tillvägagångssätt eliminerar manuellt UI‑arbete, integreras smidigt i automatiserade rapportgeneratorer och ger dig full kontroll över the

## Vad du bör lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Infoga inbäddad bild i Word‑dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Infoga en bild i Word‑dokumentets sidhuvud | Aspose.Words för .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}