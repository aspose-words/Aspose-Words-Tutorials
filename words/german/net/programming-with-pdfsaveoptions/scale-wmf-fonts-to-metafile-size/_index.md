---
title: Reduzieren Sie die PDF-Größe, indem Sie WMF-Schriftarten auf Metadateigröße skalieren
linktitle: Reduzieren Sie die PDF-Größe, indem Sie WMF-Schriftarten auf Metadateigröße skalieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Schritt-für-Schritt-Anleitung zum Reduzieren der PDF-Größe durch Skalieren von WMF-Schriftarten auf Metadateigröße bei der Konvertierung in PDF mit Aspose.Words für .NET.
weight: 10
url: /de/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reduzieren Sie die PDF-Größe, indem Sie WMF-Schriftarten auf Metadateigröße skalieren

## Einführung

Beim Arbeiten mit PDF-Dateien, insbesondere solchen, die aus Word-Dokumenten mit WMF-Grafiken (Windows Metafile) erstellt wurden, kann die Größenverwaltung zu einem entscheidenden Aspekt der Dokumentverwaltung werden. Eine Möglichkeit, die PDF-Größe zu steuern, besteht darin, die Darstellung von WMF-Schriftarten im Dokument anzupassen. In diesem Tutorial erfahren Sie, wie Sie die PDF-Größe reduzieren können, indem Sie WMF-Schriftarten mithilfe von Aspose.Words für .NET auf die Metadateigröße skalieren.

## Voraussetzungen

Bevor Sie mit den Schritten beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Wenn nicht, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Dieses Tutorial setzt voraus, dass Sie eine .NET-Entwicklungsumgebung (wie Visual Studio) eingerichtet haben, in der Sie C#-Code schreiben und ausführen können.
3. Grundlegende Kenntnisse der .NET-Programmierung: Vertrautheit mit grundlegenden Konzepten der .NET-Programmierung und der C#-Syntax ist hilfreich.
4. Word-Dokument mit WMF-Grafiken: Sie benötigen ein Word-Dokument mit WMF-Grafiken. Sie können Ihr eigenes Dokument verwenden oder zu Testzwecken ein neues erstellen.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die für die Arbeit mit Aspose.Words erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Laden Sie das Word-Dokument

 Laden Sie zunächst das Word-Dokument, das die WMF-Grafiken enthält. Dies geschieht über den`Document` Klasse von Aspose.Words.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laden Sie das Dokument
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Hier,`dataDir` ist ein Platzhalter für Ihren Dokumentverzeichnispfad. Wir erstellen eine Instanz des`Document` Klasse, indem Sie den Pfad zur Word-Datei übergeben. Dadurch wird das Dokument in den Speicher geladen und ist für die weitere Verarbeitung bereit.

## Schritt 2: Konfigurieren der Optionen für die Metadateiwiedergabe

 Als nächstes müssen Sie die Optionen für die Darstellung der Metadatei konfigurieren. Legen Sie insbesondere die`ScaleWmfFontsToMetafileSize`Eigentum an`false`. Dies steuert, ob WMF-Schriftarten entsprechend der Metadateigröße skaliert werden.

```csharp
// Erstellen Sie eine neue Instanz von MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 Der`MetafileRenderingOptions` Klasse bietet Optionen für die Darstellung von Metadateien (wie WMF). Durch die Einstellung`ScaleWmfFontsToMetafileSize` Zu`false`, weisen Sie Aspose.Words an, Schriftarten nicht entsprechend der Metadateigröße zu skalieren, was zur Reduzierung der Gesamtgröße des PDF-Dokuments beitragen kann.

## Schritt 3: PDF-Speicheroptionen festlegen

Konfigurieren Sie nun die PDF-Speicheroptionen so, dass die gerade festgelegten Metadatei-Rendering-Optionen verwendet werden. Dadurch wird Aspose.Words mitgeteilt, wie Metadateien beim Speichern des Dokuments als PDF behandelt werden sollen.

```csharp
// Erstellen Sie eine neue Instanz von PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 Der`PdfSaveOptions` Klasse können Sie verschiedene Einstellungen für das Speichern des Dokuments als PDF festlegen. Durch die Zuweisung der zuvor konfigurierten`MetafileRenderingOptions` zur`MetafileRenderingOptions` Eigentum von`PdfSaveOptions`stellen Sie sicher, dass das Dokument entsprechend den gewünschten Einstellungen für die Metadateidarstellung gespeichert wird.

## Schritt 4: Speichern Sie das Dokument als PDF

Speichern Sie das Word-Dokument abschließend mit den konfigurierten Speicheroptionen als PDF. Dadurch werden alle Einstellungen, einschließlich der Optionen zum Rendern von Metadateien, auf das Ausgabe-PDF angewendet.


```csharp
// Speichern Sie das Dokument als PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 In diesem Schritt wird der`Save` Methode der`Document` Klasse wird verwendet, um das Dokument in eine PDF-Datei zu exportieren. Der Pfad, in dem die PDF-Datei gespeichert wird, wird angegeben, zusammen mit dem`PdfSaveOptions` die die Einstellungen für das Rendern der Metadatei beinhalten.

## Abschluss

Durch Skalieren von WMF-Schriftarten auf Metadateigröße können Sie die Größe Ihrer aus Word-Dokumenten generierten PDF-Dateien erheblich reduzieren. Diese Technik hilft bei der Optimierung der Dokumentenspeicherung und -verteilung, ohne die Qualität des visuellen Inhalts zu beeinträchtigen. Wenn Sie die oben beschriebenen Schritte befolgen, stellen Sie sicher, dass Ihre PDF-Dateien handlicher und größeneffizienter sind.

## Häufig gestellte Fragen

### Was ist WMF und warum ist es für die PDF-Größe wichtig?

WMF (Windows Metafile) ist ein Grafikformat, das in Microsoft Windows verwendet wird. Es kann sowohl Vektor- als auch Bitmap-Daten enthalten. Da Vektordaten skaliert und bearbeitet werden können, ist es wichtig, sie richtig zu verarbeiten, um unnötig große PDF-Dateien zu vermeiden.

### Welche Auswirkungen hat das Skalieren von WMF-Schriftarten auf die Metadateigröße auf das PDF?

Durch das Skalieren von WMF-Schriftarten auf Metadateigröße können Sie die Gesamtgröße des PDF-Dokuments verringern, indem Sie die Darstellung hochauflösender Schriftarten vermeiden, die die Dateigröße erhöhen könnten.

### Kann ich mit Aspose.Words andere Metadateiformate verwenden?

Ja, Aspose.Words unterstützt verschiedene Metadateiformate, darunter neben WMF auch EMF (Enhanced Metafile).

### Ist diese Technik auf alle Arten von Word-Dokumenten anwendbar?

Ja, diese Technik kann auf jedes Word-Dokument angewendet werden, das WMF-Grafiken enthält, und hilft dabei, die Größe der generierten PDF-Datei zu optimieren.

### Wo finde ich weitere Informationen zu Aspose.Words?

 Weitere Informationen zu Aspose.Words finden Sie im[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) . Downloads, Testversionen und Unterstützung finden Sie im[Aspose.Words Download-Seite](https://releases.aspose.com/words/net/), [Aspose.Words kaufen](https://purchase.aspose.com/buy), [Kostenlose Testversion](https://releases.aspose.com/), [Temporäre Lizenz](https://purchase.aspose.com/temporary-license/) , Und[Support](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
