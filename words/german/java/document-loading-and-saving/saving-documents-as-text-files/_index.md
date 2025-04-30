---
"description": "Erfahren Sie, wie Sie Dokumente als Textdateien in Aspose.Words für Java speichern. Folgen Sie unserer Schritt-für-Schritt-Anleitung mit Java-Codebeispielen."
"linktitle": "Dokumente als Textdateien speichern"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Speichern von Dokumenten als Textdateien in Aspose.Words für Java"
"url": "/de/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Speichern von Dokumenten als Textdateien in Aspose.Words für Java


## Einführung in das Speichern von Dokumenten als Textdateien in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie Dokumente mit der Bibliothek Aspose.Words für Java als Textdateien speichern. Aspose.Words ist eine leistungsstarke Java-API für die Arbeit mit Word-Dokumenten und bietet verschiedene Optionen zum Speichern von Dokumenten in verschiedenen Formaten, einschließlich reinem Text. Wir erklären die Schritte dazu und stellen Ihnen dabei Beispiel-Java-Code zur Verfügung.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Auf Ihrem System ist das Java Development Kit (JDK) installiert.
- Aspose.Words für Java-Bibliothek in Ihr Projekt integriert. Sie können es herunterladen von [Hier](https://releases.aspose.com/words/java/).
- Grundkenntnisse der Java-Programmierung.

## Schritt 1: Erstellen Sie ein Dokument

Um ein Dokument als Textdatei zu speichern, müssen wir zunächst ein Dokument mit Aspose.Words erstellen. Hier ist ein einfacher Java-Codeausschnitt zum Erstellen eines Dokuments mit Inhalt:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In diesem Code erstellen wir ein neues Dokument und fügen ihm Text hinzu, darunter auch Text in verschiedenen Sprachen.

## Schritt 2: Textspeicheroptionen definieren

Als Nächstes müssen wir die Textspeicheroptionen definieren, die festlegen, wie das Dokument als Textdatei gespeichert werden soll. Wir können verschiedene Einstellungen konfigurieren, wie z. B. das Hinzufügen von Bidi-Markierungen, Listeneinrückungen und mehr. Sehen wir uns zwei Beispiele an:

### Beispiel 1: Hinzufügen von Bidi-Markierungen

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

In diesem Beispiel erstellen wir eine `TxtSaveOptions` Objekt und legen Sie die `AddBidiMarks` Eigentum zu `true` um Bidi-Markierungen in die Textausgabe einzuschließen.

### Beispiel 2: Verwenden des Tabulatorzeichens zum Einrücken von Listen

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Hier konfigurieren wir die Speicheroptionen so, dass für die Listeneinrückung ein Tabulatorzeichen mit einer Anzahl von 1 verwendet wird.

## Schritt 3: Speichern Sie das Dokument als Text

Nachdem wir die Optionen zum Speichern des Textes definiert haben, können wir das Dokument als Textdatei speichern. Der folgende Code zeigt, wie das geht:

```java
doc.save("output.txt", saveOptions);
```

Ersetzen `"output.txt"` mit dem gewünschten Dateipfad, in dem Sie die Textdatei speichern möchten.

## Vollständiger Quellcode zum Speichern von Dokumenten als Textdateien in Aspose.Words für Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Erstellen Sie eine Liste mit drei Einrückungsebenen.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Erstellen Sie eine Liste mit drei Einrückungsebenen.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Abschluss

In diesem Tutorial haben wir gelernt, wie man Dokumente als Textdateien in Aspose.Words für Java speichert. Wir haben die Schritte zum Erstellen eines Dokuments, zum Definieren von Textspeicheroptionen und zum Speichern des Dokuments im Textformat beschrieben. Aspose.Words bietet umfassende Flexibilität beim Speichern von Dokumenten und ermöglicht Ihnen, die Ausgabe an Ihre spezifischen Anforderungen anzupassen.

## Häufig gestellte Fragen

### Wie füge ich der Textausgabe Bidi-Markierungen hinzu?

Um der Textausgabe Bidi-Markierungen hinzuzufügen, setzen Sie die `AddBidiMarks` Eigentum von `TxtSaveOptions` Zu `true`. Zum Beispiel:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kann ich das Einrückungszeichen für Listen anpassen?

Ja, Sie können das Einrückungszeichen für Listen anpassen, indem Sie das `ListIndentation` Eigentum von `TxtSaveOptions`Um beispielsweise ein Tabulatorzeichen zum Einrücken von Listen zu verwenden, können Sie Folgendes tun:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Ist Aspose.Words für Java für die Verarbeitung mehrsprachiger Texte geeignet?

Ja, Aspose.Words für Java eignet sich für die Verarbeitung mehrsprachiger Texte. Es unterstützt verschiedene Sprachen und Zeichenkodierungen und ist somit eine vielseitige Lösung für die Arbeit mit Dokumenten in verschiedenen Sprachen.

### Wie kann ich auf weitere Dokumentation und Ressourcen für Aspose.Words für Java zugreifen?

Umfassende Dokumentation und Ressourcen zu Aspose.Words für Java finden Sie auf der Aspose-Dokumentationswebsite: [Aspose.Words für Java-Dokumentation](https://reference.aspose.com/words/java/).

### Wo kann ich Aspose.Words für Java herunterladen?

Sie können die Aspose.Words-Bibliothek für Java von der Aspose-Website herunterladen: [Laden Sie Aspose.Words für Java herunter](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}