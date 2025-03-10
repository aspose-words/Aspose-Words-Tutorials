---
title: Form einfügen
linktitle: Form einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Formen in Word-Dokumente einfügen und bearbeiten.
weight: 10
url: /de/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Form einfügen

## Einführung

Wenn es darum geht, optisch ansprechende und gut strukturierte Word-Dokumente zu erstellen, können Formen eine wichtige Rolle spielen. Egal, ob Sie Pfeile, Kästchen oder sogar komplexe benutzerdefinierte Formen hinzufügen, die Möglichkeit, diese Elemente programmgesteuert zu bearbeiten, bietet beispiellose Flexibilität. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET Formen in Word-Dokumente einfügen und bearbeiten.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1.  Aspose.Words für .NET: Laden Sie die neueste Version herunter und installieren Sie sie vom[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine geeignete .NET-Entwicklungsumgebung wie Visual Studio.
3. Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# und den grundlegenden Konzepten.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Schritt 1: Richten Sie Ihr Projekt ein

Bevor Sie mit dem Einfügen von Formen beginnen können, müssen Sie Ihr Projekt einrichten und die Bibliothek Aspose.Words für .NET hinzufügen.

1. Neues Projekt erstellen: Öffnen Sie Visual Studio und erstellen Sie ein neues C#-Konsolenanwendungsprojekt.
2. Aspose.Words für .NET hinzufügen: Installieren Sie die Aspose.Words-Bibliothek für .NET über den NuGet-Paket-Manager.

```bash
Install-Package Aspose.Words
```

## Schritt 2: Initialisieren Sie das Dokument

Zuerst müssen Sie ein neues Dokument und einen Dokument-Generator initialisieren, der Sie beim Erstellen des Dokuments unterstützt.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Initialisieren eines neuen Dokuments
Document doc = new Document();

// Initialisieren Sie einen DocumentBuilder, um das Erstellen des Dokuments zu unterstützen
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Eine Form einfügen

Fügen wir nun eine Form in das Dokument ein. Wir beginnen mit dem Hinzufügen eines einfachen Textfelds.

```csharp
// Einfügen einer Textfeldform in das Dokument
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Drehen Sie die Form
shape.Rotation = 30.0;
```

In diesem Beispiel fügen wir an der Position (100, 100) ein Textfeld mit einer Breite und Höhe von jeweils 50 Einheiten ein. Außerdem drehen wir die Form um 30 Grad.

## Schritt 4: Eine weitere Form hinzufügen

Fügen wir dem Dokument eine weitere Form hinzu, dieses Mal ohne Angabe der Position.

```csharp
// Eine weitere Textfeldform hinzufügen
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Drehen Sie die Form
secondShape.Rotation = 30.0;
```

Dieser Codeausschnitt fügt ein weiteres Textfeld mit denselben Abmessungen und derselben Drehung wie das erste ein, ohne jedoch dessen Position anzugeben.

## Schritt 5: Speichern Sie das Dokument

 Nachdem Sie die Formen hinzugefügt haben, müssen Sie das Dokument abschließend speichern. Wir verwenden dazu die`OoxmlSaveOptions` um das Speicherformat anzugeben.

```csharp
// Definieren Sie Speicheroptionen mit Compliance
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Speichern des Dokuments
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich Formen in ein Word-Dokument eingefügt und bearbeitet, indem Sie Aspose.Words für .NET verwendet haben. Dieses Tutorial behandelte die Grundlagen, aber Aspose.Words bietet viele erweiterte Funktionen für die Arbeit mit Formen, wie benutzerdefinierte Stile, Verbinder und Gruppenformen.

 Weitere Informationen finden Sie im[Aspose.Words für .NET-Dokumentation](https://reference.aspose.com/words/net/).

## Häufig gestellte Fragen

### Wie füge ich verschiedene Arten von Formen ein?
Sie können die`ShapeType` im`InsertShape` Methode zum Einfügen verschiedener Arten von Formen wie Kreisen, Rechtecken und Pfeilen.

### Kann ich den Formen Text hinzufügen?
 Ja, Sie können die`builder.Write` Methode zum Hinzufügen von Text innerhalb der Formen nach dem Einfügen.

### Ist es möglich, die Formen zu stylen?
 Ja, Sie können die Formen gestalten, indem Sie Eigenschaften festlegen wie`FillColor`, `StrokeColor` , Und`StrokeWeight`.

### Wie positioniere ich Formen relativ zu anderen Elementen?
 Verwenden Sie die`RelativeHorizontalPosition` Und`RelativeVerticalPosition` Eigenschaften, um Formen relativ zu anderen Elementen im Dokument zu positionieren.

### Kann ich mehrere Formen gruppieren?
 Ja, Aspose.Words für .NET ermöglicht das Gruppieren von Formen mithilfe der`GroupShape` Klasse.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
