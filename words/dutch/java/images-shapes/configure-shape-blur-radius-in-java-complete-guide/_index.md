---
category: general
date: 2026-06-27
description: Leer hoe u de vervagingsradius van vormen kunt configureren met Aspose.Words
  voor Java. Deze stapsgewijze tutorial behandelt ook schaduwinstellingen, transparantie
  en het opslaan van het document.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: nl
og_description: Configureer de vervagingsradius van een vorm in een Word‑document
  met Java. Volg deze gedetailleerde tutorial om de vormschaduwinstellingen van Aspose.Words
  onder de knie te krijgen.
og_title: Configureer de vormvervagingsradius in Java – Complete gids
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Configureer de vervagingsradius van vormen in Java – Complete gids
url: /nl/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configureer de vervagingsstraal van een vorm in Java – Complete gids

Heb je ooit moeten **de vervagingsstraal van een vorm** configureren in een Word‑document terwijl je met Java werkte? Je bent niet de enige die zich daar zorgen over maakt. Of je nu een bedrijfsrapport polijst of een subtiel visueel accent aan een flyer toevoegt, het beheersen van deze instelling kan je documenten er veel professioneler uit laten zien.

In deze tutorial lopen we het volledige proces door – van het laden van het `.docx`‑bestand tot het aanpassen van de vervaging van de schaduw en uiteindelijk het opslaan van het resultaat. Onderweg komen we ook aan gerelateerde onderwerpen zoals **Aspose.Words vormschaduw**, **Java schaduwformaat**, en algemene **Word‑document vormmanipulatie**. Aan het einde heb je een kant‑klaar code‑fragment en een duidelijk begrip van waarom elke regel belangrijk is.

## Wat je zult leren

- Hoe je een Word‑document laadt met Aspose.Words for Java.  
- Hoe je het eerste `Shape`‑object in de document‑body vindt.  
- De exacte stappen om **de vervagingsstraal van een vorm** en andere schaduweigenschappen zoals afstand en transparantie te configureren.  
- Hoe je de wijzigingen opslaat in een nieuw `.docx`‑bestand.  

Er zijn geen externe bibliotheken nodig buiten Aspose.Words, en de code werkt met Java 8‑plus en elke recente versie van Aspose.Words for Java (bijv. 24.9). Als je vertrouwd bent met basis‑Java‑syntaxis, ben je in orde.

---

## Stap 1: Laad het Word‑document

Voordat je een vorm kunt aanpassen, moet het document in het geheugen staan. Aspose.Words maakt dit een één‑regelige operatie.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Waarom dit belangrijk is:**  
Het aanmaken van een `Document`‑object parseert het volledige bestand, waardoor je toegang krijgt tot secties, alinea's, tabellen, **en vormen**. Als je deze stap overslaat, heb je geen context om de vervagingsstraal toe te passen.

> **Pro tip:** Als je met grote bestanden werkt, overweeg dan `LoadOptions` te gebruiken om alleen de delen te streamen die je nodig hebt. Dit kan het geheugenverbruik drastisch verminderen.

---

## Stap 2: Haal de doelvorm op

Vormen kunnen overal staan – kopteksten, voetteksten, tabellen, wat je maar wilt. Voor de eenvoud pakken we de eerste vorm die wordt gevonden in de hoofd‑body van de eerste sectie.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Waarom dit belangrijk is:**  
De `getChild`‑aanroep doorloopt de knoopboom diepte‑eerst en retourneert de *eerste* vorm die overeenkomt met `NodeType.SHAPE`. Als je document meerdere vormen bevat, kun je de index (`0`) aanpassen of itereren over `document.getChildNodes(NodeType.SHAPE, true)`.

> **Randgeval:** Als het document geen vormen bevat, is `shape` `null` en zal de volgende regel een `NullPointerException` veroorzaken. Zorg altijd voor een null‑check in productcode.

---

## Stap 3: Configureer de schaduw van de vorm – Stel de vervagingsstraal in

Nu komt het hoogtepunt: het aanpassen van de vervagingsstraal. Dit bevindt zich in het `ShadowFormat`‑object dat aan de vorm is gekoppeld.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### De cijfers begrijpen

- **Vervagingsstraal** (`setBlurRadius`) bepaalt hoe wazig de schaduw eruitziet. Een waarde van `0` geeft een scherpe rand, terwijl `10` of hoger een dromerige gloed oplevert.  
- **DistanceX / DistanceY** verplaatsen de schaduw ten opzichte van de vorm. Positieve X verplaatst naar rechts; positieve Y verplaatst naar beneden.  
- **Transparency** maakt de schaduw doorschijnend. Handig wanneer je een subtiel effect wilt in plaats van een massief zwart blok.

> **Waarom de vervagingsstraal configureren?**  
> In veel zakelijke sjablonen voegt een lichte vervaging diepte toe zonder de lezer af te leiden. Het is een kleine visuele aanpassing die de waargenomen kwaliteit dramatisch kan verbeteren.

---

## Stap 4: Sla het gewijzigde document op

Alle zware taken zijn voltooid; nu schrijf je de wijzigingen terug naar de schijf.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Waarom dit belangrijk is:**  
Het aanroepen van `save` schrijft het volledige document weg, inclusief het bijgewerkte `ShadowFormat`. Als je alleen de vorm als afbeelding nodig hebt, kun je deze exporteren via `shape.getImageData().save(...)` in plaats daarvan.

---

## Volledig werkend voorbeeld

Hieronder staat het complete, zelfstandige programma dat je kunt kopiëren‑plakken in elke Java‑IDE. Zorg ervoor dat je de Aspose.Words for Java‑JAR op je classpath hebt staan.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Verwachte output:**  
Het uitvoeren van het programma levert een nieuw `output.docx` op waarin de eerste vorm nu een zachte, semi‑transparante schaduw heeft met een vervagingsstraal van `5` punten. Open het bestand in Word, selecteer de vorm, en onder **Shape Format → Shadow Effects → Shadow Options** zie je de waarden die je hebt ingesteld terug in de UI.

---

## Meerdere vormen verwerken & geavanceerde scenario's

### Een specifieke vorm targeten op naam

Als je document veel vormen bevat, kun je beter de **naam** van de vorm (ingesteld in de lay‑outopties van Word) gebruiken in plaats van een index:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Verschillende vervagingsstraal toepassen

Je wilt misschien een sterkere vervaging voor achtergrondgrafieken en een subtiele voor iconen. Loop door alle vormen:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Compatibiliteitsopmerkingen

- **Eenheden:** Aspose.Words gebruikt punten (1 pt = 1/72 inch). Als je met millimeters werkt, moet je dienovereenkomstig converteren.  
- **Versie:** De getoonde API werkt met Aspose.Words for Java 24.9 en later. Oudere versies gebruiken mogelijk `setBlurRadius(double)` maar missen enkele nieuwere schaduweigenschappen.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| `NullPointerException` op `shape` | Document heeft geen vormen of de opgegeven index ligt buiten bereik | Voeg een null‑check toe voordat je `ShadowFormat` benadert. |
| Schaduw niet zichtbaar in Word | Schaduwkleur is standaard transparant of afstandswaarden duwen de schaduw buiten het zichtbare gebied | Stel een zichtbare `ShadowColor` in (`shadow.setColor(Color.BLACK)`) en houd `DistanceX/Y` bescheiden. |
| Vervagingsstraal lijkt niet te veranderen | Een verouderde Aspose.Words‑versie negeert de eigenschap | Upgrade naar de nieuwste bibliotheek; de eigenschap werd geïntroduceerd in versie 20.5. |
| Prestatie‑vertraging bij enorme documenten | Het hele document opnieuw opslaan na elke vormwijziging | Bundel alle wijzigingen en roep één keer `save` aan. |

---

## Conclusie

Je weet nu **hoe je de vervagingsstraal van een vorm** in een Word‑document configureert met Java en Aspose.Words. Van het laden van het bestand, het vinden van de juiste `Shape`, het aanpassen van `ShadowFormat`, tot het opslaan van de wijzigingen – elke stap is behandeld met uitleg en praktijk‑tips.

De techniek is niet beperkt tot één vorm; je kunt het opschalen naar volledige documenten, verschillende vervagingsniveaus toepassen, of combineren met andere schaduweigenschappen zoals **shadow transparency Java**. De logische volgende stappen zijn het verkennen van **set blur radius** voor afbeeldingen, experimenteren met **Java shadow format** op grafieken, of dieper duiken in **Word document shape manipulation** voor dynamische rapportgeneratie.

Heb je een scenario dat hier niet wordt behandeld? Laat een reactie achter of raadpleeg de Aspose.Words for Java‑documentatie voor meer geavanceerde schaduweffecten. Veel programmeerplezier!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}