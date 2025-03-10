---
title: Textwasserzeichen mit bestimmten Optionen hinzufügen
linktitle: Textwasserzeichen mit bestimmten Optionen hinzufügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Ihren Word-Dokumenten ein Textwasserzeichen mit bestimmten Optionen hinzufügen. Passen Sie Schriftart, Größe, Farbe und Layout einfach an.
weight: 10
url: /de/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Textwasserzeichen mit bestimmten Optionen hinzufügen

## Einführung

Wasserzeichen können eine stilvolle und funktionale Ergänzung zu Ihren Word-Dokumenten sein und können dazu dienen, Dokumente als vertraulich zu kennzeichnen oder ihnen eine persönliche Note zu verleihen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET einem Word-Dokument ein Textwasserzeichen hinzufügen. Wir werden uns mit den spezifischen Optionen befassen, die Sie konfigurieren können, wie z. B. Schriftfamilie, Schriftgröße, Farbe und Layout. Am Ende können Sie das Wasserzeichen Ihres Dokuments genau an Ihre Anforderungen anpassen. Also schnappen Sie sich Ihren Code-Editor und legen Sie los!

## Voraussetzungen

Bevor es losgeht, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:

1.  Aspose.Words für .NET-Bibliothek: Sie müssen die Aspose.Words-Bibliothek installiert haben. Wenn Sie dies noch nicht getan haben, können Sie es von der[Aspose.Words Download-Link](https://releases.aspose.com/words/net/).
2. Grundlegende Kenntnisse in C#: In diesem Tutorial wird C# als Programmiersprache verwendet. Grundlegende Kenntnisse der C#-Syntax sind hilfreich.
3. .NET-Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine Entwicklungsumgebung (wie Visual Studio) eingerichtet haben, in der Sie Ihre .NET-Anwendungen erstellen und ausführen können.

## Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die erforderlichen Namespaces in Ihr Projekt einbinden. Folgendes müssen Sie importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Schritt 1: Richten Sie Ihr Dokument ein

 Zuerst müssen Sie das Dokument laden, mit dem Sie arbeiten möchten. Für dieses Tutorial verwenden wir ein Beispieldokument namens`Document.docx`. Stellen Sie sicher, dass dieses Dokument in Ihrem angegebenen Verzeichnis vorhanden ist.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 In diesem Schritt definieren Sie das Verzeichnis, in dem sich Ihr Dokument befindet und laden es in eine Instanz des`Document` Klasse.

## Schritt 2: Wasserzeichenoptionen konfigurieren

Konfigurieren Sie als Nächstes die Optionen für Ihr Textwasserzeichen. Sie können verschiedene Aspekte anpassen, z. B. Schriftfamilie, Schriftgröße, Farbe und Layout. Lassen Sie uns diese Optionen einrichten.

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
- `FontSize`: Legt die Größe des Wasserzeichentextes fest.
- `Color`: Definiert die Farbe des Wasserzeichentextes.
- `Layout`Bestimmt die Ausrichtung des Wasserzeichens (horizontal oder diagonal).
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

Das Hinzufügen eines Textwasserzeichens zu Ihren Word-Dokumenten mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, wenn Sie ihn in überschaubare Schritte aufteilen. In diesem Tutorial haben Sie gelernt, wie Sie verschiedene Wasserzeichenoptionen konfigurieren, darunter Schriftart, Größe, Farbe, Layout und Transparenz. Mit diesen Fähigkeiten können Sie Ihre Dokumente jetzt besser an Ihre Anforderungen anpassen oder wichtige Informationen wie Vertraulichkeit oder Branding einfügen.

 Wenn Sie Fragen haben oder weitere Hilfe benötigen, schauen Sie sich bitte die[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) oder besuchen Sie die[Aspose Support Forum](https://forum.aspose.com/c/words/8) für weitere Hilfe.

## Häufig gestellte Fragen

### Kann ich für das Wasserzeichen verschiedene Schriftarten verwenden?

 Ja, Sie können jede auf Ihrem System installierte Schriftart auswählen, indem Sie die`FontFamily` Eigentum in der`TextWatermarkOptions`.

### Wie ändere ich die Farbe des Wasserzeichens?

 Sie können die Farbe des Wasserzeichens ändern, indem Sie die`Color` Eigentum in der`TextWatermarkOptions` zu jedem`System.Drawing.Color` Wert.

### Ist es möglich, einem Dokument mehrere Wasserzeichen hinzuzufügen?

Aspose.Words unterstützt das Hinzufügen jeweils eines Wasserzeichens. Um mehrere Wasserzeichen hinzuzufügen, müssen Sie diese nacheinander erstellen und anwenden.

### Kann ich die Position des Wasserzeichens anpassen?

 Der`WatermarkLayout`-Eigenschaft bestimmt die Ausrichtung, aber genaue Positionierungsanpassungen werden nicht direkt unterstützt. Möglicherweise müssen Sie für eine genaue Platzierung andere Techniken verwenden.

### Was ist, wenn ich ein halbtransparentes Wasserzeichen benötige?

 Legen Sie die`IsSemitrasparent`Eigentum an`true` um Ihr Wasserzeichen halbtransparent zu machen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
