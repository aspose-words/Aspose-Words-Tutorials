---
category: general
date: 2026-07-03
description: Maak een rechthoekvorm in Java en leer hoe je een schaduw aan de vorm
  toevoegt, een schaduweffect toepast, de transparantie van de vorm instelt en snel
  een leeg document maakt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: nl
og_description: Maak een rechthoekige vorm in Java met schaduw, transparantie en een
  leeg document. Volg deze gids om vormverwerking onder de knie te krijgen.
og_title: Maak een rechthoekvorm in Java – Volledige programmeertutorial
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Rechthoekvorm maken in Java – Complete stap‑voor‑stap gids
url: /nl/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Java – Complete stap‑voor‑stap gids

Heb je je ooit afgevraagd hoe je **rechthoekvorm maakt** in een Word‑document met Java? Je bent niet de enige—ontwikkelaars hebben vaak snel een manier nodig om geometrische graphics toe te voegen, en ze vervolgens een subtiele schaduw te geven zodat de lay‑out er professioneler uitziet. In deze tutorial lopen we het hele proces door: van het aanmaken van een **leeg document** tot **schaduw aan vorm toevoegen**, **schaduweffect toepassen**, en zelfs **vormtransparantie instellen** voor dat professionele uiterlijk.

Het code‑fragment hieronder is een volledig werkend voorbeeld dat je kunt kopiëren‑en‑plakken in je project. Geen externe documentatie nodig—volg gewoon de stappen, begrijp het “waarom”, en je genereert binnen enkele seconden rechthoeken met schaduw.

## Wat je zult leren

- Hoe je **rechthoekvorm maakt** programmatically met Aspose.Words for Java.
- De exacte aanroepen die nodig zijn om **schaduw aan vorm toe te voegen** en de visuele eigenschappen te configureren.
- Manieren om **schaduweffect toe te passen** en parameters zoals offset, blur‑radius en kleur aan te passen.
- Technieken om **vormtransparantie in te stellen** voor een subtielere uitstraling.
- Hoe je **leeg document maakt**, de vorm invoegt en het resultaat opslaat.

> **Pro tip:** Al deze handelingen worden uitgevoerd op één `Document`‑instantie, wat betekent dat je ze kunt chainen zonder je zorgen te maken over tussenliggende bestands‑I/O.

## Vereisten

Voordat we beginnen, zorg dat je het volgende hebt:

- Java 17 (of een recente JDK) geïnstalleerd.
- Aspose.Words for Java‑bibliotheek toegevoegd aan je project (Maven‑coördinaten: `com.aspose:aspose-words:23.12`).
- Een Java‑IDE of eenvoudige teksteditor—niets bijzonders, alleen een plek om te compileren en uit te voeren.

Als je een van deze mist, haal dan de JDK van Oracle en voeg de Aspose‑dependency toe via Maven of Gradle. Zodra dat geregeld is, ben je klaar om te starten.

## Stap 1: **Leeg document maken** – het canvas voor alles

Het allereerste wat je nodig hebt is een leeg `Document`‑object. Beschouw het als een vers vel papier; zonder dit kun je nergens je rechthoek plaatsen.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Waarom beginnen met een leeg document? Omdat elke vorm zich binnen een `Section` bevindt, en een nieuw aangemaakt `Document` al een standaardsectie bevat met een body die klaar is om knooppunten te ontvangen. Deze stap overslaan zou je later dwingen handmatig secties aan te maken, wat onnodige complexiteit toevoegt.

## Stap 2: **Rechthoekvorm maken** en de grootte definiëren

Nu we een canvas hebben, laten we **rechthoekvorm maken**. De `Shape`‑klasse neemt de documentreferentie en een `ShapeType`. Hier kiezen we `RECTANGLE` en stellen we breedte/hoogte in punten in (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Waarom `WrapType.INLINE` instellen? Inline‑wrapping zorgt ervoor dat de vorm zich gedraagt als een teken in de alinea, waardoor hij meebeweegt met de omringende tekst. Als je zwevende gedrag wilt, schakel dan over naar `WrapType.SQUARE` of `WrapType.TOP_BOTTOM`.

## Stap 3: **Schaduweffect toepassen** – geef de rechthoek diepte

Een platte rechthoek ziet er… nou ja, plat uit. Een schaduw toevoegen laat hem opvallen. We **passen schaduweffect toe** door een `ShadowEffect`‑instantie te maken en vervolgens de visuele eigenschappen aan te passen.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Laten we dit even ontleden:

- **Color** – `Color.getGray(0.5)` levert een 50 % grijs op, wat neutraal is en op de meeste achtergronden werkt.
- **OffsetX/Y** – Positieve waarden duwen de schaduw naar rechts en omlaag; negatieve waarden zouden hem naar links/omhoog verplaatsen.
- **BlurRadius** – Grotere waarden creëren een zachtere, meer diffuse schaduw.
- **Transparency** – Varieert van `0` (ondoorzichtig) tot `1` (volledig transparant). Hier hebben we `0.3` gekozen voor een subtiel effect.

## Stap 4: **Schaduw aan vorm toevoegen** – het effect binden

Het effect maken is niet genoeg; we moeten **schaduw aan vorm toevoegen** door het `ShadowEffect`‑object aan de rechthoek toe te wijzen.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Achter de schermen werkt deze aanroep de onderliggende OpenXML‑markup (`<w:shdw>`) bij die Word gebruikt om schaduwen te renderen. Als je het opgeslagen `.docx`‑bestand inspecteert, zie je een `<w:effect>`‑element gevuld met de parameters die we hebben ingesteld.

## Stap 5: **Vormtransparantie instellen** – optioneel maar vaak nuttig

Soms wil je dat de rechthoek zelf half‑transparant is, zodat onderliggende tekst erdoorheen zichtbaar blijft. De `Shape`‑klasse biedt `setFillColor` en `setFillTransparency`. Hier is een kort voorbeeld dat de rechthoek 40 % transparant maakt:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Waarom zou je dit doen? Stel je een watermerk of een gemarkeerde call‑out voor waarbij de onderliggende inhoud leesbaar moet blijven. Pas de transparantiewaarde aan naar jouw ontwerpvoorkeur.

## Stap 6: De vorm in het document invoegen

We hebben de rechthoek gebouwd, een schaduw toegevoegd en (optioneel) de transparantie ingesteld. De laatste stap is om **de vorm toe te voegen aan de eerste sectie van het document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Het toevoegen van de vorm aan de body plaatst deze aan het einde van de eerste alinea. Als je een specifiek invoegpunt nodig hebt, haal dan de doel‑`Paragraph` op en gebruik `insertBefore` of `insertAfter`.

## Stap 7: Het document opslaan – zie het resultaat

Al dat werk culmineert in één `save`‑aanroep. Kies een pad dat logisch is voor jouw omgeving.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Open het resulterende `ShadowShape.docx` in Microsoft Word of LibreOffice, en je ziet een scherpe rechthoek met een zachte grijze schaduw, licht transparant als je de optionele stap hebt uitgevoerd. Het uiterlijk komt overeen met de parameters die we programmatically hebben gedefinieerd.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Afbeeldings‑alt‑tekst:* **create rectangle shape with shadow** – visuele weergave van de uiteindelijke output.

## Veelgestelde vragen & randgevallen

### Wat als ik een andere schaduwkleur wil?

Verander simpelweg de `setColor`‑aanroep:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Onthoud dat te felle schaduwen er onprofessioneel uit kunnen zien; subtiele tinten werken meestal het beste.

### Kan ik dezelfde schaduw op meerdere vormen toepassen?

Ja. Maak één `ShadowEffect`‑instantie, configureer deze, en hergebruik hem:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Vermijd echter het muteren van de `ShadowEffect` nadat je hem aan andere vormen hebt gekoppeld, tenzij je alle vormen tegelijk wilt bijwerken.

### Hoe wijzig ik de schaduw‑blur dynamisch?

Exposeer een UI‑slider die mappt naar `setBlurRadius`. Waarden tussen `2` en `12` zijn typisch; grotere getallen produceren een “glow” in plaats van een scherpe schaduw.

### Wat als ik wil dat de vorm zweeft in plaats van inline staat?

Vervang het wrap‑type:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Zwevende vormen geven je meer lay‑out‑vrijheid, maar vereisen extra positioneringslogica.

## Volledig werkend voorbeeld

Hieronder staat het complete, kopieer‑en‑plak‑klare programma dat alle besproken stappen bevat. Voer het uit als een gewone Java‑applicatie.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Verwacht resultaat:** Wanneer je `ShadowShape.docx` opent, zie je een witte rechthoek, 200 × 100 pt, gecentreerd in de eerste alinea, met een medium‑grijze schaduw die 5 pt offset heeft, een blur‑radius van 8, en 30 % transparant. De rechthoek zelf is 40 % transparant, waardoor onderliggende tekst erdoorheen kan schijnen.

## Afronding

We hebben zojuist **rechthoekvorm gemaakt** vanaf nul, **schaduw aan vorm toegevoegd**, **schaduweffect toegepast**, en zelfs **vormtransparantie ingesteld**—allemaal terwijl we **leeg document maken** als basis gebruikten. De aanpak is eenvoudig, maakt gebruik van de fluente API van Aspose.Words, en kan worden uitgebreid naar cirkels, sterren of aangepaste polygonen.

Wat staat er hierna op je roadmap? Probeer `ShapeType.RECTANGLE` te vervangen door `ShapeType.OVAL` om schaduwranden cirkels te genereren, of experimenteer met gradient‑vullingen voor

## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}