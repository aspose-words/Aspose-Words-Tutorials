---
category: general
date: 2026-09-24
description: Button-Position in einem Word‑Dokument mit Java und Aspose.Words festlegen.
  Erfahren Sie, wie Sie einen Button einfügen, ein ActiveX‑Steuerelement hinzufügen
  und ein Word‑Dokument im Java‑Stil erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: de
lastmod: 2026-09-24
og_description: Button-Position in einem Word-Dokument mit Java festlegen. Diese Anleitung
  zeigt, wie man einen Button einfügt, ein ActiveX-Steuerelement hinzufügt und ein
  Word-Dokument mit Java und Aspose.Words erstellt.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Button-Position in einem Word-Dokument mit Java festlegen – vollständige
  Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Wie man die Position eines Buttons in einem Word‑Dokument mit Java festlegt
url: /de/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man die Schaltflächenposition in einem Word-Dokument mit Java festlegt

Wenn Sie die **Schaltflächenposition** in einer Word-Datei festlegen müssen, zeigt Ihnen dieser Leitfaden eine vollständige, ausführbare Lösung. Egal, ob Sie eine Vorlage erstellen, die Benutzerinteraktion erfordert, oder ein Formular automatisieren, Sie lernen genau **wie man eine Schaltfläche einfügt** mit Aspose.Words für Java und deren Platzierung zu steuern.

Das Tutorial behandelt alles, was Sie benötigen, um **ActiveX‑Steuerelement** zu einem Word‑Dokument hinzuzufügen, erklärt, **wie man eine Schaltfläche zu Word hinzufügt**, und demonstriert den gesamten Prozess, um **Word‑Dokument Java**‑Stil zu erstellen. Keine externen Referenzen sind nötig – einfach kopieren, ausführen und das Ergebnis überprüfen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

* Java 17 (oder jede Java 8+ Laufzeit) installiert.
* Maven oder Gradle zur Verwaltung der Abhängigkeiten.
* Eine Aspose.Words für Java Lizenz (die kostenlose Testversion funktioniert für Evaluierungen).
* Grundlegendes Verständnis der Java‑Syntax.

> **Profi‑Tipp:** Bewahren Sie Ihre Aspose.Words‑JARs in einem `libs/`‑Ordner auf und fügen Sie sie dem Klassenpfad Ihres Projekts hinzu, um Versionskonflikte zu vermeiden.

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein einfaches Maven‑Projekt (oder verwenden Sie Gradle) und fügen Sie die Aspose.Words‑Abhängigkeit hinzu:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Das Ausführen von `mvn clean compile` lädt die Bibliothek herunter und richtet den Build‑Pfad ein.

## Schritt 2: Neues Word‑Dokument erstellen

Der erste Vorgang ist, **Word‑Dokument Java**‑Stil zu **erstellen**. Sie instanziieren ein `Document`‑Objekt und einen `DocumentBuilder`, der Ihnen das Bearbeiten der Datei ermöglicht.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Die Klasse `Document` repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` eine fluente API zum Einfügen von Inhalten bereitstellt.

## Schritt 3: Schaltfläche einfügen – ActiveX‑Steuerelement hinzufügen

Aspose.Words stellt die Klasse `Forms2OleControl` bereit, um legacy ActiveX‑Steuerelemente wie einen CommandButton einzufügen. Dieser Schritt zeigt den genauen Weg, **wie man eine Schaltfläche einfügt** in das Dokument.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Die Methode `insertForms2OleControl` gibt eine `Forms2OleControl`‑Instanz zurück, die Sie konfigurieren können. Dies ist der Kern des **ActiveX‑Steuerelement‑Hinzufügens**.

## Schritt 4: Schaltflächenposition festlegen

Jetzt setzen wir tatsächlich **die Schaltflächenposition**. Die Methoden `setLeft` und `setTop` des Steuerelements akzeptieren Werte in Punkten (1 pt = 1/72 in). Um die Schaltfläche an typische Bildschirmkoordinaten anzupassen, können Sie Pixel in Punkte umrechnen (1 px ≈ 0,75 pt). Im Beispiel platzieren wir die Schaltfläche 100 px vom linken Rand und 150 px vom oberen Rand.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Da die Logik zum **Setzen der Schaltflächenposition** hier gekapselt ist, können Sie diese Zeilen wiederverwenden, wann immer Sie ein Steuerelement verschieben müssen. Passen Sie die Zahlen an Ihre Layout‑Anforderungen an.

## Schritt 5: Größe und Beschriftung festlegen

Eine Schaltfläche ohne Beschriftung ist verwirrend. Verwenden Sie `setWidth`, `setHeight` und `setCaption`, um ihr ein sichtbares Erscheinungsbild zu geben.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Die Größe wird ebenfalls in Punkten angegeben, sodass wir zur Konsistenz von Pixeln umrechnen.

## Schritt 6: Dokument speichern – den create Word document java‑Ablauf abschließen

Zum Schluss speichern Sie die Datei auf dem Datenträger. Der Pfad kann absolut oder relativ zum Projekt‑Root sein.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Das Ausführen des Programms erzeugt `CommandButtonDemo.docx` im Ordner `output`. Öffnet man die Datei in Microsoft Word, wird eine anklickbare Schaltfläche angezeigt, die exakt dort positioniert ist, wo Sie sie festgelegt haben.

### Erwartete Ausgabe

* Eine `.docx`‑Datei mit dem Namen **CommandButtonDemo.docx**.
* Im Dokument erscheint ein **CommandButton** mit der Beschriftung „Click Me“, der 100 px vom linken Rand und 150 px vom oberen Rand entfernt ist.
* Die Schaltfläche reagiert auf Klicks, wenn das Dokument in Word geöffnet wird (sie zeigt eine Standard‑ActiveX‑Meldung an, sofern Sie keinen benutzerdefinierten VBA‑Code anhängen).

## Schritt 7: Häufige Variationen und Randfälle

### Mehrere Schaltflächen hinzufügen

Wenn Sie **eine Schaltfläche zu Word** mehrmals hinzufügen müssen, wiederholen Sie die Schritte 3‑5 mit einer neuen `Forms2OleControl`‑Instanz jedes Mal. Denken Sie daran, den Wert von `setTop` anzupassen, damit sich die Schaltflächen nicht überlappen.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Ohne Lizenz arbeiten

Aspose.Words fügt ein Wasserzeichen hinzu, wenn es ohne Lizenz verwendet wird. Für Produktionscode kaufen Sie eine Lizenz und wenden sie zu Beginn von `main` an:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatibilität mit älteren Office‑Versionen

ActiveX‑Steuerelemente werden im `.doc`‑Format (Word 97‑2003) unterstützt. Um eine Legacy‑Datei zu erstellen, ändern Sie das Speicherformat:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Vollständiger Quellcode (ausführbar)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Speichern Sie die Datei als `src/main/java/CommandButtonDemo.java`, führen Sie `mvn exec:java -Dexec.mainClass=CommandButtonDemo` aus und öffnen Sie das erzeugte Dokument, um das Ergebnis zu sehen.

## Häufig gestellte Fragen

**Q: Funktioniert das mit OpenJDK?**  
A: Ja. Aspose.Words ist reines Java und läuft auf jeder JDK 8+‑Implementierung, einschließlich OpenJDK.

**Q: Kann ich die Schriftart oder Farbe der Schaltfläche ändern?**  
A: Das Aussehen einer ActiveX‑Schaltfläche wird von der Host‑Anwendung (Word) gesteuert. Sie können VBA‑Code anhängen, um Eigenschaften zur Laufzeit zu ändern, aber das statische Erscheinungsbild ist auf den Standardstil beschränkt.

**Q: Was, wenn ich die Schaltfläche in einer Tabellenzelle platzieren muss?**  
A: Bewegen Sie den `DocumentBuilder`‑Cursor in die Zelle, bevor Sie `insertForms2OleControl` aufrufen. Das Steuerelement übernimmt das Layout der Zelle, und Sie können weiterhin `setLeft`/`setTop` für Feineinstellungen verwenden.

## Fazit

Sie wissen jetzt, wie man **die Schaltflächenposition** in einem Word‑Dokument mit Java festlegt, **wie man eine Schaltfläche einfügt**, **ActiveX‑Steuerelemente hinzufügt** und **eine Schaltfläche zu Word** hinzufügt, während Sie bewährte Methoden für **create Word document java**‑Projekte befolgen. Das vollständige Beispiel demonstriert den gesamten Workflow – vom Projekt‑Setup bis zur gespeicherten `.docx`‑Datei mit einem funktionalen CommandButton.

### Nächste Schritte

* Erkunden Sie weitere Werte von `Forms2OleControl.ControlType` (z. B. `CHECKBOX`, `TEXTBOX`), um reichhaltigere Formulare zu erstellen.
* Kombinieren Sie die Schaltfläche mit VBA‑Makros für benutzerdefinierte Klick‑Verarbeitung.
* Nutzen Sie die Mail‑Merge‑Funktion von Aspose.Words, um personalisierte Dokumente zu erzeugen, die bereits interaktive Steuerelemente enthalten.

Viel Spaß beim Coden und beim Automatisieren von Word‑Dokumenten mit Java!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Ein Kombinationsfeld‑Formularfeld zu einem Word‑Dokument mit Aspose.Words für .NET hinzufügen](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Wie man Word‑Dokumente mit Aspose.Words Java lädt: Umfassender Leitfaden](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}