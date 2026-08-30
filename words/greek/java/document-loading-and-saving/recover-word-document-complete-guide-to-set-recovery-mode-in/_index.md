---
category: general
date: 2026-04-28
description: Ανακτήστε γρήγορα το έγγραφο Word ορίζοντας τη λειτουργία ανάκτησης.
  Μάθετε βήμα‑βήμα πώς να ορίσετε τη λειτουργία ανάκτησης και να διαχειριστείτε τις
  προειδοποιήσεις στην Java.
draft: false
keywords:
- recover word document
- set recovery mode
- document warnings
- Aspose.Words Java
- corrupted DOCX handling
language: el
og_description: Ανακτήστε έγγραφο Word ορίζοντας τη λειτουργία ανάκτησης στη Java.
  Αυτός ο οδηγός σας δείχνει τα ακριβή βήματα, τον κώδικα και συμβουλές για την καταγραφή
  προειδοποιήσεων.
og_title: Ανάκτηση εγγράφου Word – Πώς να ορίσετε τη λειτουργία ανάκτησης σε Java
tags:
- Java
- Aspose.Words
- Document Recovery
title: Ανάκτηση εγγράφου Word – Πλήρης οδηγός για τον καθορισμό της λειτουργίας ανάκτησης
  σε Java
url: /el/java/document-loading-and-saving/recover-word-document-complete-guide-to-set-recovery-mode-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση Εγγράφου Word – Πλήρης Οδηγός για Ορισμό Λειτουργίας Ανάκτησης σε Java

Έχετε ποτέ βρεθεί να κοιτάζετε ένα **κατεστραμμένο .docx** αρχείο και να αναρωτιέστε αν μπορείτε ακόμη να σώσετε το περιεχόμενο; Είναι ένας κοινός εφιάλτης για όποιον εργάζεται προγραμματιστικά με έγγραφα Word. Τα καλά νέα; Μπορείτε να **recover word document** αρχεία απλώς ρυθμίζοντας τη σωστή λειτουργία ανάκτησης. Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα πώς να **set recovery mode** χρησιμοποιώντας το Aspose.Words for Java, να συλλάβουμε τυχόν προειδοποιήσεις και να καταλήξουμε σε ένα χρησιμοποιήσιμο έγγραφο.

Θα καλύψουμε τα πάντα, από την μικρή εισαγωγή που χρειάζεστε, μέσω του τρι‑βήματος κώδικα, μέχρι συμβουλές για τη διαχείριση ακραίων περιπτώσεων όπως μεγάλα αρχεία ή ελλιπείς γραμματοσειρές. Στο τέλος θα μπορείτε να ανοίξετε ένα κατεστραμμένο DOCX, να αποφασίσετε αν θέλετε να εμφανίζονται προειδοποιήσεις και να αποτρέψετε την κατάρρευση της εφαρμογής σας. Χωρίς επιπλέον εργαλεία, χωρίς χειροκίνητο copy‑pasting—απλός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο.

> **Prerequisites**: Java 8 ή νεότερη, Maven ή Gradle, και άδεια Aspose.Words for Java (ή δωρεάν δοκιμή). Αν δεν έχετε χρησιμοποιήσει ποτέ το Aspose.Words, μην ανησυχείτε—αυτός ο οδηγός υποθέτει μόνο βασικές γνώσεις Java.

---

## Τι Θα Επιτύχετε

- **Recover a Word document** που διαφορετικά θα έριχνε εξαίρεση.
- **Set recovery mode** ώστε είτε να εμφανίζονται προειδοποιήσεις είτε να αγνοούνται σιωπηλά.
- Επανάληψη πάνω σε αντικείμενα `WarningInfo` για καταγραφή ή εμφάνιση προβλημάτων.
- Κατανόηση πότε να επιλέξετε `RECOVER_WITH_WARNINGS` έναντι `RECOVER_WITHOUT_WARNINGS`.

---

![παράδειγμα ανάκτησης εγγράφου word](https://example.com/images/recover-word-document.png "παράδειγμα ανάκτησης εγγράφου word")

---

## Βήμα 1: Προετοιμάστε το Έργο σας και Εισάγετε τις Κλάσεις

Πριν μπορέσετε να **set recovery mode**, χρειάζεστε τη βιβλιοθήκη Aspose.Words στο classpath σας. Αν χρησιμοποιείτε Maven, προσθέστε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<!-- Maven dependency for Aspose.Words for Java -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Για Gradle, είναι ως εξής:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Μόλις η βιβλιοθήκη είναι στη θέση της, εισάγετε τις κλάσεις που θα χρειαστείτε:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.RecoveryMode;
import com.aspose.words.WarningInfo;
```

> **Pro tip**: Διατηρήστε την έκδοση του Aspose.Words ενημερωμένη. Οι νέες εκδόσεις συχνά βελτιώνουν τους αλγόριθμους ανάκτησης για τις πιο πρόσφατες μορφές Word.

---

## Βήμα 2: Διαμορφώστε το LoadOptions για να Ορίσετε τη Λειτουργία Ανάκτησης

Η καρδιά της λογικής **recover word document** βρίσκεται στο `LoadOptions`. Ρυθμίζοντας την ιδιότητα `RecoveryMode` ελέγχετε πόσο επιθετικός θα είναι ο parser όταν αντιμετωπίζει κατεστραμμένα δεδομένα.

```java
// Step 2: Configure load options to recover the document and capture warnings
LoadOptions loadOptions = new LoadOptions();
loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS); // or RECOVER_WITHOUT_WARNINGS
```

### Γιατί να Επιλέξετε τη Μία Λειτουργία έναντι της Άλλης;

- **RECOVER_WITH_WARNINGS** – Ο φορτωτής προσπαθεί να διορθώσει τα προβλήματα *και* επιστρέφει μια λίστα αντικειμένων `WarningInfo`. Ιδανικό όταν θέλετε να καταγράψετε τι πήγε στραβά.
- **RECOVER_WITHOUT_WARNINGS** – Πιο γρήγορο, αλλά χάνετε την εικόνα των προβλημάτων. Χρησιμοποιήστε το για επεξεργασία παρτίδας όπου η απόδοση υπερισχύει της διάγνωσης.

Αν δεν είστε σίγουροι, ξεκινήστε με `RECOVER_WITH_WARNINGS`; μπορείτε πάντα να αλλάξετε αργότερα.

---

## Βήμα 3: Φορτώστε το Κατεστραμμένο Έγγραφο

Τώρα που η λειτουργία ανάκτησης έχει οριστεί, μπορείτε με ασφάλεια να φορτώσετε ένα πιθανώς κατεστραμμένο αρχείο. Ο κατασκευαστής `Document` είτε θα σας δώσει ένα χρησιμοποιήσιμο αντικείμενο είτε θα ρίξει εξαίρεση αν το αρχείο είναι πέρα από την επισκευή.

```java
// Step 3: Load the (possibly corrupted) document using the configured options
String filePath = "YOUR_DIRECTORY/corrupted.docx";
Document document = new Document(filePath, loadOptions);
```

### Συνηθισμένες Παγίδες

- **Λάθος διαδρομή** – Ελέγξτε ξανά ότι το `filePath` δείχνει στην ακριβή θέση. Οι σχετικές διαδρομές λειτουργούν, αλλά οι απόλυτες διαδρομές αφαιρούν την αβεβαιότητα.
- **Ανεπαρκής μνήμη** – Πολύ μεγάλα αρχεία DOCX μπορεί να απαιτούν περισσότερη heap μνήμη. Εκτελέστε το JVM σας με `-Xmx2g` ή περισσότερο αν αντιμετωπίσετε `OutOfMemoryError`.

---

## Βήμα 4: Εξετάστε και Εκτυπώστε τυχόν Προειδοποιήσεις

Αν επιλέξατε `RECOVER_WITH_WARNINGS`, το Aspose.Words γεμίζει μια συλλογή που μπορείτε να επαναλάβετε. Εδώ είναι που πραγματικά αποκτάτε **recover word document** πληροφορίες.

```java
// Step 4: Inspect and print any warnings that were generated during loading
for (WarningInfo warning : document.getWarnings()) {
    System.out.println("Warning: " + warning.getDescription());
}
```

Τυπικές προειδοποιήσεις περιλαμβάνουν:

- *«Λείπουν δεδομένα εικόνας – η εικόνα θα παραλειφθεί.»*
- *«Μη υποστηριζόμενο στοιχείο OpenXML – αγνοήθηκε.»*
- *«Κατεστραμμένη δομή πίνακα – οι γραμμές μπορεί να έχουν αναδιαταχθεί.»*

Μπορείτε να καταγράψετε αυτές τις προειδοποιήσεις σε αρχείο, να τις στείλετε σε υπηρεσία παρακολούθησης ή απλώς να τις εμφανίσετε στην κονσόλα για εντοπισμό σφαλμάτων.

---

## Βήμα 5: Αποθηκεύστε το Ανακτημένο Έγγραφο (Προαιρετικό)

Αφού εξετάσετε τις προειδοποιήσεις, ίσως θέλετε να γράψετε το διορθωμένο έγγραφο πίσω στο δίσκο. Αυτό το βήμα είναι προαιρετικό αλλά συχνά χρήσιμο για επεξεργασία downstream.

```java
// Optional: Save the recovered document to a new file
String outputPath = "YOUR_DIRECTORY/recovered.docx";
document.save(outputPath);
System.out.println("Recovered document saved to " + outputPath);
```

Αν το αρχικό αρχείο ήταν σοβαρά κατεστραμμένο, η αποθηκευμένη έκδοση συνήθως θα είναι πιο καθαρή—οι ελλιπείς εικόνες μπορεί να λείπουν, αλλά το κειμενικό περιεχόμενο παραμένει άθικτο.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη μέθοδος `main` που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια νέα κλάση Java με όνομα `RecoverDocx.java`.

```java
import com.aspose.words.*;

public class RecoverDocx {
    public static void main(String[] args) {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputPath = "YOUR_DIRECTORY/recovered.docx";

        try {
            // 1️⃣ Configure LoadOptions – this is where we set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);

            // 2️⃣ Load the potentially corrupted document
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Print any warnings that occurred during loading
            System.out.println("=== Recovery Warnings ===");
            for (WarningInfo warning : doc.getWarnings()) {
                System.out.println("- " + warning.getDescription());
            }

            // 4️⃣ Save the recovered file (optional but recommended)
            doc.save(outputPath);
            System.out.println("✅ Document recovered and saved to: " + outputPath);
        } catch (Exception e) {
            // If the file is beyond repair, Aspose.Words will throw an exception
            System.err.println("Failed to recover the document: " + e.getMessage());
        }
    }
}
```

### Αναμενόμενη Έξοδος

```
=== Recovery Warnings ===
- Missing image data – image will be omitted.
- Unsupported OpenXML element – ignored.
✅ Document recovered and saved to: YOUR_DIRECTORY/recovered.docx
```

Αν το αρχείο δεν μπορεί να σωθεί, θα δείτε ένα μήνυμα σφάλματος αντί για τη λίστα προειδοποιήσεων.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### 1. Τι γίνεται αν δεν έχω άδεια;

Το Aspose.Words λειτουργεί σε λειτουργία αξιολόγησης, αλλά προσθέτει υδατογράφημα στην έξοδο. Για παραγωγική χρήση, αποκτήστε άδεια ώστε να αφαιρέσετε το υδατογράφημα και να ξεκλειδώσετε πλήρεις δυνατότητες ανάκτησης.

### 2. Μπορώ να ανακτήσω παλαιότερα αρχεία `.doc` με τον ίδιο τρόπο;

Ναι. Τα ίδια `LoadOptions` και `RecoveryMode` ισχύουν για `.doc`, `.docx` και ακόμη και `.rtf`. Απλώς αλλάξτε την επέκταση του αρχείου στη διαδρομή.

### 3. Πώς επηρεάζει το `setRecoveryMode` την απόδοση;

Το `RECOVER_WITH_WARNINGS` εκτελεί μερικούς επιπλέον ελέγχους για τη συλλογή διαγνωστικών πληροφοριών, οπότε είναι ελαφρώς πιο αργό—συνήθως μερικά χιλιοστά του δευτερολέπτου σε τυπικό αρχείο. Για μαζική επεξεργασία, μεταβείτε σε `RECOVER_WITHOUT_WARNINGS` αφού επαληθεύσετε ότι οι προειδοποιήσεις δεν χρειάζονται.

### 4. Τι γίνεται αν το έγγραφο περιέχει προσαρμοσμένα XML μέρη;

Το Aspose.Words θα προσπαθήσει να διατηρήσει το προσαρμοσμένο XML, αλλά τα κατεστραμμένα τμήματα μπορεί να απορριφθούν. Μπορείτε να ανακτήσετε αυτά τα τμήματα μέσω `Document.getCustomXmlParts()` μετά τη φόρτωση για να ελέγξετε την ακεραιότητα.

### 5. Υπάρχει τρόπος να αποφασίσω προγραμματιστικά ποια λειτουργία να χρησιμοποιήσω;

Απολύτως. Μπορείτε πρώτα να δοκιμάσετε τη φόρτωση με `RECOVER_WITHOUT_WARNINGS`. Αν προκύψει εξαίρεση, ξαναδοκιμάστε με `RECOVER_WITH_WARNINGS` για να πάρετε περισσότερη εικόνα.

```java
try {
    Document doc = new Document(inputPath);
} catch (Exception ex) {
    // Fallback to warnings mode
    LoadOptions opts = new LoadOptions();
    opts.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
    Document doc = new Document(inputPath, opts);
    // handle warnings...
}
```

---

## Καλές Πρακτικές για Αξιόπιστη Ανάκτηση Εγγράφων

- **Πάντα καταγράφετε τις προειδοποιήσεις**: Ακόμα και αν τις θεωρείτε ακίνδυνες, μελλοντικά σφάλματα συχνά εντοπίζονται από αγνοημένες προειδοποιήσεις.
- **Επικυρώστε το αποτέλεσμα**: Μετά την αποθήκευση, ανοίξτε το αρχείο σε Microsoft Word (ή LibreOffice) για να βεβαιωθείτε ότι εμφανίζεται όπως αναμένεται.
- **Διαχειριστείτε μεγάλα αρχεία**: Αυξήστε το μέγεθος heap του JVM (`-Xmx`) και σκεφτείτε τη ροή του εγγράφου αν η μνήμη γίνει bottleneck.
- **Διατηρήστε το Aspose.Words ενημερωμένο**: Οι νέες εκδόσεις βελτιώνουν τη μηχανή ανάκτησης για τις πιο πρόσφατες μορφές Office.

---

## Συμπέρασμα

Δείξαμε πώς να **recover word document** αρχεία σε Java ρυθμίζοντας σωστά το **set recovery mode** και διαχειριζόμενοι τυχόν προειδοποιήσεις που προκύπτουν. Η διαδικασία είναι απλή: διαμορφώστε το `LoadOptions`, φορτώστε το αρχείο, ελέγξτε τις προειδοποιήσεις και, προαιρετικά, αποθηκεύστε το καθαρό αποτέλεσμα. Με αυτά τα βήματα θα αποφύγετε καταρρεύσεις, θα αποκτήσετε ορατότητα στα προβλήματα κατεστραμμένων αρχείων και θα διατηρήσετε τις επεξεργαστικές σας γραμμές σε άριστη κατάσταση.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να συνδυάσετε αυτήν την τεχνική με έναν επεξεργαστή παρτίδας που σαρώνει έναν φάκελο DOCX, καταγράφει όλες τις προειδοποιήσεις σε CSV και μεταφέρει τα ακατάλληλα αρχεία σε κατάλογο απομόνωσης. Ή εξερευνήστε τις πιο πλούσιες δυνατότητες του Aspose.Words—όπως εξαγωγή κειμένου, μετατροπή σε PDF ή προγραμματιστική διόρθωση κοινών προβλημάτων όπως ελλιπείς μορφές.

Αν έχετε ερωτήσεις, αφήστε σχόλιο παρακάτω ή ρίξτε μια ματιά στην τεκμηρίωση Aspose.Words Java για πιο βαθιές πληροφορίες σχετικά με `RecoveryMode` και `WarningInfo`. Καλό coding, και οι έγγραφές σας να παραμείνουν πάντα ανακτήσιμες!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}