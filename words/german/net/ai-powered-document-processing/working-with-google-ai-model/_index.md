---
title: Arbeiten mit dem Google AI-Modell
linktitle: Arbeiten mit dem Google AI-Modell
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Verbessern Sie Ihre Dokumentenverarbeitung mit Aspose.Words für .NET und Google AI, um mühelos prägnante Zusammenfassungen zu erstellen.
weight: 10
url: /de/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Arbeiten mit dem Google AI-Modell

## Einführung

In diesem Artikel erfahren Sie Schritt für Schritt, wie Sie Dokumente mit Aspose.Words und den KI-Modellen von Google zusammenfassen. Egal, ob Sie einen langen Bericht verdichten oder Erkenntnisse aus mehreren Quellen extrahieren möchten, wir haben die Lösung für Sie.

## Voraussetzungen

Bevor wir uns in den praktischen Teil stürzen, stellen wir sicher, dass Sie für den Erfolg gerüstet sind. Folgendes benötigen Sie:

1. Grundkenntnisse in C# und .NET: Die Vertrautheit mit Programmierkonzepten hilft Ihnen, die Beispiele besser zu verstehen.
   
2.  Aspose.Words für .NET-Bibliothek: Mit dieser leistungsstarken Bibliothek können Sie Word-Dokumente nahtlos erstellen und bearbeiten. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).

3. API-Schlüssel für Google AI-Modell: Um die KI-Modelle nutzen zu können, benötigen Sie einen API-Schlüssel zur Authentifizierung. Speichern Sie ihn sicher in Ihren Umgebungsvariablen.

4. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine funktionierende .NET-Umgebung eingerichtet haben (Visual Studio oder eine andere IDE).

5. Beispieldokument: Sie benötigen Beispiel-Word-Dokumente (z. B. „Großes Dokument.docx“, „Dokument.docx“), um die Zusammenfassung zu testen.

Nachdem wir nun die Grundlagen behandelt haben, tauchen wir in den Code ein!

## Pakete importieren

Um mit Aspose.Words zu arbeiten und Google AI-Modelle zu integrieren, müssen Sie die erforderlichen Namespaces importieren. So können Sie das tun:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Nachdem Sie nun die erforderlichen Pakete importiert haben, wollen wir den Vorgang der Dokumentenzusammenfassung Schritt für Schritt durchgehen.

## Schritt 1: Einrichten Ihres Dokumentverzeichnisses

Bevor wir Dokumente verarbeiten können, müssen wir angeben, wo sich unsere Dateien befinden. Dieser Schritt ist entscheidend, um sicherzustellen, dass Aspose.Words auf die Dokumente zugreifen kann.

```csharp
// Ihr Dokumentenverzeichnis
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Ihr ArtifactsDir-Verzeichnis
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Ersetzen`"YOUR_DOCUMENT_DIRECTORY"` Und`"YOUR_ARTIFACTS_DIRECTORY"` mit den tatsächlichen Pfaden auf Ihrem System, in denen Ihre Dokumente gespeichert sind. Dies dient als Grundlage zum Lesen und Speichern von Dokumenten.

## Schritt 2: Dokumente laden

Als nächstes müssen wir die Dokumente laden, die wir zusammenfassen möchten. In diesem Fall laden Sie zwei Dokumente, die wir zuvor angegeben haben.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 Der`Document` Mit der Klasse von Aspose.Words können Sie Word-Dateien in den Speicher laden. Stellen Sie sicher, dass die Dateinamen mit den tatsächlichen Dokumenten in Ihrem Verzeichnis übereinstimmen, sonst treten Fehler auf, bei denen die Datei nicht gefunden wurde!

## Schritt 3: Abrufen des API-Schlüssels

Um das KI-Modell nutzen zu können, müssen Sie Ihren API-Schlüssel abrufen. Dieser dient als Zugangspass für die Google KI-Dienste.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Diese Codezeile ruft den API-Schlüssel ab, den Sie in Ihren Umgebungsvariablen gespeichert haben. Aus Sicherheitsgründen empfiehlt es sich, vertrauliche Informationen wie API-Schlüssel aus Ihrem Code fernzuhalten.

## Schritt 4: Erstellen einer KI-Modellinstanz

Jetzt ist es an der Zeit, eine Instanz des KI-Modells zu erstellen. Hier können Sie auswählen, welches Modell verwendet werden soll. In diesem Beispiel entscheiden wir uns für das Modell GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 Diese Zeile richtet das KI-Modell ein, das Sie für die Dokumentzusammenfassung verwenden werden. Beachten Sie unbedingt[die Dokumentation](https://reference.aspose.com/words/net/) für Einzelheiten zu den verschiedenen Modellen und ihren Funktionen.

## Schritt 5: Ein einzelnes Dokument zusammenfassen

Konzentrieren wir uns auf die Zusammenfassung des ersten Dokuments. Wir können uns hier für eine kurze Zusammenfassung entscheiden.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 In diesem Schritt verwenden wir die`Summarize`Methode aus der KI-Modellinstanz, um eine Zusammenfassung des ersten Dokuments zu erhalten. Die Zusammenfassungslänge ist auf kurz eingestellt, Sie können dies jedoch je nach Bedarf anpassen. Schließlich wird das zusammengefasste Dokument in Ihrem Artefaktverzeichnis gespeichert.

## Schritt 6: Mehrere Dokumente zusammenfassen

Möchten Sie mehrere Dokumente gleichzeitig zusammenfassen? Aspose.Words macht auch das ganz einfach!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 Hier nennen wir die`Summarize` Methode erneut, aber dieses Mal mit einem Array von Dokumenten. Dadurch erhalten Sie eine lange Zusammenfassung, die das Wesentliche beider Dateien zusammenfasst. Genau wie zuvor wird das Ergebnis im angegebenen Artefaktverzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine Umgebung zum Zusammenfassen von Dokumenten mit Aspose.Words für .NET und den KI-Modellen von Google eingerichtet. Vom Laden von Dokumenten bis zum Erstellen prägnanter Zusammenfassungen bieten diese Schritte einen optimierten Ansatz zum effektiven Verwalten großer Textmengen.

## Häufig gestellte Fragen

### Was ist Aspose.Words?
Aspose.Words ist eine leistungsstarke Bibliothek zum Erstellen, Ändern und Konvertieren von Word-Dokumenten mit .NET.

### Wie erhalte ich einen API-Schlüssel für Google AI?
Normalerweise können Sie einen API-Schlüssel erwerben, indem Sie sich für Google Cloud anmelden und die erforderlichen API-Dienste aktivieren.

### Kann ich mehrere Dokumente auf einmal zusammenfassen?
Ja! Wie gezeigt, können Sie ein Array von Dokumenten an die Zusammenfassungsmethode übergeben.

### Welche Arten von Zusammenfassungen kann ich erstellen?
Sie können je nach Bedarf zwischen kurzen, mittleren und langen Zusammenfassungen wählen.

### Wo finde ich weitere Aspose.Words-Ressourcen?
 Schauen Sie sich die[Dokumentation](https://reference.aspose.com/words/net/) für weitere Beispiele und Anleitungen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
