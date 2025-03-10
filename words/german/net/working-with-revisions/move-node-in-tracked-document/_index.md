---
title: Knoten im verfolgten Dokument verschieben
linktitle: Knoten im verfolgten Dokument verschieben
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Knoten in einem verfolgten Word-Dokument verschieben. Perfekt für Entwickler.
weight: 10
url: /de/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Knoten im verfolgten Dokument verschieben

## Einführung

Hallo, Aspose.Words-Fans! Wenn Sie beim Nachverfolgen von Revisionen schon einmal einen Knoten in einem Word-Dokument verschieben mussten, sind Sie hier richtig. Heute tauchen wir ein in die Frage, wie Sie dies mit Aspose.Words für .NET erreichen können. Sie lernen nicht nur den schrittweisen Prozess kennen, sondern erhalten auch einige Tipps und Tricks, um Ihre Dokumentbearbeitung reibungslos und effizient zu gestalten.

## Voraussetzungen

Bevor wir uns mit dem Code beschäftigen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
- .NET-Umgebung: Stellen Sie sicher, dass Sie eine kompatible .NET-Entwicklungsumgebung eingerichtet haben.
- Grundlegende C#-Kenntnisse: Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse von C# verfügen.

Alles klar? Super! Fahren wir mit den Namespaces fort, die wir importieren müssen.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren. Diese sind für die Arbeit mit Aspose.Words und die Handhabung von Dokumentknoten unerlässlich.

```csharp
using Aspose.Words;
using System;
```

Okay, lassen Sie uns den Prozess in überschaubare Schritte unterteilen. Jeder Schritt wird ausführlich erklärt, damit Sie jederzeit verstehen, was passiert.

## Schritt 1: Initialisieren Sie das Dokument

 Zu Beginn müssen wir ein neues Dokument initialisieren und verwenden ein`DocumentBuilder` um einige Absätze hinzuzufügen.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einige Absätze hinzufügen
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Überprüfen Sie die anfängliche Absatzanzahl
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Schritt 2: Beginnen Sie mit der Nachverfolgung von Revisionen

Als Nächstes müssen wir mit der Nachverfolgung von Revisionen beginnen. Dies ist wichtig, da wir so die am Dokument vorgenommenen Änderungen sehen können.

```csharp
// Starten Sie die Revisionsverfolgung
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Schritt 3: Knoten verschieben

Jetzt kommt der Kernteil unserer Aufgabe: das Verschieben eines Knotens von einem Ort zum anderen. Wir werden den dritten Absatz verschieben und ihn vor den ersten Absatz setzen.

```csharp
// Definieren Sie den zu verschiebenden Knoten und seinen Endbereich
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Verschieben Sie die Knoten innerhalb des definierten Bereichs
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Schritt 4: Beenden Sie die Revisionsverfolgung

Nachdem wir die Knoten verschoben haben, müssen wir die Verfolgung der Revisionen beenden.

```csharp
// Beenden Sie die Revisionsverfolgung
doc.StopTrackRevisions();
```

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir unser geändertes Dokument im angegebenen Verzeichnis.

```csharp
// Speichern des geänderten Dokuments
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Ausgabe der endgültigen Absatzanzahl
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich einen Knoten in einem verfolgten Dokument mit Aspose.Words für .NET verschoben. Diese leistungsstarke Bibliothek erleichtert die programmgesteuerte Bearbeitung von Word-Dokumenten. Egal, ob Sie Änderungen erstellen, bearbeiten oder verfolgen, Aspose.Words bietet alles. Probieren Sie es also aus. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?

Aspose.Words für .NET ist eine Klassenbibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten. Entwickler können damit Word-Dokumente in .NET-Anwendungen erstellen, bearbeiten, konvertieren und drucken.

### Wie verfolge ich Revisionen in einem Word-Dokument mit Aspose.Words?

 Um Revisionen zu verfolgen, verwenden Sie die`StartTrackRevisions` Methode auf der`Document` Objekt. Dadurch wird die Revisionsverfolgung aktiviert und alle am Dokument vorgenommenen Änderungen werden angezeigt.

### Kann ich mehrere Knoten in Aspose.Words verschieben?

Ja, Sie können mehrere Knoten verschieben, indem Sie über sie iterieren und Methoden wie`InsertBefore` oder`InsertAfter` um sie an der gewünschten Stelle zu platzieren.

### Wie beende ich die Revisionsverfolgung in Aspose.Words?

 Verwenden Sie die`StopTrackRevisions` Methode auf der`Document` Objekt, um die Verfolgung von Revisionen zu beenden.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?

 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
