---
category: general
date: 2026-09-24
description: Erfahren Sie, wie Sie in Word mit Java ein Diagramm erstellen, ein Radialdiagramm
  einfügen und das Dokument mit Aspose.Words als DOCX speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: de
lastmod: 2026-09-24
og_description: Diagramm in Word mit Java und Aspose.Words erstellen. Dieses Tutorial
  zeigt, wie man ein Radardiagramm hinzufügt, Daten anpasst und das Dokument als DOCX
  speichert.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Diagramm in Word mit Java erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Wie man ein Diagramm in Word mit Java und Aspose.Words erstellt
url: /de/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Diagramm in Word mit Java und Aspose.Words erstellt

Wenn Sie ein **Diagramm in Word** aus einer Java-Anwendung erstellen müssen, führt Sie diese Anleitung durch den gesamten Prozess. Sie sehen, wie man ein Radialdiagramm hinzufügt, optional seine Serien füllt und schließlich **save document as docx** mit der Aspose.Words for Java-Bibliothek.

Das Erzeugen visueller Daten in einer Word-Datei ist ein häufiges Bedürfnis für Berichte, Rechnungsstellung oder automatisierte Dokumentenerstellung. Am Ende dieses Tutorials können Sie **create word document java** Projekte erstellen, die **add chart to Word** Dateien ohne manuelle Bearbeitung hinzufügen.

## Voraussetzungen

* Java Development Kit (JDK) 8 oder neuer.
* Maven oder Gradle für die Abhängigkeitsverwaltung.
* Eine IDE wie IntelliJ IDEA, Eclipse oder VS Code.
* Eine gültige Aspose.Words for Java Lizenz (die kostenlose Testversion funktioniert für die Entwicklung).

Diese Werkzeuge bilden die Grundlage für die nachfolgenden Code‑Beispiele.

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt (oder aktualisieren Sie ein bestehendes) und fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Durch das Ausführen von `mvn clean install` wird die Bibliothek heruntergeladen und Klassen wie `Document`, `DocumentBuilder` und `ChartType` stehen im Klassenpfad zur Verfügung.

> **Pro Tipp:** Halten Sie die Bibliotheksversion aktuell. Neue Versionen fügen Diagrammtypen hinzu und verbessern die Rendering‑Leistung.

## Schritt 2: Neues Word‑Dokument erstellen

Der erste programmatische Schritt, um **create chart in Word** zu erstellen, besteht darin, ein leeres `Document` zu instanziieren. Dieses Objekt repräsentiert das gesamte `.docx`‑Paket.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funktioniert wie ein Cursor; er kennt den aktuellen Einfügepunkt und bietet Methoden für Text, Tabellen und Diagramme. An diesem Punkt haben Sie **created word document java** Stil – eine leere Leinwand, bereit für Inhalte.

## Schritt 3: Radialdiagramm einfügen

Aspose.Words unterstützt viele Diagrammtypen. Um **insert radial chart** einzufügen, rufen Sie `insertChart` mit `ChartType.RADIAL` auf. Die Methode erfordert außerdem Breite und Höhe in Punkten (1 Punkt ≈ 1/72 Zoll).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Das zurückgegebene `Shape`‑Objekt enthält das zugrunde liegende Diagrammobjekt. Das Diagramm rendert automatisch Graduierungen für ein 24,9°‑Layout, das der Standard für Radialdiagramme in Word ist.

### Warum ein Radialdiagramm verwenden?

Ein Radialdiagramm visualisiert Daten, die sich um einen Kreis wickeln, und ist ideal, um zyklische Muster zu zeigen (z. B. monatliche Verkäufe, Uhr‑Ziffern‑Metriken). Mit derselben API können Balken‑, Kreis‑ oder Liniendiagramme eingefügt werden, aber der Radialtyp verleiht ein unverwechselbares Aussehen ohne zusätzlichen Styling‑Code.

## Schritt 4: (Optional) Daten für die Diagramm‑Serien hinzufügen

Wenn das Diagramm reale Werte anzeigen soll, müssen Sie Serien und Punkte hinzufügen. Das folgende Snippet fügt eine einzelne Serie mit drei Datenpunkten hinzu:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Sie können die `add`‑Aufrufe für beliebig viele Punkte wiederholen. Aspose.Words aktualisiert die visuelle Darstellung automatisch, sodass Sie sehen, wie sich die Radialsegmente an die neuen Werte anpassen.

> **Häufige Frage:** *Was, wenn ich Daten aus einer Datenbank binden muss?*  
> Rufen Sie die Zeilen ab, iterieren Sie darüber und rufen Sie innerhalb der Schleife `series.getDataPoints().add(value, label)` auf. Die API ist thread‑sicher und funktioniert mit jedem `ResultSet`, das Sie bereitstellen.

## Schritt 5: Dokument als DOCX speichern

Wenn das Diagramm fertig ist, besteht der letzte Schritt darin, **save document as docx**. Die `save`‑Methode bestimmt das Ausgabeformat anhand der Dateierweiterung.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Die erzeugte Datei enthält ein voll funktionsfähiges Radialdiagramm, das in Microsoft Word, LibreOffice oder jedem Viewer, der das DOCX‑Format unterstützt, geöffnet werden kann. Da wir die `.docx`‑Erweiterung verwendet haben, speichert Word die Datei im Open‑XML‑Format, dem modernen Standard für Word‑Dokumente.

### Ergebnis überprüfen

Öffnen Sie `RadialChartDemo.docx` in Word:

1. Sie sollten eine einzelne Seite mit einem zentrierten Radialdiagramm sehen.
2. Wenn Sie Serien‑Daten hinzugefügt haben, zeigt das Diagramm vier Segmente mit den Beschriftungen Q1‑Q4.
3. Rechtsklicken Sie das Diagramm → **Edit Data**, um die zugrunde liegende Datentabelle zu bestätigen.

Falls das Diagramm leer erscheint, überprüfen Sie, ob Sie `chart.getChart()` aufgerufen haben, bevor Sie Serien hinzufügen, und stellen Sie sicher, dass der Cursor des DocumentBuilder an der gewünschten Position für das Diagramm steht.

## Schritt 6: Erweiterte Tipps für die Arbeit mit Diagrammen

| Tipp | Warum es wichtig ist |
|-----|----------------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Verbessert die visuelle Konsistenz, ohne jedes Element manuell zu formatieren. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Ermöglicht das feine Anpassen der Diagrammgröße basierend auf dem Seitenlayout. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Gibt den Lesern Kontext, die das Dokument ohne umgebenden Text ansehen. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Nützlich, wenn Sie eine nicht editierbare Version für die Verteilung benötigen. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Verhindert das Evaluations‑Wasserzeichen in Produktions‑Builds. |

Diese Verbesserungen sind optional, zeigen jedoch, wie Sie das Diagramm weiter anpassen können, nachdem Sie gelernt haben, **add chart to Word**.

## Fazit

Sie haben nun ein vollständiges, eigenständiges Beispiel, das zeigt, wie man **create chart in Word** mit Java verwendet, **insert radial chart**, optional mit Daten füllt und **save document as docx**. Das gleiche Muster funktioniert für andere Diagrammtypen, sodass Sie dieses Tutorial bei Bedarf auf Balken‑, Linien‑ oder Kreisdiagramme erweitern können.

Als Nächstes könnten Sie erkunden:

* **create word document java** Projekte, die Tabellen, Bilder und mehrere Diagramme kombinieren.
* Verwendung von **save document as docx** zusammen mit **save document as pdf** für mehrformatige Berichte.
* Hinzufügen dynamischer Daten aus REST‑APIs oder Datenbanken zu Ihren Diagrammen.

Fühlen Sie sich frei, mit den Stiloptionen, Diagrammgrößen und Datenquellen zu experimentieren. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Leeres Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Word‑Dokument Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}