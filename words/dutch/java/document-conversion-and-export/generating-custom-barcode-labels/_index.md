---
date: 2025-12-10
description: Leer hoe u aangepaste barcode‑labels kunt genereren met Aspose.Words
  voor Java. Deze stapsgewijze handleiding laat u zien hoe u barcodes in Word‑documenten
  kunt insluiten.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Genereer aangepaste barcode‑labels in Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aangepaste barcode‑ genereren in Aspose.Words voor Java

## Introductie tot het genereren van aangepaste barcodes in Aspose.Words voor Java

Barcodes zijn onmisbaar in moderne toepassingen—of je nu voorraad beheert, tickets afdrukt of ID‑kaarten maakt. In deze tutorial **genereer je aangepaste barcode**‑labels en embed je ze direct in een Word‑document met behulp van de `IBarcodeGenerator`‑interface. We lopen elke stap door, van het opzetten van de omgeving tot het invoegen van de barcode‑afbeelding, zodat je meteen barcodes kunt gebruiken in je Java‑projecten.

## Snelle antwoorden
- **Wat leert deze tutorial?** Hoe je aangepaste barcode‑labels genereert en embed in een Word‑bestand met Aspose.Words voor Java.  
- **Welk barcode‑type wordt in het voorbeeld gebruikt?** QR‑code (je kunt het vervangen door elk ondersteund type).  
- **Heb ik een licentie nodig?** Een tijdelijke licentie is vereist voor onbeperkte toegang tijdens ontwikkeling.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.  
- **Kan ik de barcode‑grootte of kleuren aanpassen?** Ja—pas de instellingen van `BarcodeParameters` en `BarcodeGenerator` aan.

## Vereisten

Voordat we gaan coderen, zorg dat je het volgende hebt:

- Java Development Kit (JDK): Versie 8 of hoger.  
- Aspose.Words voor Java‑bibliotheek: [Download hier](https://releases.aspose.com/words/java/).  
- Aspose.BarCode voor Java‑bibliotheek: [Download hier](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse of een andere IDE naar keuze.  
- Tijdelijke licentie: Verkrijg een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor onbeperkte toegang.

## Import pakketten

We gebruiken de Aspose.Words‑ en Aspose.BarCode‑bibliotheken. Importeer de volgende pakketten in je project:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Deze imports geven ons toegang tot de barcode‑generatie‑API en de Word‑documentklassen die we nodig hebben.

## Stap 1: Maak een hulpprogrammaklasse voor barcode‑bewerkingen

Om de hoofdcode overzichtelijk te houden, kapselen we gemeenschappelijke helpers—zoals **twips naar pixels converteren** en **hex‑kleurconversie**—in een hulpprogrammaklasse.

### Code

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Uitleg**

- `twipsToPixels` – Word meet afmetingen in **twips**; deze methode converteert ze naar schermpixels, wat handig is wanneer je de barcode‑afbeelding precies wilt dimensioneren.  
- `convertColor` – Zet een hexadecimale tekenreeks (bijv. `"FF0000"` voor rood) om in een `java.awt.Color`‑object, zodat je **hoe je barcode invoegt** met aangepaste voor‑ en achtergrondkleuren.

## Stap 2: Implementeer de aangepaste barcode‑generator

Nu implementeren we de `IBarcodeGenerator`‑interface. Deze klasse is verantwoordelijk voor **generate qr code java**‑stijl afbeeldingen die Aspose.Words kan embedden.

### Code

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Uitleg**

- `getBarcodeImage` maakt een instantie van `BarcodeGenerator`, past de via `BarcodeParameters` opgegeven kleuren toe, en retourneert uiteindelijk een `BufferedImage`.  
- De methode behandelt fouten elegant door een placeholder‑afbeelding te retourneren, zodat de creatie van het Word‑document nooit crasht.

## Stap 3: Genereer een barcode en **embed barcode in Word**

Met de generator klaar, kunnen we nu een barcode‑afbeelding produceren en **invoegen in een Word‑document**.

### Code

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Uitleg**

1. **Documentinitialisatie** – Maakt een nieuw `Document` aan (of je kunt een bestaand sjabloon laden).  
2. **Barcode‑parameters** – Definieert het barcode‑type (`QR`), de te coderen waarde, en de voor‑/achtergrondkleuren.  
3. **Afbeeldingsinvoeging** – `builder.insertImage` plaatst de gegenereerde barcode op de gewenste grootte (200 × 200 pixels). Dit is de kern van **how to insert barcode** in een Word‑bestand.  
4. **Opslaan** – Het uiteindelijke document, `CustomBarcodeLabels.docx`, bevat de embedded barcode klaar voor afdrukken of distributie.

## Waarom aangepaste barcode‑labels genereren met Aspose.Words?

- **Volledige controle** over het uiterlijk van de barcode (type, grootte, kleuren).  
- **Naadloze integratie** – geen tussenliggende afbeeldingsbestanden nodig; de barcode wordt in het geheugen gegenereerd en direct ingevoegd.  
- **Cross‑platform** – werkt op elk OS dat Java ondersteunt, ideaal voor server‑side documentgeneratie.  
- **Schaalbaar** – je kunt over een gegevensbron itereren om honderden gepersonaliseerde labels in één run te maken.

## Veelvoorkomende problemen & probleemoplossing

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Barcode appears blank | `BarcodeParameters` colors are the same (e.g., black on black) | Verify `foregroundColor` and `backgroundColor` values. |
| Image is distorted | Wrong pixel dimensions passed to `insertImage` | Adjust the width/height arguments or use `twipsToPixels` conversion for precise sizing. |
| Unsupported barcode type error | Using a type not recognized by `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Ensure the barcode type string matches one of the supported `EncodeTypes` (e.g., `"QR"`, `"CODE128"`). |

## Veelgestelde vragen

**Q: Kan ik Aspose.Words voor Java gebruiken zonder licentie?**  
A: Ja, maar er zijn enkele beperkingen. Verkrijg een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor volledige functionaliteit.

**Q: Welke soorten barcodes kan ik genereren?**  
A: Aspose.BarCode ondersteunt QR, Code 128, EAN‑13 en vele andere formaten. Zie de [documentatie](https://reference.aspose.com/words/java/) voor een volledige lijst.

**Q: Hoe kan ik de barcode‑grootte wijzigen?**  
A: Pas de breedte‑ en hoogte‑argumenten in `builder.insertImage` aan, of gebruik `twipsToPixels` om Word‑meetunits naar pixels te converteren.

**Q: Is het mogelijk om aangepaste lettertypen te gebruiken voor de barcode‑tekst?**  
A: Ja, je kunt het lettertype van de tekst aanpassen via de `CodeTextParameters`‑eigenschap van de `BarcodeGenerator`.

**Q: Waar kan ik hulp krijgen als ik problemen ondervind?**  
A: Bezoek het [support forum](https://forum.aspose.com/c/words/8/) voor assistentie van de Aspose‑gemeenschap en engineers.

## Conclusie

Door de bovenstaande stappen te volgen, weet je nu hoe je **custom barcode**‑afbeeldingen genereert en **barcode embed in Word**‑documenten met Aspose.Words voor Java. Deze techniek is flexibel genoeg voor voorraadlabels, evenemententickets of elke situatie waarin een barcode deel moet uitmaken van een gegenereerd document. Experimenteer met verschillende barcode‑types en stylingopties om aan je specifieke zakelijke behoeften te voldoen.

---

**Laatst bijgewerkt:** 2025-12-10  
**Getest met:** Aspose.Words voor Java 24.12, Aspose.BarCode voor Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}