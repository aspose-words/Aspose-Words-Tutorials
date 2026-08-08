---
category: general
date: 2026-08-07
description: 'Skapa Word‑dokument i Java med Aspose.Words: infoga en ellips, sätt
  fyllningsfärg på formen och dölj formen i Word med ett kort exempel.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: sv
lastmod: 2026-08-07
og_description: Skapa Word-dokument i Java med Aspose.Words. Lär dig att infoga en
  form, sätta dess fyllningsfärg och dölja formen i Word—allt i ett enda körbart exempel.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Skapa Word-dokument i Java – dölj form och ange fyllningsfärg
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Skapa Word-dokument i Java – dölj form och sätt fyllningsfärg
url: /sv/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument java – dölja form och ange fyllningsfärg

Om du behöver **create word document java** med programmatisk hantering av former, visar den här handledningen hur du gör. Du kommer att lära dig att infoga en form, ange dess fyllningsfärg och dölja formen i Word med Aspose.Words för Java.

Guiden täcker varje steg från att initiera ett `Document`‑objekt till att verifiera att formen är osynlig när filen öppnas. Inga externa resurser krävs utöver Aspose.Words‑biblioteket, och den kompletta källkoden tillhandahålls så att du kan köra den omedelbart.

**Förutsättningar**

- Java 8 eller nyare
- Maven eller Gradle för att hantera beroenden (eller Aspose.Words‑JAR‑filen på klassökvägen)
- Grundläggande kunskap om Java‑syntax
- En IDE eller textredigerare för Java‑utveckling

Handledningen förklarar också **how to hide shape** i en Word‑fil, **how to insert shape** med exakta dimensioner, och **set shape fill color** för visuell stil.

---

![Skapa Word-dokument java – förhandsgranskning av dold form](image-placeholder.png){.align-center width=600 alt="Skapa Word-dokument java – förhandsgranskning av dold form"}

## Skapa Word-dokument java – initiera dokument och builder

Det första steget är att skapa ett tomt Word‑dokument och en `DocumentBuilder` som låter dig lägga till innehåll. Initieringen av dessa objekt allokerar de interna strukturer som Aspose.Words behöver för att spåra sidor, stycken och former.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt:* Utan en `DocumentBuilder` kan du inte infoga former, text eller andra objekt. Buildern arbetar mot den minnes‑`Document`‑instansen och säkerställer att alla ändringar fångas innan du sparar.

## Hur man infogar form med Aspose.Words

Aspose.Words stöder många geometriska former. Här infogar vi en ellips med en bredd på 150 pt och en höjd på 100 pt. Metoden `insertShape` returnerar ett `Shape`‑objekt som du kan konfigurera vidare.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Varför detta är viktigt:* Att använda `insertShape` garanterar att formen förankras korrekt i dokumentets flöde. Det returnerade `Shape`‑objektet låter dig ändra egenskaper som fyllningsfärg, linjestil och synlighet.

## Ange fyllningsfärg för form i Word

En form utan fyllning ser transparent ut. Att ange en fyllningsfärg får formen att sticka ut när den är synlig. Exemplet använder `java.awt.Color.GREEN` för att demonstrera **set shape fill color**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Varför detta är viktigt:* Fyllningsfärgen lagras i formens XML‑definition. Att ändra den vid körning låter dig generera dokument med varumärkes‑specifika färger eller markera viktiga områden.

## Hur man döljer form i Word

Ibland behöver du en form som styr layouten eller fungerar som en platshållare men som inte ska visas för slutanvändaren. Anropet `setHidden(true)` implementerar **how to hide shape** och uppfyller kravet **hide shape in word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Varför detta är viktigt:* Dolda former är fortfarande en del av dokumentets objektmodell, vilket betyder att de kan refereras senare (t.ex. för bokmärken eller programmatisk manipulation) utan att störa den visuella layouten.

## Spara dokumentet och verifiera resultatet

Efter att ha konfigurerat formen, spara filen till disk. Den sparade `.docx`‑filen kan öppnas i Microsoft Word; ellipsen kommer att vara osynlig, men dess närvaro kan bekräftas genom att inspektera dokumentets XML eller genom att använda Aspose.Words för att lista former.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Förväntat resultat:* När du öppnar `ShapeVisibilityDemo.docx` visas en normal sida utan synliga grafikobjekt. Om du granskar dokumentet med en ZIP‑visare och öppnar `word/document.xml` hittar du ett `<w:shape>`‑element med `hidden="true"` och ett `<v:fillcolor>`‑värde på `#00FF00`.

---

## Vanliga variationer och kantfall

- **Olika formtyper:** Byt `ShapeType.ELLIPSE` mot `ShapeType.RECTANGLE`, `ShapeType.CLOUD` eller någon annan stödjande enum‑värde för att uppnå önskad geometri.
- **Villkorlig synlighet:** Du kan växla `ellipse.setHidden(false)` baserat på körlogik, vilket möjliggör dynamisk dokumentgenerering.
- **Komplexa fyllningar:** Istället för en solid färg, använd `ellipse.getFill().setTextureImage(...)` för mönsterfyllningar. Samma `setHidden`‑metod styr fortfarande synligheten.
- **Flera former:** Skapa en array eller lista med `Shape`‑objekt, konfigurera varje oberoende och dölj endast de som uppfyller specifika kriterier.

*Proffstips:* När du genererar stora dokument, återanvänd en enda `DocumentBuilder`‑instans istället för att skapa en ny för varje form. Detta minskar minnesbelastningen och förbättrar prestandan.

---

## Slutsats

Du vet nu hur du **create word document java** som infogar en ellips, **set shape fill color**, och **hide shape in word** med Aspose.Words. Det kompletta, körbara exemplet demonstrerar varje API‑anrop, förklarar varför varje steg behövs och visar det förväntade resultatet.

Nästa steg är att utforska relaterade ämnen såsom **how to insert shape** med textomslag, lägga till hyperlänkar till former, och exportera dokumentet till PDF samtidigt som dolda element bevaras. Experimentera med olika färger, storlekar och synlighetsflaggor för att anpassa Word‑automatiseringen efter ditt projekts behov.

Redo att automatisera fler Word‑funktioner? Kolla in Aspose.Words för Java‑dokumentationen om [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) och börja bygga rikare, programmatisk genererade dokument redan idag.

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow‑handledning – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}