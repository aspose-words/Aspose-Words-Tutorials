---
title: Bevorzugten Breitentyp abrufen
linktitle: Bevorzugten Breitentyp abrufen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET die bevorzugte Breite von Tabellenzellen in Word-Dokumenten abrufen.
weight: 10
url: /de/net/programming-with-tables/retrieve-preferred-width-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bevorzugten Breitentyp abrufen

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie mit Aspose.Words für .NET die bevorzugte Breite von Tabellenzellen in Ihren Word-Dokumenten abrufen können? Dann sind Sie hier richtig! In diesem Tutorial erklären wir Ihnen den Vorgang Schritt für Schritt, sodass er kinderleicht ist. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, Sie werden diese Anleitung hilfreich und spannend finden. Lassen Sie uns also eintauchen und die Geheimnisse hinter der Verwaltung der Tabellenzellenbreiten in Word-Dokumenten lüften.

## Voraussetzungen

Bevor wir beginnen, benötigen Sie einige Dinge:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version installiert haben. Sie können sie herunterladen von[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Sie benötigen eine IDE wie Visual Studio.
3. Grundkenntnisse in C#: Das Verständnis der Grundlagen von C# wird Ihnen helfen, den Schritten zu folgen.
4.  Beispieldokument: Halten Sie ein Word-Dokument mit Tabellen bereit, an denen Sie arbeiten können. Sie können jedes beliebige Dokument verwenden, aber wir nennen es`Tables.docx` in diesem Lernprogramm.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dieser Schritt ist entscheidend, da er unsere Umgebung für die Verwendung der Aspose.Words-Funktionen einrichtet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Bevor wir unser Dokument bearbeiten, müssen wir das Verzeichnis angeben, in dem es sich befindet. Dies ist ein einfacher, aber wesentlicher Schritt.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. Dies sagt unserem Programm, wo es die Datei finden kann, mit der wir arbeiten möchten.

## Schritt 2: Laden Sie das Dokument

Als Nächstes laden wir das Word-Dokument in unsere Anwendung. So können wir programmgesteuert mit dem Inhalt interagieren.

```csharp
Document doc = new Document(dataDir + "Tables.docx");
```

 Diese Codezeile öffnet die`Tables.docx` Dokument aus dem angegebenen Verzeichnis. Jetzt ist unser Dokument für weitere Operationen bereit.

## Schritt 3: Zugriff auf die Tabelle

Nachdem unser Dokument nun geladen ist, müssen wir auf die Tabelle zugreifen, mit der wir arbeiten möchten. Der Einfachheit halber zielen wir auf die erste Tabelle im Dokument.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Diese Zeile ruft die erste Tabelle aus dem Dokument ab. Wenn Ihr Dokument mehrere Tabellen enthält, können Sie den Index anpassen, um eine andere auszuwählen.

## Schritt 4: AutoFit für die Tabelle aktivieren

Um sicherzustellen, dass die Tabelle ihre Spalten automatisch anpasst, müssen wir die Eigenschaft AutoFit aktivieren.

```csharp
table.AllowAutoFit = true;
```

 Einstellung`AllowAutoFit` Zu`true` stellt sicher, dass die Größe der Tabellenspalten basierend auf ihrem Inhalt angepasst wird, was unserer Tabelle ein dynamisches Aussehen verleiht.

## Schritt 5: Abrufen des bevorzugten Breitentyps der ersten Zelle

Jetzt kommt der Kern unseres Tutorials: das Abrufen des bevorzugten Breitentyps der ersten Zelle in der Tabelle.

```csharp
Cell firstCell = table.FirstRow.FirstCell;
PreferredWidthType type = firstCell.CellFormat.PreferredWidth.Type;
double value = firstCell.CellFormat.PreferredWidth.Value;
```

 Diese Codezeilen greifen auf die erste Zelle in der ersten Zeile der Tabelle zu und ermitteln deren bevorzugten Breitentyp und Wert.`PreferredWidthType` kann sein`Auto`, `Percent` , oder`Point`, die angibt, wie die Breite bestimmt wird.

## Schritt 6: Ergebnisse anzeigen

Lassen Sie uns abschließend die abgerufenen Informationen auf der Konsole anzeigen.

```csharp
Console.WriteLine("Preferred Width Type: " + type);
Console.WriteLine("Preferred Width Value: " + value);
```

Diese Zeilen drucken den bevorzugten Breitentyp und Wert auf die Konsole, sodass Sie die Ergebnisse Ihrer Codeausführung sehen können.

## Abschluss

Und da haben Sie es! Das Abrufen der bevorzugten Breite von Tabellenzellen in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert, wenn es in überschaubare Schritte unterteilt wird. Wenn Sie dieser Anleitung folgen, können Sie Tabelleneigenschaften in Ihren Word-Dokumenten problemlos bearbeiten und so Ihre Dokumentverwaltungsaufgaben wesentlich effizienter gestalten.

## Häufig gestellte Fragen

### Kann ich den bevorzugten Breitentyp für alle Zellen in einer Tabelle abrufen?

Ja, Sie können jede Zelle in der Tabelle durchlaufen und die bevorzugten Breitentypen einzeln abrufen.

###  Was sind die möglichen Werte für`PreferredWidthType`?

`PreferredWidthType` kann sein`Auto`, `Percent` , oder`Point`.

### Ist es möglich, den bevorzugten Breitentyp programmgesteuert festzulegen?

 Absolut! Sie können den gewünschten Breitentyp und -wert mit dem`PreferredWidth` Eigentum der`CellFormat` Klasse.

### Kann ich diese Methode für Tabellen in anderen Dokumenten als Word verwenden?

Dieses Tutorial behandelt speziell Word-Dokumente. Für andere Dokumenttypen müssen Sie die entsprechende Aspose-Bibliothek verwenden.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?

 Ja, Aspose.Words für .NET ist ein lizenziertes Produkt. Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/) oder eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
