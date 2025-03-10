---
title: Gliederungsoptionen in einem PDF-Dokument festlegen
linktitle: Gliederungsoptionen in einem PDF-Dokument festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Gliederungsoptionen in einem PDF-Dokument festlegen. Verbessern Sie die PDF-Navigation, indem Sie Überschriftenebenen und erweiterte Gliederungen konfigurieren.
weight: 10
url: /de/net/programming-with-pdfsaveoptions/set-outline-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gliederungsoptionen in einem PDF-Dokument festlegen

## Einführung

Beim Arbeiten mit Dokumenten, insbesondere für berufliche oder akademische Zwecke, ist es entscheidend, Ihre Inhalte effektiv zu organisieren. Eine Möglichkeit, die Benutzerfreundlichkeit Ihrer PDF-Dokumente zu verbessern, besteht darin, Gliederungsoptionen festzulegen. Gliederungen oder Lesezeichen ermöglichen Benutzern eine effiziente Navigation durch das Dokument, genau wie Kapitel in einem Buch. In diesem Handbuch erfahren Sie, wie Sie diese Optionen mit Aspose.Words für .NET festlegen können, um sicherzustellen, dass Ihre PDF-Dateien gut organisiert und benutzerfreundlich sind.

## Voraussetzungen

Bevor Sie beginnen, müssen Sie Folgendes sicherstellen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Wenn nicht, können Sie[Laden Sie hier die neueste Version herunter](https://releases.aspose.com/words/net/).
2. Eine .NET-Entwicklungsumgebung: Sie benötigen eine funktionierende .NET-Entwicklungsumgebung wie beispielsweise Visual Studio.
3. Grundlegende Kenntnisse in C#: Wenn Sie mit der Programmiersprache C# vertraut sind, können Sie den Schritten problemlos folgen.
4. Ein Word-Dokument: Halten Sie ein Word-Dokument bereit, das Sie in ein PDF konvertieren.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren. Hier fügen Sie die Aspose.Words-Bibliothek ein, um mit Ihrem Dokument zu interagieren. So richten Sie sie ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Dokumentpfad festlegen

Zu Beginn müssen Sie den Pfad zu Ihrem Word-Dokument angeben. Dies ist die Datei, die Sie in ein PDF mit Gliederungsoptionen konvertieren möchten. 

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Ersetzen Sie im obigen Codeausschnitt`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. So weiß das Programm, wo das Word-Dokument zu finden ist.

## Schritt 2: PDF-Speicheroptionen konfigurieren

 Als nächstes müssen Sie die PDF-Speicheroptionen konfigurieren. Dazu gehört die Einstellung, wie Konturen in der PDF-Ausgabe behandelt werden sollen. Sie verwenden die`PdfSaveOptions` Klasse, um dies zu tun.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
```

Legen wir nun die Gliederungsoptionen fest. 

### Gliederungsebenen für Überschriften festlegen

 Der`HeadingsOutlineLevels` Die Eigenschaft definiert, wie viele Überschriftenebenen in der PDF-Gliederung enthalten sein sollen. Wenn Sie den Wert beispielsweise auf 3 setzen, werden bis zu drei Überschriftenebenen in die PDF-Gliederung aufgenommen.

```csharp
saveOptions.OutlineOptions.HeadingsOutlineLevels = 3;
```

### Erweiterte Gliederungsebenen festlegen

 Der`ExpandedOutlineLevels`Diese Eigenschaft steuert, wie viele Gliederungsebenen standardmäßig erweitert werden sollen, wenn die PDF-Datei geöffnet wird. Wenn Sie diese Eigenschaft auf 1 setzen, werden die Überschriften der obersten Ebene erweitert, sodass die Hauptabschnitte klarer zu sehen sind.

```csharp
saveOptions.OutlineOptions.ExpandedOutlineLevels = 1;
```

## Schritt 3: Speichern Sie das Dokument als PDF

 Wenn Sie die Optionen konfiguriert haben, können Sie das Dokument als PDF speichern. Verwenden Sie die`Save` Methode der`Document` Klasse und übergeben Sie den Dateipfad und die Speicheroptionen.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SetOutlineOptions.pdf", saveOptions);
```

Diese Codezeile speichert Ihr Word-Dokument als PDF und wendet dabei die von Ihnen konfigurierten Gliederungsoptionen an. 

## Abschluss

Das Festlegen von Gliederungsoptionen in einem PDF-Dokument kann dessen Navigation erheblich verbessern und es Benutzern erleichtern, die benötigten Abschnitte zu finden und darauf zuzugreifen. Mit Aspose.Words für .NET können Sie diese Einstellungen ganz einfach an Ihre Anforderungen anpassen und so sicherstellen, dass Ihre PDF-Dokumente so benutzerfreundlich wie möglich sind.

## Häufig gestellte Fragen

### Welchen Zweck hat das Festlegen von Gliederungsoptionen in einer PDF-Datei?

Durch das Festlegen von Gliederungsoptionen können Benutzer leichter in großen PDF-Dokumenten navigieren, indem sie ein strukturiertes, anklickbares Inhaltsverzeichnis bereitstellen.

### Kann ich für unterschiedliche Abschnitte in meinem Dokument unterschiedliche Überschriftenebenen festlegen?

Nein, die Gliederungseinstellungen gelten global für das gesamte Dokument. Sie können Ihr Dokument jedoch mit entsprechenden Überschriftenebenen strukturieren, um einen ähnlichen Effekt zu erzielen.

### Wie kann ich die Änderungen in der Vorschau anzeigen, bevor ich die PDF-Datei speichere?

Um zu prüfen, wie die Gliederung aussieht, können Sie PDF-Viewer verwenden, die die Gliederungsnavigation unterstützen. Einige Anwendungen bieten hierfür eine Vorschaufunktion.

### Ist es möglich, die Gliederung nach dem Speichern der PDF-Datei zu entfernen?

Ja, Sie können Konturen mithilfe einer PDF-Bearbeitungssoftware entfernen, dies ist mit Aspose.Words jedoch nicht direkt möglich, nachdem die PDF-Datei erstellt wurde.

### Welche anderen PDF-Speicheroptionen kann ich mit Aspose.Words konfigurieren?

Aspose.Words bietet verschiedene Optionen, beispielsweise das Festlegen der PDF-Konformitätsstufe, das Einbetten von Schriftarten und das Anpassen der Bildqualität.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
