---
title: Formrevision
linktitle: Formrevision
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem umfassenden Handbuch, wie Sie mit Aspose.Words für .NET Formrevisionen in Word-Dokumenten handhaben. Meistern Sie das Verfolgen von Änderungen, das Einfügen von Formen und mehr.
weight: 10
url: /de/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formrevision

## Einführung

Das programmgesteuerte Bearbeiten von Word-Dokumenten kann eine gewaltige Aufgabe sein, insbesondere wenn es um die Handhabung von Formen geht. Egal, ob Sie Berichte erstellen, Vorlagen entwerfen oder einfach die Dokumenterstellung automatisieren, die Fähigkeit, Formrevisionen zu verfolgen und zu verwalten, ist entscheidend. Aspose.Words für .NET bietet eine leistungsstarke API, um diesen Prozess nahtlos und effizient zu gestalten. In diesem Tutorial werden wir uns mit den Besonderheiten der Überarbeitung von Formen in Word-Dokumenten befassen und sicherstellen, dass Sie über die Tools und Kenntnisse verfügen, um Ihre Dokumente problemlos zu verwalten.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Sie sollten eine Entwicklungsumgebung wie beispielsweise Visual Studio eingerichtet haben.
- Grundlegende Kenntnisse in C#: Vertrautheit mit der Programmiersprache C# und den grundlegenden Konzepten der objektorientierten Programmierung.
- Word-Dokument: Ein Word-Dokument zum Arbeiten oder Sie können während des Tutorials eines erstellen.

## Namespaces importieren

Importieren wir zunächst die erforderlichen Namespaces. Diese ermöglichen uns den Zugriff auf die Klassen und Methoden, die für die Verarbeitung von Word-Dokumenten und -Formen erforderlich sind.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Schritt 1: Einrichten Ihres Dokumentverzeichnisses

Bevor wir mit der Arbeit mit Formen beginnen, müssen wir den Pfad zu unserem Dokumentverzeichnis definieren. Hier speichern wir unsere geänderten Dokumente.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Neues Dokument erstellen

Lassen Sie uns ein neues Word-Dokument erstellen, in das wir Formen einfügen und überarbeiten.

```csharp
Document doc = new Document();
```

## Schritt 3: Einfügen einer Inline-Form

Wir beginnen damit, eine Inline-Form in unser Dokument einzufügen, ohne Revisionen zu verfolgen. Eine Inline-Form ist eine Form, die mit dem Text fließt.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Schritt 4: Beginnen Sie mit der Nachverfolgung von Revisionen

Um Änderungen in unserem Dokument nachzuverfolgen, müssen wir die Revisionsverfolgung aktivieren. Dies ist wichtig, um an Formen vorgenommene Änderungen zu identifizieren.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Schritt 5: Einfügen einer weiteren Form mit Revisionen

Nachdem die Revisionsverfolgung aktiviert ist, fügen wir eine weitere Form ein. Dieses Mal werden alle Änderungen verfolgt.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Schritt 6: Abrufen und Ändern von Formen

Wir können alle Formen im Dokument abrufen und nach Bedarf ändern. Hier holen wir die Formen und entfernen die erste.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Schritt 7: Speichern des Dokuments

Nachdem wir unsere Änderungen vorgenommen haben, müssen wir das Dokument speichern. Dadurch wird sichergestellt, dass alle Überarbeitungen und Änderungen gespeichert werden.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Schritt 8: Handhabung von Formverschiebungsrevisionen

Wenn eine Form verschoben wird, verfolgt Aspose.Words dies als Überarbeitung. Das bedeutet, dass es zwei Instanzen der Form gibt: eine an ihrem ursprünglichen Standort und eine an ihrem neuen Standort.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für .NET Formrevisionen in Word-Dokumenten handhaben. Egal, ob Sie Dokumentvorlagen verwalten, Berichte automatisieren oder einfach nur Änderungen nachverfolgen, diese Fähigkeiten sind von unschätzbarem Wert. Indem Sie dieser Schritt-für-Schritt-Anleitung folgen, beherrschen Sie nicht nur die Grundlagen, sondern gewinnen auch Einblick in fortgeschrittenere Techniken zur Dokumenthandhabung.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert mit C# zu erstellen, zu ändern und zu konvertieren.

### Kann ich an anderen Elementen in einem Word-Dokument vorgenommene Änderungen verfolgen?
Ja, Aspose.Words für .NET unterstützt die Nachverfolgung von Änderungen an verschiedenen Elementen, einschließlich Text, Tabellen und mehr.

### Wie kann ich eine kostenlose Testversion von Aspose.Words für .NET erhalten?
 Sie können eine kostenlose Testversion von Aspose.Words für .NET erhalten[Hier](https://releases.aspose.com/).

### Ist es möglich, Revisionen programmgesteuert anzunehmen oder abzulehnen?
Ja, Aspose.Words für .NET bietet Methoden zum programmgesteuerten Akzeptieren oder Ablehnen von Revisionen.

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen außer C# verwenden?
Absolut! Aspose.Words für .NET kann mit jeder .NET-Sprache verwendet werden, einschließlich VB.NET und F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
