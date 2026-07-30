---
date: 2025-11-28
description: Erfahren Sie, wie Sie Zellrahmen ändern und Tabellen mit Aspose.Words
  für Java formatieren. Diese Schritt‑für‑Schritt‑Anleitung behandelt das Festlegen
  von Rahmen, das Anwenden des Stils für die erste Spalte, das automatische Anpassen
  des Tabelleninhalts und das Anwenden von Tabellenstilen.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Wie man Zellrahmen in Tabellen ändert – Aspose.Words für Java
url: /de/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Zellränder in Tabellen ändert – Aspose.Words für Java

## Einführung

Wenn es um die Dokumentformatierung geht, spielen Tabellen eine entscheidende Rolle, und **zu wissen, wie man Zellränder ändert** ist unerlässlich, um klare, professionelle Layouts zu erstellen. Wenn Sie mit Java und Aspose.Words entwickeln, haben Sie bereits ein leistungsstarkes Toolkit zur Hand. In diesem Tutorial führen wir Sie durch den gesamten Prozess der Tabellenformatierung, dem Ändern von Zellrändern, dem Anwenden des *First Column Style* und der Nutzung von *Auto‑Fit Table Contents*, um Ihre Dokumente poliert aussehen zu lassen.

## Schnelle Antworten
- **Was ist die primäre Klasse zum Erstellen von Tabellen?** `DocumentBuilder` erstellt Tabellen und Zellen programmgesteuert.  
- **Wie ändere ich die Randstärke einer einzelnen Zelle?** Verwenden Sie `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Kann ich einen vordefinierten Tabellenstil anwenden?** Ja – rufen Sie `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` auf.  
- **Welche Methode passt eine Tabelle automatisch an ihren Inhalt an?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Benötige ich eine Lizenz für den Produktionseinsatz?** Eine gültige Aspose.Words‑Lizenz ist für die Nutzung außerhalb der Testphase erforderlich.

## Was bedeutet „Zellränder ändern“ in Aspose.Words?

Zellränder zu ändern bedeutet, die visuellen Linien, die Zellen trennen, anzupassen – Farbe, Breite und Linienstil. Aspose.Words stellt eine umfangreiche API bereit, mit der Sie diese Eigenschaften auf Tabellen‑, Zeilen‑ oder einzelner Zellebene einstellen können, sodass Sie die Darstellung Ihrer Dokumente fein steuern können.

## Warum Aspose.Words für Java für die Tabellenformatierung verwenden?

- **Konsistentes Aussehen über Plattformen hinweg** – derselbe Styling‑Code funktioniert unter Windows, Linux und macOS.  
- **Keine Abhängigkeit von Microsoft Word** – Erzeugen oder Ändern von Dokumenten serverseitig.  
- **Umfangreiche Stilbibliothek** – integrierte Tabellenstile (z. B. *First Column Style*) und volle Auto‑Fit‑Funktionen.  

## Voraussetzungen

1. **Java Development Kit (JDK) 8+** – stellen Sie sicher, dass `java` in Ihrem PATH ist.  
2. **IDE** – IntelliJ IDEA, Eclipse oder ein beliebiger Editor Ihrer Wahl.  
3. **Aspose.Words for Java** – laden Sie das neueste JAR von der [official site](https://releases.aspose.com/words/java/) herunter.  
4. **Grundlegende Java‑Kenntnisse** – Sie sollten in der Lage sein, ein Maven/Gradle‑Projekt zu erstellen und externe JARs hinzuzufügen.

## Pakete importieren

Um mit Tabellen zu arbeiten, benötigen Sie die Kernklassen von Aspose.Words:

```java
import com.aspose.words.*;
```

Dieser einzelne Import gibt Ihnen Zugriff auf `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` und viele weitere Hilfsmittel.

## Wie man Zellränder ändert

Im Folgenden erstellen wir eine einfache Tabelle, ändern ihre Gesamtränder und passen anschließend einzelne Zellen individuell an.

### Schritt 1: Ein neues Dokument laden

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Schritt 2: Tabelle erstellen und globale Ränder festlegen

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Schritt 3: Ränder einer einzelnen Zelle ändern

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Was der Code macht
- **Globale Ränder** – `table.setBorders` gibt der gesamten Tabelle eine 2‑Punkt schwarze Linie.  
- **Zellschattierung** – Zeigt, wie einzelne Zellen (rot & grün) eingefärbt werden.  
- **Benutzerdefinierte Zellränder** – Die dritte Zelle erhält einen 4‑Punkt Rand auf allen Seiten, wodurch sie hervorsticht.

## Anwenden von Tabellenstilen (einschließlich First Column Style)

Tabellenstile ermöglichen es, ein einheitliches Aussehen mit einem einzigen Aufruf zu erzielen. Wir zeigen außerdem, wie Sie das *First Column Style* aktivieren und die Tabelle automatisch an den Inhalt anpassen.

### Schritt 4: Ein neues Dokument für das Styling erstellen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Schritt 5: Einen vordefinierten Stil anwenden und First Column Formatting aktivieren

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Schritt 6: Tabelle mit Daten füllen

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Warum das wichtig ist
- **Style‑Identifier** – `MEDIUM_SHADING_1_ACCENT_1` verleiht der Tabelle ein sauberes, schattiertes Aussehen.  
- **First column style** – Das Hervorheben der ersten Spalte verbessert die Lesbarkeit, besonders in Berichten.  
- **Zeilenbänder** – Wechselnde Zeilenfarben erleichtern das Lesen großer Tabellen.  
- **Auto‑Fit** – Stellt sicher, dass die Tabellenbreite sich dem Inhalt anpasst und abgeschnittener Text vermieden wird.

## Häufige Probleme & Fehlerbehebung

| Problem | Typische Ursache | Schnelle Lösung |
|---------|------------------|-----------------|
| Ränder werden nicht angezeigt | Verwendung von `clearFormatting()` nach dem Festlegen der Ränder | Ränder **nach** dem Löschen der Formatierung setzen oder erneut anwenden. |
| Schattierung wird bei zusammengeführten Zellen ignoriert | Schattierung vor dem Zusammenführen angewendet | Schattierung **nach** dem Zusammenführen der Zellen anwenden. |
| Tabellenbreite überschreitet Seitenränder | Kein Auto‑Fit angewendet | Rufen Sie `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` auf oder setzen Sie eine feste Breite. |
| Stil wird nicht angewendet | Falscher `StyleIdentifier`‑Wert | Stellen Sie sicher, dass der Identifier in der von Ihnen verwendeten Aspose.Words‑Version existiert. |

## Häufig gestellte Fragen

**F: Kann ich benutzerdefinierte Tabellenstile verwenden, die nicht in den Standardoptionen enthalten sind?**  
A: Ja, Sie können benutzerdefinierte Stile programmgesteuert erstellen und anwenden. Siehe die [Aspose.Words‑Dokumentation](https://reference.aspose.com/words/java/) für Details.

**F: Wie kann ich bedingte Formatierung auf Zellen anwenden?**  
A: Verwenden Sie reguläre Java‑Logik, um Zellwerte zu prüfen, und rufen Sie dann die entsprechenden Formatierungsmethoden auf (z. B. Hintergrundfarbe ändern, wenn ein Wert einen Schwellenwert überschreitet).

**F: Ist es möglich, zusammengeführte Zellen genauso zu formatieren wie reguläre Zellen?**  
A: Absolut. Nach dem Zusammenführen von Zellen können Sie Schattierung oder Ränder mit denselben `CellFormat`‑APIs anwenden.

**F: Was ist, wenn die Tabelle dynamisch basierend auf Benutzereingaben die Größe ändern soll?**  
A: Passen Sie die Spaltenbreiten an oder rufen Sie `autoFit` erneut auf, nachdem neue Daten eingefügt wurden, um das Layout neu zu berechnen.

**F: Wo finde ich weitere Beispiele für Tabellenstile?**  
A: Die offizielle [Aspose.Words API‑Dokumentation](https://reference.aspose.com/words/java/) enthält eine umfassende Sammlung von Beispielen.

## Fazit

Sie verfügen jetzt über ein komplettes Werkzeugset, um **Zellränder zu ändern**, den *First Column Style* anzuwenden und **Auto‑Fit Table Contents** mit Aspose.Words für Java zu nutzen. Durch das Beherrschen dieser Techniken können Sie Dokumente erstellen, die sowohl datenreich als auch optisch ansprechend sind – ideal für Berichte, Rechnungen und jede andere geschäftskritische Ausgabe.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Zuletzt aktualisiert:** 2025-11-28  
**Getestet mit:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Autor:** Aspose