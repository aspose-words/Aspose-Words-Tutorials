---
category: general
date: 2026-10-04
description: Erfahren Sie, wie Sie ein Segment in einem Word‑Diagramm explodieren,
  ein Kuchendiagramm‑Segment explodieren und die Größe eines Donut‑Diagramms mit einem
  Schritt‑für‑Schritt‑Java‑Beispiel ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: de
lastmod: 2026-10-04
og_description: Wie man ein Segment in einem Word‑Diagramm explodiert und Kreis‑ oder
  Donutdiagramme mit Java anpasst. Folgen Sie dem vollständigen Beispiel, um das Diagramm
  in Word zu ändern.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Wie man ein Segment in einem Word‑Diagramm herauslöst – vollständige Java‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Wie man ein Segment in einem Word‑Diagramm hervorhebt und dessen Aussehen anpasst
url: /de/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Segment in einem Word-Diagramm explodiert und sein Aussehen anpasst

Wenn Sie **how to explode slice** in einem Word-Diagramm benötigen, zeigt Ihnen dieser Leitfaden genau, wie es geht. Egal, ob Sie eine Vertriebspräsentation oder einen Finanzbericht vorbereiten, das Explodieren eines Kuchendiagramm‑Segments oder das Anpassen eines Donut‑Lochs kann die wichtigsten Daten hervorheben. In den folgenden Abschnitten lernen Sie außerdem, wie Sie **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size** und **customize pie chart word** Dokumente mit Aspose.Words für Java anpassen.

Sie schließen dieses Tutorial mit einem vollständigen, sofort ausführbaren Java‑Programm ab, das eine `.docx`‑Datei lädt, das erste Segment eines Kuchendiagramms explodiert, die Größe des Donut‑Lochs ändert und das Ergebnis speichert. Keine externen Skripte oder manuelle Bearbeitung sind erforderlich.

## Voraussetzungen

- Java 17 oder höher, installiert auf Ihrem Entwicklungsrechner.  
- Maven 3.6+ (oder Gradle) zur Verwaltung von Abhängigkeiten.  
- Aspose.Words für Java Bibliothek (die kostenlose Testversion funktioniert für die Entwicklung).  
- Ein Word‑Dokument (`input.docx`), das mindestens ein Diagramm (Kuchen‑ oder Donut‑Diagramm) enthält.

## Schritt 1: Aspose.Words zu Ihrem Projekt hinzufügen

Wenn Sie Maven verwenden, fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Für Gradle platzieren Sie dies in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro Tipp:** Halten Sie Ihre Bibliotheksversion aktuell; neuere Releases fügen Unterstützung für zusätzliche Diagrammtypen hinzu und verbessern die Leistung.

## Schritt 2: Laden Sie das Word-Dokument, das ein Diagramm enthält

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Warum das wichtig ist:** Das Laden des Dokuments erzeugt eine In‑Memory‑Repräsentation, die Aspose.Words traversieren kann. Ohne dieses Objekt können Sie nicht auf die Diagrammknoten zugreifen.

## Schritt 3: Das erste Diagramm im Dokument abrufen

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Erklärung:** `NodeType.SHAPE` deckt alle Zeichenobjekte ab, einschließlich Diagrammen. Das Argument `true` weist Aspose an, rekursiv zu suchen, sodass das erste Diagramm gefunden wird, selbst wenn es in einer Tabelle verschachtelt ist.

## Schritt 4: Das erste Segment eines Kuchendiagramms explodieren

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Wie es funktioniert:** Die Methode `setExplosion` nimmt einen numerischen Wert, der bestimmt, wie weit das Segment vom Zentrum entfernt wird. Ein Wert von `20` ist visuell deutlich erkennbar, ohne das Diagrammlayout zu zerstören.

## Schritt 5: Die Größe des Donut-Lochs für ein Donut-Diagramm anpassen

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Warum das hilft:** Ein größeres Donut-Loch kann die Lesbarkeit verbessern, wenn Sie viele Datenpunkte haben. Die Methode `setDoughnutHoleSize` erwartet einen Prozentsatz (0‑100).

## Schritt 6: Das modifizierte Dokument speichern

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Erwartete Ausgabe

- Das erste Segment des ersten Kuchendiagramms wird nach außen verschoben, sodass es hervorsticht.
- Wenn das Diagramm ein Donut ist, vergrößert sich das zentrale Loch auf 40 % des Diagrammradius.
- Die resultierende Datei `PieChart.docx` kann in Microsoft Word, LibreOffice oder einem anderen kompatiblen Viewer geöffnet werden und zeigt die programmatisch vorgenommenen visuellen Änderungen.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das gesamte Programm in einem Block. Kopieren Sie es in `ChartExploder.java`, passen Sie die Dateipfade an und führen Sie es mit `mvn compile exec:java` (oder der Ausführungskonfiguration Ihrer IDE) aus.

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Das Ausführen dieses Codes wird **modify chart in Word**, **explode pie chart slice** und **change doughnut chart size** automatisch durchführen.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| *Was ist, wenn das Dokument mehrere Diagramme enthält?* | Das Beispiel greift auf das **erste** Diagramm zu (`NodeType.SHAPE, 0`). Um mit anderen Diagrammen zu arbeiten, ändern Sie den Index oder iterieren Sie über `doc.getChildNodes(NodeType.SHAPE, true)` und filtern Sie nach `shape.getChart() != null`. |
| *Kann ich ein anderes Segment als das erste explodieren?* | Ja. Greifen Sie über `chart.getSeries().get(seriesIndex)` auf die gewünschte Serie zu und rufen Sie `setExplosion(value)` auf. Indizes beginnen bei Null. |
| *Funktioniert das mit Word‑Dateien von 2007‑2021?* | Aspose.Words unterstützt `.doc`, `.docx`, `.dot` und `.dotx`. Der gleiche Code funktioniert über alle Versionen hinweg, da die Bibliothek das Dateiformat abstrahiert. |
| *Was ist, wenn das Diagramm ein Balken‑ oder Liniendiagramm ist?* | `setExplosion` und `setDoughnutHoleSize` gelten nur für Kuchendiagramme. Der Code überspringt diese Operationen sicher, wenn der Diagrammtyp anders ist. |
| *Benötige ich eine Lizenz für Aspose.Words?* | Eine kostenlose Evaluierungslizenz entfernt die 30‑Tage‑Begrenzung, fügt jedoch ein Wasserzeichen hinzu. Für den Produktionseinsatz erwerben Sie eine Lizenz, um das Wasserzeichen zu entfernen und die volle Funktionalität freizuschalten. |

## Fazit

Sie wissen jetzt, wie man **how to explode slice** in einem Word‑Diagramm durchführt, wie man **modify chart in Word** und **change doughnut chart size** mit Aspose.Words für Java anpasst. Das vollständige Beispiel demonstriert den gesamten Workflow – vom Laden eines Dokuments, über das Auffinden des Diagramms, das Anwenden visueller Anpassungen bis zum Speichern des Ergebnisses – sodass Sie diese Schritte in jede Reporting‑ oder Dokumentgenerierungs‑Pipeline integrieren können.

**Nächste Schritte**

- Erkunden Sie weitere Diagrammanpassungen wie das Ändern von Farben, das Hinzufügen von Datenbeschriftungen oder das Wechseln des Diagrammtyps (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Kombinieren Sie diese Logik mit Aspose.PDF, um eine PDF‑Version desselben Berichts zu erzeugen.  
- Automatisieren Sie den Vorgang für eine Stapelverarbeitung von Dokumenten, indem Sie über Dateien in einem Verzeichnis iterieren.

Probieren Sie gern verschiedene Explosionswerte oder Donut‑Loch‑Prozentsätze aus, um Ihren Gestaltungsrichtlinien zu entsprechen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagrammachse in einem Word-Dokument ausblenden](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Blasendiagramm in ein Word-Dokument einfügen](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}