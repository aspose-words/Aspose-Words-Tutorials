---
category: general
date: 2026-06-20
description: Ανακτήστε κατεστραμμένα αρχεία docx σε Java με το Aspose.Words. Μάθετε
  πώς να ορίσετε τη λειτουργία ανάκτησης και να φορτώσετε το έγγραφο με ανάκτηση για
  αδιάλειπτο άνοιγμα.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: el
og_description: Ανακτήστε κατεστραμμένα αρχεία docx σε Java χρησιμοποιώντας το Aspose.Words.
  Αυτό το σεμινάριο δείχνει πώς να ορίσετε τη λειτουργία ανάκτησης, να φορτώσετε το
  έγγραφο με ανάκτηση και να ανοίξετε με ασφάλεια το κατεστραμμένο docx.
og_title: Ανάκτηση κατεστραμμένου docx σε Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Ανάκτηση κατεστραμμένου docx σε Java – Πλήρης Οδηγός
url: /el/java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου docx σε Java – Πλήρης Οδηγός

Προσπαθήσατε ποτέ να **ανακτήσετε κατεστραμμένα αρχεία docx** και να βρεθείτε σε αδιέξοδο; Σε αυτό το tutorial θα σας δείξουμε πώς να **ανακτήσετε κατεστραμμένα docx** χρησιμοποιώντας το Aspose.Words for Java με **ορισμό λειτουργίας ανάκτησης** και **φόρτωση εγγράφου με ανάκτηση**, ώστε το αρχείο να ανοίγει όπως ένα υγιές έγγραφο Word.  

Αν αναρωτηθήκατε ποτέ γιατί κάποια αρχεία DOCX αρνούνται να ανοίξουν στο Word, η απάντηση είναι συχνά κρυμμένη ζημιά που ο κανονικός φορτωτής δεν μπορεί να διαχειριστεί. Θα περάσουμε από τα ακριβή βήματα που χρειάζεστε, από την προσθήκη της βιβλιοθήκης μέχρι την επαλήθευση του αριθμού σελίδων, και θα καταλήξετε με ένα καθαρό, χρησιμοποιήσιμο έγγραφο—χωρίς πια αναδυόμενα “το αρχείο είναι κατεστραμμένο”.

## Τι Θα Μάθετε

- Πώς να **ορίσετε λειτουργία ανάκτησης** για να υποδείξετε στο Aspose.Words πόσο επιθετικά πρέπει να επισκευάσει ένα κατεστραμμένο αρχείο.  
- Τον ακριβή κώδικα που απαιτείται για **φόρτωση εγγράφου με ανάκτηση** και τη διαχείριση σοβαρής ζημιάς με χάρη.  
- Συμβουλές για σενάρια **open word with recovery** και τι να κάνετε όταν το αρχείο δεν μπορεί να σωθεί.  
- Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας.  

### Προαπαιτούμενα

- Εγκατεστημένο Java 8 ή νεότερο.  
- Maven ή Gradle για διαχείριση εξαρτήσεων (θα καλύψουμε το Maven).  
- Ένα κατεστραμμένο αρχείο `.docx` που θέλετε να δοκιμάσετε (οποιοδήποτε αρχείο που αρνείται να ανοίξει στο Microsoft Word).  

Δεν απαιτείται βαθιά γνώση του Aspose API—απλώς βασικές δεξιότητες Java. Ας ξεκινήσουμε.

![recover corrupted docx example](recover_corrupted_docx.png "recover corrupted docx screenshot")

## Βήμα 1: Προσθήκη Aspose.Words for Java στο Έργο Σας

Πρώτα απ’ όλα—το έργο σας χρειάζεται το JAR του Aspose.Words. Αν χρησιμοποιείτε Maven, προσθέστε αυτό στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Οι χρήστες Gradle μπορούν να προσθέσουν:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**Συμβουλή επαγγελματία:** Ελέγχετε πάντα την ιστοσελίδα του Aspose για την πιο πρόσφατη έκδοση· οι νεότερες κυκλοφορίες συχνά περιλαμβάνουν καλύτερους αλγόριθμους ανάκτησης.

## Βήμα 2: Ορισμός Λειτουργίας Ανάκτησης – Το Κλειδί για Διόρθωση Κατεστραμμένων Αρχείων

Τώρα που η βιβλιοθήκη είναι στη θέση της, πρέπει να της πείτε **πώς** θα συμπεριφέρεται όταν συναντήσει κατεστραμμένα δεδομένα. Εδώ έρχεται το `setRecoveryMode`. Το enum `RecoveryMode` προσφέρει δύο επιλογές:

| Mode | Περιγραφή |
|------|------------|
| `RECOVER` | Προσπαθεί να διορθώσει όσο το δυνατόν περισσότερο, επιστρέφοντας ένα μερικά επισκευασμένο έγγραφο. |
| `REJECT` | Ρίχνει εξαίρεση σε οποιοδήποτε σοβαρό πρόβλημα, χρήσιμο όταν χρειάζεστε ένα καθαρό αρχείο. |

Ακολουθεί ο κώδικας που **ορίζει λειτουργία ανάκτησης** στην επιεική επιλογή `RECOVER`:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Γιατί είναι σημαντικό:** Χωρίς τον ορισμό λειτουργίας ανάκτησης, το Aspose.Words προεπιλέγει `REJECT`, πράγμα που σημαίνει ότι το πρόγραμμά σας θα ρίξει εξαίρεση τη στιγμή που εντοπίσει ένα σπασμένο τμήμα. Με την ρητή **ορισμό λειτουργίας ανάκτησης**, δίνετε στη βιβλιοθήκη την άδεια να επιδιορθώσει ελλιπή κόμβους XML, να επαναφέρει χαμένα relationships και γενικά να “καθαρίσει” το αρχείο.

## Βήμα 3: Φόρτωση Εγγράφου με Ανάκτηση – Συνδυάζοντας Όλα

Το παραπάνω απόσπασμα ήδη δείχνει **φόρτωση εγγράφου με ανάκτηση**, αλλά ας το αναλύσουμε για σαφήνεια:

1. **Δημιουργία αντικειμένου `LoadOptions`** – αυτό το αντικείμενο κρατά όλες τις σημαίες που θέλετε ο φορτωτής να σέβεται.  
2. **Κλήση `setRecoveryMode`** – επιλέξαμε `RECOVER` επειδή θέλουμε τη μεγαλύτερη πιθανότητα να ανοίξει το αρχείο.  
3. **Πέρασμα των επιλογών στον κατασκευαστή `Document`** – το Aspose.Words διαβάζει το αρχείο, εφαρμόζει τη λογική ανάκτησης και επιστρέφει ένα χρησιμοποιήσιμο αντικείμενο `Document`.

Αν προτιμάτε πιο αμυντική προσέγγιση, μπορείτε να τυλίξετε τη φόρτωση σε μπλοκ try‑catch και να επιστρέψετε στο `REJECT` αν το `RECOVER` δώσει μη ικανοποιητικό αποτέλεσμα:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Βήμα 4: Επαλήθευση του Επισκευασμένου Εγγράφου

Μόλις το έγγραφο φορτωθεί, θα θέλετε να βεβαιωθείτε ότι το περιεχόμενο είναι λογικό. Συνηθισμένοι έλεγχοι περιλαμβάνουν:

- **Αριθμός σελίδων** – γρήγορος έλεγχος λογικότητας (`doc.getPageCount()`).  
- **Εξαγωγή κειμένου** – `doc.getText()` για να δείτε αν το κύριο σώμα είναι άθικτο.  
- **Αποθήκευση αντιγράφου** – γράψτε την ανακτημένη έκδοση στο δίσκο για μετέπειτα επιθεώρηση.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

Αν η προεπισκόπηση φαίνεται χαοτική, το αρχείο μπορεί να έχει υποστεί ανεπανόρθωτη ζημιά. Σε αυτήν την περίπτωση, σκεφτείτε να χρησιμοποιήσετε τη λειτουργία `REJECT` για να αποφύγετε τη διάδοση κατεστραμμένων δεδομένων.

## Βήμα 5: Προαιρετικό – Άνοιγμα Word με Ανάκτηση (Χειροκίνητη Προσέγγιση)

Μερικές φορές δεν θέλετε να γράψετε κώδικα· απλώς χρειάζεστε να **ανοίξετε το Word με ανάκτηση** χειροκίνητα. Το Microsoft Word προσφέρει τη λειτουργία “Open and Repair”:

1. Ανοίξτε το Word → *File* → *Open*.  
2. Επιλέξτε το κατεστραμμένο `.docx`.  
3. Κάντε κλικ στο βέλος δίπλα στο *Open* και επιλέξτε **Open and Repair**.

Αν και αυτή η μέθοδος λειτουργεί για πολλούς χρήστες, λείπουν οι δυνατότητες αυτοματοποίησης και επεξεργασίας δέσμης που προσφέρει η προσέγγιση Java. Χρησιμοποιήστε τη χειροκίνητη μέθοδο για περιστασιακές διορθώσεις· βασιστείτε στο Aspose.Words όταν χρειάζεται να επεξεργαστείτε δεκάδες ή εκατοντάδες αρχεία προγραμματιστικά.

## Ακραίες Περιπτώσεις & Συνηθισμένα Πάγια

- **Σοβαρή κατεστραμμένη κατάσταση** – Αν λείπει το κεντρικό `[Content_Types].xml`, ούτε το `RECOVER` δεν μπορεί να βοηθήσει. Αναμένετε εξαίρεση και ενημερώστε τον χρήστη.  
- **Αρχεία με κωδικό πρόσβασης** – Η λειτουργία ανάκτησης δεν παρακάμπτει την κρυπτογράφηση. Πρέπει να περάσετε τον κωδικό μέσω `LoadOptions.setPassword("yourPwd")` πριν προσπαθήσετε την ανάκτηση.  
- **Μεγάλα έγγραφα** – Η φόρτωση ενός τεράστιου DOCX με `RECOVER` μπορεί να καταναλώσει περισσότερη μνήμη. Σκεφτείτε να αυξήσετε το heap του JVM (`-Xmx2g`) αν αντιμετωπίσετε `OutOfMemoryError`.  

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε άμεσα. Αντικαταστήστε τη διαδρομή του αρχείου με τη θέση του κατεστραμμένου DOCX σας.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Αναμενόμενη έξοδος (όταν η ανάκτηση πετύχει):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

Αν το έγγραφο είναι πέρα από την επισκευή, θα δείτε ένα σαφές μήνυμα σφάλματος αντί για στοίβα εξαιρέσεων, χάρη στο περιβάλλον `try‑catch`.

## Συμπέρασμα

Τώρα ξέρετε πώς να **ανακτήσετε κατεστραμμένα docx** αρχεία σε Java χρησιμοποιώντας το Aspose.Words. Με την **ορισμό λειτουργίας ανάκτησης** σε `RECOVER` και στη συνέχεια **φόρτωση εγγράφου με ανάκτηση**, μπορείτε αυτόματα να διορθώσετε πολλά κοινά προβλήματα που διαφορετικά θα εμπόδιζαν το άνοιγμα ενός αρχείου Word. Είτε χρειάζεστε να **open word with recovery** προγραμματιστικά είτε απλώς θέλετε να **open corrupted docx** χειροκίνητα, οι τεχνικές που καλύφθηκαν εδώ σας παρέχουν μια σταθερή βάση.

**Επόμενα βήματα:**  

- Πειραματιστείτε

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Recover corrupted docx – Complete Guide to Fix and Process Documents](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Merge Multiple DOCX Files Using Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}