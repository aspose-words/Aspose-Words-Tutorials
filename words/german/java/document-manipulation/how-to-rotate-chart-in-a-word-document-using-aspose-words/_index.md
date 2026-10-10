---
category: general
date: 2026-10-10
description: Erfahren Sie, wie Sie ein Diagramm in einer Word‑Datei drehen und das
  Diagramm in Word ändern, um die Größe eines Donut‑Diagramms mit einem vollständigen
  Java‑Beispiel anzupassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: de
lastmod: 2026-10-10
og_description: Wie man ein Diagramm in einer Word-Datei dreht und das Diagramm in
  Word ändert, um die Größe eines Donut‑Diagramms mit Aspose.Words für Java zu ändern.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Wie man ein Diagramm in einem Word‑Dokument dreht – Schritt‑für‑Schritt
  Java‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man ein Diagramm in einem Word‑Dokument mit Aspose.Words dreht
url: /de/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Diagramm in einem Word-Dokument mit Aspose.Words rotiert

Wenn Sie **wie man ein Diagramm rotiert** in einer Microsoft Word-Datei benötigen, zeigt Ihnen dieser Leitfaden die genauen Schritte. Sie lernen außerdem, wie Sie **Diagramm in Word ändern** können, um **die Größe eines Donut‑Diagramms zu ändern**, ohne Ihren Java‑Code zu verlassen.

Word‑Automatisierung fühlt sich oft wie eine Reihe von losgelösten API‑Aufrufen an, aber mit Aspose.Words können Sie ein Diagramm wie jeden anderen Dokumentknoten behandeln. Am Ende dieses Tutorials haben Sie ein ausführbares Programm, das eine vorhandene `.docx`‑Datei lädt, ein Donut‑Diagramm um 45° rotiert, das Loch auf 50 % des Radius reduziert und das Ergebnis als neue Datei speichert.

## Voraussetzungen

* Java 17 oder neuer installiert.
* Maven (oder Gradle) zur Verwaltung von Abhängigkeiten.
* Ein Eingabe‑Word‑Dokument (`input.docx`), das bereits ein Donut‑Diagramm enthält.
* Eine gültige Aspose.Words for Java‑Lizenz (oder den Evaluierungsmodus verwenden).

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt oder fügen Sie die folgende Abhängigkeit zu Ihrer bestehenden `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Das Ausführen von `mvn clean install` lädt die Bibliothek herunter und stellt die Klassen in Ihrem Klassenpfad zur Verfügung.

## Schritt 2: Das Word-Dokument laden, das ein Diagramm enthält

Der erste Vorgang besteht darin, das vorhandene Dokument zu öffnen. Die Klasse `Document` repräsentiert die gesamte Datei.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Das Laden der Datei **ändert** sie **nicht**; es erstellt lediglich eine In‑Memory‑Repräsentation, die Sie abfragen und bearbeiten können.

## Schritt 3: Einen DocumentBuilder für die Navigation erstellen

`DocumentBuilder` bietet Ihnen eine cursor‑ähnliche API, um durch den Dokumentbaum zu gehen. Wir werden sie verwenden, um die erste Diagramm‑Form zu finden.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder startet am Anfang des Dokuments, Sie können ihn jedoch bei Bedarf später zu jedem Knoten bewegen.

## Schritt 4: Die erste Diagramm‑Form abrufen

Diagramme werden als `Shape`‑Knoten gespeichert. Durch das Filtern von Kindknoten des Typs `NodeType.SHAPE` können wir das Diagramm‑Objekt extrahieren.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Enthält das Dokument mehrere Diagramme, können Sie über `getChildNodes` iterieren und jede `Shape` auf `hasChart()` prüfen, bevor Sie sie casten.

## Schritt 5: Das Diagramm rotieren (wie man ein Diagramm rotiert)

Ein Donut‑Diagramm ist im Wesentlichen ein Kreisdiagramm mit einem Loch. Das Rotieren ändert den Startwinkel des ersten Segments.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Die Methode `setStartAngle` erwartet einen double‑Wert, der Grad angibt. Positive Werte rotieren im Uhrzeigersinn, während negative Werte gegen den Uhrzeigersinn rotieren.

## Schritt 6: Die Größe des Donut-Lochs ändern (Donut-Diagrammgröße ändern)

Die Lochgröße wird als Bruchteil des Diagrammradius angegeben. Ein Wert von `0.5` bedeutet, dass das Loch 50 % des Gesamtradius einnimmt.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tipp:** Der gültige Bereich ist `0.0` (kein Loch, d.h. ein normales Kreisdiagramm) bis `0.9` (sehr dünner Ring). Werte außerhalb dieses Bereichs werfen eine `IllegalArgumentException`.

## Schritt 7: Das geänderte Dokument speichern

Schließlich schreiben Sie die Änderungen zurück auf die Festplatte.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Wenn Sie `DoughnutFormatted.docx` in Microsoft Word öffnen, sehen Sie das Donut‑Diagramm um 45° rotiert und das Loch auf die Hälfte seiner ursprünglichen Größe reduziert.

## Vollständiges, ausführbares Beispiel

Wenn wir alle Teile zusammenfügen, erhalten Sie das vollständige Programm, das Sie in Ihre IDE kopieren und einfügen können:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms gibt aus:

```
Chart rotated and doughnut size changed successfully.
```

Das Öffnen von `DoughnutFormatted.docx` zeigt ein Donut‑Diagramm, dessen erstes Segment bei 45° beginnt und dessen innerer Radius die Hälfte des äußeren Radius einnimmt.

## Häufige Variationen und Randfälle

| Situation | Was anzupassen | Warum es wichtig ist |
|-----------|----------------|----------------------|
| **Mehrere Diagramme** | Durchlaufen Sie `getChildNodes(NodeType.SHAPE, true)` und prüfen Sie für jedes `shape.hasChart()` | Stellt sicher, dass Sie das beabsichtigte Diagramm und nicht das erste ändern |
| **Balken‑ oder Liniendiagramm** | `setStartAngle` ist nicht anwendbar; verwenden Sie `chart.getSeries().get(0).setFillFormat(...)` für andere visuelle Anpassungen | Nicht alle Diagrammtypen unterstützen Rotation; Donut-/Kreisdiagramme sind die einzigen mit einem Startwinkel |
| **Diagramm ohne Donut-Loch** | Überspringen Sie `setDoughnutHoleSize` oder konvertieren Sie zuerst den Diagrammtyp zu Donut über `chart.setChartType(ChartType.DONUT)` | Das Ändern der Lochgröße bei einem Nicht‑Donut‑Diagramm löst eine Ausnahme aus |
| **Große Dokumente** | Verwenden Sie `DocumentBuilder.moveToDocumentStart()` und `builder.moveToNode(chartShape)` für gezielte Navigation | Verbessert die Leistung, indem eine vollständige Durchquerung nicht relevanter Knoten vermieden wird |

## Profi-Tipps für zuverlässige Diagrammbearbeitung

* **Cache die Diagramm-Referenz** – Wenn Sie mehrere Eigenschaften ändern möchten, behalten Sie eine lokale `Chart`-Variable bei, anstatt wiederholt `chartShape.getChart()` aufzurufen.
* **Eingabewerte validieren** – Überprüfen Sie vor dem Aufruf von `setStartAngle` oder `setDoughnutHoleSize` den Wertebereich, um Laufzeitfehler zu vermeiden.
* **Lizenz verwenden** – Der Evaluierungsmodus fügt auf der ersten Seite ein Wasserzeichen ein. Das Anwenden einer Lizenz (`License license = new License(); license.setLicense("Aspose.Words.lic");`) entfernt es.

## Nächste Schritte

Jetzt, da Sie **wie man ein Diagramm rotiert** und **die Donut-Diagrammgröße ändert**, können Sie weitere **Diagramm-Änderungen in Word** Szenarien erkunden:

* Ändern Sie die Segmentfarben mit `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Fügen Sie Datenbeschriftungen hinzu, indem Sie `chart.getSeries().get(0).setHasDataLabel(true)` aufrufen.
* Exportieren Sie das Diagramm als Bild mit `chart.toImage(300, 300, ImageType.PNG)`.

Jede dieser Erweiterungen folgt dem gleichen Muster: Das `Chart`-Objekt abrufen, den entsprechenden Setter aufrufen und das Dokument speichern.

**Sie haben gerade das Rotieren und Ändern der Größe von Donut-Diagrammen in Word mit Java gemeistert.** Passen Sie den Code gerne für andere Diagrammtypen an, integrieren Sie ihn in eine größere Dokument-Generierungspipeline oder kombinieren Sie ihn mit Aspose.Slides für PowerPoint-Automatisierung. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code-Beispiele mit Schritt-für-Schritt-Erklärungen, um Ihnen zu helfen, weitere API-Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagrammachse in einem Word-Dokument ausblenden](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Blasendiagramm in ein Word-Dokument einfügen](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}