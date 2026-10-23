---
date: 2026-10-23
description: Erfahren Sie, wie Sie QR‑Code‑Java‑Etiketten mit Aspose.Words erstellen.
  Diese Schritt‑für‑Schritt‑Anleitung zeigt Ihnen, wie Sie Barcodes in Word‑Dokumenten
  einbetten und size, colors und format anpassen.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Erstellung benutzerdefinierter Barcode‑Etiketten
og_description: Erfahren Sie, wie Sie QR‑Code‑Java‑Etiketten mit Aspose.Words erstellen.
  Diese Anleitung erklärt das Einbetten von Barcodes, size‑Kontrolle und color‑Anpassung
  in Word‑Dokumenten.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Wie man QR‑Code‑Java‑Etiketten mit Aspose.Words erstellt
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Wie man QR‑Code‑Java‑Etiketten mit Aspose.Words erstellt
url: /de/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man QR-Code-Java-Etiketten mit Aspose.Words erstellt

Barcodes sind in modernen Anwendungen unverzichtbar – egal, ob Sie Inventar verwalten, Tickets drucken oder Ausweise erstellen. In diesem Tutorial **erstellen Sie QR‑Code‑Java**‑Etiketten und betten sie direkt in ein Word‑Dokument ein, indem Sie die Schnittstelle `IBarcodeGenerator` verwenden. Wir führen Sie Schritt für Schritt durch die Einrichtung der Umgebung bis zum Einfügen des Barcode‑Bildes, sodass Sie Barcodes sofort in Ihren Java‑Projekten nutzen können.

## Schnelle Antworten
- **Was lehrt dieses Tutorial?** Wie man QR‑Code‑Java‑Etiketten erstellt und sie mit Aspose.Words for Java in eine Word‑Datei einbettet.  
- **Welcher Barcode‑Typ wird im Beispiel verwendet?** QR‑Code (Sie können ihn durch einen der über 20 unterstützten Typen ersetzen).  
- **Benötige ich eine Lizenz?** Für uneingeschränkten Zugriff während der Entwicklung ist eine temporäre Lizenz erforderlich.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher.  
- **Kann ich die Barcode‑Größe oder Farben ändern?** Ja – passen Sie die Einstellungen von `BarcodeParameters` und `BarcodeGenerator` an.

## Was ist create QR code Java?
`create QR code Java` bezieht sich auf das programmgesteuerte Erzeugen eines QR‑Code‑Bildes in einer Java‑Umgebung und das Einfügen in ein Dokument oder UI‑Element. Aspose.Words for Java zusammen mit Aspose.BarCode ermöglicht die komplette Bildgenerierung im Speicher, ohne temporäre Dateien.

## Warum benutzerdefinierte Barcode‑Etiketten mit Aspose.Words erzeugen?
Aspose.Words unterstützt **35+ Eingabe‑ und Ausgabeformate** und kann **500‑seitige Dokumente in unter 3 Sekunden** auf Standard‑Serverhardware verarbeiten. Durch die In‑Memory‑Barcode‑Erzeugung erhalten Sie volle Kontrolle über Typ, Größe und Farben, während der gesamte Workflow rein Java‑zentriert und plattformunabhängig bleibt.

## Voraussetzungen

- Java Development Kit (JDK): Version 8 oder höher.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Integrierte Entwicklungsumgebung (IDE): IntelliJ IDEA, Eclipse oder jede andere bevorzugte IDE.  
- Temporäre Lizenz: Eine [temporary license](https://purchase.aspose.com/temporary-license/) erhalten für uneingeschränkten Zugriff.

## Pakete importieren

Wir verwenden die Bibliotheken Aspose.Words und Aspose.BarCode. Importieren Sie die folgenden Pakete in Ihr Projekt:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Diese Importe geben uns Zugriff auf die Barcode‑Generierungs‑API und die Word‑Dokumentklassen, die wir benötigen.

## Schritt 1: Erstellen einer Hilfsklasse für Barcode‑Operationen

Die Hilfsklasse enthält wiederverwendbare Helfer wie **convert twips to pixels** und **hex‑color conversion**.  
Die Klasse `CustomBarcodeGeneratorUtils` stellt statische Methoden für Einheit‑Umwandlungen und Farb‑Handling bereit.

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

#### Erklärung
- `twipsToPixels` – Word misst Abmessungen in **twips**; diese Methode wandelt sie in Bildschirm‑Pixel um, was praktisch ist, wenn Sie das Barcode‑Bild exakt dimensionieren müssen.  
- `convertColor` – Wandelt einen hexadezimalen String (z. B. `"FF0000"` für Rot) in ein `java.awt.Color`‑Objekt um, sodass Sie **add barcode to Word document** mit benutzerdefinierten Vorder‑ und Hintergrundfarben einbinden können.

## Schritt 2: Implementieren des benutzerdefinierten Barcode‑Generators

Jetzt implementieren wir die Schnittstelle `IBarcodeGenerator`. Diese Klasse ist verantwortlich für das **generate QR code Java**‑artige Bild, das Aspose.Words einbetten kann.  
Die `IBarcodeGenerator`‑Schnittstelle definiert eine einzelne Methode, die ein `BufferedImage` zurückgibt, das den Barcode darstellt.

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

#### Erklärung
- `getBarcodeImage` erstellt eine Instanz von `BarcodeGenerator`, wendet die über `BarcodeParameters` bereitgestellten Farben an und gibt schließlich ein `BufferedImage` zurück.  
- Die Methode behandelt Fehler elegant, indem sie ein Platzhalter‑Bild zurückgibt, sodass die Erstellung des Word‑Dokuments niemals abstürzt.

## Wie man Barcode in Word mit Aspose.Words einbettet?

Laden Sie Ihre Word‑Datei mit `new Document("template.docx")` (oder erstellen Sie ein neues `Document`) und rufen Sie `builder.insertImage` mit dem vom Generator zurückgegebenen Barcode‑Bild auf. Dieses Zwei‑Schritt‑Muster bettet den Barcode direkt ein, ohne eine Zwischendatei auf die Festplatte zu schreiben. Durch Angabe der Bildabmessungen in Pixeln oder die Umrechnung von Word‑Twips zu Pixeln können Sie die genaue Größe und Position des Barcodes im Dokument steuern und ein professionelles Layout gewährleisten, das auf jedem Drucker korrekt gedruckt wird.

## Schritt 3: Einen Barcode erzeugen und in Word einbetten

Mit dem fertig konfigurierten Generator können wir nun ein Barcode‑Bild erzeugen und **in ein Word‑Dokument einfügen**.

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

#### Erklärung  

1. **Document‑Initialisierung** – Erstellt ein frisches `Document` (oder Sie laden eine vorhandene Vorlage).  
2. **Barcode‑Parameter** – Definiert den Barcode‑Typ (`QR`), den zu codierenden Wert und die Vorder‑/Hintergrundfarben.  
3. **Bild‑Einfügung** – `builder.insertImage` platziert den erzeugten Barcode in der gewünschten Größe (200 × 200 Pixel). Dies ist der Kern von **how to embed barcode in Word**.  
4. **Speichern** – Das finale Dokument `CustomBarcodeLabels.docx` enthält den eingebetteten Barcode, bereit zum Drucken oder Verteilen.

## Häufige Probleme & Fehlerbehebung

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Barcode erscheint leer | `BarcodeParameters`‑Farben sind identisch (z. B. schwarz auf schwarz) | Überprüfen Sie die Werte von `foregroundColor` und `backgroundColor`. |
| Bild ist verzerrt | Falsche Pixelabmessungen an `insertImage` übergeben | Passen Sie die Breiten-/Höhen‑Argumente an oder verwenden Sie die `twipsToPixels`‑Umrechnung für präzise Größen. |
| Fehler: Nicht unterstützter Barcode‑Typ | Verwendung eines Typs, der von `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nicht erkannt wird | Stellen Sie sicher, dass der Barcode‑Typ‑String einem der unterstützten `EncodeTypes` entspricht (z. B. "QR", "CODE128"). |

## Häufig gestellte Fragen

**F: Kann ich Aspose.Words für Java ohne Lizenz verwenden?**  
A: Ja, aber es gibt Evaluationsbeschränkungen. Eine [temporary license](https://purchase.aspose.com/temporary-license/) für volle Funktionalität erhalten.

**F: Welche Barcode‑Typen kann ich erzeugen?**  
A: Aspose.BarCode unterstützt QR, Code 128, EAN‑13, DataMatrix, PDF417 und viele weitere Formate – über 20 Symbologien insgesamt. Siehe die [documentation](https://reference.aspose.com/words/java/) für die komplette Liste.

**F: Wie kann ich die Barcode‑Größe ändern?**  
A: Passen Sie die Breiten‑ und Höhen‑Argumente in `builder.insertImage` an oder berechnen Sie exakte Word‑Twips mit `twipsToPixels` für pixelgenaue Kontrolle.

**F: Ist es möglich, benutzerdefinierte Schriftarten für den Barcode‑Text zu verwenden?**  
A: Ja, Sie können die Textschriftart über die Eigenschaft `CodeTextParameters` des `BarcodeGenerator` anpassen.

**F: Wo kann ich Hilfe erhalten, wenn ich auf Probleme stoße?**  
A: Besuchen Sie das [support forum](https://forum.aspose.com/c/words/8/) für Unterstützung von der Aspose‑Community und den Ingenieuren.

## Fazit

Durch die oben beschriebenen Schritte wissen Sie jetzt, wie Sie **QR‑Code‑Java**‑Bilder erstellen und **Barcode in Word**‑Dokumenten mit Aspose.Words for Java einbetten. Diese Technik ist flexibel genug für Inventar‑Tags, Veranstaltungstickets oder jede Situation, in der ein Barcode Teil eines generierten Dokuments sein muss. Experimentieren Sie mit verschiedenen Barcode‑Typen, Farben und Größenoptionen, um Ihre spezifischen Geschäftsanforderungen zu erfüllen.

---

**Zuletzt aktualisiert:** 2026-10-23  
**Getestet mit:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose

## Verwandte Tutorials

- [PDF aus Word mit Barcode-Generierung erstellen – Aspose.Words für Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Word als PDF speichern mit Aspose Words Schritt für Schritt Java-Anleitung](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Leeres Word-Dokument in Java mit Aspose Words erstellen](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}