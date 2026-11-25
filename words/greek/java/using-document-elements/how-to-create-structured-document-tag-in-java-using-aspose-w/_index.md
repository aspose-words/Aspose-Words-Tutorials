---
category: general
date: 2026-11-25
description: Δημιουργήστε ετικέτα δομημένου εγγράφου σε Java και μάθετε πώς να προσθέτετε
  έλεγχο περιεχομένου απλού κειμένου κατά την αποθήκευση του εγγράφου Word σε συγκεκριμένο
  φάκελο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create structured document tag
- add plain‑text content control
- save word document to specific folder
- Aspose.Words Java API
- content control example
language: el
lastmod: 2026-11-25
og_description: Δημιουργήστε ετικέτα δομημένου εγγράφου σε Java με το Aspose.Words.
  Αυτό το εκπαιδευτικό δείχνει πώς να προσθέσετε έλεγχο περιεχομένου απλού κειμένου
  και να αποθηκεύσετε το έγγραφο Word σε συγκεκριμένο φάκελο.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag
og_title: Δημιουργία ετικέτας δομημένου εγγράφου σε Java – πλήρης οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Create structured document tag in Java and learn to add plain‑text
    content control while saving the Word document to a specific folder.
  headline: How to create structured document tag in Java using Aspose.Words
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
title: Πώς να δημιουργήσετε ετικέτα δομημένου εγγράφου σε Java χρησιμοποιώντας το
  Aspose.Words
url: /el/java/using-document-elements/how-to-create-structured-document-tag-in-java-using-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ετικέτα δομημένου εγγράφου (structured document tag) στη Java χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε **δημιουργία ετικέτας δομημένου εγγράφου** σε ένα αρχείο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με τη Java. Θα μάθετε να **προσθέτετε έλεγχο περιεχομένου plain‑text**, να του δίνετε έναν φιλικό τίτλο και να **αποθηκεύετε το έγγραφο Word σε συγκεκριμένο φάκελο**—όλα σε λίγα σύντομα βήματα.

Οι ετικέτες δομημένου εγγράφου (επίσης γνωστές ως content controls) σας επιτρέπουν να ενσωματώσετε επαναλαμβανόμενες, σημασιολογικά πλούσιες περιοχές μέσα σε ένα αρχείο DOCX. Είναι ιδανικές για πρότυπα, έγγραφα τύπου φόρμας ή οποιοδήποτε σενάριο όπου θέλετε να επιβάλετε μια συνεπή δομή. Σε αυτό το tutorial θα δείτε ένα πλήρες, εκτελέσιμο πρόγραμμα, θα κατανοήσετε γιατί κάθε γραμμή είναι σημαντική και θα ανακαλύψετε κοινά λάθη που πρέπει να αποφύγετε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για εκπαιδευτικούς σκοπούς).
* Έναν εγγράψιμο φάκελο όπου θα αποθηκευτεί το παραγόμενο αρχείο.

Αν λείπει κάποιο από τα παραπάνω, εγκαταστήστε το πρώτα· ο κώδικας δεν θα μεταγλωττιστεί χωρίς τη βιβλιοθήκη Aspose.Words.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα `pom.xml` (ή προσθέστε στο υπάρχον αρχείο build) που περιλαμβάνει το Aspose.Words:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>structured-tag-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Κρατήστε την έκδοση του Aspose.Words συγχρονισμένη με τις επίσημες σημειώσεις έκδοσης για να επωφεληθείτε από διορθώσεις σφαλμάτων και νέες λειτουργίες content‑control.

## Βήμα 2: Δημιουργία ετικέτας δομημένου εγγράφου (plain‑text content control)

Ο πυρήνας του tutorial βρίσκεται στην κλάση `StructuredTagExample`. Η πρώτη λειτουργική γραμμή δημιουργεί ένα νέο κενό έγγραφο και έναν `DocumentBuilder`. Ο builder είναι το υψηλού επιπέδου API που σας επιτρέπει να εισάγετε στοιχεία χωρίς να ασχοληθείτε με λεπτομέρειες του OpenXML.

```java
import com.aspose.words.*;

public class StructuredTagExample {
    public static void main(String[] args) throws Exception {
        // Initialize an empty document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text StructuredDocumentTag (SDT) with a unique tag identifier.
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

        // Assign a human‑readable title; this appears in the Word UI and helps
        // users locate the control quickly.
        sdt.setTitle("Sample SDT");

        // Write the content that will live inside the tag.
        builder.writeln("Content inside the tag.");

        // Save the document to a folder you control.
        String outputPath = "C:/temp/output.docx"; // change to your desired folder
        doc.save(outputPath);
    }
}
```

### Γιατί αυτή η προσέγγιση;

* **`insertStructuredDocumentTag`** δημιουργεί τον έλεγχο και επιστρέφει το αντικείμενο ώστε να μπορείτε να το διαμορφώσετε αμέσως. Η χρήση του τύπου **plain‑text** εξασφαλίζει ότι το περιεχόμενο συμπεριφέρεται όπως το κανονικό κείμενο, ενώ παραμένει μια ξεχωριστή, επεξεργάσιμη περιοχή.
* Ο ορισμός **title** (`setTitle`) είναι προαιρετικός αλλά ιδιαίτερα συνιστώμενος. Εμφανίζεται στη διεπαφή του Word κάτω από *Developer → Design Mode* και διευκολύνει τον εντοπισμό της ετικέτας όταν ανοίγει το έγγραφο αργότερα.
* Η εγγραφή περιεχομένου με `builder.writeln` τοποθετεί το κείμενο **μέσα** στην ετικέτα επειδή ο κέρσορας του builder είναι αυτόματα τοποθετημένος εντός του νεοεισαχθέντος ελέγχου.

## Βήμα 3: Προσθήκη plain‑text content control σε υπάρχον έγγραφο (προαιρετικό)

Αν έχετε ήδη ένα πρότυπο (`template.docx`) και θέλετε να ενσωματώσετε μια νέα SDT, αντικαταστήστε την αρχικοποίηση του εγγράφου με:

```java
Document doc = new Document("C:/templates/template.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToDocumentEnd(); // Position cursor where you want the control.
```

Το υπόλοιπο του κώδικα παραμένει το ίδιο, και ο νέος **plain‑text content control** θα εμφανιστεί στο τέλος του υπάρχοντος εγγράφου. Αυτό το μοτίβο είναι χρήσιμο για τη δημιουργία αναφορών που μοιράζονται κοινό header/footer αλλά χρειάζονται μια δυναμική περιοχή δεδομένων.

## Βήμα 4: Αποθήκευση του εγγράφου Word σε συγκεκριμένο φάκελο

Η γραμμή `doc.save(outputPath);` επιδεικνύει την απαίτηση **save word document to specific folder**. Μπορείτε να χρησιμοποιήσετε οποιοδήποτε απόλυτο ή σχετικό μονοπάτι που η διαδικασία Java μπορεί να γράψει. Αν ο φάκελος δεν υπάρχει, το Aspose.Words θα τον δημιουργήσει αυτόματα.

```java
String outputPath = "C:/temp/output.docx"; // replace with your target directory
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

### Συνηθισμένα προβλήματα

| Πρόβλημα | Συμπτωμα | Διόρθωση |
|----------|----------|----------|
| Μη έγκυρο μονοπάτι | `java.nio.file.NoSuchFileException` | Βεβαιωθείτε ότι ο φάκελος υπάρχει ή αφήστε το Aspose να τον δημιουργήσει με `new File("C:/temp").mkdirs();` πριν το `save`. |
| Δεν έχει οριστεί άδεια | Το υδατογράφημα εμφανίζεται στο αρχείο εξόδου | Φορτώστε την άδειά σας: `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν δημιουργήσετε το `Document`. |
| Λάθος τύπος ετικέτας | Ο έλεγχος συμπεριφέρεται απρόσμενα (π.χ. εικόνα αντί για κείμενο) | Χρησιμοποιήστε `StructuredDocumentTagType.PLAIN_TEXT` για plain‑text content control. |

## Βήμα 5: Επαλήθευση του αποτελέσματος

Ανοίξτε το `output.docx` στο Microsoft Word. Θα πρέπει να δείτε:

* Ένα **plain‑text content control** με τον τίτλο *Sample SDT*.
* Το κείμενο *Content inside the tag.* εμφανιζόμενο μέσα στον έλεγχο.
* Τον έλεγχο επισημασμένο όταν ενεργοποιήσετε **Developer → Design Mode**.

![Word document showing the inserted Structured Document Tag](https://example.com/images/sdt-screenshot.png){alt="Διάγραμμα που δείχνει μια plain‑text ετικέτα δομημένου εγγράφου σε αρχείο Word"}

Αν ο έλεγχος λείπει, ελέγξτε ξανά ότι κάλεσατε `insertStructuredDocumentTag` **πριν** γράψετε οποιοδήποτε περιεχόμενο. Ο κέρσορας του builder πρέπει να βρίσκεται εντός της ετικέτας όταν προσθέτετε κείμενο.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και να εκτελέσετε μετά την προσθήκη της εξάρτησης Maven:

```java
import com.aspose.words.*;

public class StructuredTagExample {
    public static void main(String[] args) throws Exception {
        // 1. Load license (optional for evaluation)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // 2. Create a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a plain‑text StructuredDocumentTag with identifier "MyTag".
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

        // 4. Give the tag a friendly title.
        sdt.setTitle("Sample SDT");

        // 5. Write the content that belongs to the tag.
        builder.writeln("Content inside the tag.");

        // 6. Define the output path – this satisfies the save word document to specific folder requirement.
        String outputPath = "C:/temp/output.docx"; // adjust as needed
        doc.save(outputPath);

        System.out.println("Document successfully saved to: " + outputPath);
    }
}
```

Η εκτέλεση αυτού του προγράμματος παράγει το `output.docx` στον φάκελο που καθορίσατε. Το αρχείο περιέχει την **structured document tag** που δημιουργήσατε, και έχετε προσθέσει επιτυχώς **plain‑text content control** ενώ **αποθηκεύετε το έγγραφο Word σε συγκεκριμένο φάκελο**.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ετικέτα δομημένου εγγράφου** στη Java με το Aspose.Words, πώς να **προσθέσετε plain‑text content control** και πώς να **αποθηκεύσετε το έγγραφο Word σε συγκεκριμένο φάκελο**. Το παράδειγμα καλύπτει τόσο ένα ολοκαίνουργιο έγγραφο όσο και ένα υπάρχον πρότυπο, συζητά κοινά σφάλματα και παρέχει έναν πλήρη, έτοιμο για αντιγραφή κώδικα.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη **rich‑text** ή **date** content controls (`StructuredDocumentTagType.RICH_TEXT`, `StructuredDocumentTagType.DATE_TIME`).
* Σύνδεση της ετικέτας με XML δεδομένα για δυναμική δημιουργία εγγράφων.
* Χρήση του τύπου ετικέτας **RepeatingSection** για δημιουργία πινάκων από συλλογές.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους ετικετών, τίτλους και τοποθεσίες αρχείων. Το API του Aspose.Words είναι αρκετά ευέλικτο ώστε να αντιμετωπίσει πρακτικά κάθε σενάριο αυτοματοποίησης του Word που μπορεί να συναντήσετε.

---


## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία νέου εγγράφου Word – Οδηγός βήμα‑βήμα για προσθήκη Structured Tag](/words/english/java/document-manipulation/create-new-word-document-step-by-step-guide-to-adding-a-stru/)
- [Δημιουργία εγγράφου Word με plain text content control](/words/english/java/document-manipulation/create-word-document-with-a-plain-text-content-control/)
- [Προσθήκη content control σε έγγραφο Word με Aspose.Words](/words/english/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}