---
category: general
date: 2026-10-07
description: Skapa en ActiveX‑kommandoknapp i Java och programatiskt lägga till kommandoknappen
  i Word‑dokument. Lär dig hur du ställer in knappens vänstra och övre position.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: sv
lastmod: 2026-10-07
og_description: Skapa en ActiveX‑kommandoknapp i Java för att bädda in interaktiva
  kontroller i dina Word‑dokument. Lär dig hur du programatiskt lägger till en kommandoknapp,
  ställer in dess position och anpassar dess utseende.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Skapa ActiveX‑kommandoknapp i Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Hur man skapar en ActiveX‑kommandoknapp i Java
url: /sv/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du en ActiveX‑kommandoknapp i Java

Om du behöver **skapa en ActiveX‑kommandoknapp** i ett Word‑dokument med Java, visar den här guiden exakt hur du gör. Du får se ett komplett, körbart exempel som **programmerat lägger till en kommandoknapp**, placerar den med `setLeft` och `setTop`, och sparar resultatet som en `.docx`‑fil.

Att bädda in en interaktiv knapp låter dig skapa formulär, automatisera arbetsflöden eller samla in användarinmatning direkt i en Word‑fil. Stegen nedan täcker allt från projektuppsättning till slutlig verifiering, så att du kan kopiera koden till ditt eget projekt utan att missa någon detalj.

## Förutsättningar

- JDK 17 eller nyare installerat  
- Maven 3.8+ (eller ditt föredragna byggverktyg)  
- Aspose.Words för Java 23.9 eller senare – biblioteket som tillhandahåller `DocumentBuilder` och OLE‑kontrollstöd  
- Grundläggande kunskap om Java‑syntax och objekt‑orienterade koncept  

Om du använder Maven, lägg till beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Proffstips:** Använd den senaste versionen av Aspose.Words för att dra nytta av buggfixar och nya OLE‑funktioner.

## Steg 1: Skapa ett nytt tomt dokument och en DocumentBuilder

Det första steget för att **skapa en ActiveX‑kommandoknapp** är att instansiera ett tomt `Document` och en `DocumentBuilder`. Buildern ger dig ett flytande API för att infoga innehåll, inklusive OLE‑kontroller.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar Word‑filen i minnet, medan `DocumentBuilder` fungerar som en markör som låter dig placera element exakt där du behöver dem.

## Steg 2: Infoga en OLE‑kommandoknapp‑kontroll

ActiveX‑kontroller infogas som OLE‑objekt. Aspose.Words tillhandahåller klassen `Forms2OleControl` för detta ändamål.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

När du anropar `insertForms2OleControl()` skapar Aspose automatiskt en platshållarform som kommer att hysa ActiveX‑knappen.

## Steg 3: Konfigurera knappens egenskaper

Nu **programmerar du tillägg av kommandoknapp**‑detaljer såsom dess ProgID, rubrik och storlek. Den vanligaste ProgID för en kommandoknapp är `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Hur man ställer in knappens vänstra och övre position

Att positionera knappen är där det sekundära nyckelordet **how to set button left top** blir relevant. Metoderna `setLeft` och `setTop` accepterar värden i punkter (1 punkt = 1/72 tum).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Justera dessa siffror för att passa din layout. Till exempel, för att alignera knappen med en tabellcell, beräkna cellens koordinater och skicka dem till `setLeft`/`setTop`.

## Steg 4: Spara dokumentet

Slutligen, skriv dokumentet till disk. Filen kommer att innehålla ActiveX‑knappen klar för interaktion när den öppnas i Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Att köra `main`‑metoden producerar `CommandButton.docx`. Öppna filen i Word, aktivera innehåll om du blir ombedd, och du kommer att se en klickbar knapp med etiketten **Click Me** placerad på de koordinater du angav.

![Skapa ActiveX‑kommandoknapp i Java](/images/activex-button-screenshot.png){.center width=600 alt="Skärmdump av Skapa ActiveX‑kommandoknapp i Java som visar knappen i Word‑dokumentet"}

## Vanliga variationer och kantfall

### Lägga till flera knappar

Om du behöver flera knappar, upprepa **Steg 2** och **Steg 3** för varje kontroll. Kom ihåg att justera `setLeft` och `setTop` så att knapparna inte överlappar varandra.

### Ändra knappens beteende

ActiveX‑knappar kan köra VBA‑makron när de klickas. För att bifoga ett makro, sätt `setOnAction`‑egenskapen till makronamnet:

```java
commandButton.setOnAction("MyMacro");
```

Se till att mål‑dokumentet innehåller motsvarande VBA‑modul; annars kommer Word att visa ett fel.

### Kompatibilitetsanteckningar

- Knappen fungerar endast i skrivbordsversioner av Word som stödjer ActiveX (t.ex. Word för Windows). Den visas som en statisk bild i Word för Mac eller i online‑redigerare.  
- Om du riktar dig mot en blandad miljö, överväg att använda en **content control** (`RichTextContentControl`) istället för en ActiveX‑kontroll.

## Fullständig källkod för referens

Nedan är det kompletta, självständiga exemplet som du kan kopiera in i ett nytt Maven‑projekt och köra omedelbart.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Förväntad output:** Efter körning hittar du `CommandButton.docx` i ditt projekts arbetskatalog. När du öppnar filen i Microsoft Word visas en knapp på den angivna platsen med rubriken “Click Me”.

## Slutsats

Du vet nu hur du **skapar en ActiveX‑kommandoknapp** i Java, **programmerat lägger till en kommandoknapp** i ett Word‑dokument, och exakt styr dess layout med **how to set button left top**‑metoder. Denna teknik öppnar dörren till rika, interaktiva Word‑formulär som kan trigga makron, starta externa program eller samla in användarinmatning direkt i dokumentet.

### Nästa steg

- Utforska andra ActiveX‑kontroller såsom `Forms.TextBox.1` eller `Forms.CheckBox.1`.  
- Kombinera flera kontroller med en VBA‑modul för att implementera fullständiga formulär.  
- Ersätt ActiveX med content controls om du behöver plattformsoberoende kompatibilitet.

Känn dig fri att experimentera med storlek, rubrik och positionering för att matcha din UI‑design. Om du stöter på problem, dubbelkolla att den Aspose.Words‑version du använder stödjer OLE‑kontroller, och verifiera att Words säkerhetsinställningar tillåter körning av ActiveX. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Bädda in OLE‑objekt och ActiveX‑kontroller i Word‑dokument](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Skapa rektangel‑form i Word med Java – Fullständig guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}