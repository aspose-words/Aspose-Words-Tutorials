---
title: Tabelle aus Datentabelle generieren
linktitle: Tabelle aus Datentabelle generieren
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable generieren. Erstellen Sie mühelos professionelle Word-Dokumente mit formatierten Tabellen.
weight: 11
url: /de/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabelle aus Datentabelle generieren

## Einführung

Das dynamische Erstellen von Tabellen aus Datenquellen ist in vielen Anwendungen eine gängige Aufgabe. Egal, ob Sie Berichte, Rechnungen oder Datenzusammenfassungen erstellen, die Möglichkeit, eine Tabelle programmgesteuert mit Daten zu füllen, kann Ihnen viel Zeit und Mühe sparen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable erstellen. Wir unterteilen den Prozess in überschaubare Schritte, damit Sie jeden Teil klar verstehen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie zum Einstieg benötigen:

1.  Java Development Kit (JDK): Stellen Sie sicher, dass JDK auf Ihrem Rechner installiert ist. Sie können es von der[Oracle-Website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words für Java: Sie benötigen die Aspose.Words-Bibliothek. Sie können die neueste Version herunterladen von[Aspose's Veröffentlichungsseite](https://releases.aspose.com/words/java/).

3. IDE: Eine integrierte Entwicklungsumgebung (IDE) wie IntelliJ IDEA oder Eclipse erleichtert die Codierung.

4. Grundkenntnisse in Java: Die Vertrautheit mit Java-Programmierkonzepten hilft Ihnen, die Codeausschnitte besser zu verstehen.

5. Beispieldaten: Für dieses Tutorial verwenden wir eine XML-Datei namens „List of people.xml“, um eine Datenquelle zu simulieren. Sie können diese Datei mit Beispieldaten zum Testen erstellen.

## Schritt 1: Neues Dokument erstellen

Zuerst müssen wir ein neues Dokument erstellen, in dem unsere Tabelle gespeichert wird. Dies ist die Leinwand für unsere Arbeit.

```java
Document doc = new Document();
```

 Hier instantiieren wir ein neues`Document` Objekt. Dies dient uns als Arbeitsdokument, in dem wir unsere Tabelle erstellen.

## Schritt 2: DocumentBuilder initialisieren

 Als nächstes verwenden wir die`DocumentBuilder` Klasse, die es uns ermöglicht, das Dokument einfacher zu bearbeiten.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Der`DocumentBuilder` Das Objekt bietet Methoden zum Einfügen von Tabellen, Text und anderen Elementen in das Dokument.

## Schritt 3: Seitenausrichtung festlegen

Da unsere Tabelle voraussichtlich breit sein wird, stellen wir die Seitenausrichtung auf Querformat ein.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Dieser Schritt ist wichtig, da er gewährleistet, dass unsere Tabelle gut auf die Seite passt, ohne abgeschnitten zu werden.

## Schritt 4: Daten aus XML laden

 Nun müssen wir unsere Daten aus der XML-Datei in ein`DataTable`. Hierher stammen unsere Daten.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 Hier lesen wir die XML-Datei und holen die erste Tabelle aus dem Datensatz.`DataTable` enthält die Daten, die wir in unserem Dokument anzeigen möchten.

## Schritt 5: Importieren Sie die Tabelle aus DataTable

Jetzt kommt der spannende Teil: das Importieren unserer Daten in das Dokument als Tabelle.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 Wir nennen die Methode`importTableFromDataTable` , vorbei an der`DocumentBuilder` , unser`DataTable`und ein Boolescher Wert, der angibt, ob Spaltenüberschriften eingeschlossen werden sollen.

## Schritt 6: Gestalten Sie die Tabelle

Sobald wir unsere Tabelle haben, können wir sie mit etwas Stil versehen, damit sie gut aussieht.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Dieser Code wendet einen vordefinierten Stil auf die Tabelle an und verbessert so ihre optische Attraktivität und Lesbarkeit.

## Schritt 7: Unerwünschte Zellen entfernen

Wenn Sie Spalten haben, die Sie nicht anzeigen möchten, z. B. eine Bildspalte, können Sie diese einfach entfernen.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Dieser Schritt stellt sicher, dass in unserer Tabelle nur die relevanten Informationen angezeigt werden.

## Schritt 8: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument mit der generierten Tabelle.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Diese Zeile speichert das Dokument im angegebenen Verzeichnis und ermöglicht Ihnen, die Ergebnisse zu überprüfen.

## Die Methode importTableFromDataTable

 Schauen wir uns die`importTableFromDataTable` -Methode. Diese Methode ist für das Erstellen und Auffüllen der Tabellenstruktur mit Daten verantwortlich.

### Schritt 1: Starten Sie die Tabelle

Zuerst müssen wir im Dokument eine neue Tabelle beginnen.

```java
Table table = builder.startTable();
```

Dadurch wird eine neue Tabelle in unserem Dokument initialisiert.

### Schritt 2: Spaltenüberschriften hinzufügen

 Wenn wir Spaltenüberschriften einbinden möchten, aktivieren wir das Kontrollkästchen`importColumnHeadings` Flagge.

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

 Dieser Codeblock formatiert die Überschriftenzeile und fügt die Namen der Spalten aus dem`DataTable`.

### Schritt 3: Füllen Sie die Tabelle mit Daten

 Nun durchlaufen wir jede Zeile des`DataTable` um Daten in die Tabelle einzufügen.

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

Zum Schluss schließen wir die Tabelle ab, nachdem alle Daten eingefügt wurden.

```java
builder.endTable();
```

 Diese Zeile markiert das Ende unserer Tabelle und ermöglicht den`DocumentBuilder` um zu wissen, dass wir mit diesem Abschnitt fertig sind.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für Java eine Tabelle aus einer DataTable generieren. Indem Sie diese Schritte befolgen, können Sie ganz einfach dynamische Tabellen in Ihren Dokumenten basierend auf verschiedenen Datenquellen erstellen. Egal, ob Sie Berichte oder Rechnungen erstellen, diese Methode rationalisiert Ihren Arbeitsablauf und verbessert Ihren Dokumenterstellungsprozess.

## Häufig gestellte Fragen

### Was ist Aspose.Words für Java?
Aspose.Words für Java ist eine leistungsstarke Bibliothek zum programmgesteuerten Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten.

### Kann ich Aspose.Words kostenlos nutzen?
 Ja, Aspose bietet eine kostenlose Testversion an. Sie können sie hier herunterladen:[Hier](https://releases.aspose.com/).

### Wie formatiere ich Tabellen in Aspose.Words?
Sie können Stile mithilfe vordefinierter Stilkennungen und Optionen anwenden, die von der Bibliothek bereitgestellt werden.

### Welche Arten von Daten kann ich in Tabellen einfügen?
Sie können verschiedene Datentypen einfügen, darunter Text, Zahlen und Daten, die entsprechend formatiert werden können.

### Wo erhalte ich Support für Aspose.Words?
 Sie finden Unterstützung und können Fragen stellen auf der[Aspose-Forum](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
