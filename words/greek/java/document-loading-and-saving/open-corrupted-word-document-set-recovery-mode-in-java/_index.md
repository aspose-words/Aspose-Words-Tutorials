---
category: general
date: 2026-05-26
description: Ανοίξτε κατεστραμμένο έγγραφο Word σε Java με το Aspose.Words. Μάθετε
  πώς να ορίσετε τη λειτουργία ανάκτησης και να επαναφέρετε αξιόπιστα κατεστραμμένα
  αρχεία Word.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: el
og_description: Ανοίξτε κατεστραμμένο έγγραφο Word σε Java χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός δείχνει πώς να ορίσετε τη λειτουργία ανάκτησης και να ανακτήσετε
  αποδοτικά κατεστραμμένα αρχεία Word.
og_title: Άνοιγμα Κατεστραμμένου Εγγράφου Word – Ορισμός Λειτουργίας Ανάκτησης σε
  Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Άνοιγμα Κατεστραμμένου Εγγράφου Word – Ορισμός Λειτουργίας Ανάκτησης σε Java
url: /el/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Άνοιγμα Κατεστραμμένου Εγγράφου Word – Ορισμός Λειτουργίας Ανάκτησης σε Java

Ποτέ προσπαθήσατε να ανοίξετε ένα κατεστραμμένο έγγραφο Word και παρακολουθήσατε το πρόγραμμα να αποτυγχάνει με μια εξαίρεση; Δεν είστε μόνοι—αυτά τα σπασμένα .docx αρχεία μπορούν να γίνουν πραγματικό κεφάλι‑πυρήνα. Τα καλά νέα είναι ότι το Aspose.Words for Java σας δίνει λεπτομερή έλεγχο ώστε να μπορείτε να **open corrupted word document** χωρίς να καταρρεύσει η εφαρμογή, και ακόμη να αποφασίσετε αν θέλετε προειδοποιήσεις, σιωπηλή ανάκτηση ή σκληρή απόρριψη.

Σε αυτό το tutorial θα περάσουμε από τη πλήρη διαδικασία: από τη δημιουργία του σωστού `LoadOptions`, μέχρι την επιλογή της κατάλληλης τιμής **set recovery mode**, και τέλος την επιβεβαίωση ότι το έγγραφο φορτώθηκε πράγματι. Στο τέλος θα γνωρίζετε **how to recover corrupted word file** προγραμματιστικά, χωρίς να χρειάζεται χειροκίνητη αντιγραφή‑επικόλληση.

> **Τι θα χρειαστείτε**  
> * Java 8 ή νεότερη (το API λειτουργεί επίσης με Java 11)  
> * Aspose.Words for Java 23.9 (ή την πιο πρόσφατη έκδοση)  
> * Ένα δείγμα κατεστραμμένου .docx αρχείου—απλώς μετονομάστε οποιοδήποτε έγκυρο αρχείο για να προσομοιώσετε τη ζημιά αν δεν έχετε κάποιο διαθέσιμο  

Ας βουτήξουμε.

## Άνοιγμα Κατεστραμμένου Εγγράφου Word – Επισκόπηση Βήμα‑προς‑Βήμα

Παρακάτω είναι η υψηλού επιπέδου ροή που θα υλοποιήσουμε:

1. **Create `LoadOptions`** – αυτό το αντικείμενο λέει στο Aspose.Words πώς να συμπεριφέρεται όταν αντιμετωπίζει προβλήματα.  
2. **Set recovery mode** – επιλέξτε `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS`, ή `REJECT_CORRUPTED`.  
3. **Load the document** χρησιμοποιώντας τις ρυθμισμένες επιλογές.  
4. **Verify** ότι η φόρτωση πέτυχε (π.χ., εκτυπώστε τον αριθμό σελίδων).  

Κάθε βήμα εξηγείται λεπτομερώς, με αποσπάσματα κώδικα που μπορείτε να αντιγράψετε‑επικολλήσετε απευθείας στο IDE σας.

## Ορισμός Λειτουργίας Ανάκτησης για Διαφορετικά Σενάρια

Το Aspose.Words ορίζει τρεις στρατηγικές ανάκτησης μέσα στο `LoadOptions.RecoveryMode`:

| Λειτουργία | Συμπεριφορά | Πότε να χρησιμοποιηθεί |
|------------|--------------|------------------------|
| `RECOVER_WITH_WARNINGS` | Προσπαθεί να φορτώσει το έγγραφο, αλλά εμφανίζει τυχόν προβλήματα ως προειδοποιήσεις στην κονσόλα. | Θέλετε να δείτε *τι* πήγε στραβά χωρίς να διακόψετε. |
| `RECOVER_WITHOUT_WARNINGS` | Διορθώνει σιωπηλά ό,τι μπορεί και καταστέλλει τις προειδοποιήσεις. | Περιβάλλοντα παραγωγής όπου τα αρχεία καταγραφής πρέπει να παραμένουν καθαρά. |
| `REJECT_CORRUPTED` | Ρίχνει εξαίρεση τη στιγμή που εντοπίζεται η ζημιά. | Ασυστηρές γραμμές επικύρωσης που πρέπει να αποτυγχάνουν γρήγορα. |

Η επιλογή της σωστής λειτουργίας είναι η ουσία του **set recovery mode** σωστά. Στις περισσότερες συνεδρίες εντοπισμού σφαλμάτων, το `RECOVER_WITH_WARNINGS` είναι η ιδανική επιλογή επειδή σας λέει ακριβώς ποια τμήματα διορθώθηκαν.

## Πώς να Ανακτήσετε Κατεστραμμένο Αρχείο Word Χρησιμοποιώντας Aspose.Words

Παρακάτω είναι ένα **πλήρες, εκτελέσιμο πρόγραμμα Java** που δείχνει όλη τη διαδικασία. Μη διστάσετε να το τοποθετήσετε σε ένα αρχείο `RecoveryModeDemo.java`, να προσαρμόσετε τη διαδρομή και να το εκτελέσετε.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Γιατί κάθε γραμμή είναι σημαντική

* **`LoadOptions loadOptions = new LoadOptions();`** – χωρίς αυτό το αντικείμενο το Aspose.Words χρησιμοποιεί την προεπιλεγμένη ανάκτηση, η οποία *απορρίπτει* τα κατεστραμμένα αρχεία. Η δημιουργία του σας δίνει το σημείο για να αλλάξετε αυτή τη συμπεριφορά.  
* **`setRecoveryMode(...)`** – αυτή είναι η κλήση **set recovery mode** που αποφασίζει αν εμφανίζονται προειδοποιήσεις, παραμένουν κρυφές, ή προκαλούν εξαίρεση.  
* **`new Document(path, loadOptions);`** – ο κατασκευαστής δέχεται το `LoadOptions` που μόλις διαμορφώσαμε, ώστε η βιβλιοθήκη να ξέρει πώς να αντιμετωπίσει το κατεστραμμένο αρχείο από την αρχή.  
* **`doc.getPageCount()`** – ένας γρήγορος έλεγχος λογικής. Αν το έγγραφο φορτωθεί και επιστρέψει αριθμό σελίδων, έχετε επιτυχώς **how to recover corrupted word file**.  
* **`doc.save(...)`** – προαιρετικό αλλά χρήσιμο· μπορείτε να γράψετε την επισκευασμένη έκδοση ξανά στο δίσκο για μελλοντική χρήση.  

## Διαχείριση Συνηθισμένων Ακραίων Περιπτώσεων

### 1. Αρχείο Δεν Βρέθηκε

Αν η διαδρομή είναι λανθασμένη, το `Document` ρίχνει `FileNotFoundException`. Τυλίξτε τη φόρτωση σε μπλοκ try‑catch και καταγράψτε ένα φιλικό μήνυμα:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Μη Ανακτήσιμη Ζημιά

Ακόμη και με `RECOVER_WITH_WARNINGS`, ορισμένες δομές είναι πέρα από την επισκευή. Σε αυτήν την περίπτωση το Aspose.Words φορτώνει ό,τι μπορεί, αλλά θα δείτε προειδοποιήσεις όπως «Cannot read paragraph properties». Δώστε προσοχή στην έξοδο της κονσόλας· αυτές οι προειδοποιήσεις συχνά δείχνουν σε ελλιπείς ενότητες που ίσως χρειαστεί να ανακατασκευάσετε χειροκίνητα.

### 3. Μεγάλα Αρχεία και Απόδοση

Η ανάκτηση προσθέτει μικρή επιβάρυνση επειδή η βιβλιοθήκη αναλύει το αρχείο δύο φορές—μία για την ανίχνευση προβλημάτων, άλλη για την επανακατασκευή. Για έγγραφα πολλαπλών γιγαμπάιτ, σκεφτείτε τη ροή του αρχείου ή την αύξηση του heap της JVM (`-Xmx2g`) για να αποφύγετε `OutOfMemoryError`.

## Pro Συμβουλές – Κατασκευή Ανθεκτικής Ανάκτησης

* **Log warnings to a file** – ανακατευθύνετε το `System.err` σε logger ώστε να έχετε ίχνος ελέγχου για ό,τι διορθώθηκε.  
* **Validate after recovery** – εκτελέστε `doc.updatePageLayout();` και μετά ελέγξτε ξανά τον αριθμό σελίδων· μερικές φορές η διάταξη αλλάζει μετά την επισκευή των σπασμένων ενοτήτων.  
* **Automate batch recovery** – τυλίξτε το demo σε βρόχο που επεξεργάζεται ένα φάκελο κατεστραμμένων αρχείων, χρησιμοποιώντας το ίδιο `LoadOptions` κάθε φορά.  

## Συμπέρασμα

Τώρα γνωρίζετε ακριβώς **how to recover corrupted word file** χρησιμοποιώντας το Aspose.Words for Java. Δημιουργώντας μια παρουσία `LoadOptions`, **set recovery mode** στη στρατηγική που ταιριάζει στο σενάριό σας, και φορτώνοντας το έγγραφο με αυτές τις επιλογές, μπορείτε με ασφάλεια **open corrupted word document** χωρίς να καταρρεύσει η εφαρμογή σας. Ο παραπάνω κώδικας είναι μια πλήρης, έτοιμη‑για‑εκτέλεση λύση που εκτυπώνει τον αριθμό σελίδων και ακόμη αποθηκεύει ένα καθαρισμένο αντίγραφο.

Τι ακολουθεί; Δοκιμάστε να αλλάξετε τη λειτουργία ανάκτησης σε `RECOVER_WITHOUT_WARNINGS` και συγκρίνετε την έξοδο της κονσόλας, ή πειραματιστείτε με τη φόρτωση κρυπτογραφημένων εγγράφων (θα χρειαστεί να παρέχετε έναν κωδικό πρόσβασης μέσω

## Σχετικά Μαθήματα

- [Aspose.Words Java: Ολοκληρωμένος Οδηγός Επεξεργασίας Εγγράφων Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Πώς να Μετατρέψετε Word σε PDF Χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [Πώς να Συγκρίνετε Δύο Αρχεία Word με Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}