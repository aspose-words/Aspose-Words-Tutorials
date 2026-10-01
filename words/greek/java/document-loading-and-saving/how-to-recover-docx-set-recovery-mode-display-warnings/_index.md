---
category: general
date: 2026-03-04
description: Πώς να ανακτήσετε αρχεία DOCX χρησιμοποιώντας Java – μάθετε πώς να ορίσετε
  τη λειτουργία ανάκτησης και να εμφανίσετε προειδοποιήσεις φόρτωσης για κατεστραμμένα
  έγγραφα σε λίγα εύκολα βήματα.
draft: false
keywords:
- how to recover docx
- set recovery mode
- use recovery mode
- recover corrupted docx
- display load warnings
language: el
og_description: How to recover DOCX files using Java. This guide shows how to set
  recovery mode and display load warnings when loading corrupted documents.
og_title: Πώς να ανακτήσετε DOCX – Ορίστε τη λειτουργία ανάκτησης & εμφανίστε προειδοποιήσεις
tags:
- Java
- Aspose.Words
- Document Recovery
title: Πώς να ανακτήσετε DOCX – Ορίστε τη λειτουργία ανάκτησης & εμφανίστε προειδοποιήσεις
url: /el/java/document-loading-and-saving/how-to-recover-docx-set-recovery-mode-display-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε DOCX – Ορίστε τη Λειτουργία Ανάκτησης & Εμφανίστε Προειδοποιήσεις

Έχετε ανοίξει ποτέ ένα αρχείο **DOCX** μόνο για να δείτε ακατάληπτο κείμενο ή ένα ελλιπές παράγραφο; Αυτή είναι η στιγμή που αρχίζετε να αναρωτιέστε *πώς να ανακτήσετε docx* αρχεία χωρίς να χάσετε ώρες εργασίας. Τα καλά νέα είναι ότι το Aspose.Words for Java σας παρέχει μια ενσωματωμένη λειτουργία ανάκτησης που μπορεί να εντοπίσει προβλήματα, να διατηρήσει τα καλά τμήματα και ακόμη να σας πει τι πήγε στραβά.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για **set recovery mode**, **use recovery mode** κατά τη φόρτωση ενός κατεστραμμένου εγγράφου, και **display load warnings** ώστε να ξέρετε ακριβώς τι επισκευάστηκε. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση snippet που ανακτά ένα σπασμένο DOCX και σας λέει πόσες προειδοποιήσεις δημιουργήθηκαν.

> **Prerequisite:** Χρειάζεστε Aspose.Words for Java (v23.9 ή νεότερη) στο classpath σας. Αν δεν το έχετε ακόμη, πάρτε το Maven artifact `com.aspose:aspose-words:23.9` ή κατεβάστε το JAR από την ιστοσελίδα της Aspose.

![how to recover docx](/images/recover-docx.png)

---

## Τι Καλύπτει Αυτός Ο Οδηγός

* Πώς να διαμορφώσετε το **LoadOptions** για να ελέγξετε τη συμπεριφορά ανάκτησης.  
* Η διαφορά μεταξύ `RECOVER_WITH_WARNINGS` και `RECOVER_SILENTLY`.  
* Πώς να **display load warnings** μετά το άνοιγμα του εγγράφου.  
* Ένα πλήρες, εκτελέσιμο πρόγραμμα Java που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας.

Ας βουτήξουμε — χωρίς περιττές πληροφορίες, μόνο το ουσιώδες.

---

## Βήμα 1: Προετοιμασία Load Options – Επιλέξτε τη Σωστή Λειτουργία Ανάκτησης

Πριν αγγίξετε το αρχείο, πρέπει να πείτε στο Aspose.Words πώς να συμπεριφερθεί όταν συναντήσει κατεστραμμένα δεδομένα. Εδώ έρχεται το **set recovery mode**.

```java
import com.aspose.words.LoadOptions;
import com.aspose.words.LoadOptions.RecoveryMode;

// Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Choose a recovery strategy
// 1️⃣ Recover with warnings – you’ll get a list of issues.
// 2️⃣ Recover silently – the library fixes everything quietly.
loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
// Or, if you prefer no output:
// loadOptions.setRecoveryMode(RecoveryMode.RECOVER_SILENTLY);
```

*Γιατί είναι σημαντικό:* `RECOVER_WITH_WARNINGS` είναι ιδανικό όταν χρειάζεται να ελέγξετε τη διαδικασία διόρθωσης, ενώ `RECOVER_SILENTLY` είναι χρήσιμο για batch jobs όπου δεν θέλετε θόρυβο στην κονσόλα.

---

## Βήμα 2: Φόρτωση του Κατεστραμμένου DOCX Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Τώρα που οι **load options** είναι έτοιμες, το άνοιγμα του αρχείου γίνεται παιχνιδάκι. Παρατηρήστε πώς περνάμε το αντικείμενο `loadOptions` στον κατασκευαστή `Document` — αυτό είναι το βήμα **use recovery mode**.

```java
import com.aspose.words.Document;

// Path to the potentially corrupted file
String corruptedPath = "C:/Docs/corrupted.docx";

// Load the document with the previously defined options
Document document = new Document(corruptedPath, loadOptions);
```

Αν το αρχείο είναι πέρα από την επισκευή, το Aspose.Words θα ρίξει ακόμα ένα `FileCorruptedException`. Στις περισσότερες πραγματικές περιπτώσεις, όμως, η βιβλιοθήκη διασώζει τα αναγνώσιμα τμήματα και σηματοδοτεί τα υπόλοιπα.

---

## Βήμα 3: Εμφάνιση Προειδοποιήσεων Φόρτωσης – Μάθετε Ακριβώς Τι Διορθώθηκε

Αφού το έγγραφο φορτωθεί, μπορείτε να ερωτήσετε τη συλλογή προειδοποιήσεων. Αυτό είναι το **display load warnings** μέρος του tutorial μας.

```java
// Retrieve the warning collection
int warningCount = document.getWarningInfo().size();

// Print a friendly message
System.out.println("Document loaded with warnings: " + warningCount);

// Optional: iterate and print each warning for deeper insight
document.getWarningInfo().forEach(w -> System.out.println("- " + w.getDescription()));
```

Τυπική έξοδος μπορεί να μοιάζει με:

```
Document loaded with warnings: 3
- Warning: Missing end tag for <w:p>.
- Warning: Invalid hyperlink target.
- Warning: Unsupported bitmap format.
```

Η προβολή της λίστας σας επιτρέπει να αποφασίσετε αν χρειάζεται να διορθώσετε κάτι χειροκίνητα αργότερα ή αν το ανακτημένο έγγραφο είναι επαρκές για την περίπτωσή σας.

---

## Πλήρες Παράδειγμα Εργασίας – Από την Αρχή μέχρι το Τέλος

Παρακάτω υπάρχει μια αυτόνομη κλάση Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε project. Δείχνει **πώς να ανακτήσετε docx**, **set recovery mode**, **use recovery mode**, και **display load warnings** — όλα σε ένα βήμα.

```java
import com.aspose.words.*;

public class DocxRecoveryDemo {

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with the desired recovery strategy
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
            // Uncomment the line below to suppress warnings
            // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_SILENTLY);

            // 2️⃣ Load the potentially corrupted DOCX file
            String filePath = "C:/Docs/corrupted.docx";
            Document doc = new Document(filePath, loadOptions);

            // 3️⃣ Show how many warnings were generated
            int warnings = doc.getWarningInfo().size();
            System.out.println("Document loaded with warnings: " + warnings);

            // Optional: print each warning for debugging
            for (WarningInfo wi : doc.getWarningInfo()) {
                System.out.println("- " + wi.getDescription());
            }

            // 4️⃣ Save the recovered document (optional)
            String outputPath = "C:/Docs/recovered.docx";
            doc.save(outputPath);
            System.out.println("Recovered document saved to: " + outputPath);

        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το πρόγραμμα εκτυπώνει τον αριθμό των προειδοποιήσεων, παραθέτει καθεμία, και γράφει ένα καθαρό `recovered.docx` στο δίσκο. Ακόμη και αν το αρχικό αρχείο ήταν μισό‑σπασμένο, η έξοδος θα περιέχει όλο το ανακτήσιμο περιεχόμενο.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι κάνω αν πρέπει να ανακτήσω ένα DOCX από stream αντί για διαδρομή αρχείου;
Απλώς περάστε ένα `InputStream` στον κατασκευαστή `Document` μαζί με τις ίδιες `LoadOptions`. Το API λειτουργεί με τον ίδιο τρόπο.

```java
InputStream is = new FileInputStream("corrupted.docx");
Document doc = new Document(is, loadOptions);
```

### Μπορώ να αλλάξω τη λειτουργία ανάκτησης μετά το άνοιγμα του εγγράφου;
Όχι. Η λειτουργία είναι μόνο‑ανάγνωση κατά τη φάση φόρτωσης. Αν χρειάζεστε διαφορετική στρατηγική, φορτώστε ξανά το αρχείο με ένα νέο αντικείμενο `LoadOptions`.

### Πώς διαφέρει το **recover corrupted docx** από το απλό άνοιγμα στο Microsoft Word;
Το Word προσπαθεί να αυτο‑επισκευάσει αλλά συχνά κρύβει τις λεπτομέρειες. Το Aspose.Words σας δίνει μια προγραμματιστική λίστα με κάθε πρόβλημα μέσω του **display load warnings**, κάτι πολύτιμο για αυτοματοποιημένες γραμμές παραγωγής.

### Υπάρχει κόστος απόδοσης όταν χρησιμοποιείται το `RECOVER_WITH_WARNINGS`;
Λίγο — η συλλογή προειδοποιήσεων προσθέτει overhead, αλλά είναι αμελητέο για τα περισσότερα αρχεία (<5 MB). Για μαζική επεξεργασία όπου η ταχύτητα μετράει, μεταβείτε σε `RECOVER_SILENTLY`.

---

## Pro Συμβουλές & Πιθανά Παγίδες

* **Pro tip:** Καταγράψτε πάντα τις προειδοποιήσεις σε αρχείο όταν επεξεργάζεστε batch. Έτσι μπορείτε να ελέγξετε τα προβληματικά αρχεία αργότερα χωρίς να γεμίσετε την κονσόλα.
* **Προσοχή:** Πολύ μεγάλα αρχεία DOCX (>100 MB) μπορεί να προκαλέσουν `OutOfMemoryError` αν ενεργοποιήσετε και `RECOVER_WITH_WARNINGS`. Σκεφτείτε να αυξήσετε το heap της JVM ή να χρησιμοποιήσετε `RECOVER_SILENTLY` για αυτές τις περιπτώσεις.
* **Tip:** Μετά την ανάκτηση, εκτελέστε έναν γρήγορο έλεγχο λογικής — π.χ., `doc.getSections().size()` — για να βεβαιωθείτε ότι η δομή του εγγράφου είναι άθικτη πριν το παραδώσετε σε downstream services.

---

## Συμπέρασμα

Μόλις καλύψαμε **πώς να ανακτήσετε docx** αρχεία διαμορφώνοντας **load options**, **set recovery mode**, **use recovery mode**, και **display load warnings** για οποιοδήποτε κατεστραμμένο DOCX συναντήσετε. Το πλήρες παράδειγμα παραπάνω είναι έτοιμο για αντιγραφή‑επικόλληση, εκτέλεση και προσαρμογή στις δικές σας ροές εργασίας.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αντικαταστήσετε το `RECOVER_WITH_WARNINGS` με `RECOVER_SILENTLY` σε μια εργασία υψηλού όγκου, ή ενσωματώστε τη λίστα προειδοποιήσεων στο σύστημα παρακολούθησής σας. Μπορείτε επίσης να εξερευνήσετε άλλες δυνατότητες του Aspose.Words όπως **document protection** ή **format conversion** — όλες σέβονται τις ίδιες ρυθμίσεις ανάκτησης.

Έχετε περισσότερες ερωτήσεις σχετικά με την ανάκτηση εγγράφων, τη διαχείριση άλλων μορφών Office, ή τη ρύθμιση του Aspose.Words; Αφήστε ένα σχόλιο, και καλή προγραμματιστική εμπειρία!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}