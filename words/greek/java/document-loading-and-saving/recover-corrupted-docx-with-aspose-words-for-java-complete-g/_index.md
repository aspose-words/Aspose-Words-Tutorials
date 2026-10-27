---
category: general
date: 2026-05-23
description: Ανακτήστε κατεστραμμένα DOCX χρησιμοποιώντας το Aspose.Words για Java.
  Μάθετε βήμα‑βήμα πώς να διαμορφώσετε το LoadOptions, να διαχειριστείτε τις προειδοποιήσεις
  και να αποθηκεύσετε ένα καθαρό αρχείο.
draft: false
keywords:
- recover corrupted docx
- aspose.words loadoptions
- java recover docx
- handle corrupted word file
- warninginfo inspection
language: el
og_description: Ανακτήστε κατεστραμμένα DOCX σε Java με το Aspose.Words. Αυτός ο οδηγός
  δείχνει πώς να χρησιμοποιήσετε το LoadOptions, να ελέγξετε τις προειδοποιήσεις και
  να δημιουργήσετε ένα χρησιμοποιήσιμο έγγραφο.
og_title: Ανάκτηση Κατεστραμμένου DOCX με το Aspose.Words για Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Recover corrupted DOCX using Aspose.Words for Java. Learn step‑by‑step
    how to configure LoadOptions, handle warnings, and save a clean file.
  headline: Recover Corrupted DOCX with Aspose.Words for Java – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Document Recovery
title: Ανάκτηση Κατεστραμμένου DOCX με το Aspose.Words για Java – Πλήρης Οδηγός
url: /el/java/document-loading-and-saving/recover-corrupted-docx-with-aspose-words-for-java-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση Κατεστραμμένων DOCX με Aspose.Words για Java – Πλήρης Οδηγός

Ποτέ χρειάστηκε να **ανακτήσετε κατεστραμμένα αρχεία DOCX** αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είσαι μόνος—σπασμένα έγγραφα Word εμφανίζονται πιο συχνά απ' ό,τι θα θέλαμε, ειδικά μετά από ξαφνικές καταρρεύσεις συστήματος ή ημιτελείς μεταφορτώσεις. Τα καλά νέα; Το Aspose.Words για Java παρέχει ενσωματωμένο τρόπο να εξάγεις ένα χρησιμοποιήσιμο αρχείο από τα απορρίμματα.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πρακτική, ολοκληρωμένη λύση που όχι μόνο **ανακτά κατεστραμμένα docx** αρχεία, αλλά και σου επιτρέπει να εξετάσεις τυχόν προειδοποιήσεις που εμφανίζονται κατά τη διαδικασία. Στο τέλος, θα έχεις ένα καθαρό αντίγραφο έτοιμο για επεξεργασία, κοινή χρήση ή αρχειοθέτηση.

---

## Τι Θα Μάθεις

* Πώς να ρυθμίσεις **LoadOptions** για λειτουργία ανάκτησης.
* Η διαφορά μεταξύ `RECOVER_WITH_WARNINGS` και `RECOVER_WITHOUT_WARNINGS`.
* Πώς να επαναλάβεις πάνω σε αντικείμενα **WarningInfo** για να καταλάβεις τι πήγε στραβά.
* Προαιρετικά: αποθήκευση του διορθωμένου εγγράφου για μελλοντική χρήση.
* Συμβουλές για διαχείριση ειδικών περιπτώσεων, όπως κρυπτογραφημένα ή προστατευμένα με κωδικό αρχεία.

**Προαπαιτούμενα**

* Java 8 ή νεότερη εγκατεστημένη.
* Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) που μπορεί να προσθέσει τη βιβλιοθήκη Aspose.Words για Java.
* Ένα κατεστραμμένο αρχείο `.docx` για δοκιμή (μπορείς να δημιουργήσεις ένα περικόπτοντας ένα έγκυρο αρχείο).

---

![Diagram illustrating the recover corrupted docx workflow using Aspose.Words](recover-corrupted-docx-diagram.png)

*Image alt text: “διάγραμμα ροής ανάκτησης κατεστραμμένου docx”*

---

## Βήμα 1: Ρύθμιση Έργου και Προσθήκη Aspose.Words

Πριν βυθιστείς στον κώδικα, βεβαιώσου ότι το JAR του Aspose.Words βρίσκεται στο classpath. Αν χρησιμοποιείς Maven, πρόσθεσε την ακόλουθη εξάρτηση:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Οι χρήστες Gradle μπορούν να προσθέσουν:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

Αν προτιμάς τη χειροκίνητη προσέγγιση, κατέβασε το JAR από την ιστοσελίδα του Aspose και τοποθέτησέ το στον φάκελο `libs/`. Μόλις η βιβλιοθήκη είναι διαθέσιμη, είσαι έτοιμος να **χειριστείς σενάρια κατεστραμμένων αρχείων Word**.

---

## Βήμα 2: Ρύθμιση LoadOptions για Λειτουργία Ανάκτησης

Η καρδιά της διαδικασίας ανάκτησης βρίσκεται στο `LoadOptions`. Με την αλλαγή του `RecoveryMode`, λές στο Aspose.Words πόσο επιθετικά θα προσπαθήσει να διασώσει το έγγραφο.

```java
import com.aspose.words.*;

public class DocxRecovery {
    public static void main(String[] args) throws Exception {
        // Create a LoadOptions instance
        LoadOptions loadOptions = new LoadOptions();

        // Choose a recovery strategy:
        // RECOVER_WITH_WARNINGS – attempts recovery and records issues.
        // RECOVER_WITHOUT_WARNINGS – tries to fix silently.
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
```

**Γιατί είναι σημαντικό:** Το `RECOVER_WITH_WARNINGS` είναι η πιο ασφαλής επιλογή επειδή εμφανίζει κρυφά προβλήματα μέσω **επιθεώρησης warninginfo**, δίνοντάς σου την ευκαιρία να τα καταγράψεις ή να ενεργήσεις ανάλογα. Αν δουλεύεις με μαζική επεξεργασία αρχείων και δεν χρειάζεσαι λεπτομερείς καταγραφές, το `RECOVER_WITHOUT_WARNINGS` μπορεί να επιταχύνει τη διαδικασία.

---

## Βήμα 3: Φόρτωση του Κατεστραμμένου Εγγράφου με τις Ρυθμισμένες Επιλογές

Τώρα που το `LoadOptions` είναι ρυθμισμένο, μπορείς να προσπαθήσεις να ανοίξεις το κατεστραμμένο αρχείο. Το Aspose.Words θα δημιουργήσει είτε ένα χρησιμοποιήσιμο αντικείμενο `Document` είτε θα ρίξει εξαίρεση αν η κατεστραμμένη κατάσταση είναι ανυπέρβλητη.

```java
        // Path to the corrupted DOCX – adjust as needed
        String corruptedPath = "C:/Docs/Corrupted.docx";

        // Load the document with recovery options
        Document doc = new Document(corruptedPath, loadOptions);
```

**Συμβουλή:** Αν το αρχείο είναι προστατευμένο με κωδικό, μπορείς επίσης να περάσεις τον κωδικό στο `LoadOptions` πριν τη φόρτωση. Αυτό αποτρέπει την `IncorrectPasswordException` να διακόψει τη ροή ανάκτησης.

---

## Βήμα 4: Επισκόπηση Προειδοποιήσεων – Βαθιά Εξέταση WarningInfo

Μετά τη φόρτωση, το Aspose.Words γεμίζει μια συλλογή από αντικείμενα `WarningInfo`. Κάθε προειδοποίηση παρέχει μια κειμενική περιγραφή του τι διορθώθηκε, παραλείφθηκε ή δεν μπόρεσε να ανακτηθεί.

```java
        // Iterate over any warnings generated during loading
        for (WarningInfo warning : doc.getWarnings()) {
            System.out.println("Warning: " + warning.getDescription());
        }
```

Τυπικές προειδοποιήσεις περιλαμβάνουν:

* **Missing font** – το αρχικό έγγραφο αναφερόταν σε γραμματοσειρά που δεν είναι εγκατεστημένη.
* **Corrupt image** – δεν μπόρεσε να αναλυθεί η ροή μιας εικόνας.
* **Invalid XML** – ένα τμήμα του εσωτερικού XML του εγγράφου ήταν κακοδιατυπωμένο.

Καταγράφοντας αυτά τα μηνύματα, μπορείς να αποφασίσεις αν απαιτείται πρόσθετος χειροκίνητος καθαρισμός (π.χ. προσθήκη της ελλιπούς γραμματοσειράς).

---

## Βήμα 5: Αποθήκευση του Διορθωμένου Εγγράφου (Προαιρετικό αλλά Συνιστώμενο)

Αν το έγγραφο φορτώθηκε χωρίς εξαίρεση, πιθανότατα έχεις ένα χρησιμοποιήσιμο αρχείο. Η αποθήκευσή του σου δίνει ένα καθαρό αντίγραφο που μπορείς να ανοίξεις στο Microsoft Word χωρίς την ενοχλητική προειδοποίηση “Το αρχείο είναι κατεστραμμένο”.

```java
        // Define the output path for the recovered file
        String recoveredPath = "C:/Docs/Recovered.docx";

        // Save the document – you can choose any supported format
        doc.save(recoveredPath, SaveFormat.DOCX);

        System.out.println("Recovered document saved to: " + recoveredPath);
    }
}
```

**Pro tip:** Όταν επεξεργάζεσαι πολλά αρχεία, σκέψου να προσθέσεις ένα χρονικό σήμα στο όνομα του αρχείου για να αποφύγεις την αντικατάσταση προηγούμενων ανακτήσεων.

---

## Διαχείριση Ειδικών Περιπτώσεων και Συνηθισμένων Παγίδων

| Situation | What to Do |
|-----------|------------|
| **Document is encrypted** | Set `loadOptions.setPassword("yourPassword")` before loading. |
| **Recovery fails with an exception** | Switch to `RECOVER_WITHOUT_WARNINGS` and retry; if it still fails, the file may be beyond repair. |
| **Large files cause OutOfMemoryError** | Increase the JVM heap size (`-Xmx2g`) or use streaming APIs (`Document.save(OutputStream, SaveOptions)`). |
| **You need to keep original formatting** | After recovery, compare `doc.getOriginalFileInfo()` (if available) with the saved version to ensure key elements persisted. |

Αντιμετωπίζοντας αυτές τις καταστάσεις εκ των προτέρων, θα κάνεις τη **java recover docx** ρουτίνα σου πολύ πιο ανθεκτική.

---

## Πλήρες Παράδειγμα Εργασίας (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // 1️⃣ Configure LoadOptions for recovery
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
            // Uncomment and set if the file is password‑protected
            // loadOptions.setPassword("mySecret");

            // 2️⃣ Load the corrupted DOCX
            String inputPath = "YOUR_DIRECTORY/Corrupted.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Inspect any warnings (warninginfo inspection)
            for (WarningInfo warning : doc.getWarnings()) {
                System.out.println("Warning: " + warning.getDescription());
            }

            // 4️⃣ Save the recovered document
            String outputPath = "YOUR_DIRECTORY/Recovered.docx";
            doc.save(outputPath, SaveFormat.DOCX);
            System.out.println("Successfully recovered and saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Recovery failed: " + e.getMessage());
        }
    }
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
Warning: The font 'Calibri' could not be found and was substituted.
Warning: Image #3 is corrupted and was removed.
Successfully recovered and saved to: YOUR_DIRECTORY/Recovered.docx
```

Αν το αρχείο είναι ακατόρθωτο, θα δεις μήνυμα εξαίρεσης αντί για τη γραμμή επιτυχίας.

---

## Συμπέρασμα

Τώρα διαθέτεις μια στιβαρή, έτοιμη για παραγωγή μέθοδο να **ανακτήσεις κατεστραμμένα docx** αρχεία χρησιμοποιώντας το Aspose.Words για Java. Με τη ρύθμιση του `LoadOptions`, την εκτέλεση **επιθεώρησης warninginfo**, και την προαιρετική αποθήκευση του καθαρισμένου εγγράφου, μπορείς να μετατρέψεις ένα σπασμένο αρχείο Word σε χρήσιμο πόρο με λίγες μόνο γραμμές κώδικα.

Τι έπεται; Δοκίμασε να επεκτείνεις αυτήν την προσέγγιση για μαζική επεξεργασία φακέλου εγγράφων, ή πειραματίσου με σημαίες του `LoadOptions` όπως `setLoadFormat` για να διαχειριστείς άλλα φορμά Office (π.χ. `.pptx` ή `.xlsx`). Και αν αντιμετωπίσεις ένα επίμονο αρχείο, θυμήσου τις συμβουλές για κρυπτογραφημένα έγγραφα και όρια μνήμης—συχνά κάνουν τη διαφορά μεταξύ γρήγορης λύσης και αδιέξοδου.

Έχεις ερωτήσεις ή ένα δύσκολο αρχείο που δεν μπορείς να σπάσεις; Άφησε ένα σχόλιο παρακάτω, και καλή κωδικοποίηση!

## Σχετικά Tutorials

- [Recover corrupted docx – Complete Guide to Fix and Process Documents](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}