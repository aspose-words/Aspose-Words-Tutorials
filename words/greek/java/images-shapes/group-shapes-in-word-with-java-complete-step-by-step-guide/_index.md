---
category: general
date: 2026-08-01
description: Ομαδοποιήστε σχήματα στο Word με Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να ομαδοποιείτε σχήματα και να εισάγετε γρήγορα σχήμα ορθογωνίου με ένα
  πλήρες παράδειγμα κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: el
lastmod: 2026-08-01
og_description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας Java. Αυτός ο οδηγός
  δείχνει πώς να ομαδοποιήσετε σχήματα, να εισάγετε σχήμα ορθογωνίου και να αποθηκεύσετε
  ένα DOCX με το Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Ομαδοποίηση Σχημάτων στο Word με Java – Πλήρης Οδηγός Προγραμματισμού
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Ομαδοποίηση Σχημάτων στο Word με Java – Πλήρης Οδηγός Βήμα-Βήμα
url: /el/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ομαδοποίηση Σχημάτων στο Word με Java – Πλήρης Οδηγός Βήμα-Βήμα

Αν χρειάζεστε **ομαδοποίηση σχημάτων στο Word** χρησιμοποιώντας Java, αυτός ο οδηγός σας καλύπτει. Είτε δημιουργείτε έναν γεννήτρια αναφορών είτε μια δυναμική μηχανή προτύπων, η ομαδοποίηση σχημάτων κάνει τα έγγραφά σας πιο επαγγελματικά και κρατά τα σχετικά γραφικά μαζί.

Στα επόμενα λεπτά θα δείτε ακριβώς **πώς να ομαδοποιήσετε σχήματα** και **να εισάγετε αντικείμενα σχήματος ορθογωνίου** με το Aspose.Words, συν ένα σύνολο πρακτικών συμβουλών που σας σώζουν από κοινές παγίδες. Έτοιμοι να μετατρέψετε αυτά τα ελεύθερα ορθογώνια και έλλειψη σε μια τακτοποιημένη ομάδα; Ας ξεκινήσουμε.

## Τι Καλύπτει Αυτός ο Οδηγός

* Οι ελάχιστες προαπαιτήσεις (Java 17+, Aspose.Words 24.10 ή νεότερη).  
* Ένα πλήρες, εκτελέσιμο πρόγραμμα Java που δημιουργεί ένα έγγραφο Word, εισάγει ένα ορθογώνιο και μια έλλειψη, τα ομαδοποιεί, κρύβει την ομάδα αν το επιθυμείτε, και αποθηκεύει το αρχείο.  
* Γιατί κάθε κλήση API έχει σημασία, όχι μόνο τι κάνει.  
* Διαχείριση edge‑case για παλαιότερες εκδόσεις Aspose.Words και για ομαδοποίηση περισσότερων από δύο σχημάτων.  
* Αναμενόμενο αποτέλεσμα και γρήγορος τρόπος επαλήθευσης του αποτελέσματος.

Στο τέλος θα μπορείτε να ενσωματώσετε αυτό το απόσπασμα σε οποιοδήποτε έργο Java και να αρχίσετε να ομαδοποιείτε σχήματα στο Word χωρίς να ψάχνετε σε διάσπαρτη τεκμηρίωση.

---

## Προαπαιτήσεις

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| **Java 17+** | Σύγχρονα χαρακτηριστικά της γλώσσας και καλύτερη απόδοση. |
| **Aspose.Words for Java 24.10+** | Η μέθοδος `setHidden` που χρησιμοποιείται αργότερα υπάρχει μόνο από αυτήν την έκδοση και μετά. |
| **A Maven or Gradle build** | Καθιστά τη διαχείριση εξαρτήσεων απλή. |
| **An IDE (IntelliJ, Eclipse, VS Code)** | Χρήσιμη για γρήγορη δοκιμή, αλλά οποιοσδήποτε επεξεργαστής κειμένου λειτουργεί. |

Προσθέστε την εξάρτηση Aspose.Words Maven στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

## Βήμα 1: Δημιουργία Νέου Εγγράφου και Builder

Αρχικά δημιουργούμε ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder είναι ο κύριος μηχανισμός που μας επιτρέπει να εισάγουμε σχήματα, κείμενο και άλλα.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Γιατί αυτό το βήμα;*  
`Document` αντιπροσωπεύει ολόκληρο το αρχείο DOCX, ενώ `DocumentBuilder` παρέχει ένα βολικό API βασισμένο σε κέρσορα. Χωρίς έναν builder θα έπρεπε να χειρίζεστε χειροκίνητα συλλογές κόμβων χαμηλού επιπέδου — κάτι που είναι εύκολο να γίνει λάθος.

## Βήμα 2: Εισαγωγή Σχήματος Ορθογωνίου (και Έλλειψης)

Τώρα προσθέτουμε τα δύο βασικά σχήματα που θέλουμε να ομαδοποιήσουμε. Παρατηρήστε την κλήση **insert rectangle shape** — αυτό είναι ακριβώς η δευτερεύουσα λέξη-κλειδί που ψάχνετε.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Μερικά πράγματα που πρέπει να θυμάστε:

* Το πλάτος (`100`) και το ύψος (`50`) μετρώνται σε σημεία (1 pt ≈ 1/72 in). Προσαρμόστε τα ώστε να ταιριάζουν στη διάταξή σας.  
* Το ορθογώνιο σχεδιάζεται πρώτο, έτσι βρίσκεται πίσω από την έλλειψη εξ ορισμού. Αν χρειάζεστε αντίστροφη σειρά, εισάγετε πρώτα την έλλειψη.  
* Και τα δύο σχήματα κληρονομούν την τρέχουσα μορφοποίηση του builder (χρώμα, στυλ γραμμής). Μπορείτε να τα προσαρμόσετε πριν την ομαδοποίηση αν το επιθυμείτε.

## Βήμα 3: Πώς να Ομαδοποιήσετε Σχήματα με το Aspose.Words

Αυτή είναι η καρδιά του οδηγού — **πώς να ομαδοποιήσετε σχήματα**. Το API `insertGroupShape` λαμβάνει έναν πίνακα από υπάρχοντα σχήματα και επιστρέφει ένα νέο `Shape` που αντιπροσωπεύει την ομάδα.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Γιατί να χρησιμοποιήσετε μια ομάδα;  

* Μια ομάδα κινείται ως μία ενότητα, διατηρώντας τη σχετική θέση.  
* Μπορείτε να εφαρμόσετε μετασχηματισμούς (περιστροφή, κλιμάκωση) σε όλο το σύνολο με μία κλήση.  
* Η ομαδοποίηση απλοποιεί την επεξεργασία αργότερα — αποομαδοποιήστε αν χρειαστεί να τροποποιήσετε μεμονωμένα στοιχεία.

## Βήμα 4 (Προαιρετικό): Απόκρυψη της Ομάδας από την Προβολή του Εγγράφου

Αν δεν θέλετε η ομάδα να εμφανίζεται όταν ο χρήστης ανοίγει το έγγραφο στο Word, μπορείτε να την κρύψετε. Αυτό το βήμα είναι προαιρετικό αλλά χρήσιμο για γραφικά φόντου ή υδατογραφήματα.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Τι γίνεται αν χρησιμοποιείτε παλαιότερη έκδοση του Aspose.Words;**  
Η μέθοδος `setHidden` δεν θα μεταγλωττιστεί. Σε αυτήν την περίπτωση μπορείτε να πετύχετε παρόμοιο αποτέλεσμα ορίζοντας το `WrapType` του σχήματος σε `NONE` και μετακινώντας το πίσω από το επίπεδο κειμένου:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Είναι λίγο πιο εκτενές, αλλά εξακολουθεί να κρατά την ομάδα μακριά από τον αναγνώστη.

## Βήμα 5: Αποθήκευση του Εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Αλλάξτε τη διαδρομή σε όποιον φάκελο θέλετε να αποθηκευτεί το αρχείο.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Όταν ανοίξετε το `GroupShapeResult.docx` στο Microsoft Word, θα δείτε ένα ορθογώνιο και μια έλλειψη να είναι τακτοποιημένα μαζί. Αν ορίσετε `setHidden(true)`, η ομάδα θα είναι αόρατη στον επεξεργαστή αλλά θα παραμένει στο αρχείο (χρήσιμο για προγραμματική επεξεργασία αργότερα).

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα, εδώ είναι η πλήρης, αυτόνομη κλάση Java που μπορείτε να αντιγράψετε‑επικολλήσετε στο έργο σας:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ένα αρχείο με όνομα `GroupShapeResult.docx` που περιέχει μία ενιαία ομάδα που κρατά ένα μπλε-γεμισμένο ορθογώνιο και μια κόκκινη-περιγραμμένη έλλειψη (προεπιλεγμένα χρώματα). Αν ανοίξετε το έγγραφο, επιλέξετε την ομάδα και κάνετε δεξί‑κλικ → **Group → Ungroup**, θα δείτε τα δύο αρχικά σχήματα να εμφανίζονται ξανά.

## Συχνές Ερωτήσεις & Edge Cases

### 1. Μπορώ να ομαδοποιήσω περισσότερα από δύο σχήματα;

Απολύτως. Απλώς περάστε έναν μεγαλύτερο πίνακα στο `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

Το API κλιμακώνεται γραμμικά· ο μόνος περιορισμός είναι η μνήμη για εξαιρετικά μεγάλες ομάδες.

### 2. Τι γίνεται αν χρειαστεί να αλλάξω τη θέση της ομάδας μετά τη δημιουργία;

Χρησιμοποιήστε τις μεθόδους `setLeft` και `setTop` της ομάδας, όπως οποιοδήποτε άλλο σχήμα:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Επειδή η ομάδα συμπεριφέρεται σαν ένα ενιαίο σχήμα, όλα τα παιδικά σχήματα κινούνται μαζί.

### 3. Πώς μπορώ να εφαρμόσω περιθώριο ή γέμισμα σε ολόκληρη την ομάδα;

Η ίδια η ομάδα μπορεί να έχει μορφοποίηση, αλλά δεν επηρεάζει άμεσα τα παιδιά. Αν θέλετε ένα κοινό περιθώριο, τυλίξτε πρώτα τα σχήματα σε ένα σχήμα ορθογωνίου, μετά ομαδοποιήστε τα όλα. Εναλλακτικά, επαναλάβετε για κάθε παιδικό σχήμα και ορίστε το ίδιο `fillColor` ή `strokeWeight`.

### 4. Επηρεάζει η `setHidden(true)` την εκτύπωση;

Τα κρυμμένα σχήματα **δεν** εκτυπώνονται εξ ορισμού στο Word, κάτι που μπορεί να είναι χρήσιμο για υδατογραφήματα ή δείκτες προτύπων. Αν χρειάζεστε το σχήμα να εκτυπώνεται αλλά να παραμένει αόρατο στην οθόνη, θα πρέπει να χρησιμοποιήσετε διαφορετική προσέγγιση (π.χ., ορίστε τη διαφάνειά του στο 0%).

## Pro Συμβουλές από την Πρακτική

* **Ονομάστε τα σχήματά σας** – `groupShape.setName("HeaderGraphics");` κάνει την αποσφαλμάτωση πιο εύκολη όταν αργότερα ανακτάτε σχήματα με όνομα.  
* **Ξαναχρησιμοποιήστε τον builder** – Μετά την εισαγωγή μιας ομάδας, ο κέρσορας του builder παραμένει εκεί που τοποθετήθηκε η ομάδα, ώστε να μπορείτε να συνεχίσετε να προσθέτετε παραγράφους αμέσως μετά την ομάδα χωρίς να επαναρυθμίσετε τη θέση.  
* **Έλεγχος έκδοσης** – Αν διανέμετε μια βιβλιοθήκη που μπορεί να τρέξει σε παλαιότερες εκδόσεις Aspose.Words, τυλίξτε την κλήση `setHidden` σε try‑catch για `NoSuchMethodError` και επιστρέψτε στην τεχνική `WrapType.NONE` που δείξαμε νωρίτερα.  
* **Συμβουλή απόδοσης** – Όταν δημιουργείτε χιλιάδες 

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Χρήση Σχημάτων Εγγράφου στο Aspose.Words για Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Απόδοση Σχημάτων στο Aspose.Words για Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}