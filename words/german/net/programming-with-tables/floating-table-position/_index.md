---
"description": "Erfahren Sie in unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie die schwebende Position von Tabellen in Word-Dokumenten mit Aspose.Words für .NET steuern."
"linktitle": "Schwebende Tischposition"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Schwebende Tischposition"
"url": "/de/net/programming-with-tables/floating-table-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Schwebende Tischposition

## Einführung

Sind Sie bereit, mit Aspose.Words für .NET in die Welt der Tabellenpositionsmanipulation in Word-Dokumenten einzutauchen? Schnall dich an, denn heute zeigen wir dir, wie du die schwebende Position von Tabellen ganz einfach steuern kannst. Wir machen dich im Handumdrehen zum Tabellenpositionierungs-Experten!

## Voraussetzungen

Bevor wir uns auf diese aufregende Reise begeben, stellen wir sicher, dass wir alles haben, was wir brauchen:

1. Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version haben. Wenn nicht, [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. .NET Framework: Stellen Sie sicher, dass Ihre Entwicklungsumgebung mit .NET eingerichtet ist.
3. Entwicklungsumgebung: Visual Studio oder eine beliebige bevorzugte IDE.
4. Ein Word-Dokument: Halten Sie ein Word-Dokument bereit, das eine Tabelle enthält.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr .NET-Projekt importieren. Hier ist der Codeausschnitt, den Sie am Anfang Ihrer C#-Datei einfügen müssen:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt-für-Schritt-Anleitung

Lassen Sie uns den Prozess nun in einfache, verständliche Schritte unterteilen.

## Schritt 1: Laden Sie das Dokument

Zuerst müssen Sie Ihr Word-Dokument laden. Hier befindet sich Ihre Tabelle.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Stellen Sie sich vor, Ihr Word-Dokument ist eine Leinwand und Ihre Tabelle ein Kunstwerk darauf. Unser Ziel ist es, dieses Kunstwerk genau an der gewünschten Stelle auf der Leinwand zu positionieren.

## Schritt 2: Zugriff auf die Tabelle

Als Nächstes müssen wir auf die Tabelle im Dokument zugreifen. Normalerweise arbeiten Sie mit der ersten Tabelle im Hauptteil des Dokuments.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Stellen Sie sich diesen Schritt so vor, als würden Sie die Tabelle, mit der Sie arbeiten möchten, in einem physischen Dokument suchen. Sie müssen genau wissen, wo sie sich befindet, um Änderungen vornehmen zu können.

## Schritt 3: Horizontale Position einstellen

Legen wir nun die horizontale Position der Tabelle fest. Diese bestimmt, wie weit vom linken Rand des Dokuments die Tabelle platziert wird.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

Stellen Sie sich das so vor, als würden Sie die Tabelle horizontal über Ihr Dokument verschieben. `AbsoluteHorizontalDistance` ist der genaue Abstand vom linken Rand.

## Schritt 4: Vertikale Ausrichtung festlegen

Wir müssen auch die vertikale Ausrichtung der Tabelle festlegen. Dadurch wird die Tabelle vertikal im umgebenden Text zentriert.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Stellen Sie sich vor, Sie hängen ein Bild an die Wand. Aus ästhetischen Gründen möchten Sie sicherstellen, dass es vertikal zentriert ist. Mit diesem Schritt erreichen Sie dies.

## Schritt 5: Speichern des geänderten Dokuments

Speichern Sie abschließend nach dem Positionieren der Tabelle Ihr geändertes Dokument.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Dies entspricht dem Klicken auf „Speichern“ in Ihrem bearbeiteten Dokument. Alle Ihre Änderungen bleiben nun erhalten.

## Abschluss

Und da haben Sie es! Sie haben gelernt, die schwebende Position von Tabellen in einem Word-Dokument mit Aspose.Words für .NET zu steuern. Mit diesen Kenntnissen können Sie sicherstellen, dass Ihre Tabellen perfekt positioniert sind, um die Lesbarkeit und Ästhetik Ihrer Dokumente zu verbessern. Experimentieren Sie weiter und entdecken Sie die umfangreichen Möglichkeiten von Aspose.Words für .NET.

## Häufig gestellte Fragen

### Kann ich den vertikalen Abstand der Tabelle vom oberen Seitenrand einstellen?

Ja, Sie können die `AbsoluteVerticalDistance` Eigenschaft, um den vertikalen Abstand der Tabelle vom oberen Rand der Seite festzulegen.

### Wie richte ich die Tabelle rechts im Dokument aus?

Um die Tabelle rechtsbündig auszurichten, können Sie die `HorizontalAlignment` Eigenschaft der Tabelle zu `HorizontalAlignment.Right`.

### Ist es möglich, mehrere Tabellen im selben Dokument unterschiedlich zu positionieren?

Absolut! Sie können auf mehrere Tabellen einzeln zugreifen und Positionen festlegen, indem Sie die `Tables` Sammlung im Dokument.

### Kann ich die relative Positionierung für die horizontale Ausrichtung verwenden?

Ja, Aspose.Words unterstützt die relative Positionierung sowohl für horizontale als auch für vertikale Ausrichtungen mithilfe von Eigenschaften wie `RelativeHorizontalAlignment`.

### Unterstützt Aspose.Words schwebende Tabellen in verschiedenen Abschnitten eines Dokuments?

Ja, Sie können schwebende Tabellen in verschiedenen Abschnitten positionieren, indem Sie in Ihrem Dokument auf den jeweiligen Abschnitt und seine Tabellen zugreifen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}