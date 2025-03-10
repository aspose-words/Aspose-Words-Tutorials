---
title: Arbeiten mit Open AI Model
linktitle: Arbeiten mit Open AI Model
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Schalten Sie mit Aspose.Words für .NET und den leistungsstarken Modellen von OpenAI eine effiziente Dokumentzusammenfassung frei. Tauchen Sie jetzt in diesen umfassenden Leitfaden ein.
weight: 10
url: /de/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Arbeiten mit Open AI Model

## Einführung

In der heutigen digitalen Welt ist Inhalt König. Egal, ob Sie Student, Geschäftsmann oder begeisterter Autor sind, die Fähigkeit, Dokumente effizient zu bearbeiten, zusammenzufassen und zu erstellen, ist von unschätzbarem Wert. Hier kommt die Bibliothek Aspose.Words für .NET ins Spiel, mit der Sie Dokumente wie ein Profi verwalten können. In diesem umfassenden Tutorial erfahren Sie, wie Sie Aspose.Words in Verbindung mit OpenAI-Modellen nutzen können, um Dokumente effektiv zusammenzufassen. Sind Sie bereit, Ihr Dokumentenverwaltungspotenzial freizusetzen? Dann legen wir los!

## Voraussetzungen

Bevor wir die Ärmel hochkrempeln und uns in den Code stürzen, müssen Sie einige grundlegende Dinge parat haben:

### .NET Framework
Stellen Sie sicher, dass Sie eine Version des .NET-Frameworks verwenden, die mit Aspose.Words kompatibel ist. Im Allgemeinen sollten .NET 5.0 und höher einwandfrei funktionieren.

### Aspose.Words für .NET-Bibliothek
 Sie müssen die Aspose.Words-Bibliothek herunterladen und installieren. Sie finden sie unter[dieser Link](https://releases.aspose.com/words/net/).

### OpenAI API-Schlüssel
Um die Sprachmodelle von OpenAI zur Dokumentzusammenfassung zu integrieren, benötigen Sie einen API-Schlüssel. Sie erhalten ihn, indem Sie sich auf der OpenAI-Plattform anmelden und Ihren Schlüssel aus Ihren Kontoeinstellungen abrufen.

### IDE für die Entwicklung
Für die Entwicklung von .NET-Anwendungen ist die Einrichtung einer integrierten Entwicklungsumgebung (IDE) wie Visual Studio ideal.

### Grundlegende Programmierkenntnisse
Grundlegende Kenntnisse in C# und objektorientierter Programmierung helfen Ihnen, die Konzepte leichter zu verstehen.

## Pakete importieren

Nachdem wir nun alles vorbereitet haben, können wir unsere Pakete importieren. Öffnen Sie Ihr Visual Studio-Projekt und fügen Sie die erforderlichen Bibliotheken hinzu. So können Sie es tun:

### Aspose.Words-Paket hinzufügen

Sie können das Aspose.Words-Paket über den NuGet-Paket-Manager hinzufügen. So geht's:
- Gehen Sie zu Tools -> NuGet-Paket-Manager -> NuGet-Pakete für Lösung verwalten.
- Suchen Sie nach „Aspose.Words“ und klicken Sie auf Installieren.

### Systemumgebung hinzufügen

 Stellen Sie sicher, dass Sie die`System`Namespace zum Verarbeiten von Umgebungsvariablen:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Aspose.Words hinzufügen

Fügen Sie dann den Aspose.Words-Namespace in Ihre C#-Datei ein:
```csharp
using Aspose.Words;
```

### OpenAI-Bibliothek hinzufügen

Wenn Sie eine Bibliothek zur Schnittstelle mit OpenAI verwenden (z. B. einen REST-Client), müssen Sie diese ebenfalls einbinden. Möglicherweise müssen Sie sie über NuGet hinzufügen, so wie wir Aspose.Words hinzugefügt haben.

Nachdem wir nun unsere Umgebung vorbereitet und die erforderlichen Pakete importiert haben, wollen wir den Dokumentzusammenfassungsprozess Schritt für Schritt aufschlüsseln.

## Schritt 1: Definieren Sie Ihre Dokumentverzeichnisse

Bevor Sie mit Ihren Dokumenten arbeiten können, müssen Sie Verzeichnisse einrichten, in denen Ihre Dokumente und Artefakte gespeichert werden:

```csharp
// Ihr Dokumentenverzeichnis
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Ihr Artefakte-Verzeichnis
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Dadurch wird Ihr Code übersichtlicher, da Sie die Pfade bei Bedarf einfach ändern können.`MyDir` ist der Ort, an dem Ihre Eingabedokumente gespeichert werden, während`ArtifactsDir` Hier speichern Sie die generierten Zusammenfassungen.

## Schritt 2: Laden Sie Ihre Dokumente

Als nächstes laden Sie die Dokumente, die Sie zusammenfassen möchten. Mit Aspose.Words ist das ganz einfach:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Stellen Sie sicher, dass die Namen Ihrer Dokumente mit denen übereinstimmen, die Sie verwenden möchten. Andernfalls treten Fehler auf.

## Schritt 3: Holen Sie sich Ihren API-Schlüssel

Nachdem Ihre Dokumente nun geladen sind, ist es an der Zeit, Ihren OpenAI-API-Schlüssel abzurufen. Um ihn sicher aufzubewahren, rufen Sie ihn aus Umgebungsvariablen ab:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Es ist wichtig, Ihren API-Schlüssel sicher zu verwalten, um nicht autorisierte Benutzer fernzuhalten.

## Schritt 4: Erstellen Sie eine OpenAI-Modellinstanz

Mit Ihrem API-Schlüssel können Sie nun eine Instanz des OpenAI-Modells erstellen. Für die Dokumentzusammenfassung verwenden wir das Modell Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Mit diesem Schritt stellen Sie im Wesentlichen die nötigen geistigen Kapazitäten bereit, um Ihre Dokumente zusammenzufassen, und erhalten Zugriff auf eine KI-gesteuerte Zusammenfassung.

## Schritt 5: Ein einzelnes Dokument zusammenfassen

Fassen wir zunächst das erste Dokument zusammen. Hier geschieht die Magie:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Hier verwenden wir die`Summarize` Methode des Modells. Die`SummaryLength.Short`Der Parameter gibt an, dass wir eine kurze Zusammenfassung wünschen – perfekt für einen schnellen Überblick!

## Schritt 6: Mehrere Dokumente zusammenfassen

Sind Sie ehrgeizig? Sie können mehrere Dokumente auf einmal zusammenfassen. Sehen Sie, wie einfach das ist:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Diese Funktion ist besonders praktisch, wenn Sie mehrere Dateien vergleichen möchten. Vielleicht bereiten Sie sich auf ein Meeting vor und benötigen prägnante Notizen aus mehreren langen Berichten. Dies ist Ihr neuer bester Freund!

## Abschluss

Das Zusammenfassen von Dokumenten mit Aspose.Words für .NET und OpenAI ist nicht nur eine nützliche Fähigkeit, sondern auch sehr leistungsfähig. Indem Sie dieser Anleitung folgen, haben Sie lange, komplizierte Texte in prägnante Zusammenfassungen umgewandelt und sich so Zeit und Mühe gespart. Egal, ob Sie für Kunden Klarheit schaffen oder sich auf eine wichtige Präsentation vorbereiten möchten, Sie haben jetzt die Werkzeuge, um dies effizient zu tun.

Worauf warten Sie also noch? Tauchen Sie vertrauensvoll in Ihre Dokumente ein und überlassen Sie der Technologie die Schwerstarbeit!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?  
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Dokumente programmgesteuert zu erstellen, zu bearbeiten und zu konvertieren.

### Benötige ich einen API-Schlüssel für OpenAI?  
Ja, Sie müssen über einen gültigen OpenAI-API-Schlüssel verfügen, um mithilfe ihrer Modelle auf die Zusammenfassungsfunktionen zugreifen zu können.

### Kann ich mehrere Dokumente auf einmal zusammenfassen?  
Auf jeden Fall! Sie können mehrere Dokumente in einem einzigen Anruf zusammenfassen, was ideal für umfangreiche Berichte ist.

### Wie installiere ich Aspose.Words?  
Sie können es über den NuGet Package Manager in Visual Studio installieren, indem Sie nach „Aspose.Words“ suchen.

### Gibt es eine kostenlose Testversion für Aspose.Words?  
 Ja, Sie können eine kostenlose Testversion von Aspose.Words über deren[Webseite](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
