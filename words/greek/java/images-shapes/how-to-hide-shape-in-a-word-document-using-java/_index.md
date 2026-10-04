---
category: general
date: 2026-10-04
description: Μάθετε πώς να κρύψετε σχήμα στο Word με Java. Αυτός ο οδηγός βήμα‑βήμα
  σας δείχνει πώς να κρύψετε σχήμα στο Word, να κάνετε το σχήμα αόρατο στο Word και
  να κρύψετε σχήμα στο Microsoft Word προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: el
lastmod: 2026-10-04
og_description: Πώς να κρύψετε σχήμα στο Word με Java. Ακολουθήστε αυτόν τον οδηγό
  για να κρύψετε σχήμα στο Word, να κάνετε το σχήμα αόρατο στο Word και να κρύψετε
  σχήμα στο Microsoft Word με λίγες γραμμές κώδικα.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Πώς να κρύψετε σχήμα σε έγγραφο Word χρησιμοποιώντας Java – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Πώς να κρύψετε σχήμα σε ένα έγγραφο Word χρησιμοποιώντας Java
url: /el/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να κρύψετε σχήμα σε έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε να κρύψετε ένα σχήμα σε αρχείο Word, αυτός ο οδηγός σας δείχνει ακριβώς **πώς να κρύψετε σχήμα** προγραμματιστικά. Είτε δημιουργείτε αναφορές, καθαρίζετε πρότυπα, είτε προετοιμάζετε έγγραφα για συμμόρφωση, μπορείτε να κάνετε ένα σχήμα αόρατο χωρίς να το αφαιρέσετε από τη δομή του αρχείου.

Στις παρακάτω ενότητες θα μάθετε πώς να κρύψετε σχήμα στο Word, πώς να κάνετε σχήμα αόρατο στο Word, και πώς να κρύψετε σχήμα στο Microsoft Word χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Java. Το tutorial υποθέτει ότι έχετε βασικές γνώσεις Java και ένα λειτουργικό περιβάλλον ανάπτυξης Java.

## Προαπαιτούμενα

* Java Development Kit (JDK) 8 ή νεότερο  
* Maven ή Gradle για διαχείριση εξαρτήσεων  
* Aspose.Words for Java (έκδοση 23.9 ή νεότερη) – προσθέστε το Maven coordinate `com.aspose:aspose-words:23.9`  
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα σχήμα (π.χ., μια εικόνα, πλαίσιο κειμένου ή SmartArt)

## Βήμα 1: Ρυθμίστε το έργο και εισάγετε το Aspose.Words

Δημιουργήστε ένα νέο έργο Maven ή προσθέστε την εξάρτηση Aspose.Words σε ένα υπάρχον.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

Η βιβλιοθήκη παρέχει τις κλάσεις `Document`, `NodeType` και `Shape` που χρησιμοποιούνται στα επόμενα βήματα. Εισάγετε τις στην αρχή του αρχείου πηγαίου κώδικα Java:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Βήμα 2: Φορτώστε το έγγραφο Word

Η φόρτωση του εγγράφου είναι το πρώτο βήμα σε οποιαδήποτε ροή εργασίας επεξεργασίας Word. Ο κατασκευαστής `Document` διαβάζει το αρχείο στη μνήμη, διατηρώντας όλους τους κόμβους, συμπεριλαμβανομένων των κρυφών σχημάτων.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό*: Η φόρτωση του αρχείου δημιουργεί ένα DOM (Document Object Model) που σας επιτρέπει να περιηγηθείτε, να κάνετε ερωτήματα και να τροποποιήσετε μεμονωμένους κόμβους όπως σχήματα, παραγράφους ή πίνακες.

## Βήμα 3: Ανακτήστε το επιθυμητό σχήμα

Αν το έγγραφο περιέχει πολλαπλά σχήματα, μπορείτε να εντοπίσετε ένα συγκεκριμένο με βάση το δείκτη, το όνομα ή άλλα κριτήρια. Για μια γρήγορη επίδειξη, το παράδειγμα ανακτά το πρώτο σχήμα στην ιεραρχία του εγγράφου, συμπεριλαμβανομένων των σχημάτων που είναι ενσωματωμένα μέσα σε πίνακες ή ομάδες.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Γιατί είναι σημαντικό*: Η μέθοδος `getChild` με `true` για τη σημαία `isDeep` διασχίζει ολόκληρο το δέντρο κόμβων, εξασφαλίζοντας ότι θα πιάσετε σχήματα που δεν είναι άμεσα παιδιά του σώματος του εγγράφου.

## Βήμα 4: Κρύψτε το σχήμα

Ορίζοντας την ιδιότητα `Hidden` σε `true` λέει στο Microsoft Word να εξαιρέσει το σχήμα από την απόδοση της διάταξης ενώ το διατηρεί στη δομή του εγγράφου. Το σχήμα δεν θα είναι ορατό όταν το αρχείο ανοίξει στο Word, αλλά παραμένει προσβάσιμο για μεταγενέστερη επεξεργασία.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Γιατί είναι σημαντικό*: Η απόκρυψη ενός σχήματος είναι χρήσιμη όταν χρειάζεται να διατηρήσετε το σχήμα για μεταγενέστερη ενεργοποίηση (π.χ., υπό όρους περιεχόμενο, έκδοση) χωρίς να το εμφανίσετε στον τελικό χρήστη.

## Βήμα 5: Αποθηκεύστε το τροποποιημένο έγγραφο

Αφού αλλάξετε την ορατότητα του σχήματος, γράψτε το έγγραφο ξανά στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε ένα νέο· το παράδειγμα γράφει στο `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Όταν ανοίξετε το `HiddenShape.docx` στο Microsoft Word, το σχήμα θα είναι αόρατο, ωστόσο η διάταξη του εγγράφου θα αντανακλά την κρυφή του κατάσταση (χωρίς επιπλέον κενό χώρο).

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα βήματα δημιουργείται ένα αυτόνομο πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε άμεσα.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**  
Η εκτέλεση του προγράμματος παράγει το `HiddenShape.docx`. Ανοίγοντας αυτό το αρχείο στο Microsoft Word εμφανίζεται το αρχικό περιεχόμενο, αλλά το σχήμα που υπήρχε στο `input.docx` δεν είναι πλέον ορατό. Η δομή του εγγράφου εξακολουθεί να περιέχει τον κόμβο σχήματος, ο οποίος μπορεί να αποκρυφθεί αργότερα ορίζοντας `shape.setHidden(false)`.

## Γιατί να κρύψετε ένα σχήμα αντί να το διαγράψετε;

* **Διατήρηση μεταδεδομένων** – Τα σχήματα συχνά περιέχουν εναλλακτικό κείμενο, υπερσυνδέσμους ή προσαρμοσμένα δεδομένα που μπορεί να χρειαστείτε αργότερα.  
* **Υπό όρους εμφάνιση** – Σε σενάρια συγχώνευσης αλληλογραφίας ή δημιουργίας αναφορών μπορεί να εμφανίσετε το σχήμα μόνο για συγκεκριμένους παραλήπτες.  
* **Έλεγχος εκδόσεων** – Η διατήρηση του σχήματος κρυμμένου σας επιτρέπει να διατηρείτε ένα ενιαίο πρότυπο ενώ εναλλάσσετε την ορατότητα προγραμματιστικά.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Συνιστώμενη προσαρμογή |
|-----------|------------------------|
| Πολλά σχήματα, χρειάζεται ένα συγκεκριμένο | Χρησιμοποιήστε `doc.getChild(NodeType.SHAPE, index, true)` με το κατάλληλο δείκτη, ή επαναλάβετε μέσω `doc.getChildNodes(NodeType.SHAPE, true)` και ταιριάξτε με `shape.getName()` ή `shape.getAlternativeText()`. |
| Το σχήμα βρίσκεται μέσα σε GroupShape | Η βαθιά αναζήτηση (`true`) φθάνει ήδη μέσα στις ομάδες, αλλά μπορεί να χρειαστεί να κάνετε cast σε `GroupShape` πρώτα αν σκοπεύετε να κρύψετε μόνο ένα μέλος της ομάδας. |
| Θέλετε να κρύψετε όλα τα σχήματα | Επανάληψη σε όλους τους κόμβους σχήματος και κλήση `setHidden(true)` μέσα στον βρόχο. |
| Συμβατότητα με παλαιότερες εκδόσεις του Word | Η σημαία `Hidden` υποστηρίζεται από το Word 2000. Παλαιότερες μορφές (`.doc`) επίσης τη σέβονται, αλλά δοκιμάστε στην έκδοση-στόχο αν αντιμετωπίσετε απρόσμενες αλλαγές διάταξης. |

**Συμβουλή:** Μετά την απόκρυψη ενός σχήματος, μπορείτε να καλέσετε `doc.updatePageLayout()` αν χρειάζεστε την επαναϋπολογισμό της διάταξης σελίδας πριν την αποθήκευση. Αυτό είναι σπάνια απαραίτητο επειδή το Word αυτόματα επανατοποθετεί το περιεχόμενο κατά το άνοιγμα, αλλά μπορεί να είναι χρήσιμο για δημιουργία προεπισκόπησης από τον διακομιστή.

## Δοκιμή του αποτελέσματος προγραμματιστικά

Αν θέλετε να επιβεβαιώσετε ότι το σχήμα είναι κρυφό χωρίς να ανοίξετε το Word, μπορείτε να ερωτήσετε την ιδιότητα μετά την αποθήκευση:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Επόμενα βήματα

Τώρα που ξέρετε πώς να κρύψετε σχήμα στο Word, εξετάστε τα παρακάτω συναφή θέματα:

* **Κρύψτε σχήμα στο Word βάσει προσαρμοσμένων συνθηκών** – Συνδυάστε τη σημαία `Hidden` με πεδία συγχώνευσης αλληλογραφίας για εναλλαγή ορατότητας ανά παραλήπτη.  
* **Κάντε το σχήμα αόρατο στο Word χρησιμοποιώντας VBA** – Για αυτοματοποίηση στη συσκευή, η ίδια ιδιότητα μπορεί να οριστεί μέσω VBA (`Shape.Visible = msoFalse`).  
* **Κρύψτε σχήματα Microsoft Word μαζικά** – Επεξεργαστείτε έναν φάκελο εγγράφων με έναν βρόχο που εφαρμόζει τον ίδιο κώδικα σε κάθε αρχείο.  

Η εξερεύνηση αυτών των επεκτάσεων θα ενισχύσει τον έλεγχο σας πάνω στην αυτοματοποίηση εγγράφων Word και θα διατηρήσει τα παραγόμενα αρχεία σας καθαρά και επαγγελματικά.

--- 

*Αυτό το tutorial ακολουθεί το Google Developer Documentation Style Guide, χρησιμοποιεί ενεργή φωνή, προοπτική δεύτερου προσώπου, και παρέχει μια πλήρη, αξιόπιστη λύση για μηχανές αναζήτησης και βοηθούς AI.*

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία ορθογώνιου σχήματος σε Word με Java – Πλήρης Οδηγός](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Προσθήκη σκιάς σε σχήμα στο Word – Πλήρης Οδηγός Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Δημιουργία εγγράφου Word με Java – Προσθήκη ορθογώνιου σχήματος με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}