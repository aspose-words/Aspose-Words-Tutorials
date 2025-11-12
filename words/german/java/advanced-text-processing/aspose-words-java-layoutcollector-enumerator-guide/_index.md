---
date: '2025-11-12'
description: Erfahren Sie, wie Sie den LayoutCollector und LayoutEnumerator von Aspose.Words
  für Java verwenden, um Seitenbereiche zu bestimmen, Layout‑Entitäten zu durchlaufen
  und die Seitennummerierung in fortlaufenden Abschnitten neu zu starten.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: de
title: 'Aspose.Words Java: Leitfaden für LayoutCollector und LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: LayoutCollector‑ & LayoutEnumerator‑Leitfaden

## Introduction  

Haben Sie Schwierigkeiten, **den Seitenumfang** zu bestimmen, die Seitennummerierung zu analysieren oder die Seitennummerierung in komplexen Java‑Dokumenten neu zu starten? Mit **Aspose.Words for Java** können Sie diese Probleme schnell mit `LayoutCollector` und `LayoutEnumerator` lösen. In diesem Leitfaden zeigen wir Ihnen **wie Sie LayoutCollector verwenden**, **wie Sie LayoutEnumerator durchlaufen** und wie Sie die Seitennummerierung in fortlaufenden Abschnitten steuern – alles mit klaren, schrittweisen Code‑Beispielen, die Sie noch heute ausführen können.

Sie lernen:

1. `LayoutCollector` zu nutzen, um den **Seitenumfang** eines beliebigen Knotens zu **bestimmen**.  
2. **Layout‑Entitäten** mit `LayoutEnumerator` zu **durchlaufen**.  
3. Layout‑Callbacks für dynamisches Rendering zu implementieren.  
4. **Seitennummerierung** in fortlaufenden Abschnitten **neu zu starten**.  

Lassen Sie uns beginnen, indem wir sicherstellen, dass Ihre Umgebung bereit ist.

## Prerequisites  

### Required Libraries  

> **Note:** Der Code funktioniert mit der neuesten Aspose.Words for Java‑Version (keine Versionsnummer erforderlich).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Environment  

- JDK 17 oder neuer.  
- IntelliJ IDEA, Eclipse oder eine andere Java‑IDE Ihrer Wahl.  

### Knowledge  

Grundlegende Kenntnisse der Java‑Syntax und objektorientierter Konzepte helfen Ihnen, den Beispielen zu folgen.

## Setting Up Aspose.Words  

Fügen Sie zunächst die Aspose.Words‑Bibliothek zu Ihrem Projekt hinzu und wenden Sie eine Lizenz an (oder nutzen Sie die Testversion). Das folgende Snippet zeigt, wie Sie die Lizenz laden und bestätigen, dass die Bibliothek bereit ist:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Tip:** Bewahren Sie die Lizenzdatei außerhalb der Versionskontrolle auf, um Ihre Zugangsdaten zu schützen.

Jetzt können wir zu den beiden Kernfunktionen übergehen.

## 1. How to Use LayoutCollector for Page‑Span Analysis  

`LayoutCollector` ermöglicht es Ihnen, den **Seitenumfang** für jeden Knoten in einem Dokument zu **bestimmen**, was für die Analyse der Seitennummerierung unerlässlich ist.

### Step‑by‑Step Implementation  

1. **Ein neues Document‑Objekt und eine LayoutCollector‑Instanz erstellen.**  
2. **Inhalt hinzufügen, der mehrere Seiten umfasst.**  
3. **Das Layout aktualisieren und die Seiten‑Umfang‑Metriken abfragen.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Explanation**

- `DocumentBuilder` fügt Text und Seitenumbrüche ein und erzeugt ein Dokument, das natürlich mehrere Seiten füllt.  
- `updatePageLayout()` zwingt Aspose.Words, das Layout zu berechnen, sodass die Seitenzahlen exakt sind.  
- `getNumPagesSpanned()` gibt die Gesamtzahl der von dem übergebenen Knoten belegten Seiten zurück (hier das gesamte Dokument).

## 2. How to Traverse LayoutEnumerator  

`LayoutEnumerator` bietet eine **strukturierte Ansicht von Layout‑Entitäten** (Seiten, Absätze, Runs usw.) und ermöglicht das Vor‑ und Zurückbewegen durch diese.

### Step‑by‑Step Implementation  

1. Laden Sie ein vorhandenes Dokument, das Layout‑Entitäten enthält.  
2. Erstellen Sie eine `LayoutEnumerator`‑Instanz.  
3. Wechseln Sie zur Ebene der Seite und durchlaufen Sie das Layout vorwärts und rückwärts mithilfe von Hilfsmethoden.

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Note:** Die Methoden `traverseLayoutForward` und `traverseLayoutBackward` sind rekursive Hilfsfunktionen, die den Layout‑Baum durchlaufen. Sie können sie anpassen, um Informationen wie Begrenzungsrahmen, Schriftartdetails oder benutzerdefinierte Metadaten zu sammeln.

## 3. How to Implement Page‑Layout Callbacks  

Manchmal müssen Sie auf Layout‑Ereignisse reagieren – z. B. wenn ein Abschnitt das Neu‑Layout beendet hat oder die Konvertierung in ein anderes Format abgeschlossen ist. Implementieren Sie das Interface `IPageLayoutCallback`, um diese Benachrichtigungen zu erhalten.

### Step‑by‑Step Implementation  

1. Setzen Sie eine Callback‑Instanz in den Layout‑Optionen des Dokuments.  
2. Definieren Sie die Callback‑Logik, um die Ereignisse `PART_REFLOW_FINISHED` und `CONVERSION_FINISHED` zu verarbeiten.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Explanation**

- `notify()` empfängt jedes Layout‑Ereignis. Wir filtern die Ereignisse, die uns interessieren.  
- Wenn ein Teil das Neu‑Layout beendet hat, speichert `renderPage()` diese Seite als PNG‑Bild.  

## 4. How to Restart Page Numbering in Continuous Sections  

Enthält ein Dokument fortlaufende Abschnitte, möchten Sie möglicherweise, dass die Seitennummerierung nur auf einer neuen physischen Seite neu beginnt. Aspose.Words ermöglicht dies mit `ContinuousSectionRestart`.

### Step‑by‑Step Implementation  

1. Laden Sie das Ziel‑Dokument.  
2. Setzen Sie die Option `ContinuousSectionPageNumberingRestart`.  
3. Aktualisieren Sie das Layout, um die Änderung anzuwenden.

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Explanation**

- `FROM_NEW_PAGE_ONLY` weist Aspose.Words an, die Nummerierung nur dann neu zu starten, wenn eine neue physische Seite erscheint, wodurch ein nahtloser Fluss über fortlaufende Abschnitte hinweg erhalten bleibt.

## Practical Applications  

| Scenario | Which Feature Helps? | Benefit |
|----------|----------------------|---------|
| **Audit document pagination** | `LayoutCollector` | Schnell Abschnitte finden, die über Seiten hinausgehen. |
| **Render PDFs with exact visual fidelity** | `LayoutEnumerator` + callbacks | Auf Layout‑Details zugreifen für präzises Rendering. |
| **Automate watermark insertion after each page layout** | Page‑layout callbacks | Sofort reagieren, wenn eine Seite layoutet wurde. |
| **Produce multi‑section reports with custom numbering** | Continuous section restart | Professionelle Seitennummerierung beibehalten, ohne manuelle Anpassungen. |

## Performance Tips  

- **Unbenutzte Knoten** vor dem Aufruf von `updatePageLayout()` entfernen, um den Speicherverbrauch gering zu halten.  
- **Eine einzelne LayoutCollector‑Instanz** für mehrere Abfragen wiederverwenden, anstatt sie jedes Mal