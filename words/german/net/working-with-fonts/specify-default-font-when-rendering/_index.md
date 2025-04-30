---
"description": "Erfahren Sie, wie Sie beim Rendern von Word-Dokumenten mit Aspose.Words für .NET eine Standardschriftart festlegen. Sorgen Sie für ein einheitliches Erscheinungsbild der Dokumente auf allen Plattformen."
"linktitle": "Standardschriftart beim Rendern angeben"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Standardschriftart beim Rendern angeben"
"url": "/de/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Standardschriftart beim Rendern angeben

## Einführung

Die korrekte Darstellung Ihrer Word-Dokumente auf verschiedenen Plattformen kann eine Herausforderung sein, insbesondere bei der Schriftkompatibilität. Eine Möglichkeit, ein einheitliches Erscheinungsbild zu gewährleisten, besteht darin, beim Rendern Ihrer Dokumente in PDF oder andere Formate eine Standardschriftart festzulegen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET eine Standardschriftart festlegen, damit Ihre Dokumente unabhängig vom Anzeigeort optimal aussehen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, wollen wir besprechen, was Sie für dieses Tutorial benötigen:

- Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version installiert haben. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
- Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit der C#-Programmierung vertraut sind.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Diese ermöglichen Ihnen den Zugriff auf die Klassen und Methoden, die für die Arbeit mit Aspose.Words erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns nun den Vorgang zum Festlegen einer Standardschriftart in leicht verständliche Schritte unterteilen.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Definieren Sie zunächst den Pfad zu Ihrem Dokumentverzeichnis. Hier werden Ihre Eingabe- und Ausgabedateien gespeichert.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie Ihr Dokument

Laden Sie anschließend das zu rendernde Dokument. In diesem Beispiel verwenden wir die Datei „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Schriftarteinstellungen konfigurieren

Erstellen Sie eine Instanz von `FontSettings` und geben Sie die Standardschriftart an. Wenn die definierte Schriftart beim Rendern nicht gefunden werden kann, verwendet Aspose.Words die ähnlichste verfügbare Schriftart auf dem Computer.

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

Mit diesen Schritten stellen Sie sicher, dass Ihre Word-Dokumente mit einer festgelegten Standardschriftart dargestellt werden und so die Konsistenz über verschiedene Plattformen hinweg gewährleistet ist. Dies ist besonders nützlich für Dokumente, die häufig geteilt oder auf Systemen mit unterschiedlicher Schriftartenverfügbarkeit angezeigt werden.


## Häufig gestellte Fragen

### Warum eine Standardschriftart in Aspose.Words angeben?
Durch die Angabe einer Standardschriftart wird sichergestellt, dass Ihr Dokument auf verschiedenen Plattformen einheitlich angezeigt wird, auch wenn die Originalschriftarten nicht verfügbar sind.

### Was passiert, wenn die Standardschriftart beim Rendern nicht gefunden wird?
Aspose.Words verwendet die auf dem Computer am ehesten verfügbare Schriftart, um das Erscheinungsbild des Dokuments so genau wie möglich beizubehalten.

### Kann ich mehrere Standardschriftarten angeben?
Nein, Sie können nur eine Standardschriftart angeben. Sie können jedoch die Schriftarten für bestimmte Fälle mithilfe der `FontSettings` Klasse.

### Ist Aspose.Words für .NET mit allen Versionen von Word-Dokumenten kompatibel?
Ja, Aspose.Words für .NET unterstützt eine Vielzahl von Word-Dokumentformaten, darunter DOC, DOCX, RTF und mehr.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
Sie erhalten Unterstützung von der Aspose-Community und den Entwicklern auf der [Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}