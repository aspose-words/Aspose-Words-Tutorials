---
category: general
date: 2026-11-15
description: Erfahren Sie, wie Sie ein Kreisdiagramm in einem Word-Dokument erstellen
  und das DOCX mit Java als PDF speichern. Dieser Leitfaden behandelt außerdem die
  Konvertierung von Word zu PDF und das Hinzufügen von Diagrammen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: de
lastmod: 2026-11-15
og_description: Erstelle ein Kreisdiagramm in einer Word‑Datei und speichere das DOCX
  mit Java als PDF. Folge dieser Schritt‑für‑Schritt‑Anleitung, um Word in PDF zu
  konvertieren und Diagramme hinzuzufügen.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Erstelle ein Kreisdiagramm in Word und speichere die DOCX als PDF – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Wie man ein Kreisdiagramm in Word erstellt und das DOCX als PDF speichert
url: /de/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm in Word erstellt und docx als PDF speichert

Wenn Sie ein **create pie chart** in ein Word‑Dokument einfügen und anschließend **save docx as PDF** möchten, zeigt Ihnen dieses Tutorial genau, wie es geht. Sie sehen ein vollständiges, ausführbares Beispiel, das eine .docx‑Datei in ein PDF konvertiert und dabei ein Kreisdiagramm einbettet, sodass Sie die Frage „how to add chart“ beantworten können, ohne nach verstreuten Code‑Snippets zu suchen.

In diesem Leitfaden lernen Sie:

* Ein vorhandenes *.docx* laden (oder von Grund auf neu beginnen)  
* Aspose.Words für Java verwenden, um **create pie chart** zu **erstellen** und Daten zu befüllen  
* **save docx as PDF** mit korrekt gerendertem Diagramm  
* Die Feinheiten von **convert word to pdf** verstehen, wenn Diagramme beteiligt sind  

Die Schritte funktionieren mit Aspose.Words 2024‑x.x und Java 17, die Konzepte gelten jedoch für jede Bibliothek, die die Manipulation von Word‑Diagrammen unterstützt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

| Requirement | Why it matters |
|-------------|----------------|
| Java 17 (oder neuer) | Wird von der neuesten Aspose.Words‑JAR benötigt |
| Maven‑ oder Gradle‑Build‑Tool | Vereinfacht die Verwaltung von Abhängigkeiten |
| Aspose.Words for Java (neueste Version) | Stellt die Klassen `Document`, `Chart` und `ChartType` bereit |
| Eine Eingabe‑**.docx**‑Datei (oder ein leeres Dokument) | Das Diagramm wird in diese Datei eingefügt |

Fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` (Maven) oder `build.gradle` (Gradle) hinzu. Beispiel für Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Schritt 1: Das Word‑Dokument laden (oder ein neues erstellen)

Der erste Schritt besteht darin, eine `Document`‑Instanz zu erhalten. Wenn Sie bereits eine Vorlage haben, übergeben Sie deren Pfad; andernfalls erstellen Sie ein leeres Dokument.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Warum dieser Schritt?* Das `Document`‑Objekt ist der Container für alle Word‑Inhalte, einschließlich Diagrammen. Das Laden einer bestehenden Datei ermöglicht es Ihnen, umgebenden Text und Formatvorlagen beizubehalten und gleichzeitig ein neues visuelles Element hinzuzufügen.

## Schritt 2: **Create pie chart** – der Kern von „how to create chart“

Jetzt instanziieren wir ein `Chart`‑Objekt mit `ChartType.PIE`. Dadurch wird automatisch ein Platzhalter für ein Kreisdiagramm erstellt, den Sie später mit Daten füllen können.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Erklärung*: `ChartType.PIE` weist Aspose.Words an, eine Kreisdiagramm‑Vorlage zu verwenden. Das Diagramm wird dem Dokumentenkörper hinzugefügt, sodass es dort erscheint, wo Sie es benötigen. Dies erfüllt die Anforderung „how to add chart“ in einem einzigen Aufruf.

## Schritt 3: Das Diagramm befüllen – „how to add chart“ mit Daten beantworten

Ein Kreisdiagramm ist ohne Seriendaten sinnlos. Verwenden Sie die `Series`‑Sammlung, um Kategorien und Werte hinzuzufügen.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Warum das wichtig ist*: Jeder Aufruf von `add` erzeugt ein Stück des Kreises. Das erste Argument ist die Bezeichnung, das zweite der numerische Wert. Sie können diese durch dynamische Daten aus einer Datenbank oder einer CSV‑Datei ersetzen.

### Optional: Aussehen anpassen (nicht zwingend, aber nützlich)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Diese Anpassungen zeigen, wie Sie **how to create chart** mit einem professionellen Look realisieren können, ohne den Java‑Code zu verlassen.

## Schritt 4: **Save docx as PDF** – der letzte Teil von „convert word to pdf“

Nachdem das Diagramm eingebettet ist, exportieren Sie das Dokument nach PDF. Aspose.Words rendert das Diagramm als Vektorgrafik und bewahrt so die Qualität.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Wichtiger Punkt*: Die `save`‑Methode konvertiert die Word‑Datei automatisch nach PDF und übernimmt dabei die Diagrammrasterisierung, das Einbetten von Schriftarten und das Seitenlayout. Damit wird das Ziel **save docx as pdf** erreicht und ein zuverlässiger Weg gezeigt, **convert word to pdf** auszuführen, wenn Diagramme vorhanden sind.

### Erwartete Ausgabe

Beim Ausführen des Programms entsteht `output.pdf`, das Folgendes enthält:

* Den ursprünglichen Inhalt von `input.docx` (falls vorhanden)  
* Ein vollständig gerendertes Kreisdiagramm mit dem Titel *Sales Distribution Q1*  
* Präzise Prozentanteile, die den Daten entsprechen (40 %, 30 %, 30 %)

Öffnen Sie das PDF in einem beliebigen Viewer – Sie sollten ein scharfes Kreisdiagramm sehen, das dem in der Word‑Datei entspricht.

## Häufige Stolperfallen und wie man sie vermeidet

| Issue | Cause | Fix |
|-------|-------|-----|
| Diagramm erscheint leer im PDF | Schriftart‑ oder Diagrammrendereinstellungen fehlen | Stellen Sie sicher, dass Sie die neueste Aspose.Words‑Version verwenden; sie enthält die erforderlichen Rendering‑Bibliotheken. |
| Datenwerte werden falsch gerundet | Verwendung von Ganzzahlen bei großen Zahlen | Verwenden Sie `double`‑Werte oder skalieren Sie die Zahlen, bevor Sie sie zur Serie hinzufügen. |
| Ausgabepdf ist sehr groß | Bilder mit hoher DPI eingebettet | Setzen Sie `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`, wenn Sie ebenfalls Bilder einbetten. |
| „convert word to pdf“ wirft `UnsupportedOperationException` | Ältere Java‑Version (< 11) verwendet | Aktualisieren Sie auf Java 17 oder neuer, das von Aspose.Words 24.x verlangt wird. |

## Pro‑Tipp: Logik zur Diagrammerstellung wiederverwenden

Wenn Sie mehrere Diagramme in dasselbe Dokument einfügen müssen, extrahieren Sie den Diagrammerstellungs‑Code in eine Hilfsmethode:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Jetzt können Sie `doc.getFirstSection().getBody().appendChild(createPieChart(...));` für jeden Datensatz aufrufen und Ihren Code DRY (Don’t Repeat Yourself) halten.

## Fazit

Sie wissen jetzt, wie Sie ein **create pie chart** in ein Word‑Dokument einfügen, mit Daten befüllen und **save docx as PDF** mit Java durchführen. Dieses End‑to‑End‑Beispiel deckt den gesamten **convert word to pdf**‑Workflow ab, beantwortet **how to add chart** und demonstriert **how to create chart** programmgesteuert.  

Von hier aus können Sie folgendes erkunden:

* Das Hinzufügen von Balken‑ oder Liniendiagrammen (`ChartType.BAR`, `ChartType.LINE`) – ein weiteres **how to create chart**‑Szenario.  
* Export in andere Formate wie PNG oder HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamisches Erzeugen des Eingabedokuments mit Tabellen oder Platzhaltern, bevor Diagramme eingefügt werden.

Experimentieren Sie gern mit verschiedenen Datensätzen, Stiloptionen oder sogar dem Einbetten mehrerer Diagramme pro Seite. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}