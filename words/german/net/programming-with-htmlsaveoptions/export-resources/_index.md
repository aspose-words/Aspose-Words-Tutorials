---
title: Ressourcen exportieren
linktitle: Ressourcen exportieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Ressourcen wie CSS und Schriftarten exportieren, während Sie Word-Dokumente mit Aspose.Words für .NET als HTML speichern. Folgen Sie unserer Schritt-für-Schritt-Anleitung.
weight: 10
url: /de/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ressourcen exportieren

## Einführung

Hallo Technikbegeisterter! Wenn Sie schon einmal Word-Dokumente in HTML konvertieren mussten, sind Sie hier richtig. Heute tauchen wir in die wunderbare Welt von Aspose.Words für .NET ein. Diese leistungsstarke Bibliothek macht das programmgesteuerte Arbeiten mit Word-Dokumenten zum Kinderspiel. In diesem Tutorial führen wir Sie durch die Schritte zum Exportieren von Ressourcen wie Schriftarten und CSS, wenn Sie ein Word-Dokument mit Aspose.Words für .NET als HTML speichern. Schnall dich an für eine unterhaltsame und informative Reise!

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie zum Einstieg benötigen. Hier ist eine kurze Checkliste:

1.  Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist. Sie können es von der[Visual Studio-Website](https://visualstudio.microsoft.com/).
2.  Aspose.Words für .NET: Sie benötigen die Bibliothek Aspose.Words für .NET. Wenn Sie sie noch nicht haben, holen Sie sich eine kostenlose Testversion von[Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) oder kaufen Sie es bei der[Aspose Store](https://purchase.aspose.com/buy).
3. Grundkenntnisse in C#: Grundlegende Kenntnisse in C# helfen Ihnen, den Codebeispielen zu folgen.

Alles klar? Super! Fahren wir mit dem Importieren der erforderlichen Namespaces fort.

## Namespaces importieren

Um Aspose.Words für .NET zu verwenden, müssen Sie die relevanten Namespaces in Ihr Projekt einbinden. So geht's:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Diese Namespaces sind entscheidend für den Zugriff auf die Aspose.Words-Klassen und -Methoden, die wir in unserem Tutorial verwenden werden.

Lassen Sie uns den Vorgang des Ressourcenexports beim Speichern eines Word-Dokuments als HTML aufschlüsseln. Wir gehen Schritt für Schritt vor, damit es leicht nachvollziehbar ist.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Als Erstes müssen Sie den Pfad zu Ihrem Dokumentenverzeichnis angeben. Hier befindet sich Ihr Word-Dokument und hier wird auch die HTML-Datei gespeichert.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

## Schritt 2: Laden Sie das Word-Dokument

 Als nächstes laden wir das Word-Dokument, das Sie in HTML konvertieren möchten. Für dieses Tutorial verwenden wir ein Dokument namens`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Diese Codezeile lädt das Dokument aus dem angegebenen Verzeichnis.

## Schritt 3: HTML-Speicheroptionen konfigurieren

Um Ressourcen wie CSS und Schriftarten zu exportieren, müssen Sie die`HtmlSaveOptions`Dieser Schritt ist entscheidend, um sicherzustellen, dass Ihre HTML-Ausgabe gut strukturiert ist und die erforderlichen Ressourcen enthält.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Lassen Sie uns aufschlüsseln, was jede Option bewirkt:
- `CssStyleSheetType = CssStyleSheetType.External`: Diese Option gibt an, dass CSS-Stile in einem externen Stylesheet gespeichert werden sollen.
- `ExportFontResources = true`: Dies ermöglicht den Export von Schriftressourcen.
- `ResourceFolder = dataDir + "Resources"`: Gibt den lokalen Ordner an, in dem Ressourcen (wie Schriftarten und CSS-Dateien) gespeichert werden.
- `ResourceFolderAlias = "http://example.com/resources"`: Legt einen Alias für den Ressourcenordner fest, der in der HTML-Datei verwendet wird.

## Schritt 4: Speichern Sie das Dokument als HTML

Nachdem Sie die Speicheroptionen konfiguriert haben, besteht der letzte Schritt darin, das Dokument als HTML-Datei zu speichern. So geht's:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Diese Codezeile speichert das Dokument zusammen mit den exportierten Ressourcen im HTML-Format.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich Ressourcen exportiert, während Sie ein Word-Dokument mit Aspose.Words für .NET als HTML gespeichert haben. Mit dieser leistungsstarken Bibliothek wird die programmgesteuerte Handhabung von Word-Dokumenten zum Kinderspiel. Egal, ob Sie an einer Webanwendung arbeiten oder nur Dokumente für die Offline-Verwendung konvertieren müssen, Aspose.Words bietet alles.

## Häufig gestellte Fragen

### Kann ich Bilder zusammen mit Schriftarten und CSS exportieren?
 Ja, das können Sie! Aspose.Words für .NET unterstützt auch den Export von Bildern. Stellen Sie einfach sicher, dass Sie die`HtmlSaveOptions` entsprechend.

### Gibt es eine Möglichkeit, CSS einzubetten, anstatt ein externes Stylesheet zu verwenden?
 Absolut. Sie können`CssStyleSheetType` Zu`CssStyleSheetType.Embedded` wenn Sie eingebettete Stile bevorzugen.

### Wie kann ich den Namen der HTML-Ausgabedatei anpassen?
 Sie können einen beliebigen Dateinamen im Feld`doc.Save` Methode. Beispielsweise`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Unterstützt Aspose.Words andere Formate außer HTML?
 Ja, es unterstützt verschiedene Formate, darunter PDF, DOCX, TXT und mehr. Schauen Sie sich die[Dokumentation](https://reference.aspose.com/words/net/) für eine vollständige Liste.

### Wo erhalte ich weitere Unterstützung und Ressourcen?
Weitere Hilfe erhalten Sie im[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8) . Detaillierte Dokumentation und Beispiele finden Sie auch auf der[Aspose-Website](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
