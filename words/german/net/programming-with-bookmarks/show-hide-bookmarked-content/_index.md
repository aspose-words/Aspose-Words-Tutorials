---
title: Mit Lesezeichen versehenen Inhalt im Word-Dokument ein-/ausblenden
linktitle: Mit Lesezeichen versehenen Inhalt im Word-Dokument ein-/ausblenden
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET mit Lesezeichen versehene Inhalte in Word-Dokumenten ein- und ausblenden.
weight: 10
url: /de/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mit Lesezeichen versehenen Inhalt im Word-Dokument ein-/ausblenden

## Einführung

Sind Sie bereit, in die Welt der Dokumentbearbeitung mit Aspose.Words für .NET einzutauchen? Egal, ob Sie Entwickler sind und Dokumentaufgaben automatisieren möchten oder einfach nur neugierig sind, wie Word-Dateien programmgesteuert bearbeitet werden können, hier sind Sie richtig. Heute werden wir untersuchen, wie Sie mit Aspose.Words für .NET mit Lesezeichen versehene Inhalte in einem Word-Dokument ein- und ausblenden können. Mit dieser Schritt-für-Schritt-Anleitung werden Sie zum Profi bei der Steuerung der Inhaltssichtbarkeit anhand von Lesezeichen. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor wir ins Detail gehen, gibt es ein paar Dinge, die Sie brauchen:

1. Visual Studio: Jede mit .NET kompatible Version.
2.  Aspose.Words für .NET: Laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
3. Grundlegende Kenntnisse in C#: Wenn Sie ein einfaches „Hallo Welt“-Programm schreiben können, sind Sie startklar.
4. Ein Word-Dokument mit Lesezeichen: Für dieses Tutorial verwenden wir ein Beispieldokument mit Lesezeichen.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. So stellen wir sicher, dass wir über alle Tools verfügen, die wir für unsere Aufgabe benötigen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Mit diesen eingerichteten Namespaces können wir unsere Reise beginnen.

## Schritt 1: Einrichten Ihres Projekts

Okay, legen wir los, indem wir unser Projekt in Visual Studio einrichten.

### Neues Projekt erstellen

Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolen-App-Projekt (.NET Core). Geben Sie ihm einen einprägsamen Namen, etwa „BookmarkVisibilityManager“.

### Aspose.Words für .NET hinzufügen

Sie müssen Aspose.Words für .NET zu Ihrem Projekt hinzufügen. Sie können dies über den NuGet Package Manager tun.

1. Gehen Sie zu Tools > NuGet-Paket-Manager > NuGet-Pakete für Lösung verwalten.
2. Suchen Sie nach „Aspose.Words“.
3. Installieren Sie das Paket.

Großartig! Nachdem unser Projekt nun eingerichtet ist, können wir mit dem Laden unseres Dokuments fortfahren.

## Schritt 2: Laden des Dokuments

Wir müssen das Word-Dokument laden, das die Lesezeichen enthält. Für dieses Tutorial verwenden wir ein Beispieldokument mit dem Namen „Bookmarks.docx“.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Dieser Codeausschnitt setzt den Pfad zu Ihrem Dokumentverzeichnis und lädt das Dokument in das`doc` Objekt.

## Schritt 3: Mit Lesezeichen versehenen Inhalt ein-/ausblenden

Jetzt kommt der spaßige Teil – das Anzeigen oder Ausblenden des Inhalts basierend auf Lesezeichen. Wir erstellen eine Methode namens`ShowHideBookmarkedContent` um damit umzugehen.

So schalten Sie die Sichtbarkeit mit Lesezeichen versehener Inhalte um:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Aufschlüsselung der Methode

-  Lesezeichen abrufen:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` holt das Lesezeichen.
- Knotendurchquerung: Wir durchlaufen die Knoten innerhalb des Lesezeichens.
-  Sichtbarkeit umschalten: Wenn der Knoten ein`Run` (ein zusammenhängender Textabschnitt) setzen wir seine`Hidden` Eigentum.

## Schritt 4: Anwenden der Methode

Nachdem wir unsere Methode eingerichtet haben, wenden wir sie an, um Inhalte basierend auf einem Lesezeichen anzuzeigen oder auszublenden.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Diese Codezeile verbirgt den Inhalt des Lesezeichens mit dem Namen „MyBookmark1“.

## Schritt 5: Speichern des Dokuments

Zum Schluss speichern wir unser geändertes Dokument.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Dadurch wird das Dokument mit den von uns vorgenommenen Änderungen gespeichert.

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie mit Aspose.Words für .NET mit Lesezeichen versehene Inhalte in einem Word-Dokument ein- und ausblenden. Dieses leistungsstarke Tool macht die Dokumentbearbeitung zum Kinderspiel, egal ob Sie Berichte automatisieren, Vorlagen erstellen oder einfach nur an Word-Dateien herumbasteln. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich mehrere Lesezeichen gleichzeitig umschalten?
 Ja, Sie können anrufen unter`ShowHideBookmarkedContent` Methode für jedes Lesezeichen, das Sie umschalten möchten.

### Hat das Ausblenden von Inhalten Auswirkungen auf die Struktur des Dokuments?
Nein, das Ausblenden von Inhalten wirkt sich nur auf deren Sichtbarkeit aus. Der Inhalt bleibt im Dokument erhalten.

### Kann ich diese Methode für andere Arten von Inhalten verwenden?
Mit dieser Methode können Sie gezielt Textläufe umschalten. Für andere Inhaltstypen müssen Sie die Knotendurchlauflogik ändern.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words bietet eine kostenlose Testversion an[Hier](https://releases.aspose.com/) , aber für den produktiven Einsatz ist eine Volllizenz erforderlich. Sie können diese erwerben[Hier](https://purchase.aspose.com/buy).

### Wie erhalte ich Unterstützung, wenn Probleme auftreten?
 Sie können Unterstützung von der Aspose-Community erhalten[Hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
