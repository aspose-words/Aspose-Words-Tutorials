---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Revisionstypen von Wörtern in einem Word-Dokument erhalten. Diese Schritt-für-Schritt-Anleitung hilft Ihnen, Dokumentrevisionen effizient durchzuführen."
"linktitle": "Holen Sie sich Revisionsarten von Wörtern"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Holen Sie sich Revisionsarten von Wörtern"
"url": "/de/net/working-with-revisions/get-revision-types/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Holen Sie sich Revisionsarten von Wörtern

## Einführung

Haben Sie sich schon einmal mitten in einer Flut von Dokumentrevisionen herumgetrieben und sich gefragt, wer was wann verschoben hat? Sie sind nicht allein. Die Bearbeitung von Dokumentrevisionen kann mühsam sein, insbesondere bei umfangreichen Dokumenten. Aber keine Sorge! Mit Aspose.Words für .NET können Sie diese Revisionen ganz einfach identifizieren und verwalten. In dieser Anleitung erfahren Sie Schritt für Schritt, wie Sie mit Aspose.Words für .NET Revisionstypen von Wörtern in einem Word-Dokument erstellen. Also, anschnallen und los geht‘s!

## Voraussetzungen

Bevor wir uns mit dem Code die Hände schmutzig machen, benötigen Sie ein paar Dinge:

1. Aspose.Words für .NET-Bibliothek: Falls noch nicht geschehen, laden Sie es herunter von [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
3. Grundkenntnisse in C#: Kenntnisse der Programmiersprache C# sind von Vorteil.
4. Ein Word-Dokument mit Revisionen: Stellen Sie sicher, dass Sie ein `.docx` Datei mit nachverfolgten Änderungen, um den Code zu testen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Dadurch können Sie auf die Funktionen von Aspose.Words für .NET zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Zum besseren Verständnis und zur besseren Umsetzung unterteilen wir das Beispiel in mehrere Schritte.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zuerst müssen Sie den Pfad zu Ihrem Dokumentenverzeichnis definieren. Hier befindet sich Ihr Word-Dokument mit den Revisionen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentordner.

## Schritt 2: Laden Sie Ihr Word-Dokument

Als Nächstes müssen Sie das Word-Dokument in Ihr Projekt laden. Dieses Dokument sollte die Revisionen enthalten, die Sie analysieren möchten.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

Stellen Sie sicher, dass die Datei `Revisions.docx` ist im angegebenen Verzeichnis vorhanden.

## Schritt 3: Zugriff auf die Absatzsammlung

Nachdem Ihr Dokument geladen ist, müssen Sie auf die Absätze im ersten Abschnitt des Dokumenttexts zugreifen. So können Sie jeden Absatz durchlaufen und auf Änderungen prüfen.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Schritt 4: Absätze durchlaufen und auf Überarbeitungen prüfen

Und hier geschieht die Magie. Sie durchlaufen jeden Absatz und prüfen, ob er verschoben (gelöscht oder eingefügt) wurde.

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

Diese Schleife durchläuft jeden Absatz und verwendet die `IsMoveFromRevision` Und `IsMoveToRevision` Eigenschaften, um zu bestimmen, ob der Absatz verschoben (gelöscht) oder verschoben (eingefügt) wurde.

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen können Sie mit Aspose.Words für .NET die Revisionstypen in Ihrem Word-Dokument problemlos identifizieren. Diese leistungsstarke Bibliothek macht die Bearbeitung von Dokumentrevisionen zum Kinderspiel, sodass Sie sich auf wichtigere Aufgaben konzentrieren können. 

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET verwenden, um von bestimmten Benutzern vorgenommene Änderungen zu verfolgen?

Ja, Aspose.Words für .NET bietet Funktionen für den Zugriff auf Revisionsdetails, einschließlich des Autors der Änderungen.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?

Absolut! Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/).

### Wie kann ich eine temporäre Lizenz für Aspose.Words für .NET beantragen?

Sie können eine temporäre Lizenz anfordern und beantragen bei [Hier](https://purchase.aspose.com/temporary-license/).

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?

Eine ausführliche Dokumentation finden Sie auf der [Aspose-Website](https://reference.aspose.com/words/net/).

### Kann ich Aspose.Words für .NET in einem nicht kommerziellen Projekt verwenden?

Ja, Aspose.Words für .NET kann sowohl in kommerziellen als auch in nicht-kommerziellen Projekten verwendet werden. Überprüfen Sie jedoch unbedingt die Lizenzbedingungen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}