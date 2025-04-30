---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET mehrstufige nummerierte Listen und Aufzählungslisten in Word-Dokumenten erstellen. Schritt-für-Schritt-Anleitung inklusive. Perfekt für .NET-Entwickler."
"linktitle": "Listenebene angeben"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Listenebene angeben"
"url": "/de/net/working-with-list/specify-list-level/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Listenebene angeben

## Einführung

Hallo Programmierer! Wenn Sie schon einmal mit der Erstellung dynamischer und komplexer Listen in Word-Dokumenten mit .NET zu kämpfen hatten, erwartet Sie ein echter Leckerbissen. Heute tauchen wir in die Welt von Aspose.Words für .NET ein. Wir konzentrieren uns insbesondere auf die Festlegung von Listenebenen. Betrachten Sie es als eine Verbesserung Ihrer Dokumentfähigkeiten, mit der Sie mühelos professionelle, ausgefeilte Listen erstellen können. Am Ende dieses Leitfadens haben Sie einen klaren Weg gefunden, sowohl nummerierte als auch Aufzählungslisten mit mehreren Ebenen zu erstellen. Bereit? Dann legen wir gleich los!

## Voraussetzungen

Bevor wir ins Detail gehen, stellen wir sicher, dass wir alles haben, was wir brauchen. Hier ist eine kurze Checkliste:

1. Aspose.Words für .NET: Stellen Sie sicher, dass die Bibliothek Aspose.Words für .NET installiert ist. Sie können sie herunterladen [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio wird Ihnen das Leben erleichtern.
3. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
4. Grundlegende Kenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit der grundlegenden C#-Programmierung vertraut sind.

Alles da? Super! Dann legen wir los.

## Namespaces importieren

Zuerst müssen wir die benötigten Namespaces importieren. Öffnen Sie Ihr C#-Projekt und fügen Sie die folgenden using-Direktiven hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Dies bereitet die Grundlage für die Arbeit mit Aspose.Words in Ihrem Projekt.

## Schritt 1: Einrichten des Dokuments und des DocumentBuilder

Beginnen wir mit der Erstellung eines neuen Dokuments und einer `DocumentBuilder` Objekt, um damit zu arbeiten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Erstellen einer nummerierten Liste

Nun erstellen wir eine nummerierte Liste basierend auf einer der Microsoft Word-Listenvorlagen und wenden sie auf die `DocumentBuilder`'s aktueller Absatz.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.NumberArabicDot);
```

## Schritt 3: Anwenden mehrerer Listenebenen

Mit Aspose.Words können Sie bis zu neun Ebenen für eine Liste festlegen. Wenden wir alle Ebenen an, um zu sehen, wie es funktioniert.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

In dieser Schleife legen wir die Listenebene für jeden Absatz fest und schreiben eine Textzeile, die die Ebene angibt.

## Schritt 4: Erstellen einer Aufzählungsliste

Als Nächstes erstellen wir eine Aufzählungsliste. Dieses Mal verwenden wir eine andere Listenvorlage.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.BulletDiamonds);
```

## Schritt 5: Anwenden mehrerer Ebenen auf die Aufzählungsliste

Genau wie bei der nummerierten Liste wenden wir mehrere Ebenen auf unsere Aufzählungsliste an.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

## Schritt 6: Listenformatierung stoppen

Sehen wir uns abschließend an, wie wir die Listenformatierung beenden können, um zum normalen Text zurückzukehren.

```csharp
builder.ListFormat.List = null;
```

## Schritt 7: Speichern des Dokuments

Nach all der harten Arbeit ist es Zeit, unser Dokument zu speichern. Speichern wir es unter einem aussagekräftigen Namen.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.SpecifyListLevel.docx");
```

Und das war's! Sie haben gerade ein Dokument mit komplexen Listenstrukturen mit Aspose.Words für .NET erstellt.

## Abschluss

Das Erstellen strukturierter und mehrstufiger Listen in Word-Dokumenten kann die Lesbarkeit und Professionalität deutlich verbessern. Mit Aspose.Words für .NET können Sie diesen Prozess automatisieren, Zeit sparen und Konsistenz gewährleisten. Wir hoffen, dieser Leitfaden hat Ihnen geholfen, die effektive Festlegung von Listenebenen zu verstehen. Experimentieren Sie weiter und überzeugen Sie sich von der Leistungsfähigkeit dieses Tools für Ihre Dokumentverarbeitung.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente programmgesteuert in C# erstellen, bearbeiten, konvertieren und drucken können.

### Kann ich Aspose.Words kostenlos nutzen?
Aspose.Words bietet eine kostenlose Testversion an, die Sie herunterladen können [Hier](https://releases.aspose.com/). Für eine Vollversion können Sie die Kaufoptionen prüfen [Hier](https://purchase.aspose.com/buy).

### Wie viele Ebenen kann ich mit Aspose.Words in einer Liste angeben?
Mit Aspose.Words können Sie bis zu neun Ebenen in einer Liste angeben.

### Ist es möglich, nummerierte Listen und Aufzählungslisten in einem einzigen Dokument zu mischen?
Ja, Sie können verschiedene Listentypen in einem einzigen Dokument mischen, indem Sie die Listenvorlage nach Bedarf wechseln.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
Eine ausführliche Dokumentation finden Sie [Hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}