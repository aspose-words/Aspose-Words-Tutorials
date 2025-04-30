---
"description": "Lernen Sie mit diesem Schritt-für-Schritt-Tutorial, Listen in Aspose.Words für Java zu verwenden. Organisieren und formatieren Sie Ihre Dokumente effektiv."
"linktitle": "Verwenden von Listen"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Verwenden von Listen in Aspose.Words für Java"
"url": "/de/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Listen in Aspose.Words für Java


In diesem umfassenden Tutorial erfahren Sie, wie Sie Listen in Aspose.Words für Java, einer leistungsstarken API für die programmgesteuerte Arbeit mit Microsoft Word-Dokumenten, effektiv nutzen. Listen sind unerlässlich für die Strukturierung und Organisation von Dokumenteninhalten. Wir behandeln zwei wichtige Aspekte der Arbeit mit Listen: das Neustarten von Listen in jedem Abschnitt und das Festlegen von Listenebenen. Los geht’s!

## Einführung in Aspose.Words für Java

Bevor wir mit Listen arbeiten, machen wir uns mit Aspose.Words für Java vertraut. Diese API bietet Entwicklern die Werkzeuge zum Erstellen, Ändern und Bearbeiten von Word-Dokumenten in einer Java-Umgebung. Sie ist eine vielseitige Lösung für Aufgaben von der einfachen Dokumenterstellung bis hin zu komplexer Formatierung und Inhaltsverwaltung.

### Einrichten Ihrer Umgebung

Stellen Sie zunächst sicher, dass Aspose.Words für Java in Ihrer Entwicklungsumgebung installiert und eingerichtet ist. Sie können es herunterladen [Hier](https://releases.aspose.com/words/java/). 

## Listen in jedem Abschnitt neu starten

In vielen Fällen müssen Sie Listen in jedem Abschnitt Ihres Dokuments neu starten. Dies kann nützlich sein, um strukturierte Dokumente mit mehreren Abschnitten zu erstellen, z. B. Berichte, Handbücher oder wissenschaftliche Arbeiten.

Hier ist eine Schritt-für-Schritt-Anleitung, wie Sie dies mit Aspose.Words für Java erreichen:

### Initialisieren Sie Ihr Dokument: 
Beginnen Sie mit der Erstellung eines neuen Dokumentobjekts.

```java
Document doc = new Document();
```

### Fügen Sie eine nummerierte Liste hinzu: 
Fügen Sie Ihrem Dokument eine nummerierte Liste hinzu. Wir verwenden den Standardnummerierungsstil.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Listeneinstellungen konfigurieren: 
\Ermöglichen Sie der Liste, bei jedem Abschnitt neu zu starten.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder-Setup: 
Erstellen Sie einen DocumentBuilder, um Ihrem Dokument Inhalte hinzuzufügen.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Listenelemente hinzufügen: 
Verwenden Sie eine Schleife, um Listenelemente zu Ihrem Dokument hinzuzufügen. Wir fügen nach dem 15. Element einen Abschnittsumbruch ein.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Speichern Sie Ihr Dokument: 
Speichern Sie das Dokument mit den gewünschten Optionen.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Wenn Sie diese Schritte befolgen, können Sie Dokumente mit Listen erstellen, die in jedem Abschnitt neu gestartet werden, und so eine klare und organisierte Inhaltsstruktur beibehalten.

## Festlegen von Listenebenen

Mit Aspose.Words für Java können Sie Listenebenen festlegen. Dies ist besonders nützlich, wenn Sie verschiedene Listenformate in Ihrem Dokument benötigen. Sehen wir uns an, wie das geht:

### Initialisieren Sie Ihr Dokument: 
Erstellen Sie ein neues Dokumentobjekt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Erstellen Sie eine nummerierte Liste: 
Wenden Sie eine nummerierte Listenvorlage aus Microsoft Word an.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Listenebenen angeben: 
Durchlaufen Sie verschiedene Listenebenen und fügen Sie Inhalte hinzu.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Erstellen Sie eine Aufzählungsliste: 
Lassen Sie uns nun eine Aufzählungsliste erstellen.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Geben Sie die Ebenen der Aufzählungsliste an: 
Ähnlich wie bei der nummerierten Liste können Sie Ebenen angeben und Inhalte hinzufügen.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Stopplistenformatierung: 
Um die Listenformatierung zu beenden, setzen Sie die Liste auf Null.

```java
builder.getListFormat().setList(null);
```

### Speichern Sie Ihr Dokument: 
Speichern Sie das Dokument.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Wenn Sie diese Schritte befolgen, können Sie Dokumente mit benutzerdefinierten Listenebenen erstellen und so die Formatierung der Listen in Ihren Dokumenten steuern.

## Vollständiger Quellcode
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection wird nur geschrieben, wenn die Konformität höher ist als OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Erstellen Sie eine nummerierte Liste basierend auf einer der Microsoft Word-Listenvorlagen
        // und wenden Sie es auf den aktuellen Absatz des Dokumentgenerators an.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Diese Liste enthält neun Level. Probieren wir sie alle aus.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Erstellen Sie eine Aufzählungsliste basierend auf einer der Microsoft Word-Listenvorlagen
        // und wenden Sie es auf den aktuellen Absatz des Dokumentgenerators an.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Auf diese Weise können Sie die Listenformatierung beenden.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Erstellen Sie eine Liste basierend auf einer Vorlage.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Um die erste Liste wiederzuverwenden, müssen wir die Nummerierung neu starten, indem wir eine Kopie der ursprünglichen Listenformatierung erstellen.
        List list2 = doc.getLists().addCopy(list1);
        // Wir können die neue Liste beliebig ändern, einschließlich der Festlegung einer neuen Startnummer.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Abschluss

Herzlichen Glückwunsch! Sie haben gelernt, wie Sie in Aspose.Words für Java effektiv mit Listen arbeiten. Listen sind entscheidend für die Organisation und Präsentation von Dokumenteninhalten. Ob Sie Listen in jedem Abschnitt neu starten oder Listenebenen festlegen müssen – Aspose.Words für Java bietet Ihnen die Werkzeuge, die Sie für die Erstellung professioneller Dokumente benötigen.

Jetzt können Sie diese Funktionen nutzen, um Ihre Dokumenterstellung und Formatierung zu verbessern. Wenn Sie Fragen haben oder weitere Unterstützung benötigen, wenden Sie sich bitte an die [Aspose-Community-Forum](https://forum.aspose.com/) für Unterstützung.

## FAQs

### Wie installiere ich Aspose.Words für Java?
Sie können Aspose.Words für Java herunterladen von [Hier](https://releases.aspose.com/words/java/) und befolgen Sie die Installationsanweisungen in der Dokumentation.

### Kann ich das Nummerierungsformat von Listen anpassen?
Ja, Aspose.Words für Java bietet umfangreiche Optionen zum Anpassen von Listennummerierungsformaten. Weitere Informationen finden Sie in der API-Dokumentation.

### Ist Aspose.Words für Java mit den neuesten Word-Dokumentstandards kompatibel?
Ja, Sie können Aspose.Words für Java so konfigurieren, dass es verschiedenen Word-Dokumentstandards entspricht, einschließlich ISO 29500.

### Kann ich mit Aspose.Words für Java komplexe Dokumente mit Tabellen und Bildern erstellen?
Absolut! Aspose.Words für Java unterstützt erweiterte Dokumentformatierung, einschließlich Tabellen, Bildern und mehr. Beispiele finden Sie in der Dokumentation.

### Wo kann ich eine temporäre Lizenz für Aspose.Words für Java erhalten?
Sie können eine vorübergehende Lizenz erhalten [Hier](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}