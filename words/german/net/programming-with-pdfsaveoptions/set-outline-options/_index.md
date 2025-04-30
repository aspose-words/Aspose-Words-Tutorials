---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Gliederungsoptionen in einem PDF-Dokument festlegen. Verbessern Sie die PDF-Navigation durch die Konfiguration von Überschriftenebenen und erweiterten Gliederungen."
"linktitle": "Gliederungsoptionen in einem PDF-Dokument festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Gliederungsoptionen in einem PDF-Dokument festlegen"
"url": "/de/net/programming-with-pdfsaveoptions/set-outline-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gliederungsoptionen in einem PDF-Dokument festlegen

## Einführung

Bei der Arbeit mit Dokumenten, insbesondere für berufliche oder akademische Zwecke, ist die effektive Organisation Ihrer Inhalte entscheidend. Eine Möglichkeit, die Benutzerfreundlichkeit Ihrer PDF-Dokumente zu verbessern, ist das Festlegen von Gliederungsoptionen. Gliederungen oder Lesezeichen ermöglichen Benutzern eine effiziente Navigation durch das Dokument, ähnlich wie Kapitel in einem Buch. In dieser Anleitung erfahren Sie, wie Sie diese Optionen mit Aspose.Words für .NET festlegen und so sicherstellen, dass Ihre PDF-Dateien gut organisiert und benutzerfreundlich sind.

## Voraussetzungen

Bevor Sie beginnen, müssen Sie Folgendes sicherstellen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Falls nicht, können Sie [Laden Sie hier die neueste Version herunter](https://releases.aspose.com/words/net/).
2. Eine .NET-Entwicklungsumgebung: Sie benötigen eine funktionierende .NET-Entwicklungsumgebung, beispielsweise Visual Studio.
3. Grundlegende Kenntnisse in C#: Wenn Sie mit der Programmiersprache C# vertraut sind, können Sie problemlos folgen.
4. Ein Word-Dokument: Halten Sie ein Word-Dokument bereit, das Sie in ein PDF konvertieren.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces importieren. Hier binden Sie die Bibliothek Aspose.Words ein, um mit Ihrem Dokument zu interagieren. So richten Sie sie ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Dokumentpfad festlegen

Geben Sie zunächst den Pfad zu Ihrem Word-Dokument an. Dies ist die Datei, die Sie in ein PDF mit Gliederungsoptionen konvertieren möchten. 

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Ersetzen Sie im obigen Codeausschnitt `"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. Dadurch teilt das Programm mit, wo sich das Word-Dokument befindet.

## Schritt 2: PDF-Speicheroptionen konfigurieren

Als Nächstes müssen Sie die PDF-Speicheroptionen konfigurieren. Dazu gehört auch die Einstellung, wie Konturen in der PDF-Ausgabe behandelt werden sollen. Sie verwenden dazu die `PdfSaveOptions` Klasse, um dies zu tun.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
```

Legen wir nun die Gliederungsoptionen fest. 

### Gliederungsebenen für Überschriften festlegen

Der `HeadingsOutlineLevels` Die Eigenschaft definiert, wie viele Überschriftenebenen in der PDF-Gliederung enthalten sein sollen. Wenn Sie beispielsweise den Wert 3 festlegen, werden bis zu drei Überschriftenebenen in die PDF-Gliederung aufgenommen.

```csharp
saveOptions.OutlineOptions.HeadingsOutlineLevels = 3;
```

### Erweiterte Gliederungsebenen festlegen

Der `ExpandedOutlineLevels` Die Eigenschaft steuert, wie viele Gliederungsebenen beim Öffnen der PDF-Datei standardmäßig erweitert werden sollen. Bei einem Wert von 1 werden die Überschriften der obersten Ebene erweitert, wodurch die Hauptabschnitte klarer dargestellt werden.

```csharp
saveOptions.OutlineOptions.ExpandedOutlineLevels = 1;
```

## Schritt 3: Speichern Sie das Dokument als PDF

Wenn Sie die Optionen konfiguriert haben, können Sie das Dokument als PDF speichern. Verwenden Sie die `Save` Methode der `Document` Klasse und geben Sie den Dateipfad und die Speicheroptionen ein.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SetOutlineOptions.pdf", saveOptions);
```

Diese Codezeile speichert Ihr Word-Dokument als PDF und wendet dabei die von Ihnen konfigurierten Gliederungsoptionen an. 

## Abschluss

Das Festlegen von Gliederungsoptionen in einem PDF-Dokument kann dessen Navigation erheblich verbessern und Benutzern das Auffinden und Zugreifen auf die benötigten Abschnitte erleichtern. Mit Aspose.Words für .NET können Sie diese Einstellungen ganz einfach an Ihre Bedürfnisse anpassen und so Ihre PDF-Dokumente so benutzerfreundlich wie möglich gestalten.

## Häufig gestellte Fragen

### Welchen Zweck hat das Festlegen von Gliederungsoptionen in einer PDF-Datei?

Durch das Festlegen von Gliederungsoptionen können Benutzer leichter in großen PDF-Dokumenten navigieren, indem sie ein strukturiertes, anklickbares Inhaltsverzeichnis bereitstellen.

### Kann ich für verschiedene Abschnitte in meinem Dokument unterschiedliche Überschriftenebenen festlegen?

Nein, die Gliederungseinstellungen gelten global für das gesamte Dokument. Sie können Ihr Dokument jedoch mit entsprechenden Überschriftenebenen strukturieren, um einen ähnlichen Effekt zu erzielen.

### Wie kann ich eine Vorschau der Änderungen anzeigen, bevor ich die PDF-Datei speichere?

Mit PDF-Viewern, die die Gliederungsnavigation unterstützen, können Sie die Darstellung der Gliederung überprüfen. Einige Anwendungen bieten hierfür eine Vorschaufunktion.

### Ist es möglich, die Gliederung nach dem Speichern der PDF-Datei zu entfernen?

Ja, Sie können Konturen mithilfe einer PDF-Bearbeitungssoftware entfernen, dies ist jedoch mit Aspose.Words nicht direkt möglich, sobald die PDF-Datei erstellt ist.

### Welche anderen PDF-Speicheroptionen kann ich mit Aspose.Words konfigurieren?

Aspose.Words bietet verschiedene Optionen, z. B. das Festlegen der PDF-Konformitätsstufe, das Einbetten von Schriftarten und das Anpassen der Bildqualität.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}