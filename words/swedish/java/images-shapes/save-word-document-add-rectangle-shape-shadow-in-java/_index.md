---
category: general
date: 2026-06-20
description: Spara Word-dokument med Aspose.Words i Java samtidigt som du lägger till
  en rektangel och applicerar en skugga. Lär dig hur du infogar en form steg för steg.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: sv
og_description: Spara Word-dokument med Aspose.Words Java. Den här guiden visar hur
  du lägger till en rektangelform, applicerar en skugga och infogar den i ett stycke.
og_title: Spara Word-dokument – Lägg till rektangelform och skugga i Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Spara Word-dokument – Lägg till rektangelform och skugga i Java
url: /sv/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara Word‑dokument – Lägg till rektangelform & skugga i Java

Har du någonsin funderat på hur du **sparar ett Word‑dokument** efter att du har anpassat dess layout? Du är inte ensam – de flesta utvecklare stöter på detta problem när de behöver programatiskt berika en DOCX‑fil. Den goda nyheten är att du med Aspose.Words för Java kan **spara ett Word‑dokument**, placera en rektangelform precis där du vill ha den och till och med ge den en subtil skugga.

I den här handledningen går vi igenom hela processen: läsa in en befintlig fil, **lägga till en rektangelform**, konfigurera dess **skugga**, infoga formen i det första stycket och slutligen **spara Word‑dokumentet**. När du är klar har du ett körbart Java‑program som skapar en polerad `shadow.docx`‑fil – utan någon manuell justering.

> **Vad du behöver**  
> * Java 17 (eller någon nyare JDK)  
> * Aspose.Words för Java‑biblioteket (Maven/Gradle eller JAR‑filen)  
> * En inmatnings‑DOCX‑fil (`input.docx`) i en känd mapp  

Om du har dessa grunder på plats, låt oss dyka ner.

---

## Spara Word‑dokument – Komplett Java‑exempel

Nedan är den fullständiga, körklara källkoden. Kopiera den till din IDE, justera sökvägarna och tryck på **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Förväntat resultat:** Efter att programmet har körts, öppna `shadow.docx`. Du kommer att se det ursprungliga innehållet plus en svart rektangel på 100 × 50 pt med en mjuk skugga precis i början av det första stycket.

---

## Lägg till rektangelform i ett Word‑dokument

Varför använda en rektangelform överhuvudtaget? Tänk på den som ett visuellt ankare – perfekt för call‑outs, platshållare eller enkla grafikelement. I Aspose.Words abstraherar `Shape`‑klassen alla ritobjekt, och `ShapeType.RECTANGLE` ger dig en ren ruta utan extra krångel.

**Viktiga punkter när du lägger till en rektangelform**

- **Enheter är punkter** (1 pt = 1/72 tum). Justera `setWidth`/`setHeight` för att passa din layout.  
- Formen lever i dokumentets nodträd, så du kan infoga den var som helst där ett `Paragraph` eller `Run` är tillåtet.  
- Du kan styla rektangeln (fyllning, linjefärg osv.) innan du applicerar en skugga.

> **Proffstips:** Om du behöver en transparent fyllning, anropa `rectangle.getFill().setTransparent(true);`.

---

## Applicera skugga på formen

Skuggor ger djup. `Shadow`‑objektet som är kopplat till en `Shape` exponerar egenskaper som motsvarar Word‑gränssnittets alternativ.

| Egenskap | Vad den gör | Typiskt värde |
|----------|--------------|---------------|
| `setVisible(true)` | Slår på skuggan | `true` |
| `setColor(Color.BLACK)` | Skuggans färg | `Color.BLACK` |
| `setBlurRadius(5.0)` | Mjukhet på kanterna | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Horisontell/vertikal förskjutning | `4.0` vardera |
| `setTransparency(0.3)` | Opacitet (0 = ogenomskinlig, 1 = osynlig) | `0.3` |

När du frågar **hur man applicerar skugga på en form**, är svaret helt enkelt att justera dessa sex egenskaper. Du kan experimentera – större förskjutningar ger en “lyftad” känsla, medan en högre blur‑radius ger ett mer diffust utseende.

> **Vanligt fallgropp:** Att glömma `setVisible(true)` lämnar formen utan skugga även om du konfigurerar de andra egenskaperna.

---

## Hur man infogar en form i ett stycke

Att infoga en form är ingen magi; det är bara nodmanipulation. Metoden `appendChild` placerar formen i slutet av styckets barnnoder. Om du vill ha formen före texten, använd `insertBefore` istället.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Den lilla förändringen svarar på **hur man infogar en form** exakt där du behöver den – före befintliga runs, efter en rubrik eller till och med i en tabellcell (hämta bara rätt `Cell`‑nod först).

---

## Köra koden och verifiera resultatet

1. **Kompilera** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Kör** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Öppna** `shadow.docx` i Microsoft Word eller LibreOffice. Du bör se rektangeln med en mjuk svart skugga förankrad i början av det första stycket.

Om formen inte visas, dubbelkolla:

- Att sökvägen till indatafilen är korrekt.  
- Att du använder en nyare version av Aspose.Words (API:et ändrades något före 20.12).  
- Att dokumentet faktiskt har minst ett stycke (annars kastas `getParagraphs().get(0)` ett `IndexOutOfBoundsException`).

---

## Vanliga frågor (FAQ)

**Q: Kan jag lägga till formen på en specifik sida?**  
A: Ja. Hämta mål‑`Section` eller `PageSetup` och infoga formen i ett stycke som ligger på den sidan.

**Q: Fungerar detta med .doc‑filer?**  
A: Absolut. Aspose.Words abstraherar formatet, så samma kod **sparar ett Word‑dokument** oavsett om det är `.doc` eller `.docx`.

**Q: Vad händer om jag behöver en annan form, som en ellips?**  
A: Byt ut `ShapeType.RECTANGLE` mot `ShapeType.ELLIPSE`. Alla skuggegenskaper förblir desamma.

---

## Slutsats

Du vet nu hur du **sparar ett Word‑dokument** samtidigt som du **lägger till en rektangelform**, **applicerar en skugga** och **infogar formen** i det första stycket – allt med några få rena Java‑rader. Detta mönster skalar: byt formtyp, justera skuggegenskaper eller placera formen i tabeller och sidhuvuden. Möjligheterna är lika breda som dina behov av dokument‑automation.

Redo för nästa utmaning? Prova att stapla flera former, lägga till text i rektangeln eller generera en komplett rapport med diagram och vattenstämplar. Varje uppgift bygger på samma grundprinciper som behandlats här – så du ligger redan ett steg före.

Lycka till med kodandet, och må din Word‑automation vara skugg‑fri från buggar!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word‑dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hur man sparar dokument som PDF med Aspose.Words för Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Hur man sparar Word som PCL med Aspose.Words för Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}