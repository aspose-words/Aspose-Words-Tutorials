---
title: Liste in jedem Abschnitt neu starten
linktitle: Liste in jedem Abschnitt neu starten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Listen in jedem Abschnitt in Word-Dokumenten neu starten. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung, um Listen effektiv zu verwalten.
weight: 10
url: /de/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Liste in jedem Abschnitt neu starten

## Einführung

Das Erstellen strukturierter und gut organisierter Dokumente kann sich manchmal wie das Lösen eines komplexen Puzzles anfühlen. Ein Teil dieses Puzzles ist die effektive Verwaltung von Listen, insbesondere wenn Sie möchten, dass sie in jedem Abschnitt neu gestartet werden. Mit Aspose.Words für .NET können Sie dies nahtlos erreichen. Lassen Sie uns einen Blick darauf werfen, wie Sie mit Aspose.Words für .NET Listen in jedem Abschnitt Ihrer Word-Dokumente neu starten können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Laden Sie die neueste Version herunter und installieren Sie sie vom[Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) Seite.
2. .NET-Umgebung: Richten Sie Ihre Entwicklungsumgebung mit installiertem .NET ein.
3. Grundlegende Kenntnisse in C#: Vertrautheit mit der Programmiersprache C# wird empfohlen.
4.  Aspose-Lizenz: Sie können sich für eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) wenn Sie keines haben.

## Namespaces importieren

Stellen Sie vor dem Schreiben des Codes sicher, dass Sie die erforderlichen Namespaces importieren:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Lassen Sie uns den Vorgang nun in mehrere Schritte unterteilen, damit er leichter nachvollziehbar ist.

## Schritt 1: Initialisieren Sie das Dokument

Zuerst müssen Sie eine neue Dokumentinstanz erstellen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Schritt 2: Fügen Sie eine nummerierte Liste hinzu

Fügen Sie als Nächstes dem Dokument eine nummerierte Liste hinzu. Diese Liste folgt einem Standardnummerierungsformat.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## Schritt 3: Auf die Liste zugreifen und Neustarteigenschaft festlegen

Rufen Sie die soeben erstellte Liste ab und legen Sie deren`IsRestartAtEachSection`Eigentum an`true`Dadurch wird sichergestellt, dass die Nummerierung der Liste bei jedem neuen Abschnitt neu beginnt.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## Schritt 4: Erstellen Sie einen Dokumentgenerator und verknüpfen Sie die Liste

 Erstellen Sie ein`DocumentBuilder` um Inhalte in das Dokument einzufügen und mit der Liste zu verknüpfen.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## Schritt 5: Listenelemente hinzufügen und Abschnittsumbruch einfügen

Fügen Sie nun Elemente zur Liste hinzu. Um die Neustartfunktion zu veranschaulichen, fügen wir nach einer bestimmten Anzahl von Elementen einen Abschnittsumbruch ein.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend mit den entsprechenden Optionen, um die Konformität sicherzustellen.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie mit Aspose.Words für .NET mühelos Listen in jedem Abschnitt Ihrer Word-Dokumente neu starten. Diese Funktion ist unglaublich nützlich, um gut strukturierte Dokumente zu erstellen, die separate Abschnitte mit eigener Listennummerierung erfordern. Mit Aspose.Words wird die Erledigung solcher Aufgaben zum Kinderspiel, sodass Sie sich auf die Erstellung hochwertiger Inhalte konzentrieren können.

## Häufig gestellte Fragen

### Kann ich Listen für verschiedene Listentypen in jedem Abschnitt neu starten?
Ja, Aspose.Words für .NET ermöglicht Ihnen, verschiedene Listentypen neu zu starten, einschließlich Aufzählungs- und nummerierter Listen.

### Was ist, wenn ich das Nummerierungsformat anpassen möchte?
 Sie können das Nummerierungsformat anpassen, indem Sie die`ListTemplate` -Eigenschaft beim Erstellen der Liste.

### Gibt es eine Begrenzung für die Anzahl der Elemente in einer Liste?
Nein, es gibt keine bestimmte Begrenzung für die Anzahl der Elemente, die Sie mit Aspose.Words für .NET in einer Liste haben können.

### Kann ich diese Funktion in anderen Dokumentformaten wie PDF verwenden?
Ja, Sie können Aspose.Words verwenden, um Word-Dokumente in andere Formate wie PDF zu konvertieren und dabei die Listenstruktur beizubehalten.

### Wie kann ich eine kostenlose Testversion von Aspose.Words für .NET erhalten?
 Sie erhalten eine kostenlose Testversion von[Aspose-Veröffentlichungen](https://releases.aspose.com/) Seite.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
