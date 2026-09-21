---
category: general
date: 2026-02-15
description: Η λειτουργία ανάκτησης επιτρέπει τη φόρτωση του εγγράφου με ανάκτηση,
  καθιστώντας εύκολη την αποκατάσταση ενός κατεστραμμένου εγγράφου Word και τη διόρθωση
  σφαλμάτων ανάκτησης εγγράφου Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: el
og_description: Η ρύθμιση της λειτουργίας ανάκτησης είναι το κλειδί για τη φόρτωση
  ενός εγγράφου με ανάκτηση, επιτρέποντάς σας να διορθώσετε σφάλματα σπασμένων εγγράφων
  Word σε Java.
og_title: Ορίστε τη λειτουργία ανάκτησης – Ανακτήστε γρήγορα ένα κατεστραμμένο έγγραφο
  Word
tags:
- Aspose.Words
- Java
- Document Recovery
title: Ορίστε τη λειτουργία ανάκτησης για την αποκατάσταση κατεστραμμένου εγγράφου
  Word
url: /el/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Πώς να ανακτήσετε ένα κατεστραμμένο αρχείο Word με Aspose.Words

Ποτέ προσπαθήσατε να ανοίξετε ένα αρχείο Word που ξαφνικά αρνείται να φορτωθεί; Μπορεί να κοιτάζετε ένα κατεστραμμένο *.docx* και να αναρωτιέστε αν πρέπει να ξεκινήσετε από την αρχή. Τα καλά νέα; **set recovery mode** στο Aspose.Words σας παρέχει έναν ευγενικό τρόπο να *load document with recovery* και να διατηρήσετε το μεγαλύτερο μέρος του περιεχομένου ανέπαφο.  

Σε αυτό το tutorial θα μάθετε ακριβώς πώς να **set recovery mode**, γιατί η επιλογή *RELAXED* είναι συνήθως η καλύτερη για κατεστραμμένα αρχεία, και πώς να διαχειριστείτε τα περιστασιακά *recover word document errors* που εξακολουθούν να εμφανίζονται. Χωρίς εξωτερικά εργαλεία, μόνο απλή Java και μερικές γραμμές κώδικα.

> **Τι θα αποκομίσετε:** ένα πλήρες, εκτελέσιμο παράδειγμα που φορτώνει ένα κατεστραμμένο αρχείο Word, παραλείπει τα μη αναγνώσιμα τμήματα, και σας αφήνει με ένα χρησιμοποιήσιμο αντικείμενο `Document` έτοιμο για περαιτέρω επεξεργασία.

---

## Προαπαιτούμενα

Πριν προχωρήσουμε, βεβαιωθείτε ότι έχετε:

- **Aspose.Words for Java** (v24.9 ή νεότερο) προστέθηκε στο έργο σας μέσω Maven ή χειροκίνητου JAR.
- Ένα **corrupted .docx** αρχείο που θέλετε να δοκιμάσετε (θα το ονομάσουμε `Corrupted.docx`).
- Βασικές γνώσεις Java – δεν χρειάζεται να είστε μάγος επεξεργασίας Word, απλώς άνετοι με μια μέθοδο `main`.

Αν λείπει κάτι από αυτά, κατεβάστε το τελευταίο Aspose.Words JAR από την [official site](https://products.aspose.com/words/java) και προσθέστε το στο classpath σας. Αυτό είναι όλο—χωρίς επιπλέον εξαρτήσεις.

---

## Βήμα 1: Κατανόηση των Recovery Modes

Aspose.Words προσφέρει δύο στρατηγικές ανάκτησης:

| Λειτουργία | Συμπεριφορά | Πότε να χρησιμοποιηθεί |
|------------|--------------|------------------------|
| **RELAXED** | Παραλείπει τα μη αναγνώσιμα τμήματα, διατηρεί το υπόλοιπο. | Τα περισσότερα κατεστραμμένα αρχεία – θέλετε **recover broken word document** χωρίς εξαίρεση. |
| **STRICT** | Ρίχνει εξαίρεση σε οποιοδήποτε σφάλμα. | Όταν χρειάζεται να εγγυηθείτε μια τέλεια, χωρίς σφάλματα φόρτωση (σπάνιο για κατεστραμμένες πηγές). |

> **Συμβουλή:** *RELAXED* είναι η προεπιλογή για σενάρια “απλώς να πάρετε κάτι πίσω”, ενώ *STRICT* είναι χρήσιμο σε αυτοματοποιημένες διαδικασίες όπου μια αποτυχία πρέπει να σταματήσει τη διαδικασία.

---

## Βήμα 2: Δημιουργήστε ένα αντικείμενο `LoadOptions` και **set recovery mode**

Εδώ είναι που εμφανίζεται η κύρια λέξη-κλειδί στον κώδικα. Θέτουμε ρητά **set recovery mode** σε ένα αντικείμενο `LoadOptions` πριν φορτώσουμε το αρχείο.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Γιατί είναι σημαντικό:** Καλώντας το `setRecoveryMode`, λέτε στο Aspose.Words πόσο επιθετικά πρέπει να προσπαθήσει να διασώσει το αρχείο. Χωρίς αυτήν την κλήση η βιβλιοθήκη προεπιλέγει *STRICT*, που θα διακόψει στην πρώτη ένδειξη προβλήματος—αναιρώντας το σκοπό μιας ροής εργασίας *recover broken word document*.

---

## Βήμα 3: Επαληθεύστε τη φόρτωση – Ανακτήσαμε πραγματικά **recover broken word document**;

Μετά τη φόρτωση, μπορείτε να ελέγξετε το αντικείμενο `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Αν η κονσόλα εμφανίζει λογικό αριθμό ενοτήτων, έχετε φορτώσει επιτυχώς *load document with recovery*. Στην πράξη, θα παρατηρήσετε ότι το μεγαλύτερο μέρος του κειμένου, των πινάκων και των εικόνων παραμένει, ενώ τα κατεστραμμένα τμήματα απλώς εξαφανίζονται.

---

## Βήμα 4: Διαχειριστείτε τα υπόλοιπα **recover word document errors** με χάρη

Ακόμα και με τη λειτουργία *RELAXED*, μερικές ειδικές περιπτώσεις μπορούν ακόμη να προκαλέσουν προειδοποιήσεις. Τυλίξτε τη φόρτωση σε try‑catch για να κρατήσετε την εφαρμογή σας ζωντανή:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Πότε μπορεί να συμβεί αυτό;** Αν το αρχείο είναι τόσο κατεστραμμένο ώστε ακόμη και ένας relaxed parser δεν μπορεί να εντοπίσει μια έγκυρη δομή εγγράφου, το Aspose.Words θα εξακολουθήσει να ρίχνει εξαίρεση. Σε αυτές τις σπάνιες περιπτώσεις, ίσως χρειαστεί να ζητήσετε από τον χρήστη να παρέχει ένα διαφορετικό αντίγραφο.

---

## Βήμα 5: Αποθήκευση του Ανακτηθέντος Αρχείου (Προαιρετικό)

Οι περισσότεροι προγραμματιστές θέλουν μια καθαρή έκδοση για να τη μεταβιβάσουν σε downstream συστήματα. Η κλήση `save` παρακάτω γράφει ένα νέο `.docx` που δεν περιέχει πλέον τα κατεστραμμένα τμήματα.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Τώρα έχετε ένα **recover broken word document** που μπορεί να ανοίξει στο Microsoft Word, Google Docs ή οποιονδήποτε άλλο προβολέα—χωρίς διαλόγους σφάλματος.

---

## Οπτική Επισκόπηση (Εικόνα)

![Διάγραμμα που δείχνει τη ροή set recovery mode – από το κατεστραμμένο αρχείο στο ανακτηθέν έγγραφο](https://example.com/images/recovery-flow.png "διάγραμμα ροής set recovery mode")

*Το κείμενο alt περιέχει ρητά τη βασική λέξη-κλειδί, βοηθώντας τόσο τις μηχανές αναζήτησης όσο και τους αναγνώστες οθόνης.*

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|----------|
| *Τι γίνεται αν χρειάζεται να διατηρήσω τα κατεστραμμένα τμήματα για δικαστική ανάλυση;* | Χρησιμοποιήστε `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` και πιάστε την εξαίρεση. Το μήνυμα της εξαίρεσης περιέχει λεπτομέρειες για τα προβληματικά τμήματα. |
| *Μπορώ να εναλλάξω μεταξύ RELAXED και STRICT κατά το χρόνο εκτέλεσης;* | Φυσικά—απλώς δημιουργήστε ένα νέο αντικείμενο `LoadOptions` με τη ζητούμενη λειτουργία πριν από κάθε φόρτωση. |
| *Λειτουργεί αυτό με παλαιότερα αρχεία .doc;* | Ναι. Το ίδιο `LoadOptions` ισχύει και για μορφές `.doc` και `.docx`. |
| *Υπάρχει κάποια ποινή απόδοσης;* | Ελάχιστη. Το επιπλέον κόστος ανάλυσης είναι αμελητέο σε σχέση με το κόστος μιας πλήρους φόρτωσης εγγράφου. |

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Εκτελέστε το πρόγραμμα, δείξτε το στο κατεστραμμένο αρχείο σας, και παρακολουθήστε την έξοδο. Αν όλα πήγαν ομαλά, θα δείτε τον αριθμό σελίδων να εκτυπώνεται και ένα νέο `Recovered.docx` να εμφανίζεται δίπλα στην πηγή σας.

---

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **set recovery mode** στο Aspose.Words, από την επιλογή του κατάλληλου enum `RecoveryMode` μέχρι τη διαχείριση των λίγων *recover word document errors* που μπορεί ακόμη να εμφανιστούν. Ακολουθώντας τα παραπάνω βήματα μπορείτε αξιόπιστα να **load document with recovery**, να διατηρήσετε τα καλά τμήματα ενός κατεστραμμένου αρχείου, και να εξάγετε μια καθαρή έκδοση έτοιμη για οποιαδήποτε downstream επεξεργασία.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να συνδυάσετε **set recovery mode** με τα APIs **document cleaning** του Aspose.Words—αφαιρώντας κρυφές παραγράφους, διορθώνοντας σπασμένους συνδέσμους, ή ακόμη και μετατρέποντας το ανακτηθέν αρχείο σε PDF με ένα βήμα. Οι δυνατότητες είναι ατελείωτες, και τώρα έχετε μια σταθερή βάση για να αντιμετωπίσετε άμεσα τα κατεστραμμένα αρχεία Word.

Καλό κώδικα, και εύχομαι τα έγγραφά σας να παραμείνουν υγιή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}