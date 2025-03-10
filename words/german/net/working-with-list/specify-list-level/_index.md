---
title: Listenebene angeben
linktitle: Listenebene angeben
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET mehrstufige nummerierte und Aufzählungslisten in Word-Dokumenten erstellen. Schritt-für-Schritt-Anleitung enthalten. Perfekt für .NET-Entwickler.
weight: 10
url: /de/net/working-with-list/specify-list-level/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Listenebene angeben

## Einführung

Hallo, Programmiererkollege! Wenn Sie jemals mit dem Erstellen dynamischer und komplexer Listen in Word-Dokumenten mit .NET zu kämpfen hatten, erwartet Sie eine echte Freude. Heute tauchen wir in die Welt von Aspose.Words für .NET ein. Insbesondere konzentrieren wir uns auf das Festlegen von Listenebenen. Betrachten Sie es als eine Verbesserung Ihrer Dokumentfähigkeiten, mit der Sie mühelos professionelle, ausgefeilte Listen erstellen können. Am Ende dieses Handbuchs verfügen Sie über einen klaren Weg zum Erstellen sowohl nummerierter als auch Aufzählungslisten mit mehreren Ebenen. Bereit? Lassen Sie uns direkt loslegen!

## Voraussetzungen

Bevor wir uns ins Detail stürzen, stellen wir sicher, dass wir alles haben, was wir brauchen. Hier ist eine kurze Checkliste:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Sie können sie herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio wird Ihnen das Leben leichter machen.
3. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
4. Grundlegende Kenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit der grundlegenden C#-Programmierung vertraut sind.

Alles dabei? Super! Dann legen wir los.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren. Öffnen Sie Ihr C#-Projekt und fügen Sie die folgenden using-Direktiven hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Dies bereitet die Grundlage für die Arbeit mit Aspose.Words in Ihrem Projekt.

## Schritt 1: Einrichten des Dokuments und des DocumentBuilder

 Beginnen wir mit der Erstellung eines neuen Dokuments und einer`DocumentBuilder` Objekt, damit zu arbeiten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Erstellen einer nummerierten Liste

 Nun erstellen wir eine nummerierte Liste auf der Grundlage einer der Microsoft Word-Listenvorlagen und wenden sie auf die`DocumentBuilder`'s aktueller Absatz.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.NumberArabicDot);
```

## Schritt 3: Mehrere Listenebenen anwenden

Mit Aspose.Words können Sie bis zu neun Ebenen für eine Liste angeben. Wenden wir alle an, um zu sehen, wie es funktioniert.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

In dieser Schleife legen wir die Listenebene für jeden Absatz fest und schreiben eine Textzeile, die die Ebene angibt.

## Schritt 4: Erstellen einer Aufzählungsliste

Lassen Sie uns als Nächstes den Kurs ändern und eine Aufzählungsliste erstellen. Dieses Mal verwenden wir eine andere Listenvorlage.

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

Und das war’s! Sie haben gerade mit Aspose.Words für .NET ein Dokument mit komplexen Listenstrukturen erstellt.

## Abschluss

Das Erstellen strukturierter und mehrstufiger Listen in Word-Dokumenten kann die Lesbarkeit und Professionalität erheblich verbessern. Mit Aspose.Words für .NET können Sie diesen Prozess automatisieren, was Ihnen Zeit spart und Konsistenz gewährleistet. Wir hoffen, dass dieser Leitfaden Ihnen geholfen hat zu verstehen, wie Sie Listenebenen effektiv angeben können. Experimentieren Sie weiter und sehen Sie, wie leistungsstark dieses Tool für Ihre Dokumentverarbeitungsanforderungen sein kann.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente programmgesteuert in C# erstellen, bearbeiten, konvertieren und drucken können.

### Kann ich Aspose.Words kostenlos nutzen?
Aspose.Words bietet eine kostenlose Testversion an, die Sie herunterladen können[Hier](https://releases.aspose.com/) . Für eine Vollversion können Sie die Kaufoptionen prüfen[Hier](https://purchase.aspose.com/buy).

### Wie viele Ebenen kann ich mit Aspose.Words in einer Liste angeben?
Mit Aspose.Words können Sie bis zu neun Ebenen in einer Liste angeben.

### Ist es möglich, nummerierte Listen und Aufzählungslisten in einem einzigen Dokument zu mischen?
Ja, Sie können verschiedene Listentypen in einem einzigen Dokument mischen, indem Sie die Listenvorlage nach Bedarf ändern.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
