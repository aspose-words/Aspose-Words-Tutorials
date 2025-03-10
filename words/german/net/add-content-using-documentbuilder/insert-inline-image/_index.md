---
title: Inline-Bild in Word-Dokument einfügen
linktitle: Inline-Bild in Word-Dokument einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Inline-Bilder in Word-Dokumente einfügen. Schritt-für-Schritt-Anleitung mit Codebeispielen und FAQs.
weight: 10
url: /de/net/add-content-using-documentbuilder/insert-inline-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inline-Bild in Word-Dokument einfügen

## Einführung

Im Bereich der Dokumentenverarbeitung mit .NET-Anwendungen ist Aspose.Words eine robuste Lösung für die programmgesteuerte Bearbeitung von Word-Dokumenten. Eines seiner Hauptmerkmale ist die Möglichkeit, mühelos Inline-Bilder einzufügen, wodurch die visuelle Attraktivität und Funktionalität Ihrer Dokumente verbessert wird. In diesem Tutorial erfahren Sie ausführlich, wie Sie Aspose.Words für .NET nutzen können, um Bilder nahtlos in Ihre Word-Dokumente einzubetten.

## Voraussetzungen

Bevor Sie mit dem Einfügen von Inline-Bildern mit Aspose.Words für .NET beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Visual Studio-Umgebung: Visual Studio muss installiert und bereit zum Erstellen und Kompilieren von .NET-Anwendungen sein.
2.  Aspose.Words für .NET-Bibliothek: Laden Sie die Aspose.Words für .NET-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.aspose.com/words/net/).
3. Grundlegende Kenntnisse in C#: Kenntnisse der Grundlagen der Programmiersprache C# sind für die Implementierung der Codeausschnitte von Vorteil.

Lassen Sie uns nun die Schritte zum Importieren der erforderlichen Namespaces durchgehen und mit Aspose.Words für .NET ein Inline-Bild einfügen.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren, um auf die Funktionen von Aspose.Words für .NET zuzugreifen:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die für die Bearbeitung von Word-Dokumenten und die Verarbeitung von Bildern erforderlich sind.

## Schritt 1: Neues Dokument erstellen

 Beginnen Sie mit der Initialisierung einer neuen Instanz des`Document` Klasse und eine`DocumentBuilder` um die Dokumenterstellung zu erleichtern.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Einfügen des Inline-Bildes

 Verwenden Sie die`InsertImage` Methode der`DocumentBuilder` Klasse, um an der aktuellen Position ein Bild in das Dokument einzufügen.

```csharp
string imagePath = "PATH_TO_YOUR_IMAGE_FILE";
builder.InsertImage(imagePath);
```

 Ersetzen`"PATH_TO_YOUR_IMAGE_FILE"` durch den tatsächlichen Pfad zu Ihrer Bilddatei. Diese Methode integriert das Bild nahtlos in das Dokument.

## Schritt 3: Speichern Sie das Dokument

 Speichern Sie das Dokument abschließend am gewünschten Speicherort mit dem`Save` Methode der`Document` Klasse.

```csharp
doc.Save(dataDir + "InsertInlineImage.docx");
```

Dieser Schritt stellt sicher, dass das Dokument, das das Inline-Bild enthält, unter dem angegebenen Dateinamen gespeichert wird.

## Abschluss

Zusammenfassend lässt sich sagen, dass die Integration von Inline-Bildern in Word-Dokumente mit Aspose.Words für .NET ein unkomplizierter Prozess ist, der die Dokumentvisualisierung und -funktionalität verbessert. Indem Sie die oben beschriebenen Schritte befolgen, können Sie Bilder in Ihren Dokumenten effizient programmgesteuert bearbeiten und dabei die Leistungsfähigkeit von Aspose.Words nutzen.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET mehrere Bilder in ein einzelnes Word-Dokument einfügen?
 Ja, Sie können mehrere Bilder einfügen, indem Sie Ihre Bilddateien durchlaufen und aufrufen`builder.InsertImage` für jedes Bild.

### Unterstützt Aspose.Words für .NET das Einfügen von Bildern mit transparentem Hintergrund?
Ja, Aspose.Words für .NET unterstützt das Einfügen von Bildern mit transparentem Hintergrund, wobei die Transparenz des Bildes im Dokument erhalten bleibt.

### Wie kann ich die Größe eines mit Aspose.Words für .NET eingefügten Inline-Bilds ändern?
 Sie können die Größe eines Bildes ändern, indem Sie die Breite und Höhe des`Shape` Objekt zurückgegeben von`builder.InsertImage`.

### Ist es möglich, mit Aspose.Words für .NET ein Inline-Bild an einer bestimmten Stelle im Dokument zu positionieren?
 Ja, Sie können die Position eines Inline-Bildes über die Cursorposition des Dokument-Generators festlegen, bevor Sie`builder.InsertImage`.

### Kann ich mit Aspose.Words für .NET Bilder von URLs in ein Word-Dokument einbetten?
Ja, Sie können mithilfe von .NET-Bibliotheken Bilder von URLs herunterladen und sie dann mit Aspose.Words für .NET in ein Word-Dokument einfügen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
