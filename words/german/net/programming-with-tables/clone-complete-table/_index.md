---
title: Vollständige Tabelle klonen
linktitle: Vollständige Tabelle klonen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem ausführlichen Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET vollständige Tabellen in Word-Dokumenten klonen.
weight: 10
url: /de/net/programming-with-tables/clone-complete-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vollständige Tabelle klonen

## Einführung

Sind Sie bereit, Ihre Fähigkeiten zur Bearbeitung von Word-Dokumenten auf die nächste Stufe zu heben? Das Klonen von Tabellen in Word-Dokumenten kann für die Erstellung konsistenter Layouts und die Verwaltung sich wiederholender Inhalte von entscheidender Bedeutung sein. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET eine vollständige Tabelle in einem Word-Dokument klonen. Am Ende dieses Handbuchs können Sie Tabellen mühelos duplizieren und die Integrität der Formatierung Ihres Dokuments beibehalten.

## Voraussetzungen

Bevor wir uns in die Einzelheiten des Klonens von Tabellen vertiefen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1. Aspose.Words für .NET installiert: Stellen Sie sicher, dass Sie Aspose.Words für .NET auf Ihrem Computer installiert haben. Wenn Sie es noch nicht installiert haben, können Sie es von der[Website](https://releases.aspose.com/words/net/).

2. Visual Studio oder eine beliebige .NET IDE: Sie benötigen eine Entwicklungsumgebung zum Schreiben und Testen Ihres Codes. Visual Studio ist eine beliebte Wahl für die .NET-Entwicklung.

3. Grundlegende Kenntnisse in C#: Kenntnisse in der C#-Programmierung und dem .NET-Framework sind von Vorteil, da wir Code in C# schreiben werden.

4. Ein Word-Dokument mit Tabellen: Sie benötigen ein Word-Dokument mit mindestens einer Tabelle, die Sie klonen möchten. Wenn Sie keins haben, können Sie für dieses Tutorial ein Beispieldokument mit einer Tabelle erstellen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren. Diese Namespaces bieten Zugriff auf Aspose.Words-Klassen und -Methoden, die zum Bearbeiten von Word-Dokumenten erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Lassen Sie uns den Vorgang des Klonens einer Tabelle in überschaubare Schritte unterteilen. Wir beginnen mit dem Einrichten der Umgebung und fahren dann mit dem Klonen der Tabelle fort und fügen sie in das Dokument ein.

## Schritt 1: Definieren Sie den Pfad zu Ihrem Dokument

Geben Sie zunächst den Pfad zum Verzeichnis an, in dem sich Ihr Word-Dokument befindet. Dies ist wichtig, damit das Dokument korrekt geladen werden kann.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Ihr Dokument gespeichert ist.

## Schritt 2: Laden Sie das Dokument

 Laden Sie als nächstes das Word-Dokument, das die Tabelle enthält, die Sie klonen möchten. Dies geschieht mit dem`Document` Klasse von Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Tables.docx");
```

 In diesem Beispiel`"Tables.docx"` ist der Name des Word-Dokuments. Stellen Sie sicher, dass diese Datei im angegebenen Verzeichnis vorhanden ist.

## Schritt 3: Zugriff auf die zu klonende Tabelle

 Rufen Sie nun die Tabelle auf, die Sie klonen möchten.`GetChild` Methode wird verwendet, um die erste Tabelle im Dokument abzurufen.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Dieser Codeausschnitt geht davon aus, dass Sie die erste Tabelle im Dokument klonen möchten. Wenn mehrere Tabellen vorhanden sind, müssen Sie möglicherweise den Index anpassen oder andere Methoden verwenden, um die richtige Tabelle auszuwählen.

## Schritt 4: Klonen Sie die Tabelle

 Klonen Sie die Tabelle mit dem`Clone`Methode. Diese Methode erstellt eine vollständige Kopie der Tabelle, wobei Inhalt und Formatierung erhalten bleiben.

```csharp
Table tableClone = (Table) table.Clone(true);
```

 Der`true` Der Parameter stellt sicher, dass der Klon die gesamte Formatierung und den Inhalt der Originaltabelle enthält.

## Schritt 5: Einfügen der geklonten Tabelle in das Dokument

 Fügen Sie die geklonte Tabelle direkt hinter der Originaltabelle in das Dokument ein. Verwenden Sie die`InsertAfter` Methode hierfür.

```csharp
table.ParentNode.InsertAfter(tableClone, table);
```

Dieser Codeausschnitt platziert die geklonte Tabelle direkt nach der Originaltabelle innerhalb desselben übergeordneten Knotens (normalerweise ein Abschnitt oder Textkörper).

## Schritt 6: Einen leeren Absatz hinzufügen

Um sicherzustellen, dass die geklonte Tabelle nicht mit der Originaltabelle verschmilzt, fügen Sie zwischen ihnen einen leeren Absatz ein. Dieser Schritt ist wichtig, damit die Tabellen getrennt bleiben.

```csharp
table.ParentNode.InsertAfter(new Paragraph(doc), table);
```

Der leere Absatz dient als Puffer und verhindert, dass die beiden Tabellen beim Speichern des Dokuments kombiniert werden.

## Schritt 7: Speichern Sie das Dokument

Speichern Sie das geänderte Dokument abschließend unter einem neuen Namen, um die Originaldatei zu erhalten.

```csharp
doc.Save(dataDir + "WorkingWithTables.CloneCompleteTable.docx");
```

 Ersetzen`"WorkingWithTables.CloneCompleteTable.docx"` durch den gewünschten Ausgabedateinamen.

## Abschluss

Das Klonen von Tabellen in Word-Dokumenten mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, der Ihre Dokumentbearbeitungsaufgaben erheblich rationalisieren kann. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Tabellen effizient duplizieren und dabei ihre Formatierung und Struktur beibehalten. Egal, ob Sie komplexe Berichte verwalten oder Vorlagen erstellen, das Beherrschen des Tabellenklonens wird Ihre Produktivität und Genauigkeit steigern.

## Häufig gestellte Fragen

### Kann ich mehrere Tabellen gleichzeitig klonen?
Ja, Sie können mehrere Tabellen klonen, indem Sie jede Tabelle im Dokument durchlaufen und dieselbe Klonlogik anwenden.

### Was passiert, wenn die Tabelle verbundene Zellen hat?
 Der`Clone` Die Methode behält die gesamte Formatierung bei, einschließlich verbundener Zellen, und stellt so eine exakte Kopie der Tabelle sicher.

### Wie klone ich eine bestimmte Tabelle anhand des Namens?
Sie können Tabellen anhand benutzerdefinierter Eigenschaften oder eindeutiger Inhalte identifizieren und dann die gewünschte Tabelle mit ähnlichen Schritten klonen.

### Kann ich die Formatierung der geklonten Tabelle anpassen?
Ja, nach dem Klonen können Sie die Formatierung der geklonten Tabelle mit den Formatierungseigenschaften und -methoden von Aspose.Words ändern.

### Ist es möglich, Tabellen aus anderen Dokumentformaten zu klonen?
Aspose.Words unterstützt verschiedene Formate, sodass Sie Tabellen aus Formaten wie DOC, DOCX und RTF klonen können, sofern diese von Aspose.Words unterstützt werden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
