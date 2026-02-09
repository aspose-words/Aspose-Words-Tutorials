---
date: 2026-02-09
description: Erstellen Sie benutzerdefinierte Barcode‑Etiketten mit Aspose Barcode
  Java in Aspose.Words für Java. Erfahren Sie, wie Sie Barcodes in Word‑Dokumente
  einbetten und QR‑Code‑Beispiele in Java generieren.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Erzeugen benutzerdefinierter Barcode‑Etiketten mit Aspose Barcode Java
url: /de/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Erstellung benutzerdefinierter Barcode‑Etiketten mit Aspose Barcode Java

## Einführung in die Erstellung benutzerdefinierter Barcode‑Etiketten in Aspose.Words für Java

Barcodes sind in modernen Anwendungen unverzichtbar, und **Aspose Barcode Java** macht es einfach, sie direkt in Word‑Dokumenten zu erstellen. Egal, ob Sie **barcode in Word einbetten**, einen QR‑Code für eine URL generieren oder Maßeinheiten umrechnen müssen, dieses Tutorial führt Sie durch alles, was Sie benötigen. Bereit einzutauchen? Los geht's!

## Schnelle Antworten
- **Welche Bibliothek erstellt Barcodes in Java?** Aspose Barcode Java zusammen mit Aspose.Words für Java.  
- **Welcher Barcode‑Typ wird demonstriert?** QR‑Code (generate qr code java).  
- **Wie konvertiere ich Twips in Pixel?** Verwenden Sie die bereitgestellte Hilfsmethode `twipsToPixels`.  
- **Kann ich einen Barcode zu einer bestehenden Word‑Datei hinzufügen?** Ja – verwenden Sie einfach die Methode `DocumentBuilder.insertImage`.  
- **Benötige ich eine Lizenz?** Eine temporäre Lizenz entfernt die Evaluationsbeschränkungen.

## Was ist Aspose Barcode Java?
Aspose Barcode Java ist eine leistungsstarke API, die Entwicklern ermöglicht, programmgesteuert eine breite Palette von 1D‑ und 2D‑Barcodes (einschließlich QR‑Codes) zu erzeugen. In Kombination mit Aspose.Words für Java können Sie **barcode in Word** Dokumente einbetten, ohne Ihre Java‑Umgebung zu verlassen.

## Warum Aspose Barcode Java mit Aspose.Words verwenden?
- **Vollständige Kontrolle** über das Aussehen des Barcodes (Farben, Größe, Format).  
- **Nahtlose Integration** – das Barcode‑Bild kann direkt in ein Word‑Dokument eingefügt werden.  
- **Plattformübergreifend** – funktioniert auf jeder Java‑kompatiblen Plattform.  
- **Erweiterbar** – Sie können Hilfsklassen erstellen, um Barcode‑Logik projektübergreifend wiederzuverwenden.

## Voraussetzungen

- Java Development Kit (JDK): Version 8 oder höher.  
- Aspose.Words für Java Bibliothek: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode für Java Bibliothek: [Download here](https://releases.aspose.com/).  
- Integrierte Entwicklungsumgebung (IDE): IntelliJ IDEA, Eclipse oder eine beliebige IDE Ihrer Wahl.  
- Temporäre Lizenz: Holen Sie sich eine [temporary license](https://purchase.aspose.com/temporary-license/) für uneingeschränkten Zugriff.

## Pakete importieren

Wir verwenden die Bibliotheken Aspose.Words und Aspose.BarCode. Importieren Sie die folgenden Pakete in Ihr Projekt:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Diese Importe ermöglichen es uns, Barcode‑Erzeugungsfunktionen zu nutzen und sie in Word‑Dokumente zu integrieren.

Lassen Sie uns diese Aufgabe in handhabbare Schritte aufteilen.

## Schritt 1: Erstellen einer Hilfsklasse für Barcode‑Operationen

Um Barcode‑bezogene Vorgänge zu vereinfachen, erstellen wir eine Hilfsklasse mit Hilfsmethoden für gängige Aufgaben wie Farbkonvertierung und **convert twips to pixels**.

### Code:

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

- `twipsToPixels` konvertiert die von Word verwendete Maßeinheit (Twips) in Bildschirm‑Pixel – ein praktischer Helfer, wenn Sie präzise Größen benötigen.  
- `convertColor` übersetzt einen hexadezimalen Farbstring (z. B. “FF0000”) in ein Java `Color`-Objekt, sodass Sie Vorder‑ und Hintergrundfarbe des Barcodes anpassen können.

## Schritt 2: Implementieren des benutzerdefinierten Barcode‑Generators

Wir implementieren das Interface `IBarcodeGenerator`, damit Aspose.Words ein Barcode‑Bild anfordern kann, wann immer es auf ein Barcode‑Feld trifft.

### Code:

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

- `getBarcodeImage` erstellt einen `BarcodeGenerator` mit dem von Ihnen angegebenen **generate qr code java**‑Typ (QR in unserem Beispiel).  
- Es wendet Vorder‑ und Hintergrundfarben über die Hilfsmethoden an und gibt das gerenderte Bild zurück.  
- Das Ersatzbild stellt sicher, dass das Programm weiterläuft, selbst wenn die Barcode‑Erstellung fehlschlägt.

## Schritt 3: Einen Barcode erzeugen und zu einem Word‑Dokument hinzufügen

Jetzt fügen wir alles zusammen: ein Dokument erstellen, einen Barcode erzeugen und **how to add barcode** zum Word‑File.

### Code:

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

1. **Dokumentinitialisierung** – erstellt ein neues `Document` (oder Sie können ein vorhandenes .docx laden).  
2. **Barcode‑Parameter** – definieren den Typ (`QR`), den Wert und die Farben und demonstrieren die Verwendung von **generate qr code java**.  
3. **Bildeinfügung** – `builder.insertImage` platziert den Barcode an der gewünschten Stelle und zeigt damit praktisch **how to add barcode** zu einer Word‑Datei.  
4. **Speichern** – das endgültige Dokument (`CustomBarcodeLabels.docx`) enthält den eingebetteten Barcode, bereit zum Drucken oder Verteilen.

## Häufige Probleme und Lösungen

| Problem | Ursache | Lösung |
|---------|---------|--------|
| Barcode erscheint leer | Ungültiger Farbstring oder nicht unterstützter Barcode‑Typ | Überprüfen Sie das Hex‑Farbformat und verwenden Sie einen unterstützten Typ (z. B. QR, Code128). |
| Bildgröße ist falsch | Falsche Pixel‑Umrechnung | Verwenden Sie `twipsToPixels`, um genaue Abmessungen basierend auf dem Word‑Layout zu berechnen. |
| Lizenz‑Ausnahme | Keine gültige Aspose‑Lizenz | Wenden Sie vor dem Ausführen des Codes eine temporäre oder gekaufte Lizenz an. |

## Häufig gestellte Fragen

**F: Kann ich Aspose.Words für Java ohne Lizenz verwenden?**  
A: Ja, aber Sie stoßen auf Evaluationsbeschränkungen. Holen Sie sich eine [temporary license](https://purchase.aspose.com/temporary-license/) für volle Funktionalität.

**F: Welche Barcode‑Typen kann ich erzeugen?**  
A: Aspose.BarCode unterstützt QR, Code 128, EAN‑13 und viele weitere. Siehe die offizielle [documentation](https://reference.aspose.com/words/java/) für die vollständige Liste.

**F: Wie kann ich die Barcode‑Größe ändern?**  
A: Passen Sie die Breiten‑/Höhen‑Parameter in `builder.insertImage` an oder ändern Sie die Eigenschaften `XDimension` und `BarHeight` des `BarcodeGenerator`‑Objekts.

**F: Kann ich benutzerdefinierte Schriftarten für den menschenlesbaren Teil des Barcodes verwenden?**  
A: Absolut. Verwenden Sie die Eigenschaft `CodeTextParameters`, um Schriftfamilie, -größe und -stil festzulegen.

**F: Wo bekomme ich Hilfe zu Aspose.Words?**  
A: Besuchen Sie das [support forum](https://forum.aspose.com/c/words/8/) für Community‑Unterstützung und offiziellen Support.

---

**Zuletzt aktualisiert:** 2026-02-09  
**Getestet mit:** Aspose.Words für Java 24.12, Aspose.BarCode für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}