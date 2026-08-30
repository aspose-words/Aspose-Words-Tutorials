---
category: general
date: 2026-07-16
description: πώς να εισαγάγετε ομαδικό σχήμα σε Java χρησιμοποιώντας το Aspose.Words
  – προσθέστε σχήμα ορθογωνίου, ορίστε τις διαστάσεις του σχήματος και δημιουργήστε
  χρωματιστό ορθογώνιο και κύκλο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: el
lastmod: 2026-07-16
og_description: 'πώς να εισάγετε ομαδικό σχήμα στη Java: ένας πρακτικός οδηγός για
  την προσθήκη σχήματος ορθογωνίου, τον ορισμό διαστάσεων σχήματος και τη δημιουργία
  χρωματιστού ορθογωνίου και κύκλου με το Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Εισαγωγή Ομαδικού Σχήματος σε Java – Πλήρης Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: πώς να εισάγετε ομαδικό σχήμα στη Java – Πλήρης Οδηγός
url: /el/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να εισάγετε σχήμα ομάδας σε Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να εισάγετε σχήμα ομάδας** σε ένα έγγραφο Word χρησιμοποιώντας Java; Δεν είστε ο μόνος. Είτε δημιουργείτε έναν γεννήτρια αναφορών είτε έναν δυναμικό δημιουργό φυλλαδίων, η ομαδοποίηση σχημάτων διατηρεί τη διάταξη σας τακτική και τον κώδικά σας διαχειρίσιμο.

Σε αυτό το σεμινάριο θα περάσουμε βήμα-βήμα τις ακριβείς ενέργειες για **προσθήκη σχήματος ορθογωνίου**, **ορισμό διαστάσεων σχήματος**, και **δημιουργία χρωματιστού ορθογωνίου** και **δημιουργία χρωματιστού κύκλου** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words. Στο τέλος θα έχετε ένα εκτελέσιμο πρόγραμμα που παράγει ένα αρχείο .docx με ένα μπλε ορθογώνιο και έναν κόκκινο κύκλο, τυλιγμένα κομψά μέσα σε μια ομάδα.

## Προαπαιτούμενα

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ρυθμισμένο.
- Maven ή Gradle για διαχείριση εξαρτήσεων.
- Aspose.Words for Java 23.9 ή νεότερο – μπορείτε να το κατεβάσετε από το Maven Central.
- Βασική κατανόηση της σύνταξης Java – δεν απαιτείται τίποτα περίπλοκο.

Αν λείπει κάποιο από αυτά, κατεβάστε το JDK από τον ιστότοπο της Oracle και προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Τώρα που η βάση είναι έτοιμη, ας βάλουμε τα χέρια μας στη δουλειά.

## πώς να εισάγετε σχήμα ομάδας – Επισκόπηση

Η βασική ιδέα είναι απλή: δημιουργήστε ένα `Document`, ανοίξτε ένα `DocumentBuilder`, εισάγετε ένα **σχήμα ομάδας**, και στη συνέχεια προσθέστε μεμονωμένα σχήματα (ένα ορθογώνιο και έναν κύκλο) σε αυτήν την ομάδα. Η ομάδα λειτουργεί ως κοντέινερ, έτσι η μετακίνηση της αργότερα θα μετακινήσει όλα τα αντικείμενα μέσα – ιδανικό για σύνθετες διατάξεις.

Παρακάτω είναι ο πλήρης, έτοιμος‑για‑εκτέλεση κώδικας. Μπορείτε να τον αντιγράψετε‑και‑επικολλήσετε σε μια νέα κλάση Java με όνομα `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Συμβουλή:** Οι τιμές `setLeft` και `setTop` είναι σχετικές με το σημείο προέλευσης της ομάδας, όχι με τη σελίδα. Αυτό καθιστά την επανατοποθέτηση ολόκληρης της ομάδας εύκολη αργότερα.

### Τι μόλις συνέβη;

1. **Document & Builder** – Δημιουργούμε ένα κενό αρχείο Word και ένα `DocumentBuilder` που μας επιτρέπει να εισάγουμε περιεχόμενο.
2. **Group Shape** – `builder.insertGroupShape()` δημιουργεί ένα κοντέινερ. Σκεφτείτε το ως φάκελο για αντικείμενα σχεδίασης.
3. **Blue Rectangle** – Δημιουργούμε ένα `Shape` τύπου `RECTANGLE`, ορίζουμε το μέγεθός του, τη θέση του, και το γεμίζουμε με μπλε – αυτό είναι το βήμα **create colored rectangle**.
4. **Red Circle** – Το ίδιο μοτίβο, αλλά χρησιμοποιώντας `ELLIPSE` για έναν τέλειο κύκλο, και το γεμίζουμε με κόκκινο – αυτό είναι το τμήμα **create colored circle**.
5. **Saving** – Τέλος αποθηκεύουμε τα πάντα στο `GroupShapeDemo.docx`.

Εκτελέστε το πρόγραμμα (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) και ανοίξτε το παραγόμενο αρχείο. Θα πρέπει να δείτε ένα μπλε ορθογώνιο στα αριστερά και έναν κόκκινο κύκλο στα δεξιά, και τα δύο κλειδωμένα μέσα σε ένα ενιαίο πλαίσιο ομάδας.

## Προσθήκη σχήματος ορθογωνίου

Αν χρειάζεστε μόνο ένα ορθογώνιο χωρίς ομαδοποίηση, μπορείτε να παραλείψετε την κλήση `insertGroupShape()` και να προσθέσετε το ορθογώνιο απευθείας στο σώμα του εγγράφου. Ωστόσο, η ομαδοποίηση σας δίνει την ευελιξία να μετακινήσετε, περιστρέψετε ή διαγράψετε πολλά σχήματα ταυτόχρονα.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Παρατηρήστε πώς χρησιμοποιήσαμε τη λογική **add rectangle shape** εδώ. Το ορθογώνιο εμφανίζεται στη σελίδα ως ανεξάρτητο αντικείμενο. Στις περισσότερες πραγματικές περιπτώσεις θα θέλετε την ομάδα, επειδή διατηρεί τη σχετική θέση.

## Ορισμός διαστάσεων σχήματος

Όταν βλέπετε μεθόδους όπως `setWidth` και `setHeight`, θυμηθείτε ότι δέχονται **points** (1/72 inch). Αν προτιμάτε χιλιοστά, μετατρέψτε πρώτα:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Αυτό το απόσπασμα δείχνει **set shape dimensions** με μετατροπή μονάδων – χρήσιμο όταν οι προδιαγραφές σχεδίου προέρχονται από ένα UI mockup που χρησιμοποιεί μετρικές μονάδες.

## Δημιουργία χρωματιστού ορθογωνίου

Το χρώμα ενός σχήματος είναι τόσο απλό όσο η κλήση `getFill().setForeColor()`. Μπορείτε να περάσετε οποιοδήποτε `java.awt.Color`. Θέλετε διαβάθμιση; Χρησιμοποιήστε `setForeColor` για το αρχικό χρώμα και `setBackColor` για το τελικό.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Αυτή είναι ένας γρήγορος τρόπος για **create colored rectangle** με διαβαθμισμένο γέμισμα αντί για ενιαίο χρώμα.

## Δημιουργία χρωματιστού κύκλου

Οι κύκλοι είναι απλώς έλλειψη με ίσο πλάτος και ύψος. Η ίδια λογική χρώματος ισχύει:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Αν χρειάζεστε διαφανές γέμισμα, ορίστε το κανάλι άλφα:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Τώρα έχετε κατακτήσει την τεχνική **create colored circle**.

## Αποθήκευση του εγγράφου

Το Aspose.Words σας επιτρέπει να εξάγετε σε πολλές μορφές: DOCX, PDF, HTML, PNG, ό,τι θέλετε. Για αυτήν τη demo παραμένουμε στο DOCX επειδή διατηρεί τα διανυσματικά σχήματα τέλεια.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Απλώς αλλάζοντας το `SaveFormat` μπορείτε να δημιουργήσετε μια έκδοση PDF του ίδιου ομαδοποιημένου έργου.

## Συνηθισμένα λάθη & πώς να τα αποφύγετε

- **Ξεχάσατε να προσθέσετε το σχήμα στην ομάδα;** Το σχήμα θα εμφανιστεί στη σελίδα αλλά δεν θα μετακινηθεί με την ομάδα. Πάντα καλέστε `group.appendChild(yourShape)`.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω σεμινάρια καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}