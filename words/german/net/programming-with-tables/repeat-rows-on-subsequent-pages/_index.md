---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Word-Dokumente mit sich wiederholenden Tabellenkopfzeilen erstellen. Folgen Sie dieser Anleitung für professionelle und ansprechende Dokumente."
"linktitle": "Zeilen auf nachfolgenden Seiten wiederholen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Zeilen auf nachfolgenden Seiten wiederholen"
"url": "/de/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zeilen auf nachfolgenden Seiten wiederholen

## Einführung

Das programmgesteuerte Erstellen eines Word-Dokuments kann eine anspruchsvolle Aufgabe sein, insbesondere wenn die Formatierung über mehrere Seiten hinweg beibehalten werden muss. Haben Sie schon einmal versucht, eine Tabelle in Word zu erstellen, nur um dann festzustellen, dass Ihre Kopfzeilen auf den folgenden Seiten nicht wiederholt werden? Keine Sorge! Mit Aspose.Words für .NET können Sie ganz einfach sicherstellen, dass Ihre Tabellenüberschriften auf jeder Seite wiederholt werden und Ihren Dokumenten so ein professionelles und elegantes Aussehen verleihen. In diesem Tutorial führen wir Sie anhand einfacher Codebeispiele und ausführlicher Erklärungen durch die einzelnen Schritte. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
2. .NET Framework auf Ihrem Computer installiert.
3. Visual Studio oder jede andere IDE, die die .NET-Entwicklung unterstützt.
4. Grundlegende Kenntnisse der C#-Programmierung.

Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert und Ihre Entwicklungsumgebung eingerichtet haben, bevor Sie fortfahren.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Fügen Sie am Anfang Ihrer C#-Datei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Diese Namespaces umfassen die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten und -Tabellen erforderlich sind.

## Schritt 1: Initialisieren des Dokuments

Zuerst erstellen wir ein neues Word-Dokument und ein `DocumentBuilder` um unseren Tisch zu konstruieren.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Dieser Code initialisiert ein neues Dokument und ein `DocumentBuilder` Objekt, das beim Aufbau der Dokumentstruktur hilft.

## Schritt 2: Tabelle starten und Kopfzeilen definieren

Als nächstes beginnen wir mit der Tabelle und definieren die Kopfzeilen, die wir auf den folgenden Seiten wiederholen möchten.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

Hier beginnen wir eine neue Tabelle, setzen die `HeadingFormat` Eigentum zu `true` um anzugeben, dass es sich bei den Zeilen um Überschriften handelt, und um die Ausrichtung und Breite der Zellen zu definieren.

## Schritt 3: Datenzeilen zur Tabelle hinzufügen

Jetzt fügen wir unserer Tabelle mehrere Datenzeilen hinzu. Diese Zeilen werden auf nachfolgenden Seiten nicht wiederholt.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

Diese Schleife fügt 50 Datenzeilen in die Tabelle ein, mit jeweils zwei Spalten pro Zeile. Die `HeadingFormat` ist eingestellt auf `false` für diese Zeilen, da es sich nicht um Kopfzeilen handelt.

## Schritt 4: Speichern Sie das Dokument

Abschließend speichern wir das Dokument im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Dadurch wird das Dokument unter dem angegebenen Namen in Ihrem Dokumentverzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen erstellen Sie mit Aspose.Words für .NET ein Word-Dokument mit Tabellen und sich wiederholenden Kopfzeilen auf den Folgeseiten. Das verbessert nicht nur die Lesbarkeit Ihrer Dokumente, sondern sorgt auch für ein einheitliches und professionelles Erscheinungsbild. Probieren Sie es gleich in Ihren Projekten aus!

## Häufig gestellte Fragen

### Kann ich die Kopfzeilen weiter anpassen?
Ja, Sie können zusätzliche Formatierungen auf die Kopfzeilen anwenden, indem Sie die Eigenschaften von `ParagraphFormat`, `RowFormat`, Und `CellFormat`.

### Ist es möglich, der Tabelle weitere Spalten hinzuzufügen?
Absolut! Sie können beliebig viele Spalten hinzufügen, indem Sie weitere Zellen innerhalb der `InsertCell` Verfahren.

### Wie kann ich dafür sorgen, dass andere Zeilen auf den folgenden Seiten wiederholt werden?
Um eine Zeile zu wiederholen, legen Sie die `RowFormat.HeadingFormat` Eigentum zu `true` für diese bestimmte Zeile.

### Kann ich diese Methode für vorhandene Tabellen in einem Dokument verwenden?
Ja, Sie können vorhandene Tabellen ändern, indem Sie auf sie zugreifen über `Document` Objekt und Anwenden einer ähnlichen Formatierung.

### Welche anderen Optionen zur Tabellenformatierung sind in Aspose.Words für .NET verfügbar?
Aspose.Words für .NET bietet eine breite Palette an Optionen zur Tabellenformatierung, einschließlich Zellenzusammenführung, Rahmeneinstellungen und Tabellenausrichtung. Schauen Sie sich die [Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}