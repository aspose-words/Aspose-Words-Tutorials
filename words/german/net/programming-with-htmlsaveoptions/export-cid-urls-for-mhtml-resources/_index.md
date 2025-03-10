---
title: CID-URLs für MHTML-Ressourcen exportieren
linktitle: CID-URLs für MHTML-Ressourcen exportieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET Cid-URLs für MHTML-Ressourcen exportieren. Perfekt für Entwickler aller Niveaus.
weight: 10
url: /de/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CID-URLs für MHTML-Ressourcen exportieren

## Einführung

Sind Sie bereit, die Kunst des Exportierens von Cid-URLs für MHTML-Ressourcen mit Aspose.Words für .NET zu meistern? Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieser umfassende Leitfaden führt Sie durch jeden Schritt. Am Ende dieses Artikels haben Sie ein kristallklares Verständnis dafür, wie Sie MHTML-Ressourcen in Ihren Word-Dokumenten effizient handhaben können. Tauchen Sie ein!

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version von Aspose.Words für .NET installiert haben. Wenn nicht, können Sie es hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Eine Entwicklungsumgebung wie Visual Studio.
- Grundkenntnisse in C#: Obwohl ich Sie durch jeden Schritt führe, sind grundlegende Kenntnisse in C# von Vorteil.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dieser Schritt bereitet den Boden für unser Tutorial:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang nun in einfache, überschaubare Schritte unterteilen. Jeder Schritt enthält eine ausführliche Erklärung, damit Sie ihn mühelos nachvollziehen können.

## Schritt 1: Einrichten Ihres Projekts

### Schritt 1.1: Neues Projekt erstellen
Öffnen Sie Visual Studio und erstellen Sie ein neues C#-Projekt. Wählen Sie der Einfachheit halber die Vorlage „Konsolen-App“.

### Schritt 1.2: Aspose.Words für .NET-Referenz hinzufügen
Um Aspose.Words für .NET zu verwenden, müssen Sie einen Verweis auf die Aspose.Words-Bibliothek hinzufügen. Sie können dies über den NuGet-Paketmanager tun:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt.
2. Wählen Sie „NuGet-Pakete verwalten“ aus.
3. Suchen Sie nach „Aspose.Words“ und installieren Sie es.

## Schritt 2: Laden des Word-Dokuments

### Schritt 2.1: Dokumentverzeichnis festlegen
Geben Sie den Pfad zu Ihrem Dokumentverzeichnis an. Hier liegt Ihr Word-Dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

### Schritt 2.2: Laden Sie das Dokument
Laden Sie Ihr Word-Dokument in das Projekt.

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## Schritt 3: Konfigurieren der HTML-Speicheroptionen

 Erstellen Sie eine Instanz von`HtmlSaveOptions` um anzupassen, wie Ihr Dokument als MHTML gespeichert wird.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml` gibt an, dass das Ausgabeformat MHTML ist.
- `PrettyFormat = true` stellt sicher, dass die Ausgabe sauber formatiert ist.
- `ExportCidUrlsForMhtmlResources = true` ermöglicht den Export von Cid-URLs für MHTML-Ressourcen.

### Schritt 4: Speichern des Dokuments als MHTML

Schritt 4.1: Speichern des Dokuments
Speichern Sie Ihr Dokument mit den konfigurierten Optionen als MHTML-Datei.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich Cid-URLs für MHTML-Ressourcen mit Aspose.Words für .NET exportiert. Dieses Tutorial hat Sie durch das Einrichten Ihres Projekts, das Laden eines Word-Dokuments, das Konfigurieren von HTML-Speicheroptionen und das Speichern des Dokuments als MHTML geführt. Jetzt können Sie diese Schritte auf Ihre eigenen Projekte anwenden und Ihre Dokumentverwaltungsaufgaben verbessern.

## Häufig gestellte Fragen

### Was ist der Zweck des Exportierens von Cid-URLs für MHTML-Ressourcen?
Durch das Exportieren von Cid-URLs für MHTML-Ressourcen wird sichergestellt, dass auf eingebettete Ressourcen in Ihrer MHTML-Datei ordnungsgemäß verwiesen wird, wodurch die Portabilität und Integrität der Dokumente verbessert wird.

### Kann ich das Ausgabeformat weiter anpassen?
 Ja, Aspose.Words für .NET bietet umfangreiche Anpassungsoptionen zum Speichern von Dokumenten. Weitere Informationen finden Sie im[Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, Sie benötigen eine Lizenz, um Aspose.Words für .NET zu verwenden. Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/) oder eine Lizenz erwerben[Hier](https://purchase.aspose.com/buy).

### Kann ich diesen Vorgang für mehrere Dokumente automatisieren?
Auf jeden Fall! Sie können ein Skript erstellen, um den Prozess für mehrere Dokumente zu automatisieren und dabei die Leistungsfähigkeit von Aspose.Words für .NET nutzen, um Stapelverarbeitungsvorgänge effizient abzuwickeln.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
Wenn Sie Unterstützung benötigen, besuchen Sie das Aspose-Supportforum[Hier](https://forum.aspose.com/c/words/8) für Unterstützung durch die Community und die Aspose-Entwickler.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
