---
category: general
date: 2026-10-07
description: Erfahren Sie, wie Sie in Word ein Kreisdiagramm erstellen, Datenreihen
  hinzufügen und das Diagramm mit Java als PNG speichern. Folgen Sie der Schritt‑für‑Schritt‑Anleitung
  für schnelle Ergebnisse.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: de
lastmod: 2026-10-07
og_description: 'Erstelle schnell ein Kreisdiagramm in Word: Dieses Tutorial zeigt,
  wie man Datenreihen hinzufügt, das Diagramm generiert und das Word‑Diagramm als
  Bild (PNG) speichert. Folge dem vollständigen Codebeispiel.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Ein Kreisdiagramm in Word erstellen und als PNG exportieren – Anleitung
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Wie man ein Kreisdiagramm in Word erstellt und als PNG speichert
url: /de/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm in Word erstellt und als PNG speichert

Wenn Sie **Kreisdiagramme** in einer Microsoft Word‑Datei erstellen müssen, zeigt Ihnen diese Anleitung genau, wie Sie das mit Java erledigen. Sie lernen außerdem, wie Sie **Datenreihen** zum Diagramm **hinzufügen** und **das Diagramm als PNG speichern**, sodass die Visualisierung außerhalb von Word wiederverwendet werden kann.

Ein Diagramm direkt in einem Dokument zu erzeugen, erspart Ihnen das Exportieren von Daten in ein separates Grafik‑Tool. Am Ende dieses Tutorials verfügen Sie über eine voll funktionsfähige Word‑Datei, die ein Kreisdiagramm und ein entsprechendes PNG‑Bild auf der Festplatte enthält.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert.
* Die **GroupDocs.Viewer for Java** (oder eine kompatible Bibliothek, die die Klassen `Document`, `Chart`, `ChartType` und `ImageSaveOptions` bereitstellt).
* Ein Maven‑ oder Gradle‑Projekt, in dem Sie die Bibliotheksabhängigkeit hinzufügen können.
* Ein Eingabe‑Word‑Dokument (`input.docx`) in einem Ordner, den Sie im Code referenzieren können.

Wenn Sie Maven verwenden, fügen Sie die Abhängigkeit hinzu (ersetzen Sie `VERSION` durch die neueste Version):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Wie man ein Kreisdiagramm in Word erstellt

Der Kern der Lösung dreht sich um drei Aktionen:

1. Laden der Quell‑`.docx`‑Datei.
2. **Datenreihen** zu einem neuen `Chart`‑Objekt vom Typ `PIE` hinzufügen.
3. **Diagramm als PNG speichern**, sodass Sie eine Bilddatei neben dem Word‑Dokument erhalten.

Jeder Schritt wird im Folgenden detailliert erklärt, gefolgt vom genauen Java‑Code, den Sie benötigen.

### Schritt 1: Quell‑Dokument laden

Sie müssen die Word‑Datei öffnen, die das Diagramm enthalten soll. Die Klasse `Document` liest den `.docx`‑Inhalt in den Speicher.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Warum das wichtig ist*: Das Laden des Dokuments erzeugt ein veränderbares Modell. Alle nachfolgenden Diagramm‑Operationen ändern diese In‑Memory‑Repräsentation, die Sie später wieder auf die Festplatte schreiben.

### Schritt 2: Datenreihen zum Diagramm hinzufügen

Das Erstellen eines **Kreisdiagramms** beginnt mit einer `Chart`‑Instanz. Der Konstruktor erhält das übergeordnete `Document` und den Diagrammtyp (`ChartType.PIE`). Nachdem das Diagrammobjekt existiert, füllen Sie es mit numerischen Werten und optionalen Beschriftungen.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Warum das wichtig ist*: Die Methode `add` **fügt Datenreihen** zum Diagramm hinzu. Jeder Eintrag in `values` wird zu einem Stück des Kreises, während `categories` die Legenden‑Beschriftungen bereitstellen. Sie können beliebig viele Punkte angeben; die Bibliothek berechnet die Winkel der Stücke automatisch.

### Schritt 3: Diagramm als PNG speichern

Sobald das Diagramm Teil des Dokuments ist, können Sie die visuelle Darstellung exportieren. Die Methode `save` des zugrunde liegenden Diagrammobjekts schreibt eine PNG‑Datei ins Dateisystem.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Warum das wichtig ist*: Das Speichern des Diagramms als PNG liefert ein Rasterbild, das in Webseiten, E‑Mails oder Berichten eingebettet werden kann, ohne dass die ursprüngliche Word‑Datei benötigt wird. Das Objekt `ImageSaveOptions` ermöglicht die Steuerung von Format, Auflösung und anderen Export‑Einstellungen.

## Kreisdiagramm in Word erzeugen – Aussehen anpassen

Über die grundlegenden Schritte hinaus möchten Sie möglicherweise Farben, Titel oder Datenbeschriftungen anpassen. Die meisten Bibliotheken stellen ein `ChartOptions`‑ oder ähnliches Objekt bereit. Hier ein kurzes Beispiel, das einen Titel hinzufügt und die Farben der Stücke ändert:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Diese Anpassungen sind optional, zeigen jedoch, wie Sie **ein Kreisdiagramm in Word erzeugen** können, das zu Ihrem Branding passt.

## Word‑Diagramm als Bild speichern – alternative Ansätze

Wenn Sie nur das Bild benötigen und nicht das Diagramm im Dokument, können Sie das Einfügen der Diagramm‑Form in die Word‑Datei überspringen und nach der Erstellung des Diagramms direkt die Methode `save` aufrufen. Der Code bleibt unverändert; Sie lassen einfach die Schritte weg, die das Diagramm zum Dokumentenkörper hinzufügen.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Diese Technik ist nützlich, wenn Sie viele Diagramme in einem Batch‑Prozess erzeugen und nur an der PNG‑Ausgabe interessiert sind.

## Vollständiges ausführbares Beispiel

Kopieren Sie die folgende Klasse in Ihr Projekt, passen Sie die Dateipfade an und führen Sie sie aus. Das Programm wird:

1. `input.docx` laden.
2. **Ein Kreisdiagramm erstellen**, **Datenreihen hinzufügen** und es in das Dokument einbetten.
3. **Das Diagramm als PNG speichern** (`radial.png`).
4. Die modifizierte Word‑Datei als `output.docx` speichern.



## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Word‑Streudiagramm mit Aspose.Words für .NET erstellen](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Säulendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}