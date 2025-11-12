---
date: '2025-11-12'
description: Erfahren Sie, wie Sie Aspose.Words für Java s LayoutCollector und LayoutEnumerator
  verwenden, um die Paginierung zu analysieren, das Dokumentlayout zu durchlaufen,
  Layout‑Callbacks zu implementieren und die Seitennummerierung in fortlaufenden Abschnitten
  neu zu starten.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: de
title: Java-Paginierungsanalyse mit Aspose.Words-Layout-Tools
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java‑Paginierungsanalyse mit Aspose.Words Layout‑Tools

## Einleitung  

Wenn Sie in einer Java‑Anwendung **die Paginierung analysieren** oder **das Layout eines Dokuments durchlaufen** müssen, bietet Aspose.Words für Java zwei leistungsstarke APIs: **`LayoutCollector`** und **`LayoutEnumerator`**. Diese Klassen ermöglichen es Ihnen, herauszufinden, wie viele Seiten ein Knoten belegt, jedes Layout‑Element zu durchlaufen, auf Layout‑Ereignisse zu reagieren und sogar die Seitennummerierung in kontinuierlichen Abschnitten neu zu starten. In diesem Leitfaden gehen wir jede Funktion Schritt für Schritt durch, zeigen praxisnahe Code‑Snippets und erklären die erwarteten Ergebnisse, damit Sie sie sofort anwenden können.

Sie lernen, wie man:

* **LayoutCollector verwendet**, um die Start‑ und Endseite eines beliebigen Knotens zu ermitteln (use layoutcollector page span)  
* **das Dokumentlayout durchläuft** mit LayoutEnumerator (traverse document layout)  
* **Layout‑Callbacks implementiert**, um auf Paginierungs‑Ereignisse zu reagieren (implement layout callback)  
* **die Seitennummerierung** in kontinuierlichen Abschnitten neu startet (restart page numbering sections)  

Los geht’s.

## Voraussetzungen  

### Erforderliche Bibliotheken  

| Build‑Tool | Abhängigkeit |
|------------|--------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Hinweis:** Die Versionsnummer wird aus Kompatibilitätsgründen angegeben; der Code funktioniert mit jeder aktuellen Aspose.Words‑Version für Java.

### Umgebung  

* JDK 8 oder neuer  
* Eine IDE wie IntelliJ IDEA oder Eclipse  

### Kenntnisse  

Grundlegende Java‑Programmierung und Vertrautheit mit Maven/Gradle reichen aus, um den Beispielen zu folgen.

## Aspose.Words einrichten  

Bevor Sie irgendeine Layout‑API aufrufen können, muss die Bibliothek lizenziert sein (oder im Testmodus verwendet werden). Das folgende Snippet zeigt die minimale Initialisierung:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Der Code ändert kein Dokument; er bereitet lediglich die Aspose‑Umgebung vor.*  

Jetzt können wir zu den Kernfunktionen übergehen.

## Feature 1: **LayoutCollector** zur Analyse der Paginierung verwenden  

`LayoutCollector` ordnet jedem Knoten in einem `Document` die Seiten zu, die er belegt. Dies ist der zuverlässigste Weg, um **use layoutcollector page span** für die Paginierungsanalyse zu nutzen.

### Schritt‑für‑Schritt‑Implementierung  

1. **Ein neues Dokument erstellen und einen LayoutCollector anhängen.**  
2. **Inhalt einfügen, der Paginierung erzwingt** (z. B. Seiten‑ oder Abschnittsumbrüche).  
3. **Das Layout aktualisieren** mit `updatePageLayout()`.  
4. **Den Collector abfragen** nach Startseite, Endseite und Gesamtseitenzahl.

#### 1️⃣ Dokument und LayoutCollector initialisieren  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Dokument befüllen  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Layout aktualisieren und Kennzahlen abrufen  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Erwartete Ausgabe**

```
Document spans 5 pages.
```

> **Warum das funktioniert:** `updatePageLayout()` zwingt Aspose.Words, das Layout neu zu berechnen; danach kann `LayoutCollector` die Seitenbereiche exakt melden.

## Feature 2: Dokumentlayout mit **LayoutEnumerator** durchlaufen  

Wenn Sie **das Dokumentlayout durchlaufen** müssen (z. B. für benutzerdefiniertes Rendering oder Analysen), bietet `LayoutEnumerator` eine baumartige Ansicht von Seiten, Absätzen, Zeilen und Wörtern.

### Schritt‑für‑Schritt‑Implementierung  

1. Ein vorhandenes Dokument laden, das Layout‑Entitäten enthält.  
2. Eine Instanz von `LayoutEnumerator` erstellen.  
3. Zum Wurzel‑`PAGE`‑Element wechseln.  
4. Das Layout vorwärts und rückwärts mit rekursiven Hilfsmethoden durchlaufen.

#### 1️⃣ Dokument laden und Enumerator erstellen  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Position auf der Ebene „Seite“ setzen  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Vorwärts‑Durchlauf (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Rückwärts‑Durchlauf  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Hilfsmethoden** (`traverseLayoutForward` / `traverseLayoutBackward`) werden rekursiv implementiert, um jedes Kind‑Element zu besuchen und dessen Typ sowie Seitenindex auszugeben. Sie können sie anpassen, um Statistiken zu sammeln, Grafiken zu rendern oder Layout‑Eigenschaften zu ändern.

## Feature 3: **Layout‑Callbacks** implementieren  

Manchmal müssen Sie reagieren, wenn Aspose.Words einen Teil des Dokuments fertig gelayoutet hat. Die Implementierung von `IPageLayoutCallback` ermöglicht **implement layout callback**‑Logik, etwa das Speichern jeder Seite als Bild.

### Schritt‑für‑Schritt‑Implementierung  

1. Eine Callback‑Instanz den `LayoutOptions` des Dokuments zuweisen.  
2. Im Callback die Ereignisse `PART_REFLOW_FINISHED` und `CONVERSION_FINISHED` behandeln.  
3. Die aktuelle Seite mit `ImageSaveOptions` als PNG rendern.

#### 1️⃣ Callback registrieren  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback‑Klasse  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**Was passiert:** Jedes Mal, wenn ein Layout‑Teil das Nachfließen beendet, rendert der Callback diese Seite in eine PNG‑Datei und liefert Ihnen so einen visuellen Verlauf des Paginierungsprozesses.

## Feature 4: Seitennummerierung in **kontinuierlichen Abschnitten** neu starten  

Enthält ein Dokument kontinuierliche Abschnitte, möchten Sie möglicherweise, dass die Seitennummerierung nur dann neu beginnt, wenn eine neue physische Seite beginnt. Dies wird über die Einstellung `ContinuousSectionRestart` realisiert.

### Schritt‑für‑Schritt‑Implementierung  

1. Das Ziel‑Dokument laden.  
2. Die Option `ContinuousSectionPageNumberingRestart` ändern.  
3. `updatePageLayout()` erneut ausführen, um die Änderung anzuwenden.

#### 1️⃣ Dokument laden  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Neustart‑Verhalten konfigurieren  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Ergebnis:** Die Seitennummerierung startet nun nur, wenn eine neue physische Seite beginnt, wodurch Berichte oder Bücher ein sauberes, professionelles Erscheinungsbild erhalten.

## Praktische Anwendungsfälle  

| Szenario | Welches API hilft | Nutzen |
|----------|-------------------|--------|
| **Lange Verträge prüfen** | `LayoutCollector` | Schnell feststellen, welche Klauseln mehrere Seiten umfassen. |
| **Benutzerdefiniertes PDF‑Rendering** | `LayoutEnumerator` | Das Layout‑Baum durchlaufen, um jede Zeile als Vektorgrafik zu exportieren. |
| **Live‑Dokumentvorschau** | Layout‑Callbacks | Seitenbilder on‑the‑fly erzeugen, während der Benutzer Inhalte bearbeitet. |
| **Mehr‑Abschnitt‑Berichte** | Neustart der Seitennummerierung in kontinuierlichen Abschnitten | Logische Seitennummern ohne manuelle Anpassungen behalten. |

## Performance‑Tipps  

* **Unbenutzte Knoten** vor dem Aufruf von `updatePageLayout()` entfernen – weniger Elemente bedeuten schnellere Paginierung.  
* **Einen einzelnen LayoutCollector** für mehrere Abfragen wiederverwenden, anstatt ihn jedes Mal neu zu erzeugen.  
* **Die Traversaltiefe** bei Verwendung von LayoutEnumerator begrenzen, wenn nur Seiten‑Ebene‑Daten benötigt werden.  
* **Streams freigeben** (wie im Callback‑Beispiel gezeigt), um Speicherlecks bei großen Dokumenten zu vermeiden.

## Fazit  

Durch die Beherrschung von `LayoutCollector`, `LayoutEnumerator`, Layout‑Callbacks und der Neustart‑Funktion für kontinuierliche Abschnitte verfügen Sie nun über ein komplettes Werkzeugset für **analyze pagination java**, **traverse document layout** und **restart page numbering sections**. Diese APIs ermöglichen Ihnen den Aufbau robuster, leistungsstarker Textverarbeitungspipelines, die jedes Mal professionelle Ergebnisse liefern.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}