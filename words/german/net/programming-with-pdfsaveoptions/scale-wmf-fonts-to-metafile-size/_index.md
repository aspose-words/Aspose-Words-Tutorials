---
"description": "Schritt-für-Schritt-Anleitung zum Reduzieren der PDF-Größe durch Skalieren von WMF-Schriftarten auf Metadateigröße beim Konvertieren in PDF mit Aspose.Words für .NET."
"linktitle": "Reduzieren Sie die PDF-Größe mit „WMF-Schriftarten auf Metadateigröße skalieren“"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Reduzieren Sie die PDF-Größe mit „WMF-Schriftarten auf Metadateigröße skalieren“"
"url": "/de/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduzieren Sie die PDF-Größe mit „WMF-Schriftarten auf Metadateigröße skalieren“

## Einführung

Bei der Arbeit mit PDF-Dateien, insbesondere solchen, die aus Word-Dokumenten mit WMF-Grafiken (Windows Metafile) erstellt wurden, kann die Größenverwaltung ein entscheidender Aspekt der Dokumentenverwaltung sein. Eine Möglichkeit, die PDF-Größe zu steuern, besteht darin, die Darstellung von WMF-Schriftarten im Dokument anzupassen. In diesem Tutorial erfahren Sie, wie Sie die PDF-Größe reduzieren können, indem Sie WMF-Schriftarten mit Aspose.Words für .NET auf die Größe der Metadatei skalieren.

## Voraussetzungen

Bevor Sie mit den Schritten beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass die Aspose.Words-Bibliothek installiert ist. Falls nicht, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Dieses Tutorial setzt voraus, dass Sie eine .NET-Entwicklungsumgebung (wie Visual Studio) eingerichtet haben, in der Sie C#-Code schreiben und ausführen können.
3. Grundlegende Kenntnisse der .NET-Programmierung: Kenntnisse der grundlegenden Konzepte der .NET-Programmierung und der C#-Syntax sind hilfreich.
4. Word-Dokument mit WMF-Grafiken: Sie benötigen ein Word-Dokument mit WMF-Grafiken. Sie können ein eigenes Dokument verwenden oder ein Testdokument erstellen.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die für die Arbeit mit Aspose.Words erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Laden Sie das Word-Dokument

Laden Sie zunächst das Word-Dokument, das die WMF-Grafiken enthält. Dies geschieht über `Document` Klasse von Aspose.Words.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laden Sie das Dokument
Document doc = new Document(dataDir + "WMF with text.docx");
```

Hier, `dataDir` ist ein Platzhalter für Ihren Dokumentverzeichnispfad. Wir erstellen eine Instanz des `Document` Klasse, indem Sie den Pfad zur Word-Datei übergeben. Dadurch wird das Dokument in den Speicher geladen und ist für die weitere Verarbeitung bereit.

## Schritt 2: Konfigurieren der Optionen für das Metadatei-Rendering

Als nächstes müssen Sie die Optionen für die Metadatei-Darstellung konfigurieren. Legen Sie insbesondere Folgendes fest: `ScaleWmfFontsToMetafileSize` Eigentum zu `false`. Dadurch wird gesteuert, ob WMF-Schriftarten so skaliert werden, dass sie der Größe der Metadatei entsprechen.

```csharp
// Erstellen Sie eine neue Instanz von MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

Der `MetafileRenderingOptions` Klasse bietet Optionen für die Darstellung von Metadateien (wie WMF). Durch die Einstellung `ScaleWmfFontsToMetafileSize` Zu `false`, weisen Sie Aspose.Words an, Schriftarten nicht entsprechend der Metadateigröße zu skalieren, was zur Reduzierung der Gesamtgröße des PDFs beitragen kann.

## Schritt 3: PDF-Speicheroptionen festlegen

Konfigurieren Sie nun die PDF-Speicheroptionen so, dass die soeben festgelegten Optionen zur Metadateiwiedergabe verwendet werden. Dadurch wird Aspose.Words angewiesen, wie Metadateien beim Speichern des Dokuments als PDF behandelt werden sollen.

```csharp
// Erstellen Sie eine neue Instanz von PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

Der `PdfSaveOptions` Klasse können Sie verschiedene Einstellungen für das Speichern des Dokuments als PDF festlegen. Durch die Zuweisung der zuvor konfigurierten `MetafileRenderingOptions` zum `MetafileRenderingOptions` Eigentum von `PdfSaveOptions`stellen Sie sicher, dass das Dokument entsprechend Ihren gewünschten Metadatei-Rendering-Einstellungen gespeichert wird.

## Schritt 4: Speichern Sie das Dokument als PDF

Speichern Sie das Word-Dokument abschließend mit den konfigurierten Speicheroptionen als PDF. Dadurch werden alle Einstellungen, einschließlich der Optionen zur Metadateidarstellung, auf das Ausgabe-PDF angewendet.


```csharp
// Speichern Sie das Dokument als PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

In diesem Schritt wird `Save` Methode der `Document` Die Klasse wird verwendet, um das Dokument in eine PDF-Datei zu exportieren. Der Pfad, in dem die PDF-Datei gespeichert wird, wird angegeben, zusammen mit dem `PdfSaveOptions` die die Einstellungen für das Rendern der Metadatei enthalten.

## Abschluss

Durch die Skalierung von WMF-Schriftarten auf Metadateigröße können Sie die Größe Ihrer aus Word-Dokumenten generierten PDF-Dateien deutlich reduzieren. Diese Technik trägt zur Optimierung der Dokumentenspeicherung und -verteilung bei, ohne die Qualität der visuellen Inhalte zu beeinträchtigen. Mit den oben beschriebenen Schritten können Sie Ihre PDF-Dateien handlicher und größeneffizienter gestalten.

## Häufig gestellte Fragen

### Was ist WMF und warum ist es für die PDF-Größe wichtig?

WMF (Windows Metafile) ist ein Grafikformat, das in Microsoft Windows verwendet wird. Es kann sowohl Vektor- als auch Bitmap-Daten enthalten. Da Vektordaten skaliert und bearbeitet werden können, ist eine korrekte Verarbeitung wichtig, um unnötig große PDF-Dateien zu vermeiden.

### Welche Auswirkungen hat die Skalierung von WMF-Schriftarten auf die Metadateigröße auf das PDF?

Durch die Skalierung von WMF-Schriftarten auf Metadateigröße können Sie die Gesamtgröße der PDF-Datei verringern, indem Sie die Darstellung hochauflösender Schriftarten vermeiden, die die Dateigröße erhöhen könnte.

### Kann ich mit Aspose.Words andere Metadateiformate verwenden?

Ja, Aspose.Words unterstützt verschiedene Metadateiformate, darunter neben WMF auch EMF (Enhanced Metafile).

### Ist diese Technik auf alle Arten von Word-Dokumenten anwendbar?

Ja, diese Technik kann auf jedes Word-Dokument angewendet werden, das WMF-Grafiken enthält, und hilft dabei, die Größe des generierten PDFs zu optimieren.

### Wo finde ich weitere Informationen zu Aspose.Words?

Weitere Informationen zu Aspose.Words finden Sie im [Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/)Downloads, Testversionen und Support finden Sie auf der [Aspose.Words Download-Seite](https://releases.aspose.com/words/net/), [Aspose.Words kaufen](https://purchase.aspose.com/buy), [Kostenlose Testversion](https://releases.aspose.com/), [Temporäre Lizenz](https://purchase.aspose.com/temporary-license/), Und [Unterstützung](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}