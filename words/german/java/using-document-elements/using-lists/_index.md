---
title: Verwenden von Listen in Aspose.Words für Java
linktitle: Verwenden von Listen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Lernen Sie mit diesem Schritt-für-Schritt-Tutorial, Listen in Aspose.Words für Java zu verwenden. Organisieren und formatieren Sie Ihre Dokumente effektiv.
weight: 18
url: /de/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Listen in Aspose.Words für Java


In diesem umfassenden Tutorial erfahren Sie, wie Sie Listen in Aspose.Words für Java, einer leistungsstarken API für die programmgesteuerte Arbeit mit Microsoft Word-Dokumenten, effektiv nutzen können. Listen sind für die Strukturierung und Organisation von Inhalten in Ihren Dokumenten unerlässlich. Wir behandeln zwei wichtige Aspekte der Arbeit mit Listen: das Neustarten von Listen in jedem Abschnitt und das Festlegen von Listenebenen. Lassen Sie uns eintauchen!

## Einführung in Aspose.Words für Java

Bevor wir mit der Arbeit mit Listen beginnen, machen wir uns mit Aspose.Words für Java vertraut. Diese API bietet Entwicklern die Tools zum Erstellen, Ändern und Bearbeiten von Word-Dokumenten in einer Java-Umgebung. Es ist eine vielseitige Lösung für Aufgaben, die von der einfachen Dokumenterstellung bis hin zur komplexen Formatierung und Inhaltsverwaltung reichen.

### Einrichten Ihrer Umgebung

 Stellen Sie zunächst sicher, dass Sie Aspose.Words für Java in Ihrer Entwicklungsumgebung installiert und eingerichtet haben. Sie können es herunterladen[Hier](https://releases.aspose.com/words/java/). 

## Listen in jedem Abschnitt neu starten

In vielen Fällen müssen Sie Listen in jedem Abschnitt Ihres Dokuments neu starten. Dies kann beim Erstellen strukturierter Dokumente mit mehreren Abschnitten nützlich sein, z. B. bei Berichten, Handbüchern oder wissenschaftlichen Arbeiten.

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
\Aktivieren Sie die Option „Liste neu starten“ in jedem Abschnitt.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder-Einrichtung: 
Erstellen Sie einen DocumentBuilder, um Ihrem Dokument Inhalt hinzuzufügen.

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

## Angeben von Listenebenen

Mit Aspose.Words für Java können Sie Listenebenen angeben. Dies ist besonders nützlich, wenn Sie in Ihrem Dokument unterschiedliche Listenformate benötigen. Sehen wir uns an, wie das geht:

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
Iterieren Sie durch verschiedene Listenebenen und fügen Sie Inhalt hinzu.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Erstellen Sie eine Aufzählungsliste: 
Lassen Sie uns jetzt eine Aufzählungsliste erstellen.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Aufzählungslistenebenen festlegen: 
Ähnlich wie bei der nummerierten Liste können Sie Ebenen angeben und Inhalte hinzufügen.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Stopplistenformatierung: 
Um die Listenformatierung zu beenden, setzen Sie die Liste auf null.

```java
builder.getListFormat().setList(null);
```

### Speichern Sie Ihr Dokument: 
Speichern Sie das Dokument.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Indem Sie diese Schritte befolgen, können Sie Dokumente mit benutzerdefinierten Listenebenen erstellen und so die Formatierung der Listen in Ihren Dokumenten steuern.

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
        //und wenden Sie es auf den aktuellen Absatz des Dokument-Generators an.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Diese Liste enthält neun Level. Probieren wir sie alle aus.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Erstellen Sie eine Aufzählungsliste basierend auf einer der Microsoft Word-Listenvorlagen
        //und wenden Sie es auf den aktuellen Absatz des Dokument-Generators an.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Auf diese Weise können Sie die Listenformatierung stoppen.
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
        // Wir können die neue Liste beliebig verändern, darunter auch eine neue Startnummer festlegen.
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

Herzlichen Glückwunsch! Sie haben gelernt, wie Sie in Aspose.Words für Java effektiv mit Listen arbeiten. Listen sind entscheidend für die Organisation und Präsentation von Inhalten in Ihren Dokumenten. Ob Sie Listen in jedem Abschnitt neu starten oder Listenebenen angeben müssen, Aspose.Words für Java bietet die Tools, die Sie zum Erstellen professionell aussehender Dokumente benötigen.

Jetzt können Sie diese Funktionen vertrauensvoll nutzen, um Ihre Aufgaben bei der Dokumenterstellung und -formatierung zu verbessern. Wenn Sie Fragen haben oder weitere Hilfe benötigen, wenden Sie sich bitte an den[Aspose-Community-Forum](https://forum.aspose.com/) für die Unterstützung.

## FAQs

### Wie installiere ich Aspose.Words für Java?
 Sie können Aspose.Words für Java herunterladen von[Hier](https://releases.aspose.com/words/java/) und befolgen Sie die Installationsanweisungen in der Dokumentation.

### Kann ich das Nummerierungsformat von Listen anpassen?
Ja, Aspose.Words für Java bietet umfangreiche Optionen zum Anpassen von Listennummerierungsformaten. Weitere Einzelheiten finden Sie in der API-Dokumentation.

### Ist Aspose.Words für Java mit den neuesten Word-Dokumentstandards kompatibel?
Ja, Sie können Aspose.Words für Java so konfigurieren, dass es verschiedenen Word-Dokumentstandards entspricht, einschließlich ISO 29500.

### Kann ich mit Aspose.Words für Java komplexe Dokumente mit Tabellen und Bildern erstellen?
Absolut! Aspose.Words für Java unterstützt erweiterte Dokumentformatierung, einschließlich Tabellen, Bilder und mehr. Beispiele finden Sie in der Dokumentation.

### Wo kann ich eine temporäre Lizenz für Aspose.Words für Java erhalten?
Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
