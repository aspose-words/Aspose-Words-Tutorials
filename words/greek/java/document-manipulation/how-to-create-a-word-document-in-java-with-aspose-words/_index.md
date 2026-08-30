---
category: general
date: 2026-08-23
description: Μάθετε πώς να δημιουργήσετε ένα έγγραφο Word σε Java, να προσθέσετε έναν
  χώρο κράτησης ελέγχου απλού κειμένου, να γράψετε το κείμενο γύρω του και να αποθηκεύσετε
  το έγγραφο σε αρχείο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- save document to file
- write surrounding text
- add placeholder to word
- insert plain text control
language: el
lastmod: 2026-08-23
og_description: Δημιουργήστε ένα έγγραφο Word σε Java, εισάγετε έναν έλεγχο απλού
  κειμένου, γράψτε το κείμενο γύρω του και αποθηκεύστε το έγγραφο σε αρχείο χρησιμοποιώντας
  το Aspose.Words.
og_image_alt: Screenshot of a Java‑generated Word document containing a plain‑text
  control placeholder
og_title: Δημιουργία εγγράφου Word σε Java – πλήρης οδηγός με placeholder
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to create a Word document in Java, add a plain‑text control
    placeholder, write surrounding text, and save the document to file.
  headline: How to create a Word document in Java with Aspose.Words
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word Automation
- Document Generation
title: Πώς να δημιουργήσετε ένα έγγραφο Word σε Java με το Aspose.Words
url: /el/java/document-manipulation/how-to-create-a-word-document-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα έγγραφο Word σε Java με το Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε ένα έγγραφο Word σε Java**, αυτό το tutorial δείχνει τη πλήρη διαδικασία από την αρχή μέχρι το τέλος. Θα μάθετε πώς να εισάγετε έναν έλεγχο απλού κειμένου, να προσθέσετε ένα placeholder, να γράψετε κείμενο γύρω του, και τελικά **να αποθηκεύσετε το έγγραφο σε αρχείο**.

Το παράδειγμα χρησιμοποιεί το Aspose.Words for Java, μια βιβλιοθήκη που αφαιρεί την πολυπλοκότητα του μορφότυπου Office Open XML και σας επιτρέπει να χειρίζεστε αρχεία Word προγραμματιστικά. Στο τέλος αυτού του οδηγού θα έχετε ένα εκτελέσιμο πρόγραμμα που παράγει ένα αρχείο `.docx` που περιέχει μια ετικέτα δομημένου εγγράφου (SDT) με ένα φιλικό προς το χρήστη placeholder.

## Προαπαιτούμενα

* Java Development Kit 17 ή νεότερο
* Maven ή Gradle για διαχείριση εξαρτήσεων
* Ένα IDE όπως IntelliJ IDEA ή Eclipse (οποιοσδήποτε επεξεργαστής λειτουργεί)
* Ένα έγκυρο άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για αυτή τη demo)

Προσθέστε την ακόλουθη εξάρτηση Maven στο `pom.xml` σας (αντικαταστήστε την έκδοση με την πιο πρόσφατη έκδοση):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Αν χρησιμοποιείτε Gradle, η ισοδύναμη καταχώρηση είναι:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

## Βήμα 1: Δημιουργία νέου κενού εγγράφου

Η πρώτη ενέργεια είναι η δημιουργία ενός κενό αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη.

```java
import com.aspose.words.*;

public class InsertSDTDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document
        Document document = new Document();
```

Η δημιουργία του εγγράφου δεν γράφει κάτι στο δίσκο ακόμη· προετοιμάζει μόνο μια δομή στη μνήμη που θα συμπληρώσετε στα επόμενα βήματα.

## Βήμα 2: Αρχικοποίηση ενός DocumentBuilder για επεξεργασία

`DocumentBuilder` είναι το κύριο API για εισαγωγή και μορφοποίηση περιεχομένου. Περνάτε το προηγουμένως δημιουργημένο `Document` στον κατασκευαστή του.

```java
        // Step 2: Initialise a DocumentBuilder for editing the document
        DocumentBuilder docBuilder = new DocumentBuilder(document);
```

Ο builder διατηρεί έναν κέρσορα που κινείται καθώς προσθέτετε κόμβους, κάτι που καθιστά εύκολο το **να γράψετε κείμενο γύρω του** πριν ή μετά από άλλα στοιχεία.

## Βήμα 3: Εισαγωγή μιας ετικέτας δομημένου εγγράφου (SDT) απλού κειμένου

Ένα SDT απλού κειμένου λειτουργεί όπως ένας έλεγχος περιεχομένου στο Word. Μπορεί να περιέχει ένα placeholder που καθοδηγεί τον χρήστη όταν το έγγραφο ανοίγει στο Microsoft Word.

```java
        // Step 3: Insert a plain‑text Structured Document Tag (SDT) with a placeholder
        StructuredDocumentTag plainTextTag = docBuilder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, true);
        plainTextTag.setTitle("CustomerName");
        plainTextTag.setPlaceholderName("Enter customer name…");
```

* `StructuredDocumentTagType.PLAIN_TEXT` λέει στο Aspose.Words να δημιουργήσει έναν έλεγχο απλού κειμένου.
* Το όρισμα `true` κάνει την ετικέτα **επαναλαμβανόμενη**, κάτι που είναι χρήσιμο για φόρμες που μπορεί να περιέχουν πολλαπλές καταχωρήσεις.
* `setTitle` δίνει στον έλεγχο ένα λογικό όνομα που μπορεί να προσπελαστεί αργότερα μέσω του Open XML SDK ή του UI του Word.
* `setPlaceholderName` ορίζει την γκριζαρισμένη υπόδειξη που εμφανίζεται στον χρήστη.

## Βήμα 4: Γράψτε κείμενο πριν από το SDT

Τώρα που υπάρχει ο έλεγχος, μπορείτε να προσθέσετε εξηγητικό κείμενο που εμφανίζεται πριν από αυτό. Η μέθοδος `writeln` προσθέτει μια παράγραφο και μετακινεί τον κέρσορα στην επόμενη γραμμή.

```java
        // Step 4: Write surrounding text before the SDT
        docBuilder.writeln("The order belongs to:");
```

Αυτή η γραμμή δείχνει **να γράψετε κείμενο γύρω του** με φυσική σειρά ανάγνωσης. Το κείμενο θα εμφανιστεί στο τελικό έγγραφο ακριβώς όπως φαίνεται.

## Βήμα 5: Εισαγωγή του SDT στη ροή του εγγράφου

Παρόλο που το SDT δημιουργήθηκε νωρίτερα, δεν είναι ακόμη μέρος του δέντρου του εγγράφου. Η `insertNode` το τοποθετεί στην τρέχουσα θέση του κέρσορα.

```java
        // Step 5: Insert the SDT into the document flow
        docBuilder.insertNode(plainTextTag);
```

Μετά από αυτή την κλήση, ο έλεγχος placeholder βρίσκεται ακριβώς μετά τη φράση “The order belongs to:”.

## Βήμα 6: Γράψτε κείμενο μετά το SDT

Μπορείτε να συνεχίσετε να προσθέτετε περισσότερες παραγράφους μετά τον έλεγχο. Αυτό το βήμα δείχνει πώς να **γράψετε κείμενο γύρω του** που ακολουθεί το placeholder.

```java
        // Step 6: Write text after the SDT
        docBuilder.writeln("\nThank you!");
```

Ο χαρακτήρας νέας γραμμής δημιουργεί οπτικό διαχωρισμό, αλλά το Word θα το αντιμετωπίσει ως κανονική αλλαγή παραγράφου.

## Βήμα 7: Αποθήκευση του εγγράφου σε αρχείο

Τέλος, αποθηκεύστε το έγγραφο στη μνήμη στο δίσκο χρησιμοποιώντας τη μέθοδο `save`. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική με τον φάκελο του έργου σας.

```java
        // Step 7: Save the document to a file
        document.save("output/SDTDemo.docx");
    }
}
```

Όταν το πρόγραμμα ολοκληρωθεί, το `output/SDTDemo.docx` περιέχει:

* Τη εισαγωγική πρόταση “The order belongs to:”
* Έναν έλεγχο απλού κειμένου με τίτλο **CustomerName** και το placeholder **Enter customer name…**
* Μια τελική γραμμή “Thank you!”

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word. Θα πρέπει να δείτε:

```
The order belongs to: [Enter customer name…] 
Thank you!
```

Το κείμενο του placeholder εμφανίζεται σε ανοιχτό γκρι. Όταν κάνετε κλικ μέσα στον έλεγχο, το Word σας επιτρέπει να πληκτρολογήσετε το πραγματικό όνομα του πελάτη.

## Γιατί αυτή η προσέγγιση λειτουργεί

* **StructuredDocumentTag** παρέχει έναν εγγενή έλεγχο περιεχομένου Word, εξασφαλίζοντας συμβατότητα με το UI του Word και άλλα εργαλεία αυτοματοποίησης.
* Η χρήση του **DocumentBuilder** διατηρεί τον κώδικα γραμμικό και αναγνώσιμο, μειώνοντας την πιθανότητα εισαγωγής κόμβων στη λάθος θέση.
* Ο ορισμός **title** στο SDT ενεργοποιεί επεξεργασία downstream (π.χ., mail‑merge ή εξαγωγή δεδομένων) χωρίς να εξαρτάται από οπτικές ενδείξεις.
* Το **placeholder** βελτιώνει την εμπειρία του τελικού χρήστη, υποδεικνύοντας πού ανήκουν τα δεδομένα.

## Περιπτώσεις άκρων και συμβουλές βέλτιστων πρακτικών

| Κατάσταση | Συνιστώμενη αντιμετώπιση |
|-----------|--------------------------|
| Χρειάζεστε έναν **date picker** αντί για απλό κείμενο | Χρησιμοποιήστε `StructuredDocumentTagType.DATE` όταν καλείτε `insertStructuredDocumentTag`. |
| Το έγγραφο πρέπει να είναι **PDF** καθώς και DOCX | Μετά την αποθήκευση του DOCX, καλέστε `document.save("output/SDTDemo.pdf", SaveFormat.PDF);`. |
| Το placeholder πρέπει να είναι **τοπικοποιημένο** | Ανακτήστε τη μεταφρασμένη συμβολοσειρά από ένα resource bundle και περάστε τη στο `setPlaceholderName`. |
| Μεγάλα έγγραφα προκαλούν **πρόσθετο φορτίο μνήμης** | Χρησιμοποιήστε `DocumentBuilder.insertDocument` με `ImportFormatMode.KEEP_SOURCE_FORMATTING` για ροή τμημάτων, ή ενεργοποιήστε `MemoryOptimization` στο αντικείμενο `Document`. |
| Χρειάζεστε να **επαναλάβετε τον έλεγχο** για πολλαπλά στοιχεία | Διατηρήστε το όρισμα `true` στο `insertStructuredDocumentTag` και αντιγράψτε την ετικέτα προγραμματιστικά μέσα σε βρόχο. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες αρχείο πηγαίου κώδικα που μπορείτε να αντιγράψετε σε ένα έργο Maven και να εκτελέσετε απευθείας.

```java
import com.aspose.words.*;

public class InsertSDTDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder for editing the document
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // Step 3: Insert a plain‑text Structured Document Tag (SDT) with a placeholder
        StructuredDocumentTag plainTextTag = docBuilder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, true);
        plainTextTag.setTitle("CustomerName");
        plainTextTag.setPlaceholderName("Enter customer name…");

        // Step 4: Write surrounding text before the SDT
        docBuilder.writeln("The order belongs to:");

        // Step 5: Insert the SDT into the document flow
        docBuilder.insertNode(plainTextTag);

        // Step 6: Write text after the SDT
        docBuilder.writeln("\nThank you!");

        // Step 7: Save the document to a file
        document.save("output/SDTDemo.docx");
    }
}
```

Εκτελέστε την κλάση, και θα βρείτε το `SDTDemo.docx` στον φάκελο `output`. Ανοίξτε το με το Microsoft Word για να επαληθεύσετε ότι το placeholder εμφανίζεται σωστά και ότι το κείμενο γύρω του είναι τοποθετημένο όπως φαίνεται στο αναμενόμενο αποτέλεσμα.

## Επόμενα βήματα

* **Insert other control types** – εξερευνήστε `StructuredDocumentTagType.RICH_TEXT`, `CHECKBOX` και `DROP_DOWN_LIST` για τη δημιουργία πιο σύνθετων φορμών.
* **Populate the document programmatically** – χρησιμοποιήστε τα API του `StructuredDocumentTag` για να ορίσετε το κείμενο του ελέγχου χωρίς αλληλεπίδραση χρήστη.
* **Combine with mail‑merge** – συγχωνεύστε το παραγόμενο πρότυπο με μια πηγή δεδομένων για να δημιουργήσετε εξατομικευμένες συμβάσεις ή τιμολόγια.
* **Export to other formats** – το Aspose.Words μπορεί να αποθηκεύσει σε PDF, HTML και EPUB με μία κλήση μεθόδου.

Με την κατάκτηση αυτών των δομικών στοιχείων μπορείτε να αυτοματοποιήσετε πρακτικά οποιαδήποτε ροή εργασίας επεξεργασίας Word σε Java, από απλά πρότυπα μέχρι σύνθετες, δεδομενο‑κατευθυνόμενες αναφορές.

---

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word σε Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Βελτιστοποίηση μετατροπής εγγράφου σε κείμενο με Aspose.Words Java: Αποδοτικότητα και Απόδοση](/words/english/java/performance-optimization/aspose-words-java-document-to-text-conversion/)
- [Εισαγωγή πεδίου κειμένου φόρμας σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}