---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Ihren Word-Dokumenten ein Textwasserzeichen mit bestimmten Optionen hinzufügen. Passen Sie Schriftart, Größe, Farbe und Layout einfach an."
"linktitle": "Textwasserzeichen mit bestimmten Optionen hinzufügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Textwasserzeichen mit bestimmten Optionen hinzufügen"
"url": "/de/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Textwasserzeichen mit bestimmten Optionen hinzufügen

## Einführung

Wasserzeichen können eine stilvolle und funktionale Ergänzung für Ihre Word-Dokumente sein und dienen dazu, Dokumente als vertraulich zu kennzeichnen oder ihnen eine persönliche Note zu verleihen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET ein Textwasserzeichen zu einem Word-Dokument hinzufügen. Wir gehen auf die spezifischen Konfigurationsoptionen ein, wie z. B. Schriftfamilie, Schriftgröße, Farbe und Layout. Am Ende können Sie das Wasserzeichen Ihres Dokuments genau an Ihre Bedürfnisse anpassen. Also, schnappen Sie sich Ihren Code-Editor und los geht’s!

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:

1. Aspose.Words für .NET-Bibliothek: Sie benötigen die Aspose.Words-Bibliothek. Falls noch nicht geschehen, können Sie sie von der [Aspose.Words Download-Link](https://releases.aspose.com/words/net/).
2. Grundlegende Kenntnisse in C#: Dieses Tutorial verwendet C# als Programmiersprache. Grundkenntnisse der C#-Syntax sind hilfreich.
3. .NET-Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine Entwicklungsumgebung (wie Visual Studio) eingerichtet haben, in der Sie Ihre .NET-Anwendungen erstellen und ausführen können.

## Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die erforderlichen Namespaces in Ihr Projekt einbinden. Folgendes müssen Sie importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Schritt 1: Richten Sie Ihr Dokument ein

Zuerst müssen Sie das Dokument laden, mit dem Sie arbeiten möchten. Für dieses Tutorial verwenden wir ein Beispieldokument namens `Document.docx`. Stellen Sie sicher, dass dieses Dokument in Ihrem angegebenen Verzeichnis vorhanden ist.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

In diesem Schritt definieren Sie das Verzeichnis, in dem sich Ihr Dokument befindet und laden es in eine Instanz des `Document` Klasse.

## Schritt 2: Wasserzeichenoptionen konfigurieren

Konfigurieren Sie anschließend die Optionen für Ihr Textwasserzeichen. Sie können verschiedene Aspekte wie Schriftart, Schriftgröße, Farbe und Layout anpassen. Richten wir diese Optionen ein.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Die einzelnen Optionen bewirken Folgendes:
- `FontFamily`: Gibt die Schriftart des Wasserzeichentextes an.
- `FontSize`Legt die Größe des Wasserzeichentextes fest.
- `Color`: Definiert die Farbe des Wasserzeichentextes.
- `Layout`: Bestimmt die Ausrichtung des Wasserzeichens (horizontal oder diagonal).
- `IsSemitrasparent`: Legt fest, ob das Wasserzeichen halbtransparent ist.

## Schritt 3: Wasserzeichentext hinzufügen

Wenden Sie nun das Wasserzeichen mit den zuvor konfigurierten Optionen auf Ihr Dokument an. In diesem Schritt setzen Sie den Wasserzeichentext auf „Test“ und wenden die von Ihnen definierten Optionen an.

```csharp
doc.Watermark.SetText("Test", options);
```

Diese Codezeile fügt dem Dokument unter Anwendung der angegebenen Optionen das Wasserzeichen mit dem Text „Test“ hinzu.

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend mit dem neuen Wasserzeichen. Sie können es unter einem neuen Namen speichern, um ein Überschreiben des Originaldokuments zu vermeiden.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Dieser Codeausschnitt speichert das geänderte Dokument unter einem neuen Dateinamen im selben Verzeichnis.

## Abschluss

Das Hinzufügen eines Textwasserzeichens zu Ihren Word-Dokumenten mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, wenn Sie ihn in überschaubare Schritte unterteilen. In diesem Tutorial haben Sie gelernt, wie Sie verschiedene Wasserzeichenoptionen konfigurieren, darunter Schriftart, Größe, Farbe, Layout und Transparenz. Mit diesen Kenntnissen können Sie Ihre Dokumente nun besser an Ihre Bedürfnisse anpassen oder wichtige Informationen wie Vertraulichkeit oder Branding hinzufügen.

Wenn Sie Fragen haben oder weitere Hilfe benötigen, schauen Sie sich bitte die [Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) oder besuchen Sie die [Aspose Support Forum](https://forum.aspose.com/c/words/8) für weitere Hilfe.

## Häufig gestellte Fragen

### Kann ich für das Wasserzeichen verschiedene Schriftarten verwenden?

Ja, Sie können jede auf Ihrem System installierte Schriftart auswählen, indem Sie die `FontFamily` Eigentum in der `TextWatermarkOptions`.

### Wie ändere ich die Farbe des Wasserzeichens?

Sie können die Farbe des Wasserzeichens ändern, indem Sie die `Color` Eigentum in der `TextWatermarkOptions` zu jedem `System.Drawing.Color` Wert.

### Ist es möglich, einem Dokument mehrere Wasserzeichen hinzuzufügen?

Aspose.Words unterstützt das Hinzufügen jeweils eines Wasserzeichens. Um mehrere Wasserzeichen hinzuzufügen, müssen Sie diese nacheinander erstellen und anwenden.

### Kann ich die Position des Wasserzeichens anpassen?

Der `WatermarkLayout` Die Eigenschaft bestimmt die Ausrichtung, präzise Positionierungsanpassungen werden jedoch nicht direkt unterstützt. Für eine exakte Platzierung müssen Sie möglicherweise andere Techniken verwenden.

### Was ist, wenn ich ein halbtransparentes Wasserzeichen benötige?

Legen Sie die `IsSemitrasparent` Eigentum zu `true` um Ihr Wasserzeichen halbtransparent zu machen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}