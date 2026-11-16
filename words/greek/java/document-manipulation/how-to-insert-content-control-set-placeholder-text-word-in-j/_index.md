---
category: general
date: 2026-11-15
description: Πώς να εισαγάγετε έλεγχο περιεχομένου, να ορίσετε κείμενο κράτησης θέσης
  σε Word με Java χρησιμοποιώντας το Aspose.Words. Ακολουθήστε έναν οδηγό βήμα‑βήμα
  για να προσθέσετε επεξεργάσιμες ετικέτες σε ένα έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert content control
- set placeholder text word
language: el
lastmod: 2026-11-15
og_description: Πώς να εισαγάγετε έλεγχο περιεχομένου, να ορίσετε κείμενο κράτησης
  θέσης σε Word με Java και Aspose.Words. Αυτός ο οδηγός σας καθοδηγεί μέσα από την
  πλήρη υλοποίηση.
og_image_alt: Screenshot showing how to insert content control in a Word document
og_title: Εισαγάγετε έναν έλεγχο περιεχομένου και ορίστε κείμενο κράτησης θέσης σε
  Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: How to insert content control, set placeholder text word in Java using
    Aspose.Words. Follow a step‑by‑step guide to add editable tags to a Word document.
  headline: How to insert content control, set placeholder text word in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να εισάγετε έλεγχο περιεχομένου, να ορίσετε κείμενο κράτησης θέσης σε Java
url: /el/java/document-manipulation/how-to-insert-content-control-set-placeholder-text-word-in-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισαγάγετε έλεγχο περιεχομένου, ορίσετε κείμενο υπόδειξης σε Java

Αν χρειάζεστε **πώς να εισαγάγετε έλεγχο περιεχομένου** σε αρχείο Word, αυτό το tutorial σας δείχνει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα μάθετε πώς να προσθέσετε ένα επεξεργάσιμο StructuredDocumentTag, να του δώσετε έναν περιγραφικό τίτλο και **να ορίσετε κείμενο υπόδειξης** που εμφανίζεται όταν η ετικέτα είναι κενή.

Η αυτοματοποίηση του Word συχνά απαιτεί ελέγχους περιεχομένου για φόρμες, πρότυπα ή δυναμικές αναφορές. Στο τέλος αυτού του οδηγού θα μπορείτε να δημιουργήσετε ένα `.docx` που περιέχει έναν έλεγχο περιεχομένου έτοιμο για εισαγωγή από τον χρήστη, χωρίς να βγείτε από τη βάση κώδικα Java.

## Τι θα χρειαστείτε

- Java 17 ή νεότερη (ο κώδικας λειτουργεί επίσης με Java 8+)  
- Aspose.Words for Java 23.9 ή νεότερη  
- Ένα IDE ανάπτυξης (IntelliJ IDEA, Eclipse ή VS Code)  
- Βασική εξοικείωση με Maven ή Gradle για διαχείριση εξαρτήσεων  

## Βήμα 1: Προσθέστε το Aspose.Words στο έργο σας

Αν χρησιμοποιείτε Maven, προσθέστε την παρακάτω εξάρτηση στο `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

Για Gradle, τοποθετήστε αυτό στο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9:jdk17'
```

Αυτές οι γραμμές φέρνουν τη βιβλιοθήκη που παρέχει τις κλάσεις `Document`, `DocumentBuilder` και `StructuredDocumentTag` που χρειάζονται για **πώς να εισαγάγετε έλεγχο περιεχομένου**.

## Βήμα 2: Φορτώστε το πηγαίο έγγραφο

Ξεκινήστε φορτώνοντας ένα υπάρχον αρχείο `.docx`. Αν το αρχείο δεν υπάρχει, το Aspose.Words δημιουργεί αυτόματα ένα κενό έγγραφο.

```java
import com.aspose.words.*;

public class ContentControlDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing Word document or create a new one
        Document doc = new Document("src/main/resources/input.docx");
```

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word. Η φόρτωσή του πρώτα εξασφαλίζει ότι τυχόν υπάρχουσες μορφές ή ενότητες παραμένουν αμετάβλητες όταν αργότερα **πώς να εισαγάγετε έλεγχο περιεχομένου**.

## Βήμα 3: Εισάγετε έναν έλεγχο περιεχομένου απλού κειμένου

Ένας *έλεγχος περιεχομένου* στο Word αντιπροσωπεύεται από ένα `StructuredDocumentTag` (SDT). Ο παρακάτω κώδικας δημιουργεί ένα SDT απλού κειμένου που οι χρήστες μπορούν να επεξεργαστούν άμεσα.

```java
        // Create a builder attached to the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text content control (editable tag)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                SdtType.PLAIN_TEXT, true);
```

Το όρισμα `true` σηματοδοτεί την ετικέτα ως *επαναλαμβανόμενη* (μπορεί να εμφανιστεί πολλές φορές). Αυτό είναι το βασικό στοιχείο του **πώς να εισαγάγετε έλεγχο περιεχομένου** με το Aspose.Words.

## Βήμα 4: Δώστε στον έλεγχο περιεχομένου τίτλο και κείμενο υπόδειξης

Ένας τίτλος βοηθά τους προγραμματιστές να αναγνωρίζουν την ετικέτα προγραμματιστικά, ενώ το κείμενο υπόδειξης καθοδηγεί τους τελικούς χρήστες. Εδώ τόσο **ορίζουμε κείμενο υπόδειξης** όσο και αναθέτουμε έναν ευανάγνωστο τίτλο.

```java
        // Assign a meaningful title – useful for later retrieval
        sdt.setTitle("MyTag");

        // Set placeholder text that appears when the tag is empty
        sdt.setPlaceholderName("Enter text here");
```

Η υπόδειξη συμπεριφέρεται όπως η γκρι υπόδειξη που βλέπετε στη διεπαφή του Word. Αν χρειάζεστε την υπόδειξη να είναι μεταφρασμένη, απλώς αλλάξτε τη συμβολοσειρά που περνάτε στο `setPlaceholderName`.

## Βήμα 5: Αποθηκεύστε το έγγραφο και ελέγξτε το αποτέλεσμα

Τέλος, γράψτε το τροποποιημένο έγγραφο στο δίσκο. Ανοίγοντας το αρχείο στο Microsoft Word θα δείτε έναν γκρι‑σκιασμένο έλεγχο περιεχομένου με την υπόδειξη που ορίσατε.

```java
        // Optional: Save the document to see the SDT in action
        doc.save("src/main/resources/output.docx");
    }
}
```

Όταν ανοίξετε το `output.docx`, θα δείτε έναν έλεγχο περιεχομένου απλού κειμένου με τίτλο **MyTag** και την υπόδειξη «Enter text here». Οι χρήστες μπορούν να κάνουν κλικ μέσα στον έλεγχο και να αντικαταστήσουν την υπόδειξη με πραγματικά δεδομένα.

## Πώς να εισαγάγετε έλεγχο περιεχομένου σε διαφορετικά σενάρια

### Προσθήκη ελέγχου περιεχομένου μέσα σε κελί πίνακα

Αν χρειάζεστε τον έλεγχο μέσα σε πίνακα, μετακινήστε τον builder στο επιθυμητό κελί πριν καλέσετε `insertStructuredDocumentTag`:

```java
        // Create a 2x2 table
        Table table = builder.startTable();
        builder.insertCell();
        builder.write("Name:");
        builder.insertCell();
        // Move builder to the second cell
        builder.moveToCell(0, 0, 1, 0);
        StructuredDocumentTag cellSdt = builder.insertStructuredDocumentTag(
                SdtType.PLAIN_TEXT, true);
        cellSdt.setTitle("NameTag");
        cellSdt.setPlaceholderName("Full name");
        builder.endTable();
```

Αυτό το μοτίβο δείχνει **πώς να εισαγάγετε έλεγχο περιεχομένου** μέσα σε σύνθετες διατάξεις χωρίς να διασπάται η δομή του εγγράφου.

### Χρήση ελέγχου περιεχομένου πλούσιου κειμένου

Για πιο πλούσια μορφοποίηση, αντικαταστήστε το `SdtType.PLAIN_TEXT` με `SdtType.RICH_TEXT`. Η ίδια μέθοδος `setPlaceholderName` λειτουργεί, επιτρέποντάς σας **να ορίσετε κείμενο υπόδειξης** για ετικέτες πλούσιου κειμένου επίσης.

```java
        StructuredDocumentTag richSdt = builder.insertStructuredDocumentTag(
                SdtType.RICH_TEXT, true);
        richSdt.setTitle("RichTag");
        richSdt.setPlaceholderName("Enter formatted text");
```

## Συνηθισμένα προβλήματα και βέλτιστες πρακτικές

| Πρόβλημα | Γιατί συμβαίνει | Πώς να το αποφύγετε |
|----------|----------------|---------------------|
| **Η υπόδειξη δεν είναι ορατή** | Η ετικέτα είναι ήδη γεμάτη με κρυφούς χαρακτήρες. | Καλέστε `sdt.clear()` πριν ορίσετε την υπόδειξη, ή βεβαιωθείτε ότι το έγγραφο αποθηκεύεται μετά την εισαγωγή. |
| **Σύγκρουση τίτλων** | Δύο ετικέτες μοιράζονται τον ίδιο τίτλο, καθιστώντας την ανάκτηση ασαφή. | Χρησιμοποιήστε μοναδικούς τίτλους (π.χ. προσθέστε GUID ή δείκτη). |
| **Αποθήκευση σε θέση μόνο για ανάγνωση** | Το `doc.save` ρίχνει `IOException`. | Επαληθεύστε τα δικαιώματα εγγραφής ή επιλέξτε έναν φάκελο με δυνατότητα εγγραφής. |
| **Λείπει η βιβλιοθήκη κατά την εκτέλεση** | `NoClassDefFoundError` αν το Aspose.JAR δεν είναι στο classpath. | Συμπεριλάβετε την εξάρτηση μέσω Maven/Gradle και ενσωματώστε το JAR στην εφαρμογή σας. |

Ακολουθώντας αυτές τις οδηγίες, κάθε φορά που **πώς να εισαγάγετε έλεγχο περιεχομένου** θα καταλήγετε σε μια καθαρή, φιλική προς τον χρήστη υπόδειξη.

## Αναμενόμενο αποτέλεσμα

Η εκτέλεση του πλήρους προγράμματος δεν εμφανίζει έξοδο στην κονσόλα, αλλά το παραγόμενο `output.docx` φαίνεται ως εξής:

![Word document showing a content control with placeholder text](images/content-control-placeholder.png "Screenshot showing how to insert content control in a Word document")

*Image alt text:* **Screenshot showing how to insert content control in a Word document** (contains the primary keyword).

Η υπόδειξη «Enter text here» εμφανίζεται σε ανοιχτό γκρι. Κάνοντας κλικ στο πλαίσιο μπορείτε να πληκτρολογήσετε πραγματικό περιεχόμενο, αποδεικνύοντας ότι ο έλεγχος περιεχομένου λειτουργεί.

## Σύνοψη της πλήρους λύσης



## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Προσθήκη ελέγχου περιεχομένου σε έγγραφο Word με Aspose.Words](/words/english/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/)
- [Δημιουργία κενών εγγράφων Word και εισαγωγή ελέγχου απλού κειμένου](/words/english/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/)
- [Πώς να αποθηκεύσετε αρχείο DOCX με Java – Οδηγός εισαγωγής ελέγχου περιεχομένου](/words/english/java/document-loading-and-saving/how-to-save-docx-file-with-java-insert-content-control-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}