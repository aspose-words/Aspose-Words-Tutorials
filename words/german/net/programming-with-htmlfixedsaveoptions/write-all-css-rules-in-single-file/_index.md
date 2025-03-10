---
title: Schreiben Sie alle CSS-Regeln in eine einzige Datei
linktitle: Schreiben Sie alle CSS-Regeln in eine einzige Datei
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Word-Dokumente in HTML konvertieren, mit allen CSS-Regeln in einer einzigen Datei für saubereren Code und einfachere Wartung.
weight: 10
url: /de/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schreiben Sie alle CSS-Regeln in eine einzige Datei

## Einführung

Haben Sie sich beim Konvertieren von Word-Dokumenten in HTML schon einmal im Netz der überall verstreuten CSS-Regeln verheddert? Keine Sorge! Heute tauchen wir in eine nette Funktion von Aspose.Words für .NET ein, mit der Sie alle CSS-Regeln in einer einzigen Datei schreiben können. Dies räumt nicht nur Ihren Code auf, sondern macht Ihnen das Leben auch viel einfacher. Schnall dich an und lass uns auf diese Reise zu saubererer, effizienterer HTML-Ausgabe beginnen!

## Voraussetzungen

Bevor wir uns ins Detail stürzen, wollen wir erst einmal alles vorbereiten. Folgendes brauchen Sie für den Anfang:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET haben. Wenn Sie sie noch nicht haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. .NET-Entwicklungsumgebung: Sie benötigen eine .NET-Entwicklungsumgebung auf Ihrem Computer. Visual Studio ist eine beliebte Wahl.
3. Grundkenntnisse in C#: Grundlegende Kenntnisse der C#-Programmierung sind hilfreich.
4. Ein Word-Dokument: Halten Sie ein Word-Dokument (.docx) bereit, das Sie konvertieren möchten.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces in Ihr C#-Projekt. Dadurch können wir problemlos auf die Aspose.Words-Funktionen zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Okay, lassen Sie uns den Prozess in leicht verständliche Schritte unterteilen. Jeder Schritt führt Sie durch einen bestimmten Teil des Prozesses, um sicherzustellen, dass alles reibungslos abläuft.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zuerst müssen wir den Pfad zu Ihrem Dokumentverzeichnis definieren. Hier ist Ihr Word-Dokument gespeichert und hier wird auch das konvertierte HTML gespeichert.

```csharp
// Zugriffspfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Schritt 2: Laden Sie das Word-Dokument

 Als nächstes laden wir das Word-Dokument, welches wir in HTML umwandeln möchten. Dies geschieht mit dem`Document` Klasse aus der Aspose.Words-Bibliothek.

```csharp
// Laden Sie das Word-Dokument
Document doc = new Document(dataDir + "Document.docx");
```

## Schritt 3: HTML-Speicheroptionen konfigurieren

 Nun müssen wir die HTML-Speicheroptionen konfigurieren. Insbesondere möchten wir die Funktion aktivieren, die alle CSS-Regeln in eine einzige Datei schreibt. Dies erreichen wir durch die Einstellung der`SaveFontFaceCssSeparately`Eigentum an`false`.

```csharp
// Konfigurieren Sie Sicherungsoptionen mit der Funktion „Alle CSS-Regeln in eine Datei schreiben“
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Schritt 4: Dokument in festes HTML konvertieren

Abschließend speichern wir das Dokument mit den konfigurierten Speicheroptionen als HTML-Datei. Dieser Schritt stellt sicher, dass alle CSS-Regeln in einer einzigen Datei geschrieben werden.

```csharp
// Dokument in festes HTML konvertieren
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen haben Sie Ihr Word-Dokument erfolgreich in HTML konvertiert, wobei alle CSS-Regeln übersichtlich in einer einzigen Datei organisiert sind. Diese Methode vereinfacht nicht nur Ihre CSS-Verwaltung, sondern verbessert auch die Wartbarkeit Ihrer HTML-Dokumente. Wenn Sie also das nächste Mal ein Word-Dokument konvertieren müssen, wissen Sie genau, wie Sie Ordnung halten!

## Häufig gestellte Fragen

### Warum sollte ich für meine HTML-Ausgabe eine einzelne CSS-Datei verwenden?
Die Verwendung einer einzigen CSS-Datei vereinfacht die Verwaltung und Wartung Ihrer Stile. Dadurch wird Ihr HTML übersichtlicher und effizienter.

### Kann ich die CSS-Regeln für Schriftarten bei Bedarf trennen?
 Ja, durch die Einstellung`SaveFontFaceCssSeparately` Zu`true`, Sie können die CSS-Regeln für Schriftarten in eine andere Datei auslagern.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
 Aspose.Words bietet eine kostenlose Testversion an, die Sie[hier herunterladen](https://releases.aspose.com/) . Für die weitere Nutzung sollten Sie den Kauf einer Lizenz in Erwägung ziehen[Hier](https://purchase.aspose.com/buy).

### In welche anderen Formate kann Aspose.Words für .NET konvertieren?
Aspose.Words für .NET unterstützt verschiedene Formate, darunter PDF, TXT und Bildformate wie JPEG und PNG.

### Wo finde ich weitere Ressourcen zu Aspose.Words für .NET?
 Schauen Sie sich die[Dokumentation](https://reference.aspose.com/words/net/) für umfassende Anleitungen und API-Referenzen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
