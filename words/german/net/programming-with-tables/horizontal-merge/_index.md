---
title: Horizontale Zusammenführung
linktitle: Horizontale Zusammenführung
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem ausführlichen Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET Zellen in einem Word-Dokument horizontal zusammenführen.
weight: 10
url: /de/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horizontale Zusammenführung

## Einführung

Hallo! Bereit, in die Welt von Aspose.Words für .NET einzutauchen? Heute werden wir uns mit einer äußerst nützlichen Funktion befassen: horizontales Zusammenführen in Tabellen. Das mag ein wenig technisch klingen, aber keine Sorge, ich kümmere mich darum. Am Ende dieses Tutorials sind Sie ein Profi darin, Zellen in Ihren Word-Dokumenten programmgesteuert zusammenzuführen. Also, krempeln wir die Ärmel hoch und legen los!

## Voraussetzungen

Bevor wir ins Detail gehen, müssen Sie einige Dinge vorbereitet haben:

1. Aspose.Words für .NET-Bibliothek: Wenn Sie dies noch nicht getan haben, laden Sie die Aspose.Words für .NET-Bibliothek herunter. Sie können sie herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine geeignete Entwicklungsumgebung wie beispielsweise Visual Studio eingerichtet haben.
3. Grundkenntnisse in C#: Grundkenntnisse der C#-Programmierung sind von Vorteil.

Sobald Sie diese sortiert haben, können Sie loslegen!

## Namespaces importieren

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass wir die erforderlichen Namespaces importiert haben. Stellen Sie sicher, dass Sie in Ihrem C#-Projekt Folgendes einschließen:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Gut, lassen Sie uns den Prozess des horizontalen Zusammenführens von Tabellenzellen in einem Word-Dokument mit Aspose.Words für .NET aufschlüsseln.

## Schritt 1: Einrichten Ihres Dokuments

 Als erstes müssen wir ein neues Word-Dokument erstellen und das`DocumentBuilder`:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Dieser Codeausschnitt erstellt ein neues Dokument und bereitet die`DocumentBuilder` zum Handeln.

## Schritt 2: Einsetzen der ersten Zelle

Als nächstes fügen wir die erste Zelle ein und markieren sie für die horizontale Zusammenführung:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Hier fügen wir eine neue Zelle ein und setzen deren`HorizontalMerge`Eigentum an`CellMerge.First`, was darauf hinweist, dass diese Zelle der Anfang einer zusammengeführte Zellsequenz ist.

## Schritt 3: Einfügen der verbundenen Zelle

Nun fügen wir die Zelle ein, die mit der vorherigen zusammengeführt werden soll:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Diese Zelle wird mit der vorherigen Zelle verbunden.`CellMerge.Previous` Beachten Sie, dass wir die Reihe mit beenden`builder.EndRow()`.

## Schritt 4: Einfügen nicht verbundener Zellen

Um den Unterschied zu veranschaulichen, fügen wir ein paar nicht verbundene Zellen ein:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Hier fügen wir zwei Zellen ohne horizontale Zusammenführung ein. Dies zeigt, wie sich Zellen verhalten, wenn sie nicht Teil einer zusammengeführten Sequenz sind.

## Schritt 5: Fertigstellen der Tabelle

Zum Schluss beenden wir die Tabelle und speichern das Dokument:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Dieser Codeausschnitt vervollständigt die Tabelle und speichert das Dokument im angegebenen Verzeichnis.

## Abschluss

Und da haben Sie es! Sie haben gerade die Kunst des horizontalen Zusammenführens von Zellen in einem Word-Dokument mit Aspose.Words für .NET gemeistert. Wenn Sie diese Schritte befolgen, können Sie problemlos komplexe Tabellenstrukturen erstellen. Experimentieren Sie weiter und erkunden Sie die Funktionen von Aspose.Words, um Ihre Dokumente so dynamisch und flexibel zu gestalten, wie Sie es benötigen. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert in .NET-Anwendungen zu erstellen, zu bearbeiten und zu bearbeiten.

### Kann ich mit Aspose.Words für .NET Zellen vertikal zusammenführen?
 Ja, Sie können Zellen auch vertikal zusammenführen, indem Sie das`CellFormat.VerticalMerge` Eigentum.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET bietet eine kostenlose Testversion, aber für die volle Funktionalität müssen Sie eine Lizenz erwerben. Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).

### Wie kann ich mehr über Aspose.Words für .NET erfahren?
 Sie können die ausführliche Dokumentation erkunden[Hier](https://reference.aspose.com/words/net/).

### Wo erhalte ich Support für Aspose.Words für .NET?
 Bei Fragen oder Problemen können Sie das Aspose-Supportforum besuchen[Hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
