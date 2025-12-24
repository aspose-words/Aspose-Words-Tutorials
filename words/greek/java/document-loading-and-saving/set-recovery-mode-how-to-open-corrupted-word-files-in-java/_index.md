---
category: general
date: 2025-12-23
description: Ορίστε τη λειτουργία ανάκτησης για την αποκατάσταση κατεστραμμένων εγγράφων
  Word. Μάθετε πώς να ανοίγετε αρχεία DOCX, να χρησιμοποιείτε τη λειτουργία ανάκτησης
  και να διαχειρίζεστε κατεστραμμένα αρχεία σε Java.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: el
og_description: Ορίστε τη λειτουργία ανάκτησης για να επαναφέρετε κατεστραμμένα έγγραφα
  Word. Αυτός ο οδηγός δείχνει πώς να ανοίξετε αρχεία DOCX, να χρησιμοποιήσετε τη
  λειτουργία ανάκτησης και να διαχειριστείτε κατεστραμμένα αρχεία σε Java.
og_title: Ορισμός Λειτουργίας Ανάκτησης – Άνοιγμα Κατεστραμμένων Αρχείων Word σε Java
tags:
- Java
- Aspose.Words
- Document Recovery
title: Ορισμός λειτουργίας ανάκτησης – Πώς να ανοίξετε κατεστραμμένα αρχεία Word σε
  Java
url: /el/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός Λειτουργίας Ανάκτησης – Πώς να Ανοίξετε Κατεστραμμένα Αρχεία Word σε Java

Έχετε προσπαθήσει ποτέ να **ορίσετε τη λειτουργία ανάκτησης** σε ένα έγγραφο Word που αρνείται να ανοίξει; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν ένα DOCX είναι ελαφρώς κατεστραμμένο και η συνηθισμένη κλήση `new Document("file.docx")` πετάει εξαίρεση. Τα καλά νέα; Το Aspose.Words for Java σας παρέχει ενσωματωμένο τρόπο να **χρησιμοποιήσετε τη λειτουργία ανάκτησης** και πραγματικά να **ανακτήσετε κατεστραμμένα αρχεία Word**.

Σε αυτό το tutorial θα περάσουμε από όλα όσα χρειάζεται να γνωρίζετε για να **ανοίξετε ασφαλώς αρχεία Word που είναι κατεστραμμένα**, από τη διαμόρφωση του `LoadOptions` μέχρι τη διαχείριση των ακραίων περιπτώσεων που συνήθως προκαλούν προβλήματα. Χωρίς περιττές πληροφορίες—απλώς μια πρακτική, βήμα‑βήμα λύση που μπορείτε να επικολλήσετε στο έργο σας αμέσως.

> **Συμβουλή:** Αν αντιμετωπίζετε μόνο μικρά σφάλματα (π.χ. ένα ελλιπές υποσέλιδο), η λειτουργία ανάκτησης **Tolerant** είναι συνήθως αρκετή. Κρατήστε τη **Strict** για περιπτώσεις όπου χρειάζεστε το έγγραφο να είναι 100 % καθαρό πριν από την επεξεργασία.

## Τι Θα Χρειαστεί

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK· το API λειτουργεί το ίδιο)
- **Aspose.Words for Java** 23.9 (ή νεότερο) – η βιβλιοθήκη που περιλαμβάνει την κλάση `LoadOptions`.
- Ένα **κατεστραμμένο DOCX** αρχείο για δοκιμή (μπορείτε να δημιουργήσετε ένα περικόπτοντας ένα έγκυρο αρχείο με έναν επεξεργαστή hex).
- Το αγαπημένο σας IDE (IntelliJ, Eclipse, VS Code—επιλέξτε ό,τι σας βολεύει).

Αυτό είναι όλο. Χωρίς πρόσθετα Maven plugins, χωρίς εξωτερικά εργαλεία. Μόνο η βασική βιβλιοθήκη και λίγος κώδικας.

![Εικονογράφηση του ορισμού λειτουργίας ανάκτησης στο Aspose.Words Java API](/images/set-recovery-mode-java.png){.align-center alt="set recovery mode"}

## Βήμα 1 – Δημιουργία ενός `LoadOptions` Αντικειμένου

Το πρώτο που κάνετε είναι να δημιουργήσετε ένα αντικείμενο `LoadOptions`. Σκεφτείτε το ως ένα κουτί εργαλείων που λέει στο Aspose.Words **πώς να αντιμετωπίσει το εισερχόμενο αρχείο**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Γιατί να παραλείψετε αυτό το βήμα; Επειδή χωρίς ένα `LoadOptions` δεν μπορείτε να πείτε στη βιβλιοθήκη αν θέλετε να **χρησιμοποιήσετε τη λειτουργία ανάκτησης** ή όχι. Η προεπιλεγμένη συμπεριφορά είναι αυστηρή, πράγμα που σημαίνει ότι οποιαδήποτε κατεργασία ακυρώνει τη φόρτωση.

## Βήμα 2 – Επιλέξτε τη Σωστή Λειτουργία Ανάκτησης

Το Aspose.Words προσφέρει δύο τιμές enum:

| Λειτουργία | Τι κάνει |
|------|--------------|
| `RecoveryMode.Tolerant` | Προσπαθεί να διασώσει όσο το δυνατόν περισσότερο. Ιδανική για σενάρια *ανάκτησης κατεστραμμένου word* όπου το μόνο πρόβλημα είναι ένα ελλιπές στυλ ή μια σπασμένη σχέση. |
| `RecoveryMode.Strict`   | Αποτυγχάνει άμεσα σε οποιοδήποτε πρόβλημα. Χρησιμοποιήστε τη όταν χρειάζεστε εγγύηση ότι το έγγραφο είναι άψογο πριν από περαιτέρω επεξεργασία. |

Ορίστε τη λειτουργία με μία γραμμή:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Γιατί είναι σημαντικό:** Όταν **χρησιμοποιείτε τη λειτουργία ανάκτησης**, η βιβλιοθήκη εσωτερικά διορθώνει τα σπασμένα τμήματα, ξαναμιουργεί τα ελλιπή XML nodes, και σας παρέχει ένα χρησιμοποιήσιμο αντικείμενο `Document`. Σε λειτουργία *strict* θα λάβετε ένα `InvalidFormatException`.

## Βήμα 3 – Φόρτωση του Εγγράφου με τις Επιλογές Σας

Τώρα τελικά παραδίδετε το αρχείο στο Aspose.Words, περνώντας το `LoadOptions` που μόλις διαμορφώσατε.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Αν το αρχείο είναι μόνο ελαφρώς κατεστραμμένο, το `doc` θα είναι ένα πλήρως λειτουργικό αντικείμενο `Document`. Μπορείτε τώρα:

- Να διαβάσετε το κείμενο (`doc.getText()`),
- Να αποθηκεύσετε σε άλλη μορφή (`doc.save("repaired.pdf")`),
- Ή ακόμη να ελέγξετε τη λίστα των ανακτηθέντων τμημάτων μέσω του API `Document`.

### Επαλήθευση της Ανάκτησης

Μια γρήγορη έλεγχος λογικής σας βοηθά να επιβεβαιώσετε ότι η ανάκτηση πραγματικά πέτυχε:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Βήμα 4 – Διαχείριση Ακραίων Περιπτώσεων

### 4.1 Όταν η Tolerant δεν Αρκεύει

Μερικές φορές ένα αρχείο είναι τόσο σπασμένο που ακόμη και η λειτουργία **Tolerant** δεν μπορεί να το ενώσει (π.χ. το κύριο XML λείπει). Σε αυτές τις σπάνιες περιπτώσεις, μπορείτε:

1. **Προσπαθήστε μια δεύτερη φόρτωση με `RecoveryMode.Strict`** για να δείτε αν το μήνυμα σφάλματος παρέχει περισσότερες λεπτομέρειες.
2. **Επιστρέψτε σε ένα εργαλείο zip** για να εξάγετε χειροκίνητα τα XML τμήματα και να τα διορθώσετε.
3. **Καταγράψτε την εξαίρεση** και ενημερώστε τον χρήστη ότι το έγγραφο είναι αδύνατο να ανακτηθεί.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Σκέψεις για τη Μνήμη

Η φόρτωση τεράστιων αρχείων DOCX με ενεργοποιημένη την ανάκτηση μπορεί προσωρινά να διπλασιάσει τη χρήση μνήμης επειδή το Aspose.Words κρατά τόσο το αρχικό όσο και το διορθωμένο δομή στη μνήμη. Αν επεξεργάζεστε μεγάλες παρτίδες:

- **Επαναχρησιμοποιήστε το ίδιο αντικείμενο `LoadOptions`** αντί να δημιουργείτε νέο κάθε φορά.
- **Κλείστε το `Document`** (`doc.close()`) μόλις τελειώσετε.
- **Τρέξτε σε JVM με επαρκή heap** (`-Xmx2g` ή μεγαλύτερο για αρχεία πολλαπλών gigabytes).

### 4.3 Αποθήκευση του Διορθωμένου Αρχείου

Μετά από επιτυχή φόρτωση, ίσως θέλετε να **αποθηκεύσετε την καθαρή έκδοση** ώστε να μην χρειαστεί ξανά η ανάκτηση.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Τώρα, την επόμενη φορά που θα ανοίξετε το `repaired.docx` μπορείτε να παραλείψετε εντελώς το βήμα **χρήσης λειτουργίας ανάκτησης**.

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό για παλαιότερα αρχεία `.doc`;**  
Α: Ναι. Η ίδια προσέγγιση `LoadOptions` ισχύει για `.doc` και `.rtf`. Απλώς αλλάξτε την επέκταση του αρχείου.

**Ε: Μπορώ να συνδυάσω το `setRecoveryMode` με άλλες επιλογές φόρτωσης (π.χ., κωδικό πρόσβασης);**  
Α: Απόλυτα. Το `LoadOptions` έχει ιδιότητες όπως `setPassword` και `setLoadFormat`. Ορίστε τις πριν καλέσετε το `setRecoveryMode`.

**Ε: Υπάρχει κάποια ποινή απόδοσης;**  
Α: Ελαφρώς—η ανάκτηση προσθέτει επιπλέον επεξεργασία. Σε δοκιμές, ένα 5 MB κατεστραμμένο αρχείο φορτώνεται περίπου 30 % πιο αργά σε λειτουργία **Tolerant** σε σύγκριση με αυστηρή φόρτωση ενός καθαρού αρχείου. Παραμένει αποδεκτό για τις περισσότερες εργασίες παρτίδας.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω υπάρχει μια πλήρης, έτοιμη‑για‑εκτέλεση κλάση Java που δείχνει **πώς να ανοίξετε docx**, **να χρησιμοποιήσετε τη λειτουργία ανάκτησης**, και **να αποθηκεύσετε ένα διορθωμένο αντίγραφο**.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Τρέξτε αυτήν την κλάση αφού προσθέσετε το JAR του Aspose.Words for Java στο classpath του έργου σας. Αν το αρχείο εισόδου είναι μόνο ελαφρώς κατεστραμμένο, θα δείτε το μήνυμα **✅** και ένα νέο `repaired.docx` στο δίσκο.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **ορίσετε τη λειτουργία ανάκτησης** και να ανοίξετε επιτυχώς **κατεστραμμένα αρχεία word** σε Java. Δημιουργώντας ένα αντικείμενο `LoadOptions`, επιλέγοντας την κατάλληλη `RecoveryMode` και διαχειριζόμενοι τις σπάνιες ακραίες περιπτώσεις, μπορείτε να μετατρέψετε μια απογοητευτική στιγμή «το αρχείο δεν ανοίγει» σε μια ομαλή διαδικασία ανάκτησης.

- **Tolerant** είναι η προεπιλογή σας για τις περισσότερες σενάρια *ανάκτησης κατεστραμμένου word*.
- **Strict** σας παρέχει σκληρό σφάλμα όταν χρειάζεστε απόλυτη βεβαιότητα.
- Πάντα επαληθεύετε το φορτωμένο έγγραφο και, αν είναι δυνατόν, αποθηκεύστε ένα καθαρό αντίγραφο για μελλοντικές εκτελέσεις.

Τώρα μπορείτε με σιγουριά να απαντήσετε «**πώς να ανοίξετε docx** που αρνείται να φορτωθεί;» με ένα συγκεκριμένο απόσπασμα κώδικα και μια σαφή εξήγηση. Καλή προγραμματιστική, και εύχομαι τα έγγραφ σας να παραμείνουν υγιή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}