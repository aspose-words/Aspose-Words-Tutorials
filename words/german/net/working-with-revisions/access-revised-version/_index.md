---
title: Zugriff auf überarbeitete Version
linktitle: Zugriff auf überarbeitete Version
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET auf die überarbeitete Version eines Dokuments zugreifen und diese anzeigen. Folgen Sie unserer Schritt-für-Schritt-Anleitung für eine nahtlose Dokumentenverwaltung.
weight: 10
url: /de/net/working-with-revisions/access-revised-version/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zugriff auf überarbeitete Version

## Einführung

Mussten Sie schon einmal programmgesteuert auf die überarbeitete Version eines Dokuments zugreifen? Egal, ob Sie an Gemeinschaftsprojekten arbeiten oder einfach nur Dokumentrevisionen verwalten müssen, Aspose.Words für .NET ist Ihr Tool der Wahl. Dieses Tutorial führt Sie durch den gesamten Prozess, vom Einrichten Ihrer Umgebung bis zum Zugriff auf und Anzeigen von Revisionen in einem Word-Dokument. Also, legen wir gleich los!

## Voraussetzungen

Bevor wir beginnen, benötigen Sie einige Dinge:

1.  Aspose.Words für .NET-Bibliothek: Sie können sie herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede andere IDE, die .NET unterstützt.
3. Grundkenntnisse in C#: Dies wird Ihnen helfen, dem Codierungsteil zu folgen.

Stellen Sie sicher, dass diese Voraussetzungen erfüllt sind, bevor Sie mit den nächsten Schritten fortfahren.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Dies ist ein entscheidender Schritt, um sicherzustellen, dass Ihr Code die Aspose.Words-Bibliothek für .NET erkennt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Lassen Sie uns den Prozess in einfache, leicht zu befolgende Schritte unterteilen.

## Schritt 1: Einrichten des Dokumentpfads

Bevor Sie mit dem Dokument arbeiten können, müssen Sie den Pfad angeben, in dem sich Ihr Dokument befindet. Dies ist wichtig, damit der Code die Datei finden und bearbeiten kann.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden des Dokuments

 Als nächstes laden Sie das Dokument in Ihre Anwendung. In diesem Schritt erstellen Sie ein neues`Document` Objekt und initialisieren Sie es mit dem Pfad zu Ihrem Dokument.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

## Schritt 3: Aktualisieren der Listenbeschriftungen

Wenn Ihr Dokument Listen enthält, ist es wichtig, die Listenbeschriftungen zu aktualisieren. Dadurch wird sichergestellt, dass alle Listenelemente richtig nummeriert und formatiert sind.

```csharp
doc.UpdateListLabels();
```

## Schritt 4: Umstellung auf die überarbeitete Version

Wechseln wir nun zur überarbeiteten Version des Dokuments. Dieser Schritt ist wichtig, wenn Sie auf die Überarbeitungen zugreifen und diese anzeigen möchten.

```csharp
doc.RevisionsView = RevisionsView.Final;
```

## Schritt 5: Durch Revisionen iterieren

 Um auf die Revisionen zuzugreifen, müssen Sie die`Revisions` Sammlung des Dokuments. Dieser Schritt beinhaltet die Verwendung eines`foreach` Schleife, um jede Revision durchzugehen.

```csharp
foreach (Revision revision in doc.Revisions)
{
    // Hier kommt zusätzlicher Code rein
}
```

## Schritt 6: Überprüfen des übergeordneten Knotentyps

 Überprüfen Sie bei jeder Revision, ob der übergeordnete Knoten vom Typ ist`Paragraph`. Dies ist wichtig, da wir auf den Absatz zugreifen möchten, der die Überarbeitung enthält.

```csharp
if (revision.ParentNode.NodeType == NodeType.Paragraph)
{
    // Hier kommt zusätzlicher Code rein
}
```

## Schritt 7: Zugriff auf den Absatz

 Sobald Sie bestätigt haben, dass der übergeordnete Knoten ein Absatz ist, konvertieren Sie ihn in einen`Paragraph` Objekt. In diesem Schritt können Sie mit dem Absatz und seinen Eigenschaften arbeiten.

```csharp
Paragraph paragraph = (Paragraph)revision.ParentNode;
```

## Schritt 8: Überprüfen, ob der Absatz ein Listenelement ist

Überprüfen Sie als Nächstes, ob der Absatz ein Listenelement ist. Dies ist wichtig, da Listenelemente bestimmte Eigenschaften haben, auf die wir zugreifen müssen.

```csharp
if (paragraph.IsListItem)
{
    // Hier kommt zusätzlicher Code rein
}
```

## Schritt 9: Anzeigen der Listenbezeichnung und -ebene

Zeigen Sie abschließend die Listenbeschriftung und die Listenebene des Absatzes an. Dieser Schritt liefert nützliche Informationen zum Listenelement, beispielsweise dessen Nummerierung und Einrückungsebene.

```csharp
Console.WriteLine(paragraph.ListLabel.LabelString);
Console.WriteLine(paragraph.ListFormat.ListLevel);
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich auf die überarbeitete Version eines Dokuments mit Aspose.Words für .NET zugegriffen. Indem Sie diese Schritte befolgen, können Sie Dokumentrevisionen problemlos verwalten und anzeigen. Egal, ob Sie an Gemeinschaftsprojekten arbeiten oder einfach nur den Überblick über Änderungen behalten müssen, Aspose.Words für .NET ist für Sie da.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente programmgesteuert erstellen, bearbeiten und bearbeiten können.

### Kann ich in jedem Word-Dokument auf Revisionen zugreifen?
Ja, solange das Dokument Revisionen enthält, können Sie mit Aspose.Words für .NET darauf zugreifen.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, Sie können eine Lizenz erhalten von[Hier](https://purchase.aspose.com/buy) Sie bieten auch eine[Kostenlose Testversion](https://releases.aspose.com/) und ein[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

### Ist Aspose.Words für .NET mit allen .NET-Versionen kompatibel?
Aspose.Words für .NET ist mit einer Vielzahl von .NET-Versionen kompatibel. Weitere Details finden Sie im[Dokumentation](https://reference.aspose.com/words/net/).

### Wo erhalte ich Support für Aspose.Words für .NET?
 Sie können Unterstützung von der Aspose-Community erhalten über deren[Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
