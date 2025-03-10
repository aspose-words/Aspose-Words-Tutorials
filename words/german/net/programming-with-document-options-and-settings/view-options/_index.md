---
title: Optionen anzeigen
linktitle: Optionen anzeigen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Optionen in Word-Dokumenten anzeigen. In diesem Handbuch erfahren Sie, wie Sie Ansichtstypen festlegen, Zoomstufen anpassen und Ihr Dokument speichern.
weight: 10
url: /de/net/programming-with-document-options-and-settings/view-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Optionen anzeigen

## Einführung

Hallo, Programmierkollege! Haben Sie sich schon einmal gefragt, wie Sie die Anzeige Ihrer Word-Dokumente mit Aspose.Words für .NET ändern können? Egal, ob Sie zu einem anderen Ansichtstyp wechseln oder hinein- und herauszoomen möchten, um Ihr Dokument perfekt anzuzeigen, hier sind Sie richtig. Heute tauchen wir in die Welt von Aspose.Words für .NET ein und konzentrieren uns insbesondere darauf, wie Sie die Anzeigeoptionen manipulieren können. Wir unterteilen alles in einfache, leicht verständliche Schritte, sodass Sie im Handumdrehen zum Experten werden. Bereit? Dann legen wir los!

## Voraussetzungen

Bevor wir uns kopfüber in den Code stürzen, stellen wir sicher, dass wir alles haben, was wir brauchen, um diesem Tutorial zu folgen. Hier ist eine kurze Checkliste:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words für .NET-Bibliothek haben. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Auf Ihrem Computer sollte eine IDE wie Visual Studio installiert sein.
3. Grundkenntnisse in C#: Wir halten die Dinge zwar einfach, aber ein grundlegendes Verständnis von C# ist von Vorteil.
4. Beispiel-Word-Dokument: Halten Sie ein Beispiel-Word-Dokument bereit. In diesem Tutorial nennen wir es „Dokument.docx“.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Dadurch können Sie auf die Funktionen von Aspose.Words für .NET zugreifen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns jeden Schritt zum Bearbeiten der Anzeigeoptionen Ihres Word-Dokuments aufschlüsseln.

## Schritt 1: Laden Sie Ihr Dokument

Der erste Schritt besteht darin, das Word-Dokument zu laden, mit dem Sie arbeiten möchten. Dies ist ganz einfach, indem Sie auf den richtigen Dateipfad verweisen.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 In diesem Snippet definieren wir den Pfad zu unserem Dokument und laden es mit dem`Document` Klasse. Stellen Sie sicher, dass Sie ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokument.

## Schritt 2: Festlegen des Ansichtstyps

Als Nächstes ändern wir den Ansichtstyp des Dokuments. Der Ansichtstyp bestimmt, wie das Dokument angezeigt wird, z. B. Drucklayout, Weblayout oder Gliederungsansicht.

```csharp
doc.ViewOptions.ViewType = ViewType.PageLayout;
```

 Hier setzen wir den Ansichtstyp auf`PageLayout`, die der Drucklayoutansicht in Microsoft Word ähnelt. Dadurch erhalten Sie eine genauere Darstellung des gedruckten Aussehens Ihres Dokuments.

## Schritt 3: Passen Sie die Zoomstufe an

Manchmal müssen Sie Ihr Dokument vergrößern oder verkleinern, um es besser sehen zu können. Dieser Schritt zeigt Ihnen, wie Sie die Zoomstufe anpassen.

```csharp
doc.ViewOptions.ZoomPercent = 50;
```

 Durch die Einstellung der`ZoomPercent` Zu`50`, wir verkleinern das Bild auf 50% der tatsächlichen Größe. Sie können diesen Wert Ihren Bedürfnissen entsprechend anpassen.

## Schritt 4: Speichern Sie Ihr Dokument

Nachdem Sie die erforderlichen Änderungen vorgenommen haben, möchten Sie Ihr Dokument abschließend speichern, um die Änderungen in Aktion zu sehen.

```csharp
doc.Save(dataDir + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
```

Diese Codezeile speichert das geänderte Dokument unter einem neuen Namen, sodass Sie Ihre Originaldatei nicht überschreiben. Sie können diese Datei jetzt öffnen, um die aktualisierten Anzeigeoptionen anzuzeigen.

## Abschluss

Und da haben Sie es! Das Ändern der Ansichtsoptionen Ihres Word-Dokuments mit Aspose.Words für .NET ist unkompliziert, wenn Sie die Schritte kennen. In diesem Tutorial haben Sie gelernt, wie Sie ein Dokument laden, den Ansichtstyp ändern, die Zoomstufe anpassen und das Dokument mit den neuen Einstellungen speichern. Denken Sie daran, der Schlüssel zur Beherrschung von Aspose.Words für .NET ist Übung. Probieren Sie also verschiedene Einstellungen aus, um herauszufinden, was für Sie am besten funktioniert. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Welche anderen Ansichtstypen kann ich für mein Dokument festlegen?

 Aspose.Words für .NET unterstützt mehrere Ansichtstypen, darunter`PrintLayout`, `WebLayout`, `Reading` , Und`Outline`. Sie können diese Optionen je nach Ihren Anforderungen erkunden.

### Kann ich für verschiedene Abschnitte meines Dokuments unterschiedliche Zoomstufen einstellen?

Nein, die Zoomstufe wird auf das gesamte Dokument angewendet, nicht auf einzelne Abschnitte. Sie können die Zoomstufe jedoch manuell anpassen, wenn Sie in Ihrem Textverarbeitungsprogramm verschiedene Abschnitte anzeigen.

### Ist es möglich, die ursprünglichen Anzeigeeinstellungen des Dokuments wiederherzustellen?

Ja, Sie können zu den ursprünglichen Ansichtseinstellungen zurückkehren, indem Sie das Dokument erneut laden, ohne die Änderungen zu speichern, oder indem Sie die Ansichtsoptionen auf die ursprünglichen Werte zurücksetzen.

### Wie kann ich sicherstellen, dass mein Dokument auf verschiedenen Geräten gleich aussieht?

Um Konsistenz zu gewährleisten, speichern Sie Ihr Dokument mit den gewünschten Ansichtsoptionen und verteilen Sie dieselbe Datei. Ansichtseinstellungen wie Zoomstufe und Ansichtstyp sollten auf allen Geräten konsistent bleiben.

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?

 Ausführlichere Dokumentation und Beispiele finden Sie auf der[Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
