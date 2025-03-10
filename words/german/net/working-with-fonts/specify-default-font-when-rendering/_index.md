---
title: Beim Rendern die Standardschriftart angeben
linktitle: Beim Rendern die Standardschriftart angeben
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie beim Rendern von Word-Dokumenten mit Aspose.Words für .NET eine Standardschriftart angeben. Stellen Sie ein einheitliches Erscheinungsbild des Dokuments auf allen Plattformen sicher.
weight: 10
url: /de/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beim Rendern die Standardschriftart angeben

## Einführung

Es kann eine Herausforderung sein, sicherzustellen, dass Ihre Word-Dokumente auf verschiedenen Plattformen korrekt dargestellt werden, insbesondere wenn es um die Schriftartkompatibilität geht. Eine Möglichkeit, ein einheitliches Erscheinungsbild beizubehalten, besteht darin, beim Rendern Ihrer Dokumente in PDF oder andere Formate eine Standardschriftart anzugeben. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET eine Standardschriftart festlegen, damit Ihre Dokumente überall gut aussehen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, besprechen wir, was Sie zum Befolgen dieses Tutorials benötigen:

- Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version installiert haben. Sie können es herunterladen[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
- Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit der C#-Programmierung vertraut sind.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Diese ermöglichen Ihnen den Zugriff auf die Klassen und Methoden, die für die Arbeit mit Aspose.Words erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns nun den Vorgang zum Festlegen einer Standardschriftart in leicht verständliche Schritte aufteilen.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Definieren Sie zunächst den Pfad zu Ihrem Dokumentverzeichnis. Hier werden Ihre Eingabe- und Ausgabedateien gespeichert.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie Ihr Dokument

Laden Sie als Nächstes das Dokument, das Sie rendern möchten. In diesem Beispiel verwenden wir eine Datei mit dem Namen „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Schriftarteinstellungen konfigurieren

 Erstellen Sie eine Instanz von`FontSettings` und geben Sie die Standardschriftart an. Wenn die definierte Schriftart beim Rendern nicht gefunden werden kann, verwendet Aspose.Words die ähnlichste verfügbare Schriftart auf dem Computer.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Schritt 4: Schrifteinstellungen auf das Dokument anwenden

Weisen Sie Ihrem Dokument die konfigurierten Schrifteinstellungen zu.

```csharp
doc.FontSettings = fontSettings;
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im gewünschten Format. In diesem Fall speichern wir es als PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Abschluss

Wenn Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Word-Dokumente mit einer angegebenen Standardschriftart wiedergegeben werden und so die Konsistenz über verschiedene Plattformen hinweg gewahrt bleibt. Dies kann insbesondere bei Dokumenten nützlich sein, die weit verbreitet sind oder auf Systemen mit unterschiedlicher Schriftartenverfügbarkeit angezeigt werden.


## Häufig gestellte Fragen

### Warum eine Standardschriftart in Aspose.Words angeben?
Durch die Angabe einer Standardschriftart wird sichergestellt, dass Ihr Dokument auf verschiedenen Plattformen einheitlich angezeigt wird, auch wenn die Originalschriftarten nicht verfügbar sind.

### Was passiert, wenn die Standardschriftart beim Rendern nicht gefunden wird?
Aspose.Words verwendet die auf dem Computer am ehesten verfügbare Schriftart, um das Erscheinungsbild des Dokuments so genau wie möglich beizubehalten.

### Kann ich mehrere Standardschriftarten angeben?
 Nein, Sie können nur eine Standardschriftart angeben. Sie können jedoch die Schriftartenersetzung für bestimmte Fälle mithilfe der`FontSettings` Klasse.

### Ist Aspose.Words für .NET mit allen Versionen von Word-Dokumenten kompatibel?
Ja, Aspose.Words für .NET unterstützt eine breite Palette von Word-Dokumentformaten, darunter DOC, DOCX, RTF und mehr.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
 Sie erhalten Unterstützung von der Aspose-Community und den Entwicklern auf der[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
