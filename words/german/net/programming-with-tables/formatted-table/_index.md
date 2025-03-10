---
title: Formatierte Tabelle
linktitle: Formatierte Tabelle
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Tabellen in Word-Dokumenten erstellen und formatieren.
weight: 10
url: /de/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatierte Tabelle

## Einführung

Das programmgesteuerte Erstellen und Formatieren von Tabellen in Word-Dokumenten kann eine gewaltige Aufgabe sein, aber mit Aspose.Words für .NET wird es unkompliziert und handhabbar. In diesem Tutorial zeigen wir Ihnen, wie Sie mit Aspose.Words für .NET eine formatierte Tabelle in einem Word-Dokument erstellen. Wir behandeln alles, vom Einrichten Ihrer Umgebung bis zum Speichern Ihres Dokuments mit einer schön formatierten Tabelle.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET-Bibliothek: Laden Sie es herunter von[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio.
3. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.

## Namespaces importieren

Bevor Sie den eigentlichen Code schreiben, müssen Sie die erforderlichen Namespaces importieren:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zuerst müssen Sie den Pfad festlegen, in dem Ihr Dokument gespeichert wird.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie das Dokument speichern möchten.

## Schritt 2: Initialisieren Sie das Dokument und den DocumentBuilder

Initialisieren Sie jetzt ein neues Dokument und ein DocumentBuilder-Objekt.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Der`DocumentBuilder` ist eine Hilfsklasse, die den Prozess der Dokumenterstellung vereinfacht.

## Schritt 3: Starten Sie die Tabelle

 Als nächstes beginnen Sie mit der Erstellung der Tabelle mit dem`StartTable` Verfahren.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Um mit der Tabelle zu beginnen, ist das Einfügen einer Zelle erforderlich.

## Schritt 4: Tabellenweite Formatierung anwenden

Sie können Formatierungen anwenden, die sich auf die gesamte Tabelle auswirken. So können Sie beispielsweise den linken Einzug festlegen:

```csharp
table.LeftIndent = 20.0;
```

## Schritt 5: Formatieren Sie die Kopfzeile

Legen Sie Höhe, Ausrichtung und andere Eigenschaften für die Kopfzeile fest.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

In diesem Schritt heben wir die Kopfzeile hervor, indem wir eine Hintergrundfarbe, Schriftgröße und Ausrichtung festlegen.

## Schritt 6: Zusätzliche Kopfzellen einfügen

Fügen Sie weitere Zellen für die Kopfzeile ein:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Schritt 7: Formatieren Sie die Textzeilen

Nachdem Sie die Kopfzeile eingerichtet haben, formatieren Sie den Hauptteil der Tabelle:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Schritt 8: Körperzeilen einfügen

Fügen Sie die Textzeilen mit Inhalt ein:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Wiederholen Sie dies für weitere Zeilen:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Schritt 9: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Dadurch wird ein Word-Dokument mit der formatierten Tabelle erstellt und gespeichert.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie mit Aspose.Words für .NET eine gut formatierte Tabelle in einem Word-Dokument erstellen. Diese leistungsstarke Bibliothek erleichtert die programmgesteuerte Bearbeitung von Word-Dokumenten und spart Ihnen Zeit und Mühe.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zum programmgesteuerten Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten.

### Kann ich für unterschiedliche Reihen unterschiedliche Farben verwenden?
Ja, Sie können auf unterschiedliche Zeilen oder Zellen unterschiedliche Formatierungen, einschließlich Farben, anwenden.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET ist eine kostenpflichtige Bibliothek, aber Sie können eine[Kostenlose Testversion](https://releases.aspose.com/).

### Wie erhalte ich Unterstützung für Aspose.Words für .NET?
 Unterstützung erhalten Sie vom[Aspose-Community-Foren](https://forum.aspose.com/c/words/8).

### Kann ich mit Aspose.Words für .NET andere Dokumenttypen erstellen?
Ja, Aspose.Words für .NET unterstützt verschiedene Dokumentformate, darunter PDF, HTML und TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
