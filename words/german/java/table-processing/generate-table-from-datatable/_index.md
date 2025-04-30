---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable generieren. Erstellen Sie mühelos professionelle Word-Dokumente mit formatierten Tabellen."
"linktitle": "Tabelle aus Datentabelle generieren"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Tabelle aus Datentabelle generieren"
"url": "/de/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tabelle aus Datentabelle generieren

## Einführung

Das dynamische Erstellen von Tabellen aus Datenquellen ist in vielen Anwendungen eine gängige Aufgabe. Ob Sie Berichte, Rechnungen oder Datenzusammenfassungen erstellen – die Möglichkeit, Tabellen programmgesteuert mit Daten zu füllen, spart Ihnen viel Zeit und Aufwand. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable generieren. Wir unterteilen den Prozess in überschaubare Schritte, damit Sie jeden Teil klar verstehen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie für den Einstieg benötigen:

1. Java Development Kit (JDK): Stellen Sie sicher, dass JDK auf Ihrem Rechner installiert ist. Sie können es von der [Oracle-Website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Aspose.Words für Java: Sie benötigen die Aspose.Words-Bibliothek. Die neueste Version finden Sie hier: [Asposes Veröffentlichungsseite](https://releases.aspose.com/words/java/).

3. IDE: Eine integrierte Entwicklungsumgebung (IDE) wie IntelliJ IDEA oder Eclipse erleichtert das Codieren.

4. Grundkenntnisse in Java: Wenn Sie mit den Konzepten der Java-Programmierung vertraut sind, können Sie die Codeausschnitte besser verstehen.

5. Beispieldaten: Für dieses Tutorial verwenden wir die XML-Datei „List of people.xml“, um eine Datenquelle zu simulieren. Sie können diese Datei mit Beispieldaten zum Testen erstellen.

## Schritt 1: Erstellen Sie ein neues Dokument

Zuerst müssen wir ein neues Dokument erstellen, in dem unsere Tabelle gespeichert wird. Dies ist die Leinwand für unsere Arbeit.

```java
Document doc = new Document();
```

Hier instantiieren wir eine neue `Document` Objekt. Dies dient als Arbeitsdokument, in dem wir unsere Tabelle erstellen.

## Schritt 2: DocumentBuilder initialisieren

Als nächstes verwenden wir die `DocumentBuilder` Klasse, die es uns ermöglicht, das Dokument einfacher zu bearbeiten.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der `DocumentBuilder` Das Objekt bietet Methoden zum Einfügen von Tabellen, Text und anderen Elementen in das Dokument.

## Schritt 3: Seitenausrichtung festlegen

Da wir davon ausgehen, dass unsere Tabelle breit ist, stellen wir die Seitenausrichtung auf Querformat ein.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Dieser Schritt ist entscheidend, da er sicherstellt, dass unsere Tabelle gut auf die Seite passt, ohne abgeschnitten zu werden.

## Schritt 4: Daten aus XML laden

Nun müssen wir unsere Daten aus der XML-Datei in eine `DataTable`. Hierher stammen unsere Daten.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

Hier lesen wir die XML-Datei und holen die erste Tabelle aus dem Datensatz. `DataTable` enthält die Daten, die wir in unserem Dokument anzeigen möchten.

## Schritt 5: Importieren Sie die Tabelle aus DataTable

Jetzt kommt der spannende Teil: das Importieren unserer Daten in das Dokument als Tabelle.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

Wir nennen die Methode `importTableFromDataTable`, vorbei an der `DocumentBuilder`, unser `DataTable`und ein Boolescher Wert, der angibt, ob Spaltenüberschriften eingeschlossen werden sollen.

## Schritt 6: Gestalten Sie die Tabelle

Sobald wir unsere Tabelle haben, können wir sie mit etwas Styling versehen, damit sie gut aussieht.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Dieser Code wendet einen vordefinierten Stil auf die Tabelle an und verbessert so ihre visuelle Attraktivität und Lesbarkeit.

## Schritt 7: Unerwünschte Zellen entfernen

Wenn Sie Spalten haben, die Sie nicht anzeigen möchten, beispielsweise eine Bildspalte, können Sie diese einfach entfernen.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Dieser Schritt stellt sicher, dass unsere Tabelle nur die relevanten Informationen anzeigt.

## Schritt 8: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument mit der generierten Tabelle.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Diese Zeile speichert das Dokument im angegebenen Verzeichnis, sodass Sie die Ergebnisse überprüfen können.

## Die Methode importTableFromDataTable

Schauen wir uns die `importTableFromDataTable` -Methode. Diese Methode ist für die Erstellung der Tabellenstruktur und das Auffüllen mit Daten verantwortlich.

### Schritt 1: Starten Sie die Tabelle

Zuerst müssen wir eine neue Tabelle im Dokument beginnen.

```java
Table table = builder.startTable();
```

Dadurch wird eine neue Tabelle in unserem Dokument initialisiert.

### Schritt 2: Spaltenüberschriften hinzufügen

Wenn wir Spaltenüberschriften einfügen möchten, aktivieren wir das Kontrollkästchen `importColumnHeadings` Flagge.

```java
if (importColumnHeadings) {
    // Ursprüngliche Formatierung speichern
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Überschriftenformatierung festlegen
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Spaltennamen einfügen
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Wiederherstellen der ursprünglichen Formatierung
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

Dieser Codeblock formatiert die Überschriftenzeile und fügt die Namen der Spalten aus dem `DataTable`.

### Schritt 3: Füllen Sie die Tabelle mit Daten

Nun durchlaufen wir jede Zeile des `DataTable` um Daten in die Tabelle einzufügen.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

In diesem Abschnitt behandeln wir verschiedene Datentypen, formatieren Daten entsprechend und fügen andere Daten als Text ein.

### Schritt 4: Beenden Sie die Tabelle

Abschließend beenden wir die Tabelle, nachdem alle Daten eingefügt wurden.

```java
builder.endTable();
```

Diese Zeile markiert das Ende unserer Tabelle und ermöglicht es dem `DocumentBuilder` um zu wissen, dass wir mit diesem Abschnitt fertig sind.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable generieren. Mit diesen Schritten können Sie ganz einfach dynamische Tabellen in Ihren Dokumenten basierend auf verschiedenen Datenquellen erstellen. Egal, ob Sie Berichte oder Rechnungen erstellen, diese Methode optimiert Ihren Workflow und verbessert Ihren Dokumenterstellungsprozess.

## Häufig gestellte Fragen

### Was ist Aspose.Words für Java?
Aspose.Words für Java ist eine leistungsstarke Bibliothek zum programmgesteuerten Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten.

### Kann ich Aspose.Words kostenlos nutzen?
Ja, Aspose bietet eine kostenlose Testversion an. Sie können sie hier herunterladen. [Hier](https://releases.aspose.com/).

### Wie formatiere ich Tabellen in Aspose.Words?
Sie können Stile mithilfe vordefinierter Stilkennungen und von der Bibliothek bereitgestellter Optionen anwenden.

### Welche Datentypen kann ich in Tabellen einfügen?
Sie können verschiedene Datentypen einfügen, darunter Text, Zahlen und Datumsangaben, die entsprechend formatiert werden können.

### Wo erhalte ich Support für Aspose.Words?
Sie finden Unterstützung und können Fragen stellen auf der [Aspose-Forum](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}