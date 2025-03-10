---
title: Arbeiten mit KI-Modellen
linktitle: Arbeiten mit KI-Modellen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Dokumente mit KI zusammenfassen. Einfache Schritte zur Verbesserung des Dokumentenmanagements.
weight: 10
url: /de/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Arbeiten mit KI-Modellen

## Einführung

Willkommen in der faszinierenden Welt von Aspose.Words für .NET! Wenn Sie schon immer Ihr Dokumentenmanagement auf die nächste Stufe heben wollten, sind Sie hier richtig. Stellen Sie sich vor, Sie könnten große Dokumente mit nur wenigen Codezeilen automatisch zusammenfassen. Klingt fantastisch, oder? In diesem Handbuch tauchen wir tief in die Verwendung von Aspose.Words ein, um Zusammenfassungen von Dokumenten mithilfe leistungsstarker KI-Sprachmodelle wie GPT von OpenAI zu erstellen. Egal, ob Sie ein Entwickler sind, der seine Anwendungen verbessern möchte, oder ein Technikbegeisterter, der etwas Neues lernen möchte, dieses Tutorial hat alles für Sie.

## Voraussetzungen

Bevor wir die Ärmel hochkrempeln und mit dem Programmieren beginnen, müssen Sie einige grundlegende Dinge parat haben:

1. Visual Studio installiert: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist. Sie können es kostenlos herunterladen, falls Sie es noch nicht haben.
  
2. .NET Framework: Stellen Sie sicher, dass Sie eine kompatible Version des .NET Frameworks für Aspose.Words verwenden. Es unterstützt sowohl .NET Framework als auch .NET Core.

3.  Aspose.Words für .NET: Sie müssen Aspose.Words herunterladen und installieren. Sie können die neueste Version herunterladen[Hier](https://releases.aspose.com/words/net/).

4. Ein API-Schlüssel für KI-Modelle: Um die KI-Zusammenfassung nutzen zu können, benötigen Sie Zugriff auf ein KI-Modell. Holen Sie sich Ihren API-Schlüssel von Plattformen wie OpenAI oder Google.

5. Grundkenntnisse in C#: Um dieses Tutorial optimal nutzen zu können, sind grundlegende Kenntnisse der C#-Programmierung erforderlich.

Alles dabei? Super! Kommen wir nun zum spaßigen Teil – dem Importieren unserer benötigten Pakete.

## Pakete importieren

Um die Leistungsfähigkeit von Aspose.Words zu nutzen und mit KI-Modellen zu arbeiten, importieren wir zunächst die erforderlichen Pakete. So geht's:

### Neues Projekt erstellen

Starten Sie zunächst Visual Studio und erstellen Sie ein neues Konsolenanwendungsprojekt.

1. Öffnen Sie Visual Studio.
2. Klicken Sie auf „Neues Projekt erstellen“.
3. Wählen Sie je nach Setup „Konsolen-App (.NET Framework)“ oder „Konsolen-App (.NET Core)“ aus.
4. Geben Sie Ihrem Projekt einen Namen und geben Sie den Standort an.

### Installieren Sie Aspose.Words und AI-Modellpakete

Um Aspose.Words zu verwenden, müssen Sie das Paket über NuGet installieren.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt und wählen Sie „NuGet-Pakete verwalten“.
2. Suchen Sie nach „Aspose.Words“ und klicken Sie auf „Installieren“.
3. Wenn Sie bestimmte KI-Modellpakete (wie OpenAI) verwenden, stellen Sie sicher, dass diese ebenfalls installiert sind.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Glückwunsch! Jetzt, da die Pakete fertig sind, können wir tiefer in unsere Implementierung eintauchen.

## Schritt 1: Richten Sie Ihre Dokumentverzeichnisse ein

In unserem Code definieren wir Verzeichnisse, um zu verwalten, wo unsere Dokumente gespeichert werden und wohin unsere Ausgabe geht. 

```csharp
// Ihr Dokumentenverzeichnis
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Ihr ArtifactsDir-Verzeichnis
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Ersetzen Sie hier`YOUR_DOCUMENT_DIRECTORY` mit dem Ort, an dem Ihre Dokumente gespeichert sind und`YOUR_ARTIFACTS_DIRECTORY` wo Sie die zusammengefassten Dateien speichern möchten.

## Schritt 2: Dokumente laden

Als nächstes laden wir die Dokumente, die wir zusammenfassen möchten, in unser Programm. Das ist kinderleicht! So geht's:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Passen Sie die Dateinamen an die von Ihnen gespeicherten Dateien an. Im Beispiel wird davon ausgegangen, dass Sie zwei Dokumente mit den Namen „Großes Dokument.docx“ und „Dokument.docx“ haben.

## Schritt 3: Initialisieren Sie das KI-Modell

Unser nächster Schritt besteht darin, eine Verbindung mit dem KI-Modell herzustellen. Hier kommt der API-Schlüssel ins Spiel, den Sie zuvor erhalten haben.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Stellen Sie sicher, dass Ihr API-Schlüssel als Umgebungsvariable gespeichert ist. So bewahren Sie Ihre Geheimzutat sicher auf!

## Schritt 4: Erstellen Sie eine Zusammenfassung für das erste Dokument

Lassen Sie uns nun eine Zusammenfassung für unser erstes Dokument erstellen. Wir legen auch Parameter fest, um die Länge der Zusammenfassung zu definieren.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Dieses Snippet fasst das erste Dokument zusammen und speichert die Ausgabe in Ihrem angegebenen Artefaktverzeichnis. Sie können die Länge der Zusammenfassung nach Belieben ändern!

## Schritt 5: Erstellen Sie eine Zusammenfassung für mehrere Dokumente

Lust auf Abenteuer? Sie können auch mehrere Dokumente auf einmal zusammenfassen! So geht's:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Und schon fassen Sie zwei Dokumente gleichzeitig zusammen! Das ist doch mal Effizienz, oder?

## Abschluss

Und da haben Sie es! Indem Sie dieser Anleitung folgen, beherrschen Sie die Kunst, Dokumente mit Aspose.Words für .NET und leistungsstarken KI-Modellen zusammenzufassen. Es ist eine spannende Funktion, die Ihnen jede Menge Zeit sparen kann, egal ob für den persönlichen Gebrauch oder die Integration in professionelle Anwendungen. Jetzt legen Sie los, entfesseln Sie die Kraft der Automatisierung und beobachten Sie, wie Ihre Produktivität in die Höhe schießt!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert zu erstellen, zu ändern, zu konvertieren und zu rendern.

### Wie erhalte ich einen API-Schlüssel für KI-Modelle?
Sie können einen API-Schlüssel von KI-Anbietern wie OpenAI oder Google erhalten. Erstellen Sie unbedingt ein Konto und folgen Sie deren Anweisungen zum Generieren Ihres Schlüssels.

### Kann ich Aspose.Words für andere Dateiformate verwenden?
Ja! Aspose.Words unterstützt verschiedene Dateiformate, darunter DOCX, RTF und HTML, und bietet umfangreiche Funktionen über reine Textdokumente hinaus.

### Gibt es eine kostenlose Version von Aspose.Words?
Aspose bietet eine kostenlose Testversion an, mit der Sie die Funktionen testen können. Sie können die Testversion von der Website herunterladen.

### Wo finde ich weitere Ressourcen für Aspose.Words?
 Sie können die Dokumentation einsehen[Hier](https://reference.aspose.com/words/net/) für umfassende Anleitungen und Einblicke.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
