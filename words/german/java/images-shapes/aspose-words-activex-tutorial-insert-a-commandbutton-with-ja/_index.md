---
category: general
date: 2026-08-07
description: Das Aspose.Words ActiveX‑Tutorial zeigt, wie man mit Java ein CommandButton‑Steuerelement
  zu einem Word‑Dokument hinzufügt. Lernen Sie den vollständigen Code, die Konfiguration
  und die Speicher­schritte.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: de
lastmod: 2026-08-07
og_description: Das Aspose.Words ActiveX‑Tutorial erklärt, wie man ein CommandButton‑ActiveX‑Steuerelement
  in ein Word‑Dokument mit Java einbettet. Folgen Sie dem vollständigen Beispiel,
  um das Dokument zu erstellen, zu konfigurieren und zu speichern.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX‑Tutorial – Java Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX‑Tutorial – Einen CommandButton mit Java einfügen
url: /de/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX‑Tutorial – Einfügen eines CommandButton mit Java

Wenn Sie ein ActiveX‑Steuerelement in einer Word‑Datei einbetten müssen, führt Sie dieses **Aspose.Words ActiveX‑Tutorial** durch den gesamten Vorgang. Sie sehen, wie man ein leeres Dokument erstellt, einen CommandButton einfügt, dessen Eigenschaften festlegt und das Ergebnis speichert – alles mit einfachem Java‑Code.

Das Beispiel verwendet die Aspose.Words for Java API, die die Notwendigkeit von Microsoft Office auf dem Build‑Server eliminiert. Am Ende dieses Leitfadens können Sie .docx‑Dateien erzeugen, die voll funktionsfähige CommandButton‑Steuerelemente enthalten und in Windows‑Umgebungen einsatzbereit sind.

## Voraussetzungen

- Java Development Kit (JDK) 8 oder neuer installiert.
- Maven oder ein anderes Build‑Tool zur Verwaltung von Abhängigkeiten.
- Eine Aspose.Words for Java Lizenz (oder ein temporärer Evaluierungsschlüssel), um Evaluierungs‑Wasserzeichen zu vermeiden.
- Grundlegende Kenntnisse der Java‑Syntax und objektorientierten Programmierung.

> **Pro‑Tipp:** Fügen Sie die Aspose.Words Maven‑Abhängigkeit zu Ihrer `pom.xml` hinzu, damit die IDE Klassen automatisch auflösen kann:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Schritt 1: Erstellen eines neuen leeren Dokuments und eines `DocumentBuilder`

Die Klasse `Document` repräsentiert die Word‑Datei im Speicher, während `DocumentBuilder` eine fluente API zum Bearbeiten des Dokuments bereitstellt. Das Initialisieren beider Objekte bereitet das Dokument für weitere Änderungen vor.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:**  
`DocumentBuilder` verfolgt die aktuelle Cursor‑Position, sodass jede nachfolgende Einfügeoperation – wie das Hinzufügen eines Steuerelements – genau dort erscheint, wo Sie es beabsichtigen.

## Schritt 2: Einfügen eines CommandButton‑ActiveX‑Steuerelements

Aspose.Words stellt `Forms2OleControl` für ActiveX‑Objekte bereit. Die Methode `insertForms2OleControl` erfordert den Steuertyp, den Sie über die Aufzählung `Forms2OleControlType` angeben.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Erklärung:**  
Das eingefügte Steuerelement ist ein COM‑basiertes Objekt, das Word beim Öffnen des Dokuments in einer Windows‑Umgebung als anklickbaren Button darstellt.

## Schritt 3: Konfigurieren der Eigenschaften des Buttons

Nach dem Einfügen können Sie den Namen, die Beschriftung, Größe und Position des Buttons anpassen. Diese Eigenschaften beeinflussen das Aussehen und Verhalten des Steuerelements in Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Warum diese Einstellungen wichtig sind:**  

- **Name** – Ermöglicht VBA‑Makros, das Steuerelement zu referenzieren (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Bestimmt die sichtbare Beschriftung, auf die Benutzer klicken.
- **Left / Top** – Steuert die Platzierung relativ zu den Seitenrändern.
- **Width / Height** – Gewährleistet eine konsistente visuelle Größe über verschiedene Bildschirmauflösungen hinweg.

## Schritt 4: Dokument speichern

Der Aufruf von `save` schreibt die In‑Memory‑Repräsentation in eine physische Datei. Sie können jedes unterstützte Format wählen (`.docx`, `.doc`, `.pdf` usw.). Für dieses Tutorial behalten wir das native Word‑Format bei.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Ergebnis:**  
Öffnet man `ActiveXDemo.docx` in Microsoft Word, wird ein CommandButton mit der Beschriftung **Submit** an den angegebenen Koordinaten angezeigt. Das Klicken des Buttons löst das Standardverhalten aus (standardmäßig ist kein VBA‑Code angehängt).

## Vollständiger Quellcode

Wenn man die Teile zusammenfügt, sieht das vollständige, ausführbare Programm wie folgt aus:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Erwartete Ausgabe

- Eine Datei namens **ActiveXDemo.docx**, die im Ordner `output` liegt.
- Beim Öffnen in Microsoft Word (Windows) zeigt das Dokument einen anklickbaren **Submit**‑Button an der definierten Position.
- Der Button kann ausgewählt, verschoben oder über die Word‑Benutzeroberfläche (Entwicklertools → Eigenschaften) mit VBA‑Code verknüpft werden.

## Umgang mit gängigen Variationen

| Szenario | Anpassung |
|----------|------------|
| **Als .doc speichern** (Legacy‑Format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Einen Ereignishandler hinzufügen** | Word stellt ActiveX‑Ereignisse nicht über Aspose.Words bereit. Sie müssen nach der Dokumenterstellung manuell VBA‑Code hinzufügen. |
| **Mehrere Steuerelemente** | Wiederholen Sie den Insert/Configure‑Block mit unterschiedlichen `setName`‑ und `setCaption`‑Werten. |
| **Anderer Steuertyp (z. B. CheckBox)** | Verwenden Sie `Forms2OleControlType.CHECKBOX` im Aufruf von `insertForms2OleControl`. |
| **Nicht‑Windows‑Plattformen** | ActiveX‑Steuerelemente werden nur in Word für Windows gerendert. Für plattformübergreifende Lösungen sollten Sie Inhaltssteuerelemente (`StructuredDocumentTag`) in Betracht ziehen. |

## Bewährte Vorgehensweisen und Fallstricke

- **License early** – Registrieren Sie Ihre Aspose.Words‑Lizenz, bevor Sie das `Document` erstellen, um Evaluierungs‑Hinweise zu vermeiden.
- **Coordinate system** – Positionen werden in Punkten gemessen (1 pt = 1/72 in). Konvertieren Sie von Pixeln oder Zentimetern, falls Ihr UI‑Design diese Einheiten verwendet.
- **File paths** – Verwenden Sie absolute Pfade oder die Java‑`Paths`‑API, um `FileNotFoundException` zu vermeiden, wenn das Ausgabeverzeichnis nicht existiert.
- **Thread safety** – `Document` und `DocumentBuilder` sind nicht thread‑sicher. Erzeugen Sie separate Instanzen pro Thread, wenn Sie Dokumente parallel generieren.
- **Testing** – Überprüfen Sie das erzeugte Dokument in der Ziel‑Word‑Version (z. B. Word 2016, Word 365), da ältere Versionen ActiveX‑Steuerelemente anders darstellen können.

## Fazit

Dieses **Aspose.Words ActiveX‑Tutorial** zeigt, wie man programmgesteuert ein CommandButton‑Steuerelement zu einem Word‑Dokument mit Java hinzufügt. Sie haben gelernt, wie man:

1. Ein `Document` und einen `DocumentBuilder` initialisiert.
2. Ein `Forms2OleControl` vom Typ `COMMAND_BUTTON` einfügt.
3. Den Namen, die Beschriftung, Größe und Position des Buttons festlegt.
4. Das Dokument als .docx‑Datei speichert, die das ActiveX‑Steuerelement enthält.

Ab hier können Sie weitere Steuerelementtypen erkunden, die VBA‑Makro‑Einfügung automatisieren oder ActiveX‑Steuerelemente mit anderen Aspose.Words‑Funktionen wie Seriendruck und Inhaltssteuerelementen kombinieren. Experimentieren Sie mit verschiedenen Layouts und integrieren Sie die erzeugten Dokumente in Ihre größere, Java‑basierte Reporting‑Pipeline.

---

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Verwendung von OLE‑Objekten und ActiveX‑Steuerelementen in Aspose.Words für Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Erstellen von Formularfeldern und Hinzufügen von Inhalten mit DocumentBuilder in Aspose.Words für Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word nach RTF konvertieren mit Aspose.Words für Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}