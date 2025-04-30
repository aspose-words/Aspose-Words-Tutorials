---
"description": "Mit dieser Schritt-für-Schritt-Anleitung können Sie Tabellen mit Aspose.Words für .NET ganz einfach automatisch an das Fenster in Word-Dokumenten anpassen. Perfekt für übersichtlichere, professionelle Dokumente."
"linktitle": "Automatisch an Fenster anpassen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Automatisch an Fenster anpassen"
"url": "/de/net/programming-with-tables/auto-fit-to-page-width/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Automatisch an Fenster anpassen

## Einführung

Kennen Sie die Frustration, dass Tabellen in Word-Dokumenten nicht perfekt auf die Seite passen? Sie passen Ränder an, ändern die Spaltengröße, und trotzdem sieht es unpassend aus. Mit Aspose.Words für .NET gibt es eine elegante Lösung für dieses Problem: Tabellen werden automatisch an das Fenster angepasst. Diese praktische Funktion passt die Tabellenbreite perfekt an die Seitenbreite an und verleiht Ihrem Dokument ein elegantes und professionelles Aussehen. In dieser Anleitung zeigen wir Ihnen Schritt für Schritt, wie Sie dies mit Aspose.Words für .NET erreichen und dafür sorgen, dass Ihre Tabellen immer perfekt passen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass alles bereit ist:

1. Visual Studio: Sie benötigen eine IDE wie Visual Studio, um Ihren .NET-Code zu schreiben und auszuführen.
2. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
3. Grundkenntnisse in C#: Wenn Sie mit der Programmiersprache C# vertraut sind, können Sie die Codeausschnitte leichter verstehen.

Nachdem diese Voraussetzungen erfüllt sind, kommen wir zum spannenden Teil – dem Programmieren!

## Namespaces importieren

Um mit Aspose.Words für .NET arbeiten zu können, müssen Sie die erforderlichen Namespaces importieren. Dadurch wird Ihrem Programm mitgeteilt, wo sich die zu verwendenden Klassen und Methoden befinden.

So importieren Sie den Aspose.Words-Namespace:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Der `Aspose.Words` Namespace enthält die Kernklassen für die Bearbeitung von Word-Dokumenten, während `Aspose.Words.Tables` ist speziell für die Handhabung von Tabellen.

## Schritt 1: Richten Sie Ihr Dokument ein

Zuerst müssen Sie das Word-Dokument laden, das die Tabelle enthält, die Sie automatisch anpassen möchten. Dazu verwenden Sie die `Document` Klasse bereitgestellt von Aspose.Words.

```csharp
// Definieren Sie den Pfad zu Ihrem Dokumentenverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laden Sie das Dokument vom angegebenen Pfad
Document doc = new Document(dataDir + "Tables.docx");
```

In diesem Schritt definieren Sie den Pfad, in dem Ihr Dokument gespeichert ist und laden es in ein `Document` Objekt. Ersetzen `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Dokument befindet.

## Schritt 2: Zugriff auf die Tabelle

Nachdem Sie Ihr Dokument geladen haben, müssen Sie im nächsten Schritt auf die Tabelle zugreifen, die Sie ändern möchten. So rufen Sie die erste Tabelle im Dokument ab:

```csharp
// Holen Sie sich die erste Tabelle aus dem Dokument
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Dieser Codeausschnitt ruft die erste im Dokument gefundene Tabelle ab. Wenn Ihr Dokument mehrere Tabellen enthält und Sie eine bestimmte benötigen, müssen Sie den Index möglicherweise entsprechend anpassen.

## Schritt 3: Tabelle automatisch anpassen

Nachdem Sie die Tabelle erstellt haben, können Sie die Funktion „Automatisch anpassen“ anwenden. Dadurch wird die Tabelle automatisch an die Seitenbreite angepasst:

```csharp
// Automatische Anpassung der Tabelle an die Fensterbreite
table.AutoFit(AutoFitBehavior.AutoFitToWindow);
```

Der `AutoFit` Methode mit `AutoFitBehavior.AutoFitToWindow` sorgt dafür, dass die Tabellenbreite an die gesamte Seitenbreite angepasst wird.

## Schritt 4: Speichern des geänderten Dokuments

Nachdem die Tabelle automatisch angepasst wurde, besteht der letzte Schritt darin, die Änderungen in einem neuen Dokument zu speichern:

```csharp
// Speichern Sie das geänderte Dokument in einer neuen Datei
doc.Save(dataDir + "WorkingWithTables.AutoFitTableToWindow.docx");
```

Dadurch wird das geänderte Dokument mit der automatisch angepassten Tabelle in einer neuen Datei gespeichert. Sie können das Dokument nun in Word öffnen, und die Tabelle passt perfekt auf die Seitenbreite.

## Abschluss

Und fertig – Tabellen automatisch an das Fenster anzupassen ist mit Aspose.Words für .NET ein Kinderspiel! Mit diesen einfachen Schritten stellen Sie sicher, dass Ihre Tabellen stets professionell aussehen und perfekt in Ihre Dokumente passen. Egal, ob Sie mit umfangreichen Tabellen arbeiten oder Ihr Dokument einfach nur aufräumen möchten, diese Funktion ist bahnbrechend. Probieren Sie es aus und lassen Sie Ihre Dokumente mit sauberen, gut ausgerichteten Tabellen glänzen!

## Häufig gestellte Fragen

### Kann ich mehrere Tabellen automatisch in ein Dokument einpassen?  
Ja, Sie können alle Tabellen in einem Dokument durchlaufen und die Auto-Fit-Methode auf jede einzelne anwenden.

### Beeinflusst die automatische Anpassung den Inhalt der Tabelle?  
Nein, die automatische Anpassung passt die Breite der Tabelle an, ändert jedoch nicht den Inhalt innerhalb der Zellen.

### Was ist, wenn meine Tabelle bestimmte Spaltenbreiten hat, die ich beibehalten möchte?  
Die automatische Anpassung überschreibt bestimmte Spaltenbreiten. Wenn Sie bestimmte Breiten beibehalten müssen, müssen Sie die Spalten möglicherweise manuell anpassen, bevor Sie die automatische Anpassung anwenden.

### Kann ich die automatische Anpassung für Tabellen in anderen Dokumentformaten verwenden?  
Aspose.Words unterstützt hauptsächlich Word-Dokumente (.docx). Andere Formate müssen möglicherweise zuerst in das .docx-Format konvertiert werden.

### Wie kann ich eine Testversion von Aspose.Words erhalten?  
Sie können eine kostenlose Testversion herunterladen [Hier](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}