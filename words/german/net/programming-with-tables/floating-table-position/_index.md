---
title: Schwebende Tischposition
linktitle: Schwebende Tischposition
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET die schwebende Position von Tabellen in Word-Dokumenten steuern.
weight: 10
url: /de/net/programming-with-tables/floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schwebende Tischposition

## Einführung

Sind Sie bereit, in die Welt der Manipulation von Tabellenpositionen in Word-Dokumenten mit Aspose.Words für .NET einzutauchen? Schnall dich an, denn heute werden wir erkunden, wie man die schwebende Position von Tabellen ganz einfach steuern kann. Wir machen Sie im Handumdrehen zu einem Zauberer der Tabellenpositionierung!

## Voraussetzungen

Bevor wir uns auf diese aufregende Reise begeben, stellen wir sicher, dass wir alles haben, was wir brauchen:

1. Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version haben. Wenn nicht,[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. .NET Framework: Stellen Sie sicher, dass Ihre Entwicklungsumgebung mit .NET eingerichtet ist.
3. Entwicklungsumgebung: Visual Studio oder eine bevorzugte IDE.
4. Ein Word-Dokument: Halten Sie ein Word-Dokument bereit, das eine Tabelle enthält.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr .NET-Projekt importieren. Hier ist der Codeausschnitt, den Sie oben in Ihre C#-Datei einfügen müssen:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt-für-Schritt-Anleitung

Lassen Sie uns den Prozess nun in einfache, leicht verständliche Schritte unterteilen.

## Schritt 1: Dokument laden

Als Erstes müssen Sie Ihr Word-Dokument laden. Hier befindet sich Ihre Tabelle.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Stellen Sie sich vor, Ihr Word-Dokument ist eine Leinwand und Ihre Tabelle ist ein Kunstwerk darauf. Unser Ziel ist es, dieses Kunstwerk genau dort auf der Leinwand zu positionieren, wo wir es haben möchten.

## Schritt 2: Zugriff auf die Tabelle

Als nächstes müssen wir auf die Tabelle im Dokument zugreifen. Normalerweise arbeiten Sie mit der ersten Tabelle im Hauptteil des Dokuments.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Stellen Sie sich diesen Schritt so vor, als würden Sie die Tabelle, mit der Sie arbeiten möchten, in einem physischen Dokument lokalisieren. Sie müssen genau wissen, wo sie sich befindet, um Änderungen vornehmen zu können.

## Schritt 3: Horizontale Position festlegen

Legen wir nun die horizontale Position der Tabelle fest. Diese bestimmt, wie weit vom linken Rand des Dokuments die Tabelle platziert wird.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

 Stellen Sie sich das so vor, als würden Sie die Tabelle horizontal über Ihr Dokument verschieben.`AbsoluteHorizontalDistance` ist der genaue Abstand vom linken Rand.

## Schritt 4: Vertikale Ausrichtung festlegen

Wir müssen auch die vertikale Ausrichtung der Tabelle festlegen. Dadurch wird die Tabelle vertikal innerhalb des umgebenden Textes zentriert.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Stellen Sie sich vor, Sie möchten ein Bild an die Wand hängen. Sie möchten sicherstellen, dass es vertikal zentriert ist, damit es optisch ansprechend aussieht. Mit diesem Schritt erreichen Sie das.

## Schritt 5: Speichern Sie das geänderte Dokument

Speichern Sie abschließend nach dem Positionieren der Tabelle Ihr geändertes Dokument.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Dies ist so, als ob Sie in Ihrem bearbeiteten Dokument auf „Speichern“ klicken. Alle Ihre Änderungen bleiben nun erhalten.

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie die schwebende Position von Tabellen in einem Word-Dokument mit Aspose.Words für .NET steuern. Mit diesen Fähigkeiten können Sie sicherstellen, dass Ihre Tabellen perfekt positioniert sind, um die Lesbarkeit und Ästhetik Ihrer Dokumente zu verbessern. Experimentieren Sie weiter und erkunden Sie die umfangreichen Funktionen von Aspose.Words für .NET.

## Häufig gestellte Fragen

### Kann ich den vertikalen Abstand der Tabelle vom oberen Seitenrand einstellen?

 Ja, Sie können die`AbsoluteVerticalDistance` , um den vertikalen Abstand der Tabelle vom oberen Seitenrand festzulegen.

### Wie richte ich die Tabelle rechts im Dokument aus?

 Um die Tabelle rechtsbündig auszurichten, können Sie die`HorizontalAlignment` Eigenschaft der Tabelle zu`HorizontalAlignment.Right`.

### Ist es möglich, mehrere Tabellen im selben Dokument unterschiedlich zu positionieren?

 Absolut! Sie können auf mehrere Tabellen einzeln zugreifen und Positionen für diese festlegen, indem Sie die`Tables` Sammlung im Dokument.

### Kann ich die relative Positionierung für die horizontale Ausrichtung verwenden?

Ja, Aspose.Words unterstützt die relative Positionierung sowohl für horizontale als auch vertikale Ausrichtungen mit Eigenschaften wie`RelativeHorizontalAlignment`.

### Unterstützt Aspose.Words schwebende Tabellen in verschiedenen Abschnitten eines Dokuments?

Ja, Sie können schwebende Tabellen in verschiedenen Abschnitten positionieren, indem Sie in Ihrem Dokument auf den jeweiligen Abschnitt und seine Tabellen zugreifen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
