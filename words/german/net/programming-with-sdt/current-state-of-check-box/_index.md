---
title: Aktueller Status des Kontrollkästchens
linktitle: Aktueller Status des Kontrollkästchens
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Kontrollkästchen in Word-Dokumenten mit Aspose.Words für .NET verwalten. In diesem Handbuch wird das programmgesteuerte Einrichten, Aktualisieren und Speichern von Kontrollkästchen beschrieben.
weight: 10
url: /de/net/programming-with-sdt/current-state-of-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktueller Status des Kontrollkästchens

## Einführung

In diesem Tutorial gehen wir den Prozess der Arbeit mit Kontrollkästchen in Word-Dokumenten durch. Wir zeigen Ihnen, wie Sie auf ein Kontrollkästchen zugreifen, seinen Status bestimmen und es entsprechend aktualisieren. Egal, ob Sie ein Formular entwickeln, das ankreuzbare Optionen benötigt, oder Dokumentänderungen automatisieren, dieser Leitfaden bietet Ihnen eine solide Grundlage.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Wenn Sie dies noch nicht getan haben, können Sie sie von der[Aspose-Website](https://releases.aspose.com/words/net/).

2. Visual Studio: Zum Kompilieren und Ausführen Ihres Codes ist eine .NET-Entwicklungsumgebung wie Visual Studio erforderlich.

3. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie die bereitgestellten Beispiele besser verstehen und nachvollziehen.

4. Word-Dokument mit Kontrollkästchen: Für dieses Tutorial benötigen Sie ein Word-Dokument mit Kontrollkästchen-Formularfeldern. Wir verwenden dieses Dokument, um zu demonstrieren, wie Kontrollkästchen programmgesteuert bearbeitet werden können.

## Namespaces importieren

Um mit Aspose.Words für .NET zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie am Anfang Ihrer C#-Datei die folgenden using-Direktiven ein:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Diese Namespaces ermöglichen Ihnen den Zugriff auf die Aspose.Words-API und die Arbeit mit dieser sowie die Handhabung strukturierter Dokument-Tags, einschließlich Kontrollkästchen.

## Schritt 1: Einrichten des Dokumentpfads

 Zuerst müssen Sie den Pfad zu Ihrem Word-Dokument angeben. Hier sucht Aspose.Words nach der Datei, um Operationen durchzuführen. Ersetzen Sie`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Ihr Dokument gespeichert ist.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden des Dokuments

 Laden Sie anschließend das Word-Dokument in eine Instanz des`Document` Klasse. Diese Klasse stellt Ihr Word-Dokument im Code dar und bietet verschiedene Methoden zur Bearbeitung.

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

 Hier,`"Structured document tags.docx"` sollte durch den Namen Ihrer Word-Datei ersetzt werden.

## Schritt 3: Zugriff auf das Kontrollkästchen-Formularfeld

Um auf ein bestimmtes Kontrollkästchen zuzugreifen, müssen Sie es aus dem Dokument abrufen. Aspose.Words behandelt Kontrollkästchen als strukturierte Dokument-Tags. Der folgende Code ruft das erste strukturierte Dokument-Tag im Dokument ab und prüft, ob es sich um ein Kontrollkästchen handelt.

```csharp
//Holen Sie sich das erste Inhaltssteuerelement aus dem Dokument.
StructuredDocumentTag sdtCheckBox =
    (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## Schritt 4: Überprüfen und Aktualisieren des Kontrollkästchenstatus

 Sobald Sie die`StructuredDocumentTag` Instanz können Sie den Typ prüfen und den Status aktualisieren. In diesem Beispiel wird das Kontrollkästchen aktiviert, wenn es sich tatsächlich um ein Kontrollkästchen handelt.

```csharp
if (sdtCheckBox.SdtType == SdtType.Checkbox)
    sdtCheckBox.Checked = true;
```

## Schritt 5: Speichern des Dokuments

Speichern Sie das geänderte Dokument abschließend in einer neuen Datei. So bleibt das Originaldokument erhalten und Sie können mit der aktualisierten Version arbeiten.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CurrentStateOfCheckBox.docx");
```

 In diesem Beispiel`"WorkingWithSdt.CurrentStateOfCheckBox.docx"` ist der Name der Datei, in der das geänderte Dokument gespeichert wird.

## Abschluss

In diesem Tutorial haben wir erläutert, wie Sie Kontrollkästchen-Formularfelder in Word-Dokumenten mit Aspose.Words für .NET bearbeiten. Wir haben untersucht, wie Sie den Dokumentpfad einrichten, das Dokument laden, auf Kontrollkästchen zugreifen, ihren Status aktualisieren und die Änderungen speichern. Mit diesen Fähigkeiten können Sie jetzt programmgesteuert interaktivere und dynamischere Word-Dokumente erstellen.

## Häufig gestellte Fragen

### Welche Arten von Dokumentelementen kann ich mit Aspose.Words für .NET bearbeiten?
Mit Aspose.Words für .NET können Sie verschiedene Dokumentelemente bearbeiten, darunter Absätze, Tabellen, Bilder, Kopf- und Fußzeilen sowie strukturierte Dokument-Tags wie Kontrollkästchen.

### Wie kann ich mehrere Kontrollkästchen in einem Dokument handhaben?
Um mehrere Kontrollkästchen zu verarbeiten, würden Sie die Sammlung strukturierter Dokument-Tags durchlaufen und jedes einzelne überprüfen, um zu ermitteln, ob es sich um ein Kontrollkästchen handelt.

### Kann ich Aspose.Words für .NET verwenden, um neue Kontrollkästchen in einem Word-Dokument zu erstellen?
 Ja, Sie können neue Kontrollkästchen erstellen, indem Sie strukturierte Dokument-Tags vom Typ`SdtType.Checkbox` zu Ihrem Dokument.

### Ist es möglich, den Status eines Kontrollkästchens aus einem Dokument zu lesen?
 Absolut. Sie können den Status eines Kontrollkästchens lesen, indem Sie auf das`Checked` Eigentum der`StructuredDocumentTag` wenn es vom Typ ist`SdtType.Checkbox`.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words für .NET?
 Eine vorläufige Lizenz erhalten Sie bei der[Aspose-Kaufseite](https://purchase.aspose.com/temporary-license/), wodurch Sie die volle Funktionalität der Bibliothek bewerten können.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
