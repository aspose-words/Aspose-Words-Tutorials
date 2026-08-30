---
category: general
date: 2026-05-04
description: Μάθετε πώς οι επιλογές φόρτωσης του Aspose.Words μπορούν να ανακτήσουν
  κατεστραμμένα αρχεία Word, να χρησιμοποιήσουν λειτουργία ανάκτησης, να επισκευάσουν
  κατεστραμμένα docx και να υπολογίσουν τον αριθμό σελίδων του Word σε έναν ενιαίο
  οδηγό.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: el
og_description: Κατακτήστε τις επιλογές φόρτωσης του Aspose.Words για την αποκατάσταση
  κατεστραμμένων αρχείων Word, επιλέξτε τη σωστή λειτουργία ανάκτησης, επισκευάστε
  κατεστραμμένα docx και ανακτήστε τον αριθμό σελίδων.
og_title: aspose words loadoptions – Ανάκτηση Κατεστραμμένων Εγγράφων Word
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Ανάκτηση Κατεστραμμένων Εγγράφων Word σε Java
url: /el/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Ανάκτηση Κατεστραμμένων Εγγράφων Word σε Java

Ποτέ προσπαθήσατε να ανοίξετε ένα αρχείο Word που ξαφνικά αρνείται να φορτωθεί; Είναι εκείνη η αίσθηση χτυπήματος στην κοιλιά όταν ένας πελάτης σας στέλνει ένα **corrupted docx** και δεν έχετε ιδέα αν μπορείτε να το σώσετε. Τα καλά νέα; Με **aspose words loadoptions** μπορείτε να πείτε στην Aspose.Words ακριβώς πώς να συμπεριφέρεται όταν ένα έγγραφο είναι κατεστραμμένο, είτε να ρίξει μια εξαίρεση είτε να επιχειρήσει μια σιωπηλή διόρθωση.  

Σε αυτόν τον οδηγό θα περάσουμε από τη χρήση του `LoadOptions` για **recover corrupted Word** αρχεία, θα εξερευνήσουμε τις ρυθμίσεις **use recovery mode**, θα δούμε πώς να **repair corrupted docx** αυτόματα, και θα ολοκληρώσουμε με το **getting the word page count** του αποκατεστημένου εγγράφου. Χωρίς εξωτερικά εργαλεία, μόνο καθαρή Java και Aspose.Words.

## Τι Θα Χρειαστείτε

- **Aspose.Words for Java** (v24.12 ή νεότερη) – η τελευταία έκδοση προσθέτει μερικούς επιπλέον ελέγχους ασφαλείας.
- Ένα **Java IDE** (IntelliJ IDEA, Eclipse, ή ακόμη και ένας απλός επεξεργαστής κειμένου με `javac`).
- Το **corrupted DOCX** που θέλετε να δοκιμάσετε (θα το ονομάσουμε `Corrupted.docx`).
- Μια **βασική κατανόηση** της σύνταξης Java – τίποτα περίπλοκο, μόνο το συνηθισμένο `public static void main`.

> **Pro tip:** κρατήστε ένα αντίγραφο ασφαλείας του αρχικού αρχείου· οι προσπάθειες ανάκτησης μπορούν μερικές φορές να ξαναγράψουν μέρη του δυαδικού.

## Step 1: Create LoadOptions – the Core of Recovery

Το πρώτο πράγμα που κάνετε είναι να δημιουργήσετε ένα αντικείμενο `LoadOptions`. Αυτό το αντικείμενο είναι ο πίνακας ελέγχου σας· λέει στην Aspose.Words πώς να αντιμετωπίσει το αρχείο όταν συναντήσει προβλήματα.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Γιατί είναι κρίσιμο αυτό το βήμα; Επειδή χωρίς `LoadOptions` η βιβλιοθήκη επιστρέφει στην προεπιλεγμένη συμπεριφορά της, η οποία μπορεί σιωπηρά να αγνοήσει σφάλματα ή, χειρότερα, να επιστρέψει ένα μερικά‑φορτωμένο έγγραφο που θα καταρρεύσει αργότερα. Με την ρητή διαμόρφωση των επιλογών κερδίζετε καθορισμένη διαχείριση σφαλμάτων.

## Step 2: Choose the Right Recovery Mode

Η Aspose.Words προσφέρει δύο στρατηγικές ανάκτησης:

| Λειτουργία | Συμπεριφορά |
|------------|-------------|
| `RecoveryMode.STRICT` | Ρίχνει εξαίρεση εάν το έγγραφο δεν μπορεί να επισκευαστεί πλήρως. |
| `RecoveryMode.REPAIR` | Προσπαθεί να διορθώσει το αρχείο και συνεχίζει τη φόρτωση, ακόμη και αν χαθεί κάποιο περιεχόμενο. |

Για ένα σενάριο **recover corrupted word** όπου χρειάζεται να ξέρετε αν η διόρθωση πέτυχε, το `STRICT` είναι η πιο ασφαλής επιλογή. Αν προτιμάτε μια προσέγγιση καλύτερης προσπάθειας, αλλάξτε σε `REPAIR`.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Γιατί να διαλέξετε το ένα αντί του άλλου;**  
> *STRICT* σας δίνει ένα σαφές σήμα—είτε το έγγραφο είναι χρήσιμο είτε πρέπει να ειδοποιήσετε τον χρήστη. *REPAIR* είναι χρήσιμο σε εργασίες batch όπου μπορείτε να χάσετε μια τυχαία εικόνα ή δύο.

## Step 3: Load the Possibly‑Corrupted Document

Τώρα ανοίγετε πραγματικά το αρχείο, περνώντας το `LoadOptions` που μόλις διαμορφώσατε. Αν το αρχείο είναι πέρα από την επισκευή και επιλέξατε `STRICT`, μια εξαίρεση θα ανέβει· διαφορετικά θα λάβετε ένα αντικείμενο `Document` έτοιμο για επιθεώρηση.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Σημειώστε ότι η διαδρομή μπορεί να είναι απόλυτη ή σχετική με τη ρίζα του έργου σας. Η κλάση `Document` αφαιρεί την πολυπλοκότητα του πλήρους αρχείου Word, καθιστώντας εύκολο το ερώτημα για αριθμό σελίδων, ενότητες ή ακόμη και την επεξεργασία του περιεχομένου μετά την ανάκτηση.

## Step 4: Verify the Load – Get Word Page Count

Μια γρήγορη επιβεβαίωση είναι να ρωτήσετε την Aspose.Words πόσες σελίδες εκτιμά ότι έχει το έγγραφο. Αν ο αριθμός δεν είναι μηδέν, πιθανότατα έχετε **repair corrupted docx** με επιτυχία.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Τυπική έξοδος:

```
Loaded successfully, page count = 12
```

Αν το έγγραφο ήταν πραγματικά μη αναγνώσιμο υπό `STRICT`, ο κώδικας θα είχε ρίξει εξαίρεση πριν φτάσει σε αυτή τη γραμμή. Αυτό κάνει τον έλεγχο `page count` τόσο επαλήθευση όσο και χρήσιμη πληροφορία για λογική downstream (π.χ., σελιδοποίηση σε web viewer).

## Full Working Example

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα Java που ενώνει όλα τα κομμάτια. Αντιγράψτε‑και‑επικολλήστε το σε ένα αρχείο με όνομα `RecoveryModeDemo.java`, προσαρμόστε τη διαδρομή, και τρέξτε `javac RecoveryModeDemo.java && java RecoveryModeDemo`.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Expected Result

- **Αν το αρχείο είναι ανακτήσιμο:** η κονσόλα εκτυπώνει τον αριθμό σελίδων και μπορείτε με ασφάλεια να συνεχίσετε την επεξεργασία του αντικειμένου `Document`.
- **Αν το αρχείο είναι πέρα από την επισκευή (λειτουργία STRICT):** ρίχνεται ένα `com.aspose.words.UnsupportedFileFormatException` (ή παρόμοιο), το οποίο μπορείτε να πιάσετε και να το διαχειριστείτε με χάρη.

## Common Questions & Edge Cases

### What if I need to log the exact error details?

Τυλίξτε τον κώδικα φόρτωσης σε ένα μπλοκ `try‑catch` και καταγράψτε το `e.getMessage()`. Αυτό σας δίνει έναν σαφή λόγο—είτε είναι ένα ελλιπές τμήμα, μια σπασμένη σχέση, ή ένα κατεστραμμένο ρεύμα.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Can I recover only specific parts (like text but not images)?

Η Aspose.Words δεν εκθέτει λεπτομερείς επιλογές ανάκτησης, αλλά μετά τη φόρτωση μπορείτε να διατρέξετε τα στοιχεία `NodeType` και να απορρίψετε όσα είναι `NodeType.SHAPE` (εικόνες) εάν προκαλούν προβλήματα downstream.

### Does this work with older `.doc` files?

Ναι. Το `LoadOptions` λειτουργεί σε όλες τις μορφές Word (`.doc`, `.docx`, `.dot`, `.dotx`). Η ίδια λογική ανάκτησης ισχύει.

### How does the library handle password‑protected files?

Αν ένα αρχείο είναι κρυπτογραφημένο, το `LoadOptions` δεν παρακάμπτει τον κωδικό. Πρέπει να παρέχετε τον κωδικό μέσω `loadOptions.setPassword("yourPassword")`. Η λειτουργία ανάκτησης ενεργοποιείται μόνο μετά την επιτυχή αποκρυπτογράφηση.

## Tips for Production Use

- **Καταγράψτε τη επιλεγμένη λειτουργία ανάκτησης** – Βοηθά όταν αργότερα ελέγχετε γιατί ένα συγκεκριμένο αρχείο πέτυχε ή απέτυχε.
- **Ποτέ μην αντικαθιστάτε το αρχικό αρχείο** – Αποθηκεύστε το αποκατεστημένο έγγραφο σε νέα θέση (`document.save("Recovered.docx")`).
- **Συνδυάστε με επικύρωση** – Μετά την ανάκτηση, τρέξτε έναν γρήγορο ορθογραφικό ή δομικό έλεγχο για να διασφαλίσετε ότι το έγγραφο πληροί τους επιχειρηματικούς σας κανόνες.
- **Επεξεργασία batch** – Όταν διαχειρίζεστε πολλά αρχεία, κάντε βρόχο πάνω τους, πιάστε τις εξαιρέσεις ξεχωριστά, και κρατήστε μια σύνοψη επιτυχιών vs. αποτυχιών.

## Conclusion

Τώρα έχετε μια στέρεη, από‑αρχή‑μέχρι‑τέλος συνταγή για τη χρήση του **aspose words loadoptions** ώστε να **recover corrupted Word** έγγραφα, να αποφασίσετε αν θα **use recovery mode** αυστηρά ή επιεικώς, προαιρετικά να **repair corrupted docx**, και τέλος να **get the word page count** του αποκατεστημένου αρχείου. Η προσέγγιση είναι καθοριστική, εύκολη στην ενσωμάτωση σε υπάρχουσες pipelines Java, και σας δίνει πλήρη έλεγχο στο πόσο επιθετική πρέπει να είναι η βιβλιοθήκη όταν αντιμετωπίζει σπασμένα δυαδικά.

Έτοιμοι να προχωρήσετε παραπέρα; Δοκιμάστε να αλλάξετε το `RecoveryMode.STRICT` σε `REPAIR` σε μια εργασία batch, ή επεκτείνετε το παράδειγμα ώστε να αποθηκεύει αυτόματα το διορθωμένο αρχείο σε ασφαλή φάκελο. Οι δυνατότητες είναι ατελείωτες, και με την Aspose.Words είστε εξοπλισμένοι να αντιμετωπίσετε ακόμη και τα πιο επίμονα σφάλματα αρχείων Word.

Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας πάντα να φορτώνουν καθαρά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}