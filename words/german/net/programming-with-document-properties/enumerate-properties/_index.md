---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Eigenschaften in einem Word-Dokument aufzählen. Perfekt für Entwickler aller Erfahrungsstufen."
"linktitle": "Eigenschaften aufzählen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Eigenschaften aufzählen"
"url": "/de/net/programming-with-document-properties/enumerate-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eigenschaften aufzählen

## Einführung

Möchten Sie Word-Dokumente programmgesteuert bearbeiten? Aspose.Words für .NET ist ein leistungsstarkes Tool, das Ihnen dabei hilft. Heute zeige ich Ihnen, wie Sie die Eigenschaften eines Word-Dokuments mit Aspose.Words für .NET aufzählen. Egal, ob Sie Anfänger oder erfahren sind, diese Anleitung erklärt es Schritt für Schritt und ist leicht verständlich.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, benötigen Sie für den Einstieg einige Dinge:

- Aspose.Words für .NET: Sie können [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio wird empfohlen, Sie können jedoch jede C#-IDE verwenden.
- Grundkenntnisse in C#: Ein grundlegendes Verständnis von C# wird Ihnen helfen, dem Stück zu folgen.

Und jetzt legen wir direkt los!

## Schritt 1: Einrichten Ihres Projekts

Als Erstes müssen Sie Ihr Projekt in Visual Studio einrichten.

1. Neues Projekt erstellen: Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolenanwendungsprojekt.
2. Installieren Sie Aspose.Words für .NET: Verwenden Sie den NuGet-Paketmanager, um Aspose.Words für .NET zu installieren. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“ und suchen Sie nach „Aspose.Words“. Installieren Sie das Paket.

## Schritt 2: Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer Datei Program.cs Folgendes hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## Schritt 3: Laden Sie Ihr Dokument

Laden Sie als Nächstes das Word-Dokument, mit dem Sie arbeiten möchten. Für dieses Beispiel verwenden wir das Dokument „Properties.docx“ aus Ihrem Projektverzeichnis.

1. Dokumentpfad definieren: Geben Sie den Pfad zu Ihrem Dokument an.
2. Laden Sie das Dokument: Verwenden Sie Aspose.Words `Document` Klasse zum Laden des Dokuments.

Hier ist der Code:

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## Schritt 4: Dokumentnamen anzeigen

Sobald Ihr Dokument geladen ist, möchten Sie möglicherweise seinen Namen anzeigen. Aspose.Words bietet hierfür eine Eigenschaft:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## Schritt 5: Integrierte Eigenschaften aufzählen

Integrierte Eigenschaften sind von Microsoft Word vordefinierte Metadateneigenschaften. Dazu gehören Titel, Autor und mehr.

1. Zugriff auf integrierte Eigenschaften: Verwenden Sie die `BuiltInDocumentProperties` Sammlung.
2. Eigenschaften durchlaufen: Durchlaufen Sie die Eigenschaften und zeigen Sie ihre Namen und Werte an.

Hier ist der Code:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Schritt 6: Benutzerdefinierte Eigenschaften aufzählen

Benutzerdefinierte Eigenschaften sind benutzerdefinierte Metadateneigenschaften. Diese können beliebige Elemente sein, die Sie Ihrem Dokument hinzufügen möchten.

1. Zugriff auf benutzerdefinierte Eigenschaften: Verwenden Sie die `CustomDocumentProperties` Sammlung.
2. Eigenschaften durchlaufen: Durchlaufen Sie die Eigenschaften und zeigen Sie ihre Namen und Werte an.

Hier ist der Code:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Abschluss

Und da haben Sie es! Sie haben sowohl integrierte als auch benutzerdefinierte Eigenschaften eines Word-Dokuments mit Aspose.Words für .NET erfolgreich aufgelistet. Dies ist nur die Spitze des Eisbergs der Möglichkeiten von Aspose.Words. Ob Sie die Dokumenterstellung automatisieren oder komplexe Dokumente bearbeiten – Aspose.Words bietet Ihnen eine Vielzahl von Funktionen, die Ihnen die Arbeit erleichtern.

## Häufig gestellte Fragen

### Kann ich einem Dokument neue Eigenschaften hinzufügen?
Ja, Sie können neue benutzerdefinierte Eigenschaften hinzufügen, indem Sie `CustomDocumentProperties` Sammlung.

### Ist die Nutzung von Aspose.Words kostenlos?
Aspose.Words bietet eine [kostenlose Testversion](https://releases.aspose.com/) und anders [Kaufoptionen](https://purchase.aspose.com/buy).

### Wie erhalte ich Support für Aspose.Words?
Sie können Unterstützung von der Aspose-Community erhalten [Hier](https://forum.aspose.com/c/words/8).

### Kann ich Aspose.Words mit anderen .NET-Sprachen verwenden?
Ja, Aspose.Words unterstützt mehrere .NET-Sprachen, einschließlich VB.NET.

### Wo finde ich weitere Beispiele?
Schauen Sie sich die [Aspose.Words für .NET-Dokumentation](https://reference.aspose.com/words/net/) für weitere Beispiele und ausführliche Informationen.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}