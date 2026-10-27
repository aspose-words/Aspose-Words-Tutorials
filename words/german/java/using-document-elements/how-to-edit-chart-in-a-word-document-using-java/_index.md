---
category: general
date: 2026-09-11
description: Wie man ein Diagramm in einem Word‑Dokument mit Java bearbeitet – lerne,
  Diagrammeinstellungen zu aktualisieren, Rasterlinien zu aktivieren, Diagrammoptionen
  zu ändern und das aktualisierte Dokument zu speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: de
lastmod: 2026-09-11
og_description: Wie man ein Diagramm in einem Word-Dokument mit Java bearbeitet. Folgen
  Sie dieser Anleitung, um Diagrammeinstellungen zu aktualisieren, Diagrammgitternetzlinien
  zu aktivieren, Diagrammoptionen zu ändern und das aktualisierte Dokument zu speichern.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Wie man ein Diagramm in einem Word‑Dokument mit Java bearbeitet – vollständige
  Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Wie man ein Diagramm in einem Word-Dokument mit Java bearbeitet
url: /de/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Diagramm in einem Word-Dokument mit Java bearbeitet

Wenn Sie **ein Diagramm bearbeiten** in einer Word‑Datei, zeigt Ihnen dieser Leitfaden die genauen Schritte. Sie lernen, wie Sie Diagrammeinstellungen aktualisieren, Diagramm‑Gitternetzlinien aktivieren, Diagrammoptionen ändern und schließlich **das aktualisierte Dokument speichern** ohne Formatierung zu verlieren.

Die programmgesteuerte Arbeit mit Diagrammen fühlt sich oft wie ein Black‑Box‑Vorgang an, besonders wenn Sie visuelle Details wie Graduierungen oder Gitternetzlinien anpassen möchten. Dieses Tutorial deckt alles ab, was Sie wissen müssen – vom Laden des Dokuments bis zum Persistieren der Änderungen. Es werden keine externen Werkzeuge benötigt – nur die Aspose.Words for Java‑Bibliothek (Version 24.9 oder neuer).

Am Ende dieses Artikels können Sie:

* Eine `.docx`‑Datei laden, die ein Diagramm enthält.
* Die Diagramm‑Form finden und deren Eigenschaften ändern.
* Diagramm‑Gitternetzlinien (Graduierungen) aktivieren und weitere Optionen anpassen.
* **Das aktualisierte Dokument** in einer neuen Datei speichern.

## Voraussetzungen

* Java 17 oder neuer auf Ihrem Rechner installiert.  
* Maven oder Gradle zur Verwaltung von Abhängigkeiten.  
* Aspose.Words for Java 24.9+ (die Version, die `setShowGraduations` eingeführt hat).  
* Eine Word‑Datei (`input.docx`), die bereits mindestens ein Diagramm enthält.

Falls Sie mit Aspose.Words nicht vertraut sind, denken Sie daran, dass es sich um eine voll ausgestattete API handelt, mit der Sie Word‑Dokumente programmgesteuert lesen, ändern und schreiben können – ähnlich wie Sie ein DOM in einem Web‑Browser manipulieren würden.

## Schritt 1: Projekt einrichten und Bibliothek importieren

Erstellen Sie ein neues Maven‑Projekt oder fügen Sie die Abhängigkeit zu einem bestehenden Projekt hinzu:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro‑Tipp:** Verwenden Sie die neueste stabile Version, um sicherzustellen, dass die Methode `setShowGraduations` verfügbar ist. Ältere Versionen lassen sich nicht kompilieren.

## Schritt 2: Das Word‑Dokument laden, das ein Diagramm enthält

Der erste Schritt in jedem **Diagramm‑bearbeiten**‑Workflow ist das Laden der Quelldatei. Aspose.Words repräsentiert das gesamte Dokument mit der Klasse `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Das `Document`‑Objekt gibt Ihnen Zugriff auf jeden Knoten innerhalb der Datei, einschließlich Formen, Tabellen und Absätzen.  

## Schritt 3: Die erste Diagramm‑Form im Dokument finden

Diagramme werden als `Shape`‑Knoten gespeichert, deren Renderer ein `Chart` ist. Um ein Diagramm zu bearbeiten, müssen Sie zunächst diesen Knoten abrufen.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Enthält das Dokument mehrere Diagramme, iterieren Sie über `shapes` und prüfen Sie `chartShape.getChart() != null`, bevor Sie casten. Das verhindert `ClassCastException` und stellt sicher, dass Sie **Diagrammoptionen ändern** nur an gültigen Diagramm‑Objekten vornehmen.

## Schritt 4: Diagramm‑Gitternetzlinien (Graduierungen) aktivieren – eine neue Eigenschaft in Version 24.9

Die Eigenschaft `setShowGraduations` schaltet die Sichtbarkeit von Hilfslinien auf der Werte‑Achse ein bzw. aus. Das Aktivieren verbessert häufig die Lesbarkeit bei dichten Datensätzen.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Warum das wichtig ist:** Gitternetzlinien geben dem Betrachter einen visuellen Referenzpunkt für jeden Datenpunkt, wodurch Trends leichter erkennbar werden. Der Standardwert ist `false`, Sie müssen sie also explizit aktivieren, wenn sie benötigt werden.

Sie können zudem weitere Aspekte anpassen, etwa die Haupt‑Gitternetzlinien, Achsentitel oder die Legenden‑Position. Nachfolgend ein Beispiel, das den Diagrammtitel und die Legenden‑Position ändert – beides Teil von **Diagrammoptionen ändern**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Schritt 5: Das Dokument mit den aktualisierten Diagrammeinstellungen speichern

Nachdem das Diagramm geändert wurde, speichern Sie die Änderungen. Dieser Schritt schließt die **Dokument‑aktualisieren‑und‑speichern**‑Phase ab.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Das Ausführen des Programms erzeugt `output.docx`, in dem das Diagramm nun Gitternetzlinien, einen neuen Titel und eine verschobene Legende anzeigt. Öffnen Sie die Datei in Microsoft Word, um die visuellen Änderungen zu prüfen.

## Vollständiger Quellcode (ausführbar)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Erwartetes Ergebnis

Wenn Sie `output.docx` öffnen:

* Das Diagramm zeigt kleine Gitternetzlinien auf der Werte‑Achse.  
* Der Titel lautet **„Sales Overview 2026“**.  
* Die Legende erscheint unten im Diagramm.

War das ursprüngliche Diagramm bereits mit Gitternetzlinien versehen, bleibt das Aussehen unverändert, was bestätigt, dass der Code **idempotent** ist.

## Häufige Fragen und Sonderfall‑Behandlung

### Was, wenn das Dokument kein Diagramm enthält?

Der Versuch, eine Nicht‑Diagramm‑Form zu casten, löst eine `ClassCastException` aus. Schützen Sie sich, indem Sie den Formtyp prüfen:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Wie bearbeite ich ein bestimmtes Diagramm statt des ersten?

Iterieren Sie über `shapes` und vergleichen Sie einen bekannten Titel oder einen anderen Identifier:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Kann ich Gitternetzlinien später wieder deaktivieren?

Ja, setzen Sie die Eigenschaft einfach auf `false`:

```java
chart.setShowGraduations(false);
```

### Funktioniert das mit `.doc` (binären) Dateien?

Aspose.Words abstrahiert das Dateiformat, sodass derselbe Code für `.doc` und `.docx` funktioniert. Einige neuere Diagramm‑Funktionen (wie Graduierungen) werden jedoch nur im OOXML‑Format gespeichert, sodass Sie den Effekt nur bei einer Speicherung als `.docx` sehen.

## Tipps für produktionsreife Code

* **Eingabepfade validieren** – verwenden Sie `Files.exists(Paths.get(inputPath))` bevor Sie laden.  
* **API‑Aufrufe in try‑catch‑Blöcken** einbetten, um `Exception`‑Details sichtbar zu machen, besonders bei beschädigten Dokumenten.  
* **Ressourcen freigeben** – obwohl Aspose.Words den Speicher verwaltet, kann ein Aufruf von `doc.close()` (oder die Verwendung von try‑with‑resources, falls verfügbar) native Handles früher freigeben.  
* **Versionsprüfung** – stellen Sie sicher, dass die Laufzeitbibliothek Version ≥ 24.9 hat, bevor Sie `setShowGraduations` aufrufen. Sie können `License.getVersion()` abfragen, um programmgesteuert zu prüfen.

## Fazit

Sie wissen jetzt **wie man ein Diagramm** in einem Word‑Dokument mit Java bearbeitet. Der Prozess – Dokument laden, Diagramm finden, Gitternetzlinien aktivieren, Diagrammoptionen ändern und **das aktualisierte Dokument speichern** – deckt die gängigsten Szenarien der programmgesteuerten Diagrammbearbeitung ab.  

Ab hier können Sie weitere Anpassungen erkunden, etwa das Ändern von Datenreihen‑Farben, das Anwenden von Diagramm‑Stilen oder das Exportieren des Diagramms als Bild. Jede dieser Aufgaben folgt demselben Muster: `Chart`‑Instanz abrufen, Eigenschaften anpassen und **das aktualisierte Dokument speichern**.

Viel Spaß beim Coden und experimentieren Sie gern mit anderen Diagrammeinstellungen, um Ihre Berichte optimal zu gestalten!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Wie man ein Säulendiagramm mit Aspose.Words for Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Wie man ein Dokument mit Aspose.Words for Java als PDF speichert](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Standardoptionen für Datenbeschriftungen in einem Diagramm festlegen](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}