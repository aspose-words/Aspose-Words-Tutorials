---
date: 2025-12-10
description: Erfahren Sie, wie Sie benutzerdefinierte Barcode‑Etiketten mit Aspose.Words
  für Java erstellen. Diese Schritt‑für‑Schritt‑Anleitung zeigt Ihnen, wie Sie Barcodes
  in Word‑Dokumente einbetten.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Benutzerdefinierte Barcode‑Etiketten in Aspose.Words für Java generieren
url: /de/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Benutzerdefinierte Barcode-Etiketten in Aspose.Words für Java generieren

## Einführung in die Erstellung benutzerdefinierter Barcodes in Aspose.Words für Java

Barcodes sind in modernen Anwendungen unverzichtbar – egal, ob Sie Inventar verwalten, Tickets drucken oder Ausweise erstellen. In diesem Tutorial werden Sie **benutzerdefinierte Barcode**‑Etiketten erzeugen und direkt in ein Word‑Dokument einbetten, indem Sie das `IBarcodeGenerator`‑Interface verwenden. Wir gehen jeden Schritt durch, von der Einrichtung der Umgebung bis zum Einfügen des Barcode‑Bildes, sodass Sie Barcodes sofort in Ihren Java‑Projekten einsetzen können.

## Schnelle Antworten
- **Was lehrt dieses Tutorial?** Wie man benutzerdefinierte Barcode‑Etiketten erzeugt und in einer Word‑Datei mit Aspose.Words für Java einbettet.  
- **Welcher Barcode‑Typ wird im Beispiel verwendet?** QR‑Code (kann durch jeden unterstützten Typ ersetzt werden).  
- **Benötige ich eine Lizenz?** Eine temporäre Lizenz ist für uneingeschränkten Zugriff während der Entwicklung erforderlich.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher.  
- **Kann ich die Barcode‑Größe oder Farben ändern?** Ja – passen Sie die Einstellungen von `BarcodeParameters` und `BarcodeGenerator` an.

## Voraussetzungen

Bevor wir mit dem Codieren beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- Java Development Kit (JDK): Version 8 oder höher.  
- Aspose.Words für Java Bibliothek: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode für Java Bibliothek: [Download here](https://releases.aspose.com/).  
- Integrierte Entwicklungsumgebung (IDE): IntelliJ IDEA, Eclipse oder eine andere IDE Ihrer Wahl.  
- Temporäre Lizenz: Holen Sie sich eine [temporary license](https://purchase.aspose.com/temporary-license/) für uneingeschränkten Zugriff.

## Pakete importieren

Wir verwenden die Aspose.Words‑ und Aspose.BarCode‑Bibliotheken. Importieren Sie die folgenden Pakete in Ihr Projekt:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Diese Importe geben uns Zugriff auf die Barcode‑Generierungs‑API und die Word‑Dokumentklassen, die wir benötigen.

## Schritt 1: Erstellen einer Hilfsklasse für Barcode‑Operationen

Um den Hauptcode sauber zu halten, kapseln wir gängige Helfer‑Methoden – wie **twips in Pixel umrechnen** und **Hex‑Farbkonvertierung** – in einer Hilfsklasse.

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

**Erklärung**

- `twipsToPixels` – Word misst Abmessungen in **twips**; diese Methode konvertiert sie in Bildschirm‑Pixel, was praktisch ist, wenn Sie das Barcode‑Bild exakt dimensionieren müssen.  
- `convertColor` – Wandelt einen hexadezimalen String (z. B. `"FF0000"` für Rot) in ein `java.awt.Color`‑Objekt um, sodass Sie **wie man Barcode einfügt** mit benutzerdefinierten Vorder‑ und Hintergrundfarben.

## Schritt 2: Implementieren des benutzerdefinierten Barcode‑Generators

Jetzt implementieren wir das `IBarcodeGenerator`‑Interface. Diese Klasse ist dafür verantwortlich, **generate qr code java**‑artige Bilder zu erzeugen, die Aspose.Words einbetten kann.

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

**Erklärung**

- `getBarcodeImage` erstellt eine Instanz von `BarcodeGenerator`, wendet die über `BarcodeParameters` bereitgestellten Farben an und gibt schließlich ein `BufferedImage` zurück.  
- Die Methode behandelt Fehler elegant, indem sie ein Platzhalter‑Bild zurückgibt, sodass die Erstellung des Word‑Dokuments niemals abstürzt.

## Schritt 3: Einen Barcode generieren und **Barcode in Word einbetten**

Mit dem Generator bereit, können wir nun ein Barcode‑Bild erzeugen und **es in ein Word‑Dokument einfügen**.

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

**Erklärung**

1. **Dokumentinitialisierung** – Erstellt ein frisches `Document` (oder Sie können eine vorhandene Vorlage laden).  
2. **Barcode‑Parameter** – Definiert den Barcode‑Typ (`QR`), den zu codierenden Wert und die Vorder‑/Hintergrundfarben.  
3. **Bildeinfügung** – `builder.insertImage` platziert den erzeugten Barcode in der gewünschten Größe (200 × 200 Pixel). Dies ist der Kern von **how to insert barcode** in eine Word‑Datei.  
4. **Speichern** – Das abschließende Dokument `CustomBarcodeLabels.docx` enthält den eingebetteten Barcode, bereit zum Drucken oder Verteilen.

## Warum benutzerdefinierte Barcode‑Etiketten mit Aspose.Words erzeugen?

- **Vollständige Kontrolle** über das Aussehen des Barcodes (Typ, Größe, Farben).  
- **Nahtlose Integration** – keine Zwischenspeicherung von Bilddateien; der Barcode wird im Speicher erzeugt und direkt eingefügt.  
- **Plattformübergreifend** – funktioniert auf jedem OS, das Java unterstützt, und ist ideal für serverseitige Dokumentenerstellung.  
- **Skalierbar** – Sie können über eine Datenquelle iterieren, um Hunderte personalisierter Etiketten in einem Durchlauf zu erstellen.

## Häufige Probleme & Fehlersuche

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Barcode erscheint leer | `BarcodeParameters`‑Farben sind identisch (z. B. Schwarz auf Schwarz) | Überprüfen Sie die Werte von `foregroundColor` und `backgroundColor`. |
| Bild ist verzerrt | Falsche Pixel‑Abmessungen an `insertImage` übergeben | Passen Sie die Breiten‑/Höhen‑Argumente an oder verwenden Sie die `twipsToPixels`‑Umrechnung für präzise Größen. |
| Fehler: Nicht unterstützter Barcode‑Typ | Ein Typ wird verwendet, der von `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nicht erkannt wird | Stellen Sie sicher, dass der Barcode‑Typ‑String einem der unterstützten `EncodeTypes` entspricht (z. B. `"QR"`, `"CODE128"`). |

## Häufig gestellte Fragen

**F: Kann ich Aspose.Words für Java ohne Lizenz verwenden?**  
A: Ja, jedoch mit einigen Einschränkungen. Holen Sie sich eine [temporary license](https://purchase.aspose.com/temporary-license/) für die volle Funktionalität.

**F: Welche Barcode‑Typen kann ich erzeugen?**  
A: Aspose.BarCode unterstützt QR, Code 128, EAN‑13 und viele weitere Formate. Siehe die [Dokumentation](https://reference.aspose.com/words/java/) für eine vollständige Liste.

**F: Wie kann ich die Barcode‑Größe ändern?**  
A: Passen Sie die Breiten‑ und Höhen‑Argumente in `builder.insertImage` an oder nutzen Sie `twipsToPixels`, um Word‑Maßeinheiten in Pixel umzuwandeln.

**F: Ist es möglich, benutzerdefinierte Schriftarten für den Barcode‑Text zu verwenden?**  
A: Ja, Sie können die Textschriftart über die Eigenschaft `CodeTextParameters` des `BarcodeGenerator` anpassen.

**F: Wo bekomme ich Hilfe, wenn ich Probleme habe?**  
A: Besuchen Sie das [support forum](https://forum.aspose.com/c/words/8/) für Unterstützung durch die Aspose‑Community und die Entwickler.

## Fazit

Durch Befolgen der obigen Schritte wissen Sie jetzt, wie man **benutzerdefinierte Barcode**‑Bilder erzeugt und **Barcode in Word**‑Dokumente mit Aspose.Words für Java einbettet. Diese Technik ist flexibel genug für Inventur‑Etiketten, Veranstaltungstickets oder jede Situation, in der ein Barcode Teil eines generierten Dokuments sein muss. Experimentieren Sie mit verschiedenen Barcode‑Typen und Stiloptionen, um Ihre spezifischen Geschäftsanforderungen zu erfüllen.

---

**Last Updated:** 2025-12-10  
**Getestet mit:** Aspose.Words für Java 24.12, Aspose.BarCode für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}