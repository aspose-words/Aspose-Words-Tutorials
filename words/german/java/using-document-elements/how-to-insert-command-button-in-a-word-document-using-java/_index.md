---
category: general
date: 2026-08-23
description: Erfahren Sie, wie Sie in einem Word‑Dokument mit Java und Aspose.Words
  einen Befehlsbutton einfügen. Dieser Leitfaden zeigt, wie man ein Formularsteuerelement
  hinzufügt, den Buttonnamen festlegt und einen ActiveX‑Button einbettet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: de
lastmod: 2026-08-23
og_description: Fügen Sie in einem Word-Dokument mit Java einen Befehlsbutton ein.
  Folgen Sie dieser Anleitung, um ein Formularsteuerelement hinzuzufügen, den Button-Namen
  festzulegen und einen ActiveX-Button mit Aspose.Words einzubetten.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Befehlsschaltfläche in Word mit Java einfügen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man mit Java eine Befehlsschaltfläche in ein Word‑Dokument einfügt
url: /de/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So fügen Sie eine CommandButton‑Schaltfläche in ein Word‑Dokument mit Java ein

Wenn Sie **command button** in eine Word‑Datei einfügen müssen, zeigt Ihnen dieses Tutorial eine komplette Lösung mit Aspose.Words für Java. Sie sehen, wie Sie ein Form Control hinzufügen, dessen Beschriftung konfigurieren und den Schaltflächennamen festlegen, ohne Ihre IDE zu verlassen.

Der Leitfaden deckt alles ab, was Sie benötigen, um ein `.docx` zu erstellen, das einen ActiveX‑Button enthält, der in Microsoft Word einsatzbereit ist. Es werden keine zusätzlichen Werkzeuge benötigt, und das Beispiel läuft auf Java 8+.

## Was Sie lernen werden

* Wie man ein Form Control vom Typ **CommandButton** zu einem Word‑Dokument hinzufügt.  
* Die genauen Schritte, um **button name** festzulegen und **add activex button**‑Eigenschaften zu setzen.  
* Wie man das Dokument speichert, damit die Schaltfläche beim Öffnen in Word korrekt angezeigt wird.  

Sie sollten eine grundlegende Java‑Entwicklungsumgebung sowie ein Maven‑ oder Gradle‑Projekt haben, das die Aspose.Words‑Bibliothek importieren kann.

## Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| Java 8 oder neuer | Aspose.Words für Java läuft auf Java 8+. |
| Maven‑ oder Gradle‑Build‑Tool | Vereinfacht das Hinzufügen der Aspose.Words‑Abhängigkeit. |
| Aspose.Words für Java Lizenz (oder kostenlose Testversion) | Erforderlich für den vollen Funktionsumfang; die API funktioniert im Evaluierungsmodus. |
| Eine IDE wie IntelliJ IDEA oder Eclipse | Erleichtert das Bearbeiten und Ausführen des Beispiels. |

## Schritt 1: Aspose.Words zu Ihrem Projekt hinzufügen

Wenn Sie Maven verwenden, fügen Sie die folgende Abhängigkeit zu `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Für Gradle fügen Sie diese Zeile in `build.gradle` ein:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Nachdem die Abhängigkeit aufgelöst wurde, können Sie die Bibliotheksklassen in Ihrer Java-Quelldatei importieren.

## Schritt 2: CommandButton einfügen – der Kerncode

Erstellen Sie eine neue Java‑Klasse namens `InsertCommandButtonDemo`. Der untenstehende Code führt alle vier Aktionen aus, die zum **insert command button** erforderlich sind:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Warum jede Zeile wichtig ist

* **Document & DocumentBuilder** – Sie stellen die In‑Memory‑Repräsentation einer Word‑Datei und die API zum Ändern ihres Inhalts bereit.  
* **insertForms2OleControl** – Diese Methode **adds form control** vom Typ `COMMAND_BUTTON`. Das zurückgegebene `Forms2OleControl`‑Objekt repräsentiert das ActiveX‑Steuerelement.  
* **setName** – Weist einen programmatischen Bezeichner zu (`btnSubmit`). Word‑Makros oder VBA können später auf diesen Namen verweisen.  
* **setCaption** – Definiert den Text, den der Benutzer auf der Schaltfläche sieht, und beantwortet die Frage „wie fügt man eine Schaltfläche hinzu“.  
* **save** – Schreibt das `.docx` auf die Festplatte und bewahrt den eingebetteten ActiveX‑Button.  

Das Ausführen des Programms erzeugt `CommandButtonDemo.docx` im Arbeitsverzeichnis. Öffnet man die Datei in Microsoft Word, wird eine Schaltfläche mit der Beschriftung **Submit** angezeigt, die man anklicken kann (sie zeigt im Evaluierungsmodus einen Standard‑ActiveX‑Dialog an).

## Schritt 3: Überprüfen Sie die eingefügte Schaltfläche in Word

1. Öffnen Sie `CommandButtonDemo.docx` mit Microsoft Word (2016 oder neuer).  
2. Die **Submit**‑Schaltfläche erscheint dort, wo der Cursor beim Einfügen positioniert war.  
3. Klicken Sie mit der rechten Maustaste auf die Schaltfläche und wählen Sie **Properties**, um zu sehen, dass das Feld **Name** `btnSubmit` enthält.  

Falls die Schaltfläche nicht angezeigt wird, stellen Sie sicher, dass **ActiveX controls** in den Trust‑Center‑Einstellungen von Word aktiviert sind.

## Schritt 4: Anpassen der Schaltfläche (optional)

Sie können die Schaltfläche weiter anpassen, indem Sie Größe, Position ändern oder ein VBA‑Makro hinzufügen. Die Klasse `Forms2OleControl` stellt zusätzliche Eigenschaften wie `setWidth`, `setHeight` und `setLeft` bereit. Nachfolgend ein Beispiel, das die Schaltfläche vergrößert:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Diese Zeilen können nach dem Aufruf von `setCaption` eingefügt werden. Sie demonstrieren **add activex button**‑Anpassungen über das grundlegende Einfügen hinaus.

## Häufige Fallstricke und wie man sie vermeidet

| Symptom | Ursache | Lösung |
|---------|---------|--------|
| Schaltfläche wird in Word nicht angezeigt | Dokument wurde gespeichert, bevor das Steuerelement hinzugefügt wurde | Stellen Sie sicher, dass `insertForms2OleControl` vor `doc.save` aufgerufen wird. |
| Schaltflächenbeschriftung ist leer | `setCaption` wurde nicht aufgerufen oder mit einem leeren String aufgerufen | Geben Sie einen nicht‑leeren String an, z. B. `"Submit"`. |
| VBA kann die Schaltfläche nicht finden | Namensabweichung zwischen VBA‑Code und `setName`‑Wert | Behalten Sie den Namen konsistent; verwenden Sie `setName("btnSubmit")` und referenzieren Sie `btnSubmit` in VBA. |
| Sicherheitswarnung beim Öffnen der Datei | Word‑Makrosicherheit blockiert ActiveX‑Steuerelemente | Passen Sie Trust Center > Macro Settings an oder signieren Sie das Dokument mit einem vertrauenswürdigen Zertifikat. |

## Vollständiges, ausführbares Beispiel

Nachfolgend die komplette Quelldatei, bereit zum Kopieren und Einfügen in Ihre IDE. Sie enthält die Import‑Anweisungen, Ausnahmebehandlung und einen Kommentarblock, der jeden wichtigen Schritt erklärt.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Erwartetes Ergebnis:** Nach dem Ausführen des Programms enthält `CommandButtonDemo.docx` eine einzelne **Submit**‑Schaltfläche. Öffnet man die Datei in Word, wird die Schaltfläche genau an der Stelle angezeigt, an der sich der `DocumentBuilder`‑Cursor befand.

## Nächste Schritte

* **Weitere Form Controls hinzufügen** – Verwenden Sie `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` oder `TEXT_BOX`, um vollständige Word‑Formulare zu erstellen.  
* **Mit Seriendruck kombinieren** – Schaltflächen in ein seriendruckgeneriertes Dokument einfügen, um personalisierte interaktive Formulare zu erstellen.  
* **VBA‑Makros anhängen** – Programmatisch VBA einbetten, das auf das `Click`‑Ereignis der Schaltfläche reagiert, für erweiterte Automatisierung.  

Diese Themen erweitern die **add form control**‑Technik, die Sie gerade gemeistert haben, auf natürliche Weise.

---

### Zusammenfassung

Sie wissen jetzt, wie man **insert command button** in ein Word‑Dokument mit Java einfügt, wie man **add form control** verwendet, wie man **set button name** festlegt und wie man **add activex button**‑Anpassungen vornimmt. Das komplette Beispiel läuft sofort, und Sie können es an jeden Dokument‑Generierungs‑Workflow anpassen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Combo‑Box‑Formfeld in Word‑Dokument einfügen](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Check‑Box‑Formfeld in Word‑Dokument einfügen](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}