---
title: Schriftartenersetzung aktivieren/deaktivieren
linktitle: Schriftartenersetzung aktivieren/deaktivieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie die Schriftartenersetzung in Word-Dokumenten mit Aspose.Words für .NET aktivieren oder deaktivieren. Stellen Sie sicher, dass Ihre Dokumente auf allen Plattformen einheitlich aussehen.
weight: 10
url: /de/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftartenersetzung aktivieren/deaktivieren

## Einführung

Haben Sie sich schon einmal in einer Situation befunden, in der Ihre sorgfältig ausgewählten Schriftarten in einem Word-Dokument ersetzt werden, wenn Sie es auf einem anderen Computer anzeigen? Ärgerlich, oder? Dies geschieht aufgrund der Schriftartenersetzung, einem Prozess, bei dem das System eine fehlende Schriftart durch eine verfügbare ersetzt. Aber keine Sorge! Mit Aspose.Words für .NET können Sie die Schriftartenersetzung einfach verwalten und steuern. In diesem Tutorial führen wir Sie durch die Schritte zum Aktivieren oder Deaktivieren der Schriftartenersetzung in Ihren Word-Dokumenten, damit Ihre Dokumente immer so aussehen, wie Sie es möchten.

## Voraussetzungen

Bevor wir uns in die einzelnen Schritte stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Laden Sie die neueste Version herunter[Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Jede Version, die .NET unterstützt.
- Grundkenntnisse in C#: Diese helfen Ihnen dabei, den Codebeispielen zu folgen.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Fügen Sie diese oben in Ihrer C#-Datei hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns den Prozess nun in einfache, überschaubare Schritte unterteilen.

## Schritt 1: Richten Sie Ihr Projekt ein

Richten Sie zunächst ein neues Projekt in Visual Studio ein und fügen Sie einen Verweis auf die Aspose.Words for .NET-Bibliothek hinzu. Wenn Sie dies noch nicht getan haben, laden Sie sie von der[Aspose-Website](https://releases.aspose.com/words/net/).

## Schritt 2: Laden Sie Ihr Dokument

Laden Sie als Nächstes das Dokument, mit dem Sie arbeiten möchten. So gehen Sie dabei vor:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. Dieser Code lädt das Dokument in den Speicher, damit Sie es bearbeiten können.

## Schritt 3: Schriftarteinstellungen konfigurieren

 Erstellen wir nun ein`FontSettings` Objekt zum Verwalten der Schriftartenersetzungseinstellungen:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Schritt 4: Standardmäßige Schriftartenersetzung festlegen

Legen Sie die Standardschriftart-Ersetzung auf eine Schriftart Ihrer Wahl fest. Diese Schriftart wird verwendet, wenn die Originalschriftart nicht verfügbar ist:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In diesem Beispiel verwenden wir Arial als Standardschriftart.

## Schritt 5: Deaktivieren Sie die Schriftinfo-Ersetzung

Um die Schriftinfo-Ersetzung zu deaktivieren, die das System daran hindert, fehlende Schriftarten durch verfügbare zu ersetzen, verwenden Sie den folgenden Code:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Schritt 6: Schrifteinstellungen auf das Dokument anwenden

Wenden Sie nun diese Einstellungen auf Ihr Dokument an:

```csharp
doc.FontSettings = fontSettings;
```

## Schritt 7: Speichern Sie Ihr Dokument

Speichern Sie abschließend Ihr geändertes Dokument. Sie können es in jedem beliebigen Format speichern. Für dieses Tutorial speichern wir es als PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie die Schriftartenersetzung in Ihren Word-Dokumenten mit Aspose.Words für .NET problemlos steuern. Dadurch wird sichergestellt, dass Ihre Dokumente unabhängig vom Anzeigeort ihr beabsichtigtes Erscheinungsbild beibehalten.

## Häufig gestellte Fragen

### Kann ich als Ersatz andere Schriftarten als Arial verwenden?

 Natürlich! Sie können jede auf Ihrem System verfügbare Schriftart angeben, indem Sie den Schriftartnamen im`DefaultFontName` Eigentum.

### Was passiert, wenn die angegebene Standardschriftart nicht verfügbar ist?

Wenn die Standardschriftart nicht verfügbar ist, verwendet Aspose.Words einen Fallback-Mechanismus des Systems, um einen geeigneten Ersatz zu finden.

### Kann ich die Schriftartenersetzung nach der Deaktivierung wieder aktivieren?

 Ja, Sie können die`Enabled` Eigentum von`FontInfoSubstitution` zurück zu`true` , wenn Sie die Schriftartenersetzung wieder aktivieren möchten.

### Gibt es eine Möglichkeit zu überprüfen, welche Schriftarten ersetzt werden?

Ja, Aspose.Words bietet Methoden zum Protokollieren und Verfolgen von Schriftartenersetzungen, sodass Sie sehen können, welche Schriftarten ersetzt werden.

### Kann ich diese Methode auch für andere Dokumentformate außer DOCX verwenden?

Auf jeden Fall! Aspose.Words unterstützt verschiedene Formate und Sie können diese Schrifteinstellungen auf jedes unterstützte Format anwenden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
