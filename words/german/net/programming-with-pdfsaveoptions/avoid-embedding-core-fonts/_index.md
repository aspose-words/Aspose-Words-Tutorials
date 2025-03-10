---
title: Reduzieren Sie die PDF-Dateigröße, indem Sie keine Kernschriftarten einbetten
linktitle: Reduzieren Sie die PDF-Dateigröße, indem Sie keine Kernschriftarten einbetten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie die PDF-Dateigröße reduzieren, indem Sie mit Aspose.Words für .NET keine Kernschriftarten einbetten. Folgen Sie unserer Schritt-für-Schritt-Anleitung zur Optimierung Ihrer PDFs.
weight: 10
url: /de/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reduzieren Sie die PDF-Dateigröße, indem Sie keine Kernschriftarten einbetten

## Einführung

Haben Sie sich schon einmal gefragt, warum Ihre PDF-Dateien so groß sind? Nun, Sie sind nicht allein. Ein häufiger Grund dafür ist das Einbetten von Kernschriften wie Arial und Times New Roman. Glücklicherweise bietet Aspose.Words für .NET eine raffinierte Möglichkeit, dieses Problem anzugehen. In diesem Tutorial zeige ich Ihnen, wie Sie die Größe Ihrer PDF-Datei reduzieren können, indem Sie das Einbetten dieser Kernschriften vermeiden. Lassen Sie uns direkt loslegen!

## Voraussetzungen

Bevor wir uns auf diese spannende Reise begeben, stellen wir sicher, dass Sie alles haben, was Sie brauchen. Hier ist eine kurze Checkliste:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Wenn Sie es noch nicht haben, können Sie es herunterladen[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Sie benötigen eine Entwicklungsumgebung wie Visual Studio.
- Ein Word-Dokument: Für dieses Tutorial verwenden wir ein Word-Dokument (z. B. „Rendering.docx“).
- Grundlegende C#-Kenntnisse: Grundlegende Kenntnisse in C# erleichtern Ihnen den weiteren Verlauf.

Gut, da wir nun bereit sind, können wir ans Eingemachte gehen!

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dieser Schritt stellt sicher, dass wir Zugriff auf alle Aspose.Words-Funktionen haben, die wir benötigen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Initialisieren Sie Ihr Dokumentverzeichnis

Bevor wir mit der Bearbeitung unseres Dokuments beginnen, müssen wir das Verzeichnis angeben, in dem unsere Dokumente gespeichert sind. Dies ist für den Zugriff auf die Dateien wichtig.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Word-Dokument befindet.

## Schritt 2: Laden Sie das Word-Dokument

Als nächstes müssen wir das Word-Dokument laden, das wir in PDF konvertieren möchten. In diesem Beispiel verwenden wir ein Dokument namens „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Diese Codezeile lädt das Dokument in den Speicher, bereit zur weiteren Verarbeitung.

## Schritt 3: PDF-Speicheroptionen konfigurieren

Jetzt kommt der magische Teil! Wir konfigurieren die PDF-Speicheroptionen, um das Einbetten von Kernschriftarten zu vermeiden. Dies ist der entscheidende Schritt, der dabei hilft, die PDF-Dateigröße zu reduzieren.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Einstellung`UseCoreFonts` Zu`true` stellt sicher, dass Kernschriftarten wie Arial und Times New Roman nicht in das PDF eingebettet werden, was die Dateigröße erheblich reduziert.

## Schritt 4: Speichern Sie das Dokument als PDF

Abschließend speichern wir das Word-Dokument mit den konfigurierten Speicheroptionen als PDF. Dieser Schritt erzeugt die PDF-Datei ohne Einbettung der Kernschriftarten.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

Und da haben Sie es! Ihre PDF-Datei ist jetzt ohne diese sperrigen Kernschriftarten im angegebenen Verzeichnis gespeichert.

## Abschluss

Mit Aspose.Words für .NET ist die Reduzierung der PDF-Dateigröße ein Kinderspiel. Indem Sie die Einbettung von Kernschriftarten vermeiden, können Sie die Dateigröße erheblich verringern und so das Teilen und Speichern Ihrer Dokumente vereinfachen. Ich hoffe, dieses Tutorial war hilfreich und hat Ihnen ein klares Verständnis des Prozesses vermittelt. Denken Sie daran, kleine Optimierungen können einen großen Unterschied machen!

## Häufig gestellte Fragen

### Warum sollte ich das Einbetten von Kernschriftarten in PDFs vermeiden?
Durch das Vermeiden der Einbettung von Kernschriftarten wird die Dateigröße reduziert, was die Weitergabe und Speicherung erleichtert.

### Kann ich das PDF auch ohne eingebettete Kernschriftarten korrekt anzeigen?
Ja, Kernschriftarten wie Arial und Times New Roman sind grundsätzlich auf den meisten Systemen verfügbar.

### Was ist, wenn ich benutzerdefinierte Schriftarten einbetten muss?
 Sie können die`PdfSaveOptions`um nach Bedarf bestimmte Schriftarten einzubetten.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET erfordert eine Lizenz. Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/).

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
