---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Aufzählungslisten in Word-Dokumenten erstellen und anpassen."
"linktitle": "Aufzählungsliste"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Aufzählungsliste"
"url": "/de/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aufzählungsliste

## Einführung

Sind Sie bereit, in die Welt von Aspose.Words für .NET einzutauchen? Heute zeigen wir Ihnen, wie Sie eine Aufzählungsliste in Ihren Word-Dokumenten erstellen. Ob Sie Ideen organisieren, Elemente auflisten oder Ihrem Dokument einfach etwas Struktur verleihen möchten – Aufzählungslisten sind äußerst praktisch. Also, los geht‘s!

## Voraussetzungen

Bevor wir uns in den Programmierspaß stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass die Aspose.Words-Bibliothek installiert ist. Falls Sie sie noch nicht haben, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: AC#-Entwicklungsumgebung wie Visual Studio.
3. Grundlegende C#-Kenntnisse: Ein grundlegendes Verständnis der C#-Programmierung wird Ihnen helfen, dem Ablauf zu folgen.

## Namespaces importieren

Zuerst importieren wir die erforderlichen Namespaces. Damit schaffen wir die Voraussetzungen für einen reibungslosen Ablauf unseres Codes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Lassen Sie uns den Prozess nun in einfache, überschaubare Schritte unterteilen.

## Schritt 1: Erstellen Sie ein neues Dokument

Okay, beginnen wir mit der Erstellung eines neuen Dokuments. Hier geschieht der ganze Zauber.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 2: Aufzählungslistenformat anwenden

Als Nächstes wenden wir ein Aufzählungslistenformat an. Dadurch wird dem Dokument mitgeteilt, dass wir eine Aufzählungsliste beginnen.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Schritt 3: Aufzählungsliste anpassen

Hier passen wir die Aufzählungsliste nach unseren Wünschen an. In diesem Beispiel verwenden wir einen Bindestrich (-) als Aufzählungszeichen.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Schritt 4: Listenelemente hinzufügen

Fügen wir nun unserer Aufzählungsliste einige Elemente hinzu. Hier können Sie Ihrer Kreativität freien Lauf lassen und beliebige Inhalte hinzufügen.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Schritt 5: Unterelemente hinzufügen

Um die Sache interessanter zu gestalten, fügen wir unter „Punkt 2“ einige Unterpunkte hinzu. Dies erleichtert die Organisation der Unterpunkte.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Zurück zur Hauptlistenebene
```

## Abschluss

Und da haben Sie es! Sie haben gerade mit Aspose.Words für .NET eine Aufzählungsliste in einem Word-Dokument erstellt. Es ist ein unkomplizierter Prozess, aber unglaublich leistungsstark für die Organisation Ihrer Dokumente. Egal, ob Sie einfache Listen oder komplexe verschachtelte Listen erstellen, Aspose.Words unterstützt Sie dabei.

Experimentieren Sie mit verschiedenen Listenstilen und -formaten, um Ihren Anforderungen gerecht zu werden. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich in der Liste andere Aufzählungszeichen verwenden?
   Ja, Sie können die Aufzählungszeichen anpassen, indem Sie die `NumberFormat` Eigentum.

### Wie füge ich weitere Einrückungsebenen hinzu?
   Verwenden Sie die `ListIndent` Methode, um weitere Ebenen hinzuzufügen und `ListOutdent` um auf eine höhere Ebene zurückzukehren.

### Ist es möglich, Aufzählungs- und Nummerierungslisten zu mischen?
   Absolut! Sie können zwischen Aufzählungszeichen- und Nummerierungsformaten wechseln, indem Sie `ApplyNumberDefault` Und `ApplyBulletDefault` Methoden.

### Kann ich den Text in den Listenelementen formatieren?
   Ja, Sie können verschiedene Stile, Schriftarten und Formatierungen auf den Text in Listenelementen anwenden, indem Sie die `Font` Eigentum der `DocumentBuilder`.

### Wie kann ich eine mehrspaltige Aufzählungsliste erstellen?
   Mithilfe der Tabellenformatierung können Sie mehrspaltige Listen erstellen, in denen jede Zelle eine separate Aufzählungsliste enthält.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}