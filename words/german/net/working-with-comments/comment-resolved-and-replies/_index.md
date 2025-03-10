---
title: Kommentar gelöst und Antworten
linktitle: Kommentar gelöst und Antworten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Automatisieren Sie das Auflösen und Beantworten von Kommentaren in Word-Dokumenten mit Aspose.Words für .NET. Schritt-für-Schritt-Anleitung enthalten.
weight: 10
url: /de/net/working-with-comments/comment-resolved-and-replies/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kommentar gelöst und Antworten

## Einführung

Wenn Sie mit Word-Dokumenten arbeiten, haben Sie wahrscheinlich schon mit Kommentaren gearbeitet. Sie sind großartig für die Zusammenarbeit, aber ihre Verwaltung kann mühsam sein. Mit Aspose.Words für .NET können Sie den Prozess der Auflösung und Beantwortung von Kommentaren automatisieren. Diese Anleitung führt Sie durch die Schritte, um genau das zu tun.

## Voraussetzungen

Stellen Sie vor dem Eintauchen sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Sie können es herunterladen von[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eingerichtet mit .NET Framework.
3. Grundkenntnisse in C#: Vertrautheit mit der Syntax und den Konzepten.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dadurch wird sichergestellt, dass alle benötigten Klassen und Methoden sofort verfügbar sind.

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

Lassen Sie uns den Prozess in einfache, leicht verständliche Schritte unterteilen. Jeder Schritt hilft Ihnen, den Code und seine Funktionalität zu verstehen.

## Schritt 1: Dokument laden

 Laden Sie zunächst das Word-Dokument mit den Kommentaren. Verwenden Sie die`Document` Klasse dafür.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

 Diese Codezeile initialisiert eine neue`Document` Objekt durch den Pfad zu Ihrem Word-Dokument.

## Schritt 2: Kommentare abrufen

 Als nächstes müssen wir alle Kommentare im Dokument abrufen. Wir verwenden dazu`GetChildNodes` Methode zum Abrufen einer Sammlung von`Comment` Knoten.

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

Dieser Code ruft alle Kommentare im Dokument ab und speichert sie in einer`NodeCollection`.

## Schritt 3: Zugriff auf den übergeordneten Kommentar

In unserem Beispiel konzentrieren wir uns auf den ersten Kommentar in der Sammlung. Dies wird unser übergeordneter Kommentar sein.

```csharp
Comment parentComment = (Comment)comments[0];
```

 Hier konvertieren wir den ersten Knoten in der Sammlung in einen`Comment` Objekt.

## Schritt 4: Antworten durchlaufen

 Lassen Sie uns nun die Antworten auf den übergeordneten Kommentar durchgehen. Wir verwenden eine`foreach` Schleife, um jede Antwort zu durchlaufen.

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

In dieser Schleife drucken wir die ID des Vorgängerkommentars und seinen Status (ob er erledigt ist oder nicht). Dann markieren wir jede Antwort als erledigt.

## Schritt 5: Speichern Sie das Dokument

Speichern Sie abschließend das geänderte Dokument in Ihrem Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

Dieser Code speichert die Änderungen in einem neuen Dokument und stellt sicher, dass Ihre Originaldatei unverändert bleibt.

## Abschluss

Die Bearbeitung von Kommentaren in Word-Dokumenten muss keine manuelle Aufgabe sein. Mit Aspose.Words für .NET können Sie den Prozess automatisieren, Zeit sparen und Fehler reduzieren. Folgen Sie dieser Anleitung, um Kommentare in Ihren Dokumenten effizient aufzulösen und zu beantworten.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET andere kommentarbezogene Aufgaben automatisieren?  
Ja, Sie können verschiedene Aufgaben wie das Hinzufügen, Löschen und Ändern von Kommentaren automatisieren.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?  
Ja, Aspose.Words für .NET unterstützt sowohl .NET Framework als auch .NET Core.

### Wie kann ich eine kostenlose Testversion von Aspose.Words für .NET erhalten?  
 Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.aspose.com/).

### Kann ich Aspose.Words für .NET verwenden, um mit anderen Dokumenttypen zu arbeiten?  
Ja, Aspose.Words unterstützt verschiedene Formate, darunter DOCX, PDF, HTML und mehr.

### Wo finde ich eine ausführliche Dokumentation für Aspose.Words für .NET?  
 Sie können auf die Dokumentation zugreifen[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
