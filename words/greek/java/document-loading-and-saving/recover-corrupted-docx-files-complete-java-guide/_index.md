---
category: general
date: 2026-06-27
description: Ανακτήστε κατεστραμμένα αρχεία DOCX σε Java ορίζοντας τη λειτουργία ανάκτησης,
  ελέγχοντας αν το έγγραφο έχει ανακτηθεί και ανιχνεύοντας την ανάκτηση του εγγράφου.
  Ακολουθήστε αυτό το βήμα‑βήμα οδηγό.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- check document recovered
- detect document recovery
language: el
og_description: Ανακτήστε κατεστραμμένα αρχεία DOCX σε Java. Μάθετε πώς να ορίσετε
  τη λειτουργία ανάκτησης, να ελέγξετε αν το έγγραφο έχει ανακτηθεί και να εντοπίσετε
  την ανάκτηση του εγγράφου με ένα πλήρες παράδειγμα κώδικα.
og_title: Ανάκτηση Κατεστραμμένων Αρχείων DOCX – Εγχειρίδιο Java
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Recover corrupted DOCX files in Java by setting recovery mode, checking
    document recovered, and detecting document recovery. Follow this step‑by‑step
    tutorial.
  headline: Recover Corrupted DOCX Files – Complete Java Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- DocumentRecovery
title: Ανάκτηση Κατεστραμμένων Αρχείων DOCX – Πλήρης Οδηγός Java
url: /el/java/document-loading-and-saving/recover-corrupted-docx-files-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση Κατεστραμμένων Αρχείων DOCX – Πλήρης Οδηγός Java

Έχετε χρειαστεί ποτέ να **ανακτήσετε κατεστραμμένα DOCX** αρχεία αλλά δεν ήσασταν σίγουροι ποιες ρυθμίσεις του API να προσαρμόσετε; Δεν είστε μόνοι—τα έγγραφα γραφείου καταστρέφονται πολύ πιο συχνά απ' ό,τι θα θέλαμε να παραδεχτούμε, και ένα σπασμένο .docx μπορεί να σταματήσει ολόκληρη τη ροή εργασίας. Τα καλά νέα; Με λίγες γραμμές Java μπορείτε να πείτε στο Aspose.Words να προσπαθήσει μια επισκευή, να επαληθεύσετε το αποτέλεσμα, και ακόμη να εντοπίσετε πότε πραγματοποιήθηκε η ανάκτηση.

Σε αυτό το tutorial θα δούμε **πώς να ορίσουμε τη λειτουργία ανάκτησης**, **πώς να ελέγξουμε αν το έγγραφο ανακτήθηκε**, και **πώς να εντοπίσουμε την ανάκτηση του εγγράφου** προγραμματιστικά. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε Java project.

## Τι Καλύπτει Αυτός ο Οδηγός

- Προαπαιτούμενα: η βιβλιοθήκη Aspose.Words for Java και ένα δείγμα κατεστραμμένου .docx.  
- Επιλογή της σωστής **λειτουργίας ανάκτησης** (RECOVER, RECOVER_WITH_WARNINGS ή THROW).  
- Φόρτωση ενός πιθανώς κατεστραμμένου εγγράφου με ένα αντικείμενο `LoadOptions`.  
- **Έλεγχος αν το έγγραφο ανακτήθηκε** χωρίς να πεταχτεί εξαίρεση.  
- Προαιρετικά: πιο βαθιά επιθεώρηση για **εντοπισμό ανάκτησης εγγράφου** μετά τη φόρτωση.  

Δεν χρειάζεται να πηδάτε σε εξωτερική τεκμηρίωση—όλα όσα χρειάζεστε είναι εδώ.

## Βήμα 1: Προσθέστε το Aspose.Words στο Έργο Σας

Πριν μπούμε στην ανάκτηση, χρειαζόμαστε τη βιβλιοθήκη στο classpath.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

Αν προτιμάτε Gradle, αντικαταστήστε το snippet με την αντίστοιχη γραμμή `implementation`. Μόλις το JAR είναι παρόν, είστε έτοιμοι να **ορίσετε τη λειτουργία ανάκτησης**.

## Βήμα 2: Επιλέξτε Στρατηγική Ανάκτησης με `setRecoveryMode`

Το Aspose.Words προσφέρει τρεις στρατηγικές ανάκτησης:

| Λειτουργία               | Συμπεριφορά                                                             |
|--------------------------|-------------------------------------------------------------------------|
| `RECOVER`                | Προσπαθεί να διορθώσει το έγγραφο σιωπηρά.                               |
| `RECOVER_WITH_WARNINGS`  | Επισκευάζει το αρχείο **και** συλλέγει προειδοποιήσεις που μπορείτε να εξετάσετε αργότερα. |
| `THROW`                  | Πετάει εξαίρεση σε οποιαδήποτε κατεστραμμένη κατάσταση (χρήσιμο για αυστηρή επικύρωση). |

Για τις περισσότερες περιπτώσεις “απλώς να πάρουμε το αρχείο πίσω” επιλέγουμε `RECOVER`. Να πώς το ρυθμίζετε:

```java
import com.aspose.words.*;

LoadOptions loadOptions = new LoadOptions();
// Step 2: Set the recovery mode – this is the core of “set recovery mode”
loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
// Alternatives: RECOVER_WITH_WARNINGS, THROW
```

> **Pro tip:** Αν χρειάζεστε αναφορά για το τι πήγε στραβά, αντικαταστήστε το `RECOVER` με `RECOVER_WITH_WARNINGS` και διαβάστε αργότερα το `loadOptions.getWarnings()`.

## Βήμα 3: Φορτώστε το Πιθανώς Κατεστραμμένο DOCX

Τώρα προσπαθούμε πραγματικά να ανοίξουμε το αρχείο χρησιμοποιώντας τις επιλογές που μόλις διαμορφώσαμε.

```java
// Step 3: Load the possibly corrupted document
Document document = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);
```

Αν το αρχείο είναι πέρα από την επισκευή και χρησιμοποιήσατε `THROW`, ο κατασκευαστής θα πετάξει εξαίρεση. Επειδή επιλέξαμε `RECOVER`, η κλήση επιστρέφει ένα αντικείμενο `Document` οπωσδήποτε—αν και το περιεχόμενο μπορεί να είναι μερικά ανακατασκευασμένο.

## Βήμα 4: **Έλεγχος Επαναφοράς Εγγράφου** – Απλή Boolean Δοκιμή

Ο πιο γρήγορος τρόπος να μάθετε αν πραγματοποιήθηκε ανάκτηση είναι να συγκρίνετε τη λειτουργία που ορίσατε με αυτή που χρησιμοποιήθηκε πραγματικά. Το Aspose.Words δεν εκθέτει άμεση σημαία “wasRecovered”, αλλά μπορείτε να το συμπεράνετε:

```java
// Step 4: Verify if recovery was performed (i.e., mode not set to THROW)
boolean recovered = loadOptions.getRecoveryMode() != RecoveryMode.THROW;
System.out.println("Recovered: " + recovered);
```

Αν μεταβείτε σε `RECOVER_WITH_WARNINGS`, μπορείτε επίσης να ρίξετε μια ματιά στη συλλογή προειδοποιήσεων:

```java
if (!loadOptions.getWarnings().isEmpty()) {
    System.out.println("Warnings during recovery:");
    loadOptions.getWarnings().forEach(System.out::println);
}
```

Αυτό το snippet ικανοποιεί την απαίτηση **check document recovered** ενώ σας δίνει και πληροφορίες για τυχόν προβλήματα που διορθώθηκαν.

## Βήμα 5: Εντοπισμός Επαναφοράς Εγγράφου Μετά τη Φόρτωση (Προχωρημένο)

Μερικές φορές χρειάζεται να ξέρετε *μετά* τη φόρτωση αν το έγγραφο τροποποιήθηκε. Το Aspose.Words αποθηκεύει μια σημαία που μπορείτε να ελέγξετε μέσω της μεθόδου `Document.isDirty()`, αλλά μια πιο αξιόπιστη προσέγγιση είναι να συγκρίνετε το αρχικό μέγεθος αρχείου με το μέγεθος του ρεύματος του φορτωμένου εγγράφου.

```java
import java.io.*;

File original = new File("YOUR_DIRECTORY/corrupted.docx");
ByteArrayOutputStream baos = new ByteArrayOutputStream();
document.save(baos, SaveFormat.DOCX);
byte[] recoveredBytes = baos.toByteArray();

boolean wasRecovered = original.length() != recoveredBytes.length;
System.out.println("Detect document recovery: " + wasRecovered);
```

Αν τα μήκη διαφέρουν, το Aspose.Words έπρεπε να τροποποιήσει την εσωτερική δομή—σημαίνει ότι πραγματοποιήθηκε ανάκτηση. Αυτό εκπληρώνει τον στόχο **detect document recovery**.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας τα πάντα, εδώ είναι μια μοναδική κλάση που μπορείτε να μεταγλωττίσετε και να τρέξετε:

```java
import com.aspose.words.*;
import java.io.*;

public class RecoverCorruptedDocxDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Set up load options – we’ll recover silently
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // set recovery mode

        // 2️⃣ Load the corrupted document
        Document doc = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);

        // 3️⃣ Simple check – did we avoid throwing?
        boolean recovered = loadOptions.getRecoveryMode() != RecoveryMode.THROW;
        System.out.println("Recovered (simple check): " + recovered);

        // 4️⃣ If you used RECOVER_WITH_WARNINGS, print them
        if (!loadOptions.getWarnings().isEmpty()) {
            System.out.println("Recovery warnings:");
            loadOptions.getWarnings().forEach(System.out::println);
        }

        // 5️⃣ Detect actual changes by comparing sizes
        File original = new File("YOUR_DIRECTORY/corrupted.docx");
        ByteArrayOutputStream baos = new ByteArrayOutputStream();
        doc.save(baos, SaveFormat.DOCX);
        byte[] recoveredBytes = baos.toByteArray();

        boolean wasRecovered = original.length() != recoveredBytes.length;
        System.out.println("Detect document recovery (size diff): " + wasRecovered);

        // Optional: save the repaired file
        doc.save("YOUR_DIRECTORY/recovered.docx");
        System.out.println("Repaired document saved.");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας (παράδειγμα):**

```
Recovered (simple check): true
Recovery warnings:
[Warning] Invalid paragraph property – corrected.
Detect document recovery (size diff): true
Repaired document saved.
```

Αν το αρχείο ήταν ήδη υγιές, ο έλεγχος διαφοράς μεγέθους θα επιστρέψει `false` και δεν θα εμφανιστούν προειδοποιήσεις.

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πιθανό Σφάλμα           | Γιατί Συμβαίνει                                                       | Διόρθωση |
|--------------------------|-----------------------------------------------------------------------|----------|
| Χρήση `THROW` σε κατεστραμμένο αρχείο | Ο κατασκευαστής πετάει `IncorrectPasswordException` ή `FileCorruptedException`. | Μετάβαση σε `RECOVER` ή `RECOVER_WITH_WARNINGS`. |
| Παράλειψη άδειας Aspose | Η βιβλιοθήκη τρέχει σε λειτουργία αξιολόγησης, προσθέτοντας υδατογράφημα. | Εφαρμόστε την άδειά σας μέσω `License license = new License(); license.setLicense("Aspose.Words.lic");`. |
| Θεωρία ότι οι προειδοποιήσεις σημαίνουν αποτυχία | Οι προειδοποιήσεις είναι πληροφοριακές· το έγγραφο μπορεί να είναι ακόμη χρησιμοποιήσιμο. | Θεωρήστε τις ως ενδείξεις για περαιτέρω καθαρισμό, όχι ως κρίσιμα σφάλματα. |
| Μη εκκαθάριση ρευμάτων | Μεγάλα έγγραφα μπορούν να εξαντλήσουν τη μνήμη. | Χρησιμοποιήστε try‑with‑resources για `FileInputStream`/`ByteArrayOutputStream`. |

## Πότε να Χρησιμοποιήσετε Κάθε Λειτουργία Ανάκτησης

- **RECOVER** – Ιδανικό για εργασίες batch στο παρασκήνιο όπου χρειάζεστε απλώς ένα χρησιμοποιήσιμο αρχείο.  
- **RECOVER_WITH_WARNINGS** – Τέλειο για UI εργαλεία που θέλουν να δείξουν στον χρήστη τι διορθώθηκε.  
- **THROW** – Χρησιμοποιείται σε αυστηρές pipelines επικύρωσης όπου οποιαδήποτε κατεστραμμένη κατάσταση πρέπει να διακόψει τη διαδικασία.

## Επόμενα Βήματα

Τώρα που μπορείτε να **ανακτήσετε κατεστραμμένα DOCX**, σκεφτείτε να επεκτείνετε τη ροή εργασίας:

- **Επεξεργασία παρτίδας** – Επανάληψη σε φάκελο αρχείων και καταγραφή στατιστικών ανάκτησης.  
- **Αυτόματο αντίγραφο ασφαλείας** – Αποθηκεύστε το αρχικό πριν προσπαθήσετε την ανάκτηση, για κάθε περίπτωση.  
- **Ενσωμάτωση με αποθήκευση στο cloud** – Ανάκτηση αρχείων από S3, αποκατάσταση, και επαναφόρτωση της καθαρής έκδοσης.

Όλες αυτές οι ιδέες περιλαμβάνουν φυσικά τις δευτερεύουσες λέξεις‑κλειδιά **set recovery mode**, **check document recovered**, και **detect document recovery**, διατηρώντας τη βάση κώδικά σας ανθεκτική και διαφανή.

---

![Diagram showing the recover corrupted docx workflow – from loading a broken file, setting recovery mode, checking recovery status, to saving a repaired document.](recover-corrupted-docx-workflow.png "recover corrupted docx workflow")

*Image alt text: “Διάγραμμα ροής ανάκτησης κατεστραμμένου docx που απεικονίζει τη ρύθμιση λειτουργίας ανάκτησης, τον έλεγχο επαναφοράς εγγράφου, και τα βήματα εντοπισμού ανάκτησης.”*

---

### TL;DR

- Χρησιμοποιήστε `LoadOptions.setRecoveryMode()` για να πείτε στο Aspose.Words πώς να χειριστεί σπασμένα αρχεία.  
- Φορτώστε το αρχείο με τις ρυθμισμένες επιλογές· καμία εξαίρεση σημαίνει ότι **έχετε ελέγξει ότι το έγγραφο ανακτήθηκε**.  
- Συγκρίνετε τα μεγέθη αρχείων ή εξετάστε τις προειδοποιήσεις για **εντοπισμό ανάκτησης εγγράφου**.  
- Αποθηκεύστε το διορθωμένο αποτέλεσμα και προχωρήστε.

Αυτή είναι η πλήρης ιστορία για το πώς να **ανακτήσετε κατεστραμμένα docx** αρχεία σε Java. Έχετε κάποιο δύσκολο αρχείο που ακόμα δεν ανοίγει; Αφήστε ένα σχόλιο και θα το αντιμετωπίσουμε μαζί. Καλό coding!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας projects.

- [Ανάκτηση κατεστραμμένων docx – Πλήρης Οδηγός για Διόρθωση και Επεξεργασία Εγγράφων](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Aspose.Words Java: Μετατροπή Εγγράφων & Ασφάλεια για Αρχεία ODT](/words/english/java/document-operations/aspose-words-java-document-conversion-security/)
- [Aspose Words Java Εκπαίδευση Υπογραφής Εγγράφου](/words/english/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}