---
title: Sortierte Liste
linktitle: Sortierte Liste
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET geordnete Listen in Word-Dokumenten erstellen. Perfekt für die Automatisierung der Dokumenterstellung.
weight: 10
url: /de/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sortierte Liste

## Einführung

Sie haben sich also entschieden, in Aspose.Words für .NET einzutauchen, um programmgesteuert fantastische Word-Dokumente zu erstellen. Fantastische Wahl! Heute werden wir aufschlüsseln, wie man eine geordnete Liste in einem Word-Dokument erstellt. Wir gehen Schritt für Schritt vor, sodass Sie diese Anleitung sowohl für Programmieranfänger als auch für erfahrene Profis sehr hilfreich finden werden. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor wir uns in den Code vertiefen, benötigen Sie einige Dinge:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Wenn nicht, können Sie es herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
3. Grundkenntnisse in C#: Sie sollten mit den Grundlagen von C# vertraut sein, um problemlos folgen zu können.

## Namespaces importieren

Um Aspose.Words in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Dies ist so, als würden Sie Ihren Werkzeugkasten einrichten, bevor Sie mit der Arbeit beginnen.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Lassen Sie uns den Code in mundgerechte Schritte aufteilen und jeden Teil erklären. Bereit? Los geht‘s!

## Schritt 1: Initialisieren Sie das Dokument

Als Erstes müssen Sie ein neues Dokument erstellen. Stellen Sie sich das so vor, als würden Sie ein leeres Word-Dokument auf Ihrem Computer öffnen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier initialisieren wir ein neues Dokument und ein DocumentBuilder-Objekt. Der DocumentBuilder ist wie Ihr Stift, mit dem Sie Inhalte in das Dokument schreiben können.

## Schritt 2: Nummeriertes Listenformat anwenden

Wenden wir nun ein standardmäßiges nummeriertes Listenformat an. Das ist so, als würden Sie Ihr Word-Dokument so einrichten, dass nummerierte Aufzählungszeichen verwendet werden.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Diese Codezeile richtet die Nummerierung für Ihre Liste ein. Einfach, oder?

## Schritt 3: Listenelemente hinzufügen

Als nächstes fügen wir unserer Liste einige Artikel hinzu. Stellen Sie sich vor, Sie schreiben eine Einkaufsliste.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Mit diesen Zeilen fügst du die ersten beiden Elemente zu deiner Liste hinzu.

## Schritt 4: Einrücken der Liste

Was ist, wenn Sie einem Artikel Unterelemente hinzufügen möchten? Machen wir das!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

 Der`ListIndent` Methode rückt die Liste ein und erstellt eine Unterliste. Sie erstellen jetzt eine hierarchische Liste, ähnlich einer verschachtelten Aufgabenliste.

## Abschluss

Das programmgesteuerte Erstellen einer geordneten Liste in einem Word-Dokument kann zunächst entmutigend erscheinen, aber mit Aspose.Words für .NET ist es ein Kinderspiel. Indem Sie diese einfachen Schritte befolgen, können Sie Ihren Dokumenten problemlos Listen hinzufügen und diese verwalten. Egal, ob Sie Berichte erstellen, strukturierte Dokumente erstellen oder einfach nur Ihre Arbeitsabläufe automatisieren, Aspose.Words für .NET bietet alles. Worauf also warten? Beginnen Sie mit dem Programmieren und erleben Sie, wie die Magie sich entfaltet!

## Häufig gestellte Fragen

### Kann ich den Nummerierungsstil der Liste anpassen?  
 Ja, Sie können den Nummerierungsstil anpassen mit dem`ListFormat`Eigenschaften. Sie können verschiedene Nummerierungsstile wie römische Ziffern, Buchstaben usw. festlegen.

### Wie füge ich weitere Einrückungsebenen hinzu?  
 Sie können die`ListIndent` Methode mehrmals, um tiefere Ebenen von Unterlisten zu erstellen. Jeder Aufruf von`ListIndent` fügt eine Einrückungsebene hinzu.

### Kann ich Aufzählungszeichen und nummerierte Listen mischen?  
 Auf jeden Fall! Sie können verschiedene Listenformate innerhalb desselben Dokuments anwenden, indem Sie`ListFormat` Eigentum.

### Ist es möglich, die Nummerierung einer vorherigen Liste fortzusetzen?  
Ja, Sie können die Nummerierung fortsetzen, indem Sie dasselbe Listenformat verwenden. Aspose.Words ermöglicht Ihnen die Steuerung der Listennummerierung über verschiedene Absätze hinweg.

### Wie kann ich das Listenformat entfernen?  
 Sie können das Listenformat entfernen, indem Sie`ListFormat.RemoveNumbers()`. Dadurch werden die Listenelemente wieder in normale Absätze umgewandelt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
