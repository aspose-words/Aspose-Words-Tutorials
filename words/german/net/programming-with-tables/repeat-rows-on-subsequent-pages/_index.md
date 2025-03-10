---
title: Zeilen auf nachfolgenden Seiten wiederholen
linktitle: Zeilen auf nachfolgenden Seiten wiederholen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Word-Dokumente mit sich wiederholenden Tabellenkopfzeilen erstellen. Folgen Sie dieser Anleitung, um professionelle und ansprechende Dokumente zu erhalten.
weight: 10
url: /de/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zeilen auf nachfolgenden Seiten wiederholen

## Einführung

Das programmgesteuerte Erstellen eines Word-Dokuments kann eine gewaltige Aufgabe sein, insbesondere wenn Sie die Formatierung über mehrere Seiten hinweg beibehalten müssen. Haben Sie schon einmal versucht, eine Tabelle in Word zu erstellen, nur um festzustellen, dass sich Ihre Kopfzeilen auf den folgenden Seiten nicht wiederholen? Keine Angst! Mit Aspose.Words für .NET können Sie ganz einfach sicherstellen, dass sich Ihre Tabellenüberschriften auf jeder Seite wiederholen, was Ihren Dokumenten ein professionelles und elegantes Aussehen verleiht. In diesem Tutorial führen wir Sie anhand einfacher Codebeispiele und ausführlicher Erklärungen durch die Schritte, um dies zu erreichen. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Sie können es herunterladen[Hier](https://releases.aspose.com/words/net/).
2. .NET Framework muss auf Ihrem Computer installiert sein.
3. Visual Studio oder jede andere IDE, die .NET-Entwicklung unterstützt.
4. Grundlegende Kenntnisse der C#-Programmierung.

Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert und Ihre Entwicklungsumgebung eingerichtet haben, bevor Sie fortfahren.

## Namespaces importieren

Zu Beginn müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Fügen Sie oben in Ihrer C#-Datei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Diese Namespaces umfassen die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten und -Tabellen erforderlich sind.

## Schritt 1: Initialisieren Sie das Dokument

 Erstellen wir zunächst ein neues Word-Dokument und ein`DocumentBuilder` um unseren Tisch zu konstruieren.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Dieser Code initialisiert ein neues Dokument und ein`DocumentBuilder` Objekt, das beim Aufbau der Dokumentstruktur hilft.

## Schritt 2: Tabelle starten und Kopfzeilen definieren

Als nächstes starten wir die Tabelle und definieren die Kopfzeilen, die wir auf den Folgeseiten wiederholen möchten.

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

 Hier beginnen wir eine neue Tabelle, setzen die`HeadingFormat`Eigentum an`true` um anzugeben, dass es sich bei den Zeilen um Überschriften handelt, und um die Ausrichtung und Breite der Zellen zu definieren.

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

 Diese Schleife fügt 50 Datenzeilen in die Tabelle ein, mit jeweils zwei Spalten in jeder Zeile.`HeadingFormat` ist eingestellt auf`false` für diese Zeilen, da es sich nicht um Kopfzeilen handelt.

## Schritt 4: Speichern Sie das Dokument

Abschließend speichern wir das Dokument im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Dadurch wird das Dokument unter dem angegebenen Namen in Ihrem Dokumentverzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen können Sie mit Aspose.Words für .NET ein Word-Dokument mit Tabellen erstellen, die auf den nachfolgenden Seiten wiederkehrende Kopfzeilen aufweisen. Dies verbessert nicht nur die Lesbarkeit Ihrer Dokumente, sondern sorgt auch für ein einheitliches und professionelles Erscheinungsbild. Probieren Sie es jetzt in Ihren Projekten aus!

## Häufig gestellte Fragen

### Kann ich die Kopfzeilen weiter anpassen?
 Ja, Sie können zusätzliche Formatierungen auf die Kopfzeilen anwenden, indem Sie die Eigenschaften von`ParagraphFormat`, `RowFormat` , Und`CellFormat`.

### Ist es möglich, der Tabelle weitere Spalten hinzuzufügen?
 Absolut! Sie können so viele Spalten wie nötig hinzufügen, indem Sie weitere Zellen in den`InsertCell` Verfahren.

### Wie kann ich dafür sorgen, dass sich andere Zeilen auf den Folgeseiten wiederholen?
 Um eine Zeile zu wiederholen, setzen Sie die`RowFormat.HeadingFormat`Eigentum an`true` für diese bestimmte Zeile.

### Kann ich diese Methode für vorhandene Tabellen in einem Dokument verwenden?
 Ja, Sie können vorhandene Tabellen ändern, indem Sie auf sie zugreifen über`Document` Objekt und Anwenden einer ähnlichen Formatierung.

### Welche anderen Optionen zur Tabellenformatierung sind in Aspose.Words für .NET verfügbar?
 Aspose.Words für .NET bietet eine breite Palette an Optionen zur Tabellenformatierung, einschließlich Zellzusammenführung, Rahmeneinstellungen und Tabellenausrichtung. Schauen Sie sich die[Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
