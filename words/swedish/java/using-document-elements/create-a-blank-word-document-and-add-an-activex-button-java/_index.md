---
category: general
date: 2026-10-16
description: Skapa ett tomt Word‑dokument med Java och lär dig hur du lägger till
  en ActiveX‑knapp, sätter dess rubrik och justerar dess dimensioner med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: sv
lastmod: 2026-10-16
og_description: Skapa ett tomt Word‑dokument med Java, lägg sedan till en ActiveX‑knapp,
  sätt dess rubrik och definiera dess dimensioner med Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Skapa ett tomt Word‑dokument och bädda in en ActiveX‑knapp – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Skapa ett tomt Word‑dokument och lägg till en ActiveX‑knapp (Java)
url: /sv/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och lägg till en ActiveX-knapp (Java)

Om du behöver **skapa ett tomt Word-dokument** programatiskt, visar den här guiden hur du gör det med Java och Aspose.Words. Du kommer också att lära dig hur du **lägger till en ActiveX-knapp**, **sätter knappens rubrik** och **sätter knappens dimensioner** så att kontrollen ser exakt ut som du förväntar dig.

Denna handledning täcker:

* Initiering av en tom Word‑fil med Aspose.Words för Java.  
* Infogning av en ActiveX `CommandButton`‑kontroll.  
* Konfiguration av knappens rubrik och storlek.  
* Sparande av den slutgiltiga `.docx`‑filen.

Du bör ha grundläggande kunskaper i Java och en aktuell version av Aspose.Words för Java‑biblioteket (koden fungerar med 23.9 och senare). Inga ytterligare beroenden krävs.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Skapa ett tomt Word-dokument med en ActiveX-knapp"}

## Skapa ett tomt Word-dokument med Aspose.Words

Det första steget är att instansiera ett tomt `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet och tillhandahåller klassen `DocumentBuilder` för redigering.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Varför detta är viktigt:**  
Att skapa ett tomt dokument ger dig en ren canvas, vilket undviker dolda stilar eller sektioner som kan störa senare layoutberäkningar.

## Lägg till en ActiveX‑knapp i dokumentet

Aspose.Words låter dig bädda in äldre ActiveX‑kontroller via klassen `Forms2OleControl`. Följande kod infogar en `CommandButton`‑kontroll vid den aktuella markörpositionen.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tips:** Värdet `setOleClassName` `"Forms.CommandButton.1"` är ProgID för den standardiserade Microsoft Forms‑knappen. Att använda ett annat ProgID (t.ex. `"Forms.CheckBox.1"`) skulle infoga en annan typ av kontroll.

## Sätt knappens rubrik

En rubrik är den text som visas på knappens yta. Du kan ändra den när som helst innan du sparar dokumentet.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Varför du behöver detta:** Användare förstår bara en kontroll när dess syfte är tydligt. Att sätta en meningsfull rubrik förbättrar användbarheten, särskilt när dokumentet öppnas i Word på Windows.

## Sätt knappens dimensioner

Position och storlek anges i punkter (1 punkt = 1/72 tum). Justera värdena så att de passar din layout.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Vanliga variationer:**

| Scenario | Justering |
|----------|------------|
| Större knapp för pekskärmar | Öka `setWidth` och `setHeight` proportionellt |
| Centrerad knapp på sidan | Beräkna `left = (pageWidth - width) / 2` |
| Flera knappar i en kolumn | Öka `setTop` för varje ny knapp |

## Spara dokumentet som innehåller ActiveX‑knappen

Slutligen skriver du dokumentet till disk. `.docx`‑formatet bevarar ActiveX‑kontrollen för Windows‑versioner av Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Förväntat resultat:** Att öppna `ActiveXCommandButton.docx` i Word (Windows) visar en tom sida med en klickbar knapp märkt **Click Me** placerad 100 pt från vänstermarginalen och 200 pt från toppmarginalen.

## Fullt körbart exempel

Kopiera hela klassen nedan till din IDE, lägg till Aspose.Words för Java‑JAR‑filen i projektets klassväg och kör den.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

När programmet körs skapas `ActiveXCommandButton.docx` i arbetskatalogen. Öppna den med Microsoft Word (Windows) för att verifiera att knappen visas exakt som konfigurerad.

## Varför detta tillvägagångssätt rekommenderas

* **Enkelhet:** Endast kärn‑API:et i Aspose.Words används; ingen COM‑interop eller extra bibliotek krävs.  
* **Portabilitet:** Koden körs på vilken plattform som helst som stödjer Java, även om ActiveX‑kontrollen själv endast fungerar i Windows‑versioner av Word.  
* **Underhållbarhet:** Alla egenskaper (rubrik, dimensioner, position) sätts via tydliga, själv‑dokumenterande metoder, vilket gör framtida justeringar enkla.

## Vanliga fallgropar och hur du undviker dem

| Fallgropar | Lösning |
|------------|----------|
| Knappen visas inte i Word på macOS eller Linux | ActiveX‑kontroller är endast för Windows. Använd en annan kontroll (t.ex. en innehållskontroll) för plattformsoberoende dokument. |
| Rubriken kapas | Se till att knappens bredd är tillräckligt stor för texten; öka `setWidth` eller använd en kortare rubrik. |
| Knappen överlappar annat innehåll | Justera `setTop` och `setLeft`‑värden, eller infoga ett nytt stycke före kontrollen för att ge den eget utrymme. |

## Nästa steg

Nu när du kan **skapa ett tomt Word-dokument**, **lägga till en ActiveX‑knapp**, **sätta knappens rubrik** och **sätta knappens dimensioner**, kan du utforska:

* Att lägga till händelsehanteringskod via VBA‑makron (kräver inbäddning av ett makromodul).  
* Att infoga flera kontroller i en tabell‑layout för formulärliknande dokument.  
* Att använda Aspose.Words **FormField**‑API:er för plattformsoberoende formulärlösningar.

Experimentera med olika storlekar, positioner och rubriker för att passa din specifika dokumentdesign. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Lägg till en vattenstämpel i ett dokument med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}