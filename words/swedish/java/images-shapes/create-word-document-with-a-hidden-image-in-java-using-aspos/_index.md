---
category: general
date: 2026-09-24
description: Skapa ett Word‑dokument i Java och lär dig hur du döljer en bild, lägger
  till en bild i Word och infogar en dold bild med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to hide image
- add image word
- how to hide shape
- insert hidden picture
language: sv
lastmod: 2026-09-24
og_description: Skapa Word-dokument i Java och upptäck hur du döljer en bild, lägger
  till en bild i Word och infogar en dold bild med Aspose.Words.
og_image_alt: Screenshot of a create word document example with a hidden image
og_title: Skapa Word-dokument med en dold bild – steg‑för‑steg Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Create word document in Java and learn how to hide image, add image
    word, and insert hidden picture with Aspose.Words.
  headline: Create word document with a hidden image in Java using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa Word-dokument med en dold bild i Java med Aspose.Words
url: /sv/java/images-shapes/create-word-document-with-a-hidden-image-in-java-using-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument med en dold bild i Java med Aspose.Words

Om du behöver **skapa Word-dokument** programatiskt gör Aspose.Words för Java det enkelt. Denna handledning visar **hur du döljer en bild**, **lägger till bild i Word**, och **infogar dold bild** i ett enda dokument samtidigt som layouten hålls ren.

Dokumentautomatisering kräver ofta inbäddning av logotyper, vattenstämplar eller platshållare som inte ska störa det synliga innehållet. Genom att markera en form som dold behåller du bilden i filen för senare bruk (t.ex. för villkorlig innehållsgenerering) utan att den visas för slutanvändaren. Du kommer att gå igenom hela arbetsflödet, från att initiera ett dokument till att spara den slutgiltiga `.docx`‑filen.

## Vad du kommer att lära dig

* Hur du **skapar Word-dokument** från grunden med `Document` och `DocumentBuilder`.
* De exakta stegen för att **lägga till bild i Word** och sedan dölja den bilden med metoden `setHidden(true)`.
* Hur **tekniken för att dölja form** fungerar under huven och varför den är pålitlig över olika Word‑versioner.
* Sätt att **infoga dold bild** så att bilden förblir i filen men är osynlig i layouten.
* Vanliga fallgropar såsom felaktiga filsökvägar, bildformat som inte stöds, och hur du verifierar att bilden verkligen är dold.

> **Förutsättningar** – Du behöver Java 8+ installerat, ett Maven‑ eller Gradle‑projekt, och en giltig Aspose.Words för Java‑licens (eller en gratis utvärderingslicens). Inga andra externa bibliotek krävs.

## Skapa Word-dokument och infoga en dold bild

Det första steget är att instansiera ett nytt `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt*: `Document` är behållaren för alla delar av en Word‑fil (stilar, sektioner, bilder osv.). `DocumentBuilder` erbjuder ett flytande API för att lägga till innehåll utan att behöva hantera låg‑nivå Open XML‑strukturer.

## Hur du döljer bild med formegenskaper

Bilder i ett Word‑dokument lagras som `Shape`‑objekt. Att sätta `Hidden`‑flaggan talar om för Word att exkludera formen från layouten samtidigt som den bevaras i filen.

```java
        // Step 3: Insert an image into the document
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // Step 4: Mark the inserted shape as hidden so it won't appear in the layout
        imageShape.setHidden(true);
```

*Förklaring*:  
* `insertImage` skapar en `Shape` av typen `Picture`.  
* `setHidden(true)` slår på Word‑attributet “Hidden”, vilket layoutmotorn respekterar. Bilden förblir inbäddad, så du kan senare avdölj den programatiskt eller via Words UI.

> **Proffstips**: Använd PNG för förlustfri kvalitet, och håll bildstorleken måttlig (under 200 KB) för att undvika att `.docx`‑filen blir för stor.

## Lägg till bild i Word och verifiera dold status

Även om bilden är dold kan du vilja referera till den i dokumenttexten (t.ex. “Företagslogotyp”). Du kan lägga till en bildtext eller ett platshållar‑stycke innan du döljer formen.

```java
        // Optional: Add a caption that explains the hidden image
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)"); // This text is visible
```

*Varför du kan vilja göra detta*: Vissa arbetsflöden kräver en textuell markör så att efterföljande processer kan lokalisera den dolda bilden utan att behöva parsra dokumentets binära delar.

## Infoga dold bild och spara filen

Till sist sparar du dokumentet till disk. Den dolda bilden förblir inbäddad men osynlig när filen öppnas i Microsoft Word.

```java
        // Step 5: Save the document with the hidden shape
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

*Verifiering*: Öppna `HiddenShapeDemo.docx` i Word. Du bör se bildtexten “Company logo (hidden)” men ingen synlig bild. För att bekräfta att bilden finns, öppna filen som ett ZIP‑arkiv (`.docx`‑filer är ZIP‑behållare) och inspektera `word/media`. PNG‑filen du lade till kommer att finnas där.

## Vanliga kantfall och hur du hanterar dem

| Situation | Vad att hålla utkik efter | Rekommenderad åtgärd |
|-----------|---------------------------|---------------------|
| **Ogiltig bildsökväg** | `FileNotFoundException` vid `insertImage` | Använd `Paths.get(...).toAbsolutePath()` eller kontrollera `Files.exists()` innan insättning. |
| **Bildformat som inte stöds** (t.ex. BMP) | Aspose kastar `UnsupportedImageFormatException` | Konvertera bilden till PNG eller JPEG innan du anropar `insertImage`. |
| **Dold flagga ignoreras** (sällsynt Word‑version) | Bilden visas fortfarande i layouten | Säkerställ att du använder Aspose.Words 22.9+ där `setHidden` mappar till rätt OOXML‑attribut (`<w:hidden/>`). |
| **Stor bildfil** | Dokumentet blir segt | Ändra storlek på bilden med `imageShape.setWidth(100); imageShape.setHeight(50);` innan du döljer den. |

## Fullt körbart exempel

Nedan är det kompletta programmet som du kan kopiera, justera sökvägarna och köra direkt.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document document = new Document();

        // 2. Prepare a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Insert the image (replace with your actual file)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 4. Hide the shape so it doesn't affect layout
        imageShape.setHidden(true);

        // 5. (Optional) Add a visible caption for context
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)");

        // 6. Save the result
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

**Förväntat resultat**: När du öppnar `HiddenShapeDemo.docx` i Microsoft Word innehåller dokumentet texten “Company logo (hidden)” och ingen synlig bild. Den dolda PNG‑filen kan bekräftas i `word/media`‑mappen i den zippade `.docx`‑filen.

## Hur du döljer form vs. hur du döljer bild

I Word‑terminologi behandlas både bilder och teckningar som **shapes**. Metoden `setHidden(true)` fungerar för alla shape‑typer, så samma tillvägagångssätt gäller för vektorgrafik, textrutor eller diagram. Om du behöver dölja en form som inte är en bild, hämta helt enkelt `Shape`‑referensen (t.ex. via `builder.insertShape(ShapeType.LINE, 100, 0)`) och anropa `setHidden(true)`.

## Nästa steg och relaterade ämnen

* **Byt ut dold bild vid körning** – Ladda dokumentet senare, lokalisera den dolda formen via dess `Name` eller `AlternativeText`, och ersätt bilddata.  
* **Villkorligt innehåll** – Kombinera dolda former med Mail Merge för att visa eller dölja bilder baserat på datafält.  
* **Arbeta med WordprocessingML** – Inspektera den underliggande XML‑en (`<w:pict>` och `<w:hidden/>`) om du behöver låg‑nivåjusteringar.  

Dessa tillägg låter dig bygga sofistikerade dokumentgenererings‑pipelines samtidigt som kärnlogiken för **skapa Word-dokument** hålls ren och underhållbar.

---

*Du vet nu hur du skapar ett Word‑dokument, lägger till en bild och döljer den bilden med Aspose.Words för Java. Experimentera med att infoga flera dolda bilder, växla deras synlighet, eller integrera tekniken i ett större rapporteringssystem.*


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Inline Image In Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}