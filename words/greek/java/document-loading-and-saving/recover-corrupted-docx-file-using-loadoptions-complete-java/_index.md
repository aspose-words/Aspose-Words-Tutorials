---
category: general
date: 2025-12-18
description: Μάθετε πώς να ανακτήσετε ένα κατεστραμμένο αρχείο docx με το Aspose.Words
  LoadOptions, εξερευνήστε τις χαλαρές και αυστηρές λειτουργίες ανάκτησης και λάβετε
  πλήρως εκτελέσιμο κώδικα Java.
draft: false
keywords:
- recover corrupted docx file
- lenient recovery mode
- strict recovery mode
- LoadOptions
- Aspose.Words
language: el
og_description: Ανακαλύψτε πώς να ανακτήσετε ένα κατεστραμμένο αρχείο docx με το Aspose.Words
  LoadOptions, καλύπτοντας τόσο τις χαλαρές όσο και τις αυστηρές λειτουργίες ανάκτησης
  σε έναν βήμα‑βήμα οδηγό.
og_title: Ανάκτηση κατεστραμμένου αρχείου docx χρησιμοποιώντας το LoadOptions – Java
  Tutorial
tags:
- docx recovery
- Java
- document processing
title: Ανάκτηση κατεστραμμένου αρχείου docx χρησιμοποιώντας LoadOptions – Πλήρης Οδηγός
  Java
url: /el/java/document-loading-and-saving/recover-corrupted-docx-file-using-loadoptions-complete-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου αρχείου docx – Πλήρης Εκπαίδευση Java

Έχετε ανοίξει ποτέ ένα **.docx** μόνο για να δείτε ένα ακατάστατο σύνολο χαρακτήρων και να σκεφτείτε, “Πώς μπορώ να ανακτήσω το κατεστραμμένο αρχείο docx χωρίς να χάσω τα πάντα;” Δεν είστε μόνοι· πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν ενσωματώνουν ροές εγγράφων. Τα καλά νέα; Η Aspose.Words σας παρέχει μια βολική `LoadOptions` κλάση που μπορεί να επαναφέρει τη ζωή σε ένα χαλασμένο αρχείο. Σε αυτόν τον οδηγό θα περάσουμε από κάθε λεπτομέρεια—*γιατί* θα επιλέξετε μια λειτουργία ανάκτησης έναντι της άλλης, *πώς* να τη ρυθμίσετε, και ακόμη τι να κάνετε όταν τα πράγματα εξακολουθούν να πάουν στραβά.

![recover corrupted docx file illustration](https://example.com/images/recover-corrupted-docx.png)

> **Συνοπτικά:** Η χρήση του `LoadOptions` με **lenient recovery mode** είναι συνήθως αρκετή για τα περισσότερα κατεστραμμένα αρχεία, ενώ το **strict recovery mode** επιβάλλει πλήρη επικύρωση και θα διακόψει την εκτέλεση σε οποιοδήποτε σφάλμα.

## Τι Θα Μάθετε

- Η διαφορά μεταξύ **lenient** και **strict** λειτουργιών ανάκτησης.  
- Πώς να διαμορφώσετε το `LoadOptions` σε Java για **ανάκτηση κατεστραμμένου αρχείου docx**.  
- Πλήρης, έτοιμος‑για‑εκτέλεση κώδικας που μπορείτε να ενσωματώσετε σε οποιοδήποτε Maven project.  
- Συμβουλές για την αντιμετώπιση ειδικών περιπτώσεων, όπως αρχεία προστατευμένα με κωδικό ή σοβαρά κατεστραμμένα έγγραφα.  
- Ιδέες για τα επόμενα βήματα, όπως η αποθήκευση μιας καθαρής έκδοσης ή η εξαγωγή κειμένου για ανάλυση.

Καμία προϋπάρχουσα εμπειρία με την Aspose.Words δεν απαιτείται—απλώς μια βασική ρύθμιση Java και ένα σπασμένο `.docx` που θέλετε να διορθώσετε.

---

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

1. **Java 17** (ή νεότερη) εγκατεστημένη.  
2. **Maven** για διαχείριση εξαρτήσεων.  
3. Τη βιβλιοθήκη **Aspose.Words for Java** (η δωρεάν δοκιμή λειτουργεί καλά για δοκιμές).  
4. Ένα δείγμα κατεστραμμένου εγγράφου, π.χ. `corrupted.docx` τοποθετημένο στο `src/main/resources`.

Αν κάποιο από αυτά σας είναι άγνωστο, κάντε παύση εδώ και εγκαταστήστε τα πρώτα—διαφορετικά ο κώδικας δεν θα μεταγλωττιστεί.

---

## Step 1 – Set up LoadOptions to recover corrupted docx file

Το πρώτο που χρειαζόμαστε είναι μια παρουσία του `LoadOptions`. Αυτό το αντικείμενο λέει στην Aspose.Words πώς να αντιμετωπίσει το εισερχόμενο αρχείο.

```java
// Step 1: Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Choose the recovery mode: Lenient (default) or Strict
loadOptions.setRecoveryMode(RecoveryMode.Lenient); // or RecoveryMode.Strict
```

**Γιατί είναι σημαντικό:**  
- **Lenient recovery mode** προσπαθεί να αγνοήσει μικρά προβλήματα, ανακατασκευάζοντας όσο το δυνατόν περισσότερο τη δομή του εγγράφου.  
- **Strict recovery mode** επικυρώνει κάθε μέρος του αρχείου και ρίχνει εξαίρεση αν κάτι φαίνεται λανθασμένο. Χρησιμοποιήστε το όταν χρειάζεστε απόλυτη βεβαιότητα ότι το αποτέλεσμα ταιριάζει με το αρχικό προδιαγραφικό.

## Step 2 – Load the potentially corrupted document

Τώρα που το `LoadOptions` είναι έτοιμο, φορτώνουμε το αρχείο. Ο κατασκευαστής που χρησιμοποιούμε δέχεται τη διαδρομή του αρχείου και τις επιλογές που μόλις διαμορφώσαμε.

```java
import com.aspose.words.*;

public class DocxRecovery {
    public static void main(String[] args) {
        // Path to the corrupted DOCX
        String filePath = "src/main/resources/corrupted.docx";

        // LoadOptions prepared in Step 1
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.Lenient); // Change to Strict if needed

        try {
            // Step 2: Load the document with the configured options
            Document doc = new Document(filePath, loadOptions);
            System.out.println("Document loaded successfully!");

            // Optional: Save a clean copy
            doc.save("recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load the document: " + e.getMessage());
            // If Lenient failed, you might retry with Strict or log the details
        }
    }
}
```

**Τι συμβαίνει εδώ;**  
- `new Document(filePath, loadOptions)` λέει στην Aspose.Words, *«Επεξεργάσου αυτό το αρχείο όπως το περιέγραψα.»*  
- Αν το αρχείο μπορεί να σωθεί, θα δείτε το μήνυμα “Document loaded successfully!” και ένα καθαρό αντίγραφο αποθηκευμένο ως `recovered.docx`.  
- Αν η ανάκτηση αποτύχει, το τμήμα catch εκτυπώνει το σφάλμα, δίνοντάς σας την ευκαιρία να αλλάξετε σε διαφορετική λειτουργία ή να ερευνήσετε περαιτέρω.

## Step 3 – Verify the recovered document

Μετά την αποθήκευση, είναι σοφό να επιβεβαιώσετε ότι το αποτέλεσμα είναι χρησιμοποιήσιμο. Ένας γρήγορος έλεγχος μπορεί να είναι τόσο απλός όσο το άνοιγμα του αρχείου προγραμματιστικά και η εκτύπωση της πρώτης παραγράφου.

```java
try {
    Document recovered = new Document("recovered.docx");
    Paragraph firstPara = recovered.getFirstSection().getBody().getFirstParagraph();
    System.out.println("First paragraph text: " + firstPara.toTxt());
} catch (Exception ex) {
    System.err.println("Verification failed: " + ex.getMessage());
}
```

Αν δείτε ουσιώδες κείμενο αντί για ακαταλαβίστικο, συγχαρητήρια—έχετε επιτυχώς **ανακτήσει το κατεστραμμένο αρχείο docx**.

## H3 – When to use lenient recovery mode

- **Τυπική κατεστραμμένη κατάσταση** (λείπουν ετικέτες XML, μικρά σφάλματα zip).  
- Χρειάζεστε μια προσπάθεια ανάκτησης χωρίς αυστηρή συμμόρφωση.  
- Η απόδοση μετράει· η λειτουργία lenient είναι ταχύτερη επειδή παραλείπει εξαντλητικούς ελέγχους.

> **Pro tip:** Ξεκινήστε με τη λειτουργία lenient. Αν το έγγραφο εξακολουθεί να μην φορτώνεται, περάστε στο **strict recovery mode** για να λάβετε μια λεπτομερή εξαίρεση που μπορεί να σας καθοδηγήσει στο προβληματικό τμήμα.

## H3 – When strict recovery mode is your friend

- **Περιβάλλοντα κρίσιμης συμμόρφωσης** (νομικά έγγραφα, ελέγχοι).  
- Πρέπει να εγγυηθείτε ότι κάθε στοιχείο συμμορφώνεται με το προδιαγραφικό Office Open XML.  
- Εντοπισμός σφαλμάτων σε επίμονο αρχείο—η λειτουργία strict σας λέει ακριβώς πού παραβιάζεται η προδιαγραφή.

## Edge Cases & Common Pitfalls

| Σενάριο | Προτεινόμενη Προσέγγιση |
|----------|----------------------|
| **Αρχείο προστατευμένο με κωδικό** | Παρέχετε τον κωδικό μέσω `LoadOptions.setPassword("yourPwd")` πριν τη φόρτωση. |
| **Σοβαρά κατεστραμμένο αρχείο zip** | Τυλίξτε την κλήση φόρτωσης σε `try‑catch` και σκεφτείτε τη χρήση εργαλείου τρίτου μέρους για επισκευή zip πριν την Aspose.Words. |
| **Μεγάλα έγγραφα (>100 MB)** | Αυξήστε τη μνήμη heap του JVM (`-Xmx2g`) και προτιμήστε `Lenient` για να αποφύγετε σφάλματα OutOfMemory. |
| **Πολλαπλά κατεστραμμένα τμήματα** | Φορτώστε με `Lenient`, στη συνέχεια επαναλάβετε πάνω σε `doc.getSections()` για να εντοπίσετε κενά ή κακοσχηματισμένα τμήματα. |

## Full Working Example (All Steps Combined)

```java
// Maven dependency (add to pom.xml):
/*
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version> <!-- Use latest -->
</dependency>
*/

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        String sourcePath = "src/main/resources/corrupted.docx";
        String outputPath = "recovered.docx";

        // 1️⃣ Prepare LoadOptions
        LoadOptions options = new LoadOptions();
        // Try Lenient first; switch to Strict if needed
        options.setRecoveryMode(RecoveryMode.Lenient);

        try {
            // 2️⃣ Load the corrupted document
            Document doc = new Document(sourcePath, options);
            System.out.println("[INFO] Document loaded with Lenient mode.");

            // 3️⃣ Save a clean copy
            doc.save(outputPath);
            System.out.println("[SUCCESS] Recovered file saved at: " + outputPath);

            // 4️⃣ Quick verification
            Document verify = new Document(outputPath);
            String firstLine = verify.getFirstSection()
                                      .getBody()
                                      .getFirstParagraph()
                                      .toTxt()
                                      .trim();
            System.out.println("[VERIFY] First paragraph: " + (firstLine.isEmpty() ? "(empty)" : firstLine));
        } catch (Exception e) {
            System.err.println("[ERROR] Lenient mode failed: " + e.getMessage());
            System.err.println("[ACTION] Retrying with Strict mode...");

            // Retry with Strict recovery
            options.setRecoveryMode(RecoveryMode.Strict);
            try {
                Document docStrict = new Document(sourcePath, options);
                docStrict.save(outputPath);
                System.out.println("[SUCCESS] Recovered with Strict mode.");
            } catch (Exception ex) {
                System.err.println("[FAIL] Strict mode also failed. Details: " + ex.getMessage());
                // At this point you may need external repair tools.
            }
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα (όταν η ανάκτηση επιτύχει):**

```
[INFO] Document loaded with Lenient mode.
[SUCCESS] Recovered file saved at: recovered.docx
[VERIFY] First paragraph: This is the first line of the original document.
```

Αν και οι δύο λειτουργίες αποτύχουν, η κονσόλα θα εμφανίσει τα μηνύματα εξαίρεσης, βοηθώντας σας να εντοπίσετε την ακριβή κατεστραμμένη περιοχή.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **ανακτήσετε το κατεστραμμένο αρχείο docx** χρησιμοποιώντας το `LoadOptions` της Aspose.Words. Ξεκινώντας με μια απλή ανάκτηση `Lenient`, προχωρώντας σε `Strict` όταν χρειάζεται, και επαληθεύοντας το αποτέλεσμα—όλα σε ένα ενιαίο, αυτόνομο πρόγραμμα Java.

Από εδώ μπορείτε:

- Να αυτοματοποιήσετε την ανάκτηση παρτίδας για έναν φάκελο με σπασμένα έγγραφα.  
- Να εξάγετε απλό κείμενο από το ανακτημένο αρχείο για ευρετηρίαση.  
- Να συνδυάσετε αυτό με μια λειτουργία cloud για επιδιόρθωση ανεβάσματος σε πραγματικό χρόνο.

Θυμηθείτε, το κλειδί είναι να ξεκινάτε ήπια με **lenient recovery mode**, ανεβάζοντας μόνο σε **strict recovery mode** όταν πραγματικά χρειάζεστε αυτή τη σκληρή επικύρωση. Καλή

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}