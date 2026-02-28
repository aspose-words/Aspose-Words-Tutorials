---
category: general
date: 2026-02-28
description: Μάθετε πώς να ανακτήσετε αρχεία DOCX χρησιμοποιώντας τη λειτουργία ανάκτησης
  του Aspose.Words. Περιλαμβάνει συμβουλές για την ανάκτηση εγγράφων Word, παραδείγματα
  ρύθμισης της λειτουργίας ανάκτησης και πλήρες κώδικα Java.
draft: false
keywords:
- how to recover docx
- recover word document
- set recovery mode
- Aspose.Words recovery
- Java document loading
language: el
og_description: Πώς να ανακτήσετε γρήγορα αρχεία DOCX με το Aspose.Words. Αυτό το
  σεμινάριο δείχνει πώς να ορίσετε τη λειτουργία ανάκτησης, να φορτώσετε κατεστραμμένα
  αρχεία και να διαχειριστείτε τις προειδοποιήσεις.
og_title: Πώς να ανακτήσετε αρχεία DOCX με το Aspose.Words – Πλήρης οδηγός
tags:
- Aspose.Words
- Java
- Document Processing
title: Πώς να ανακτήσετε αρχεία DOCX με το Aspose.Words – Οδηγός βήμα‑προς‑βήμα
url: /el/java/document-loading-and-saving/how-to-recover-docx-files-with-aspose-words-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε Αρχεία DOCX με το Aspose.Words – Πλήρης Οδηγός

Έχετε ανοίξει ποτέ ένα έγγραφο Word μόνο για να αντιμετωπίσετε ένα ακατανόητο μήνυμα σφάλματος; Αν χρειάζεστε να **ανακτήσετε ένα DOCX** αρχείο που αρνείται να φορτωθεί, η εκμάθηση του **πώς να ανακτήσετε DOCX** με το Aspose.Words είναι η πιο γρήγορη λύση. Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που **ανακτά ένα έγγραφο Word** ενώ σας δίνει πλήρη έλεγχο του τρόπου ανάκτησης.

Φανταστείτε ότι δημιουργείτε ένα αυτοματοποιημένο σύστημα email που αντλεί πρότυπα από έναν κοινόχρηστο φάκελο. Μια μέρα ένα πρότυπο καταστρέφεται—χωρίς στρατηγική ανάκτησης ολόκληρη η αλυσίδα σας σταματά. Καμία ανησυχία· τα παρακάτω βήματα θα σας επαναφέρουν σε λειτουργία μέσα σε λίγα λεπτά.

Θα καλύψουμε όλα όσα χρειάζεται να γνωρίζετε:

* Ορισμός του σωστού τρόπου ανάκτησης (`set recovery mode`)  
* Φόρτωση ενός κατεστραμμένου αρχείου με ασφάλεια  
* Επιθεώρηση προειδοποιήσεων για να αποφασίσετε αν το ανακτημένο έγγραφο είναι επαρκές  

Δεν απαιτούνται εξωτερικά έγγραφα—μόνο ο κώδικας που μπορείτε να αντιγράψετε‑επικολλήσετε στο IDE σας.

---

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

* **Java 17** (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο  
* **Aspose.Words for Java** βιβλιοθήκη (έκδοση 23.12 ή νεότερη) στο classpath σας  
* Ένα **κατεστραμμένο DOCX** αρχείο για δοκιμή (μπορείτε να το καταστρέψετε σκόπιμα αφαιρώντας μερικά bytes με έναν επεξεργαστή hex)  

Αυτό είναι όλο. Αν είστε ήδη εξοικειωμένοι με Maven ή Gradle, η προσθήκη της εξάρτησης είναι παιχνιδάκι:

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

```groovy
// Gradle
implementation 'com.aspose:aspose-words:23.12'
```

---

## Πώς να Ανακτήσετε DOCX Χρησιμοποιώντας LoadOptions

Η καρδιά της λύσης βρίσκεται στο **LoadOptions**, μια κλάση που σας επιτρέπει να πείτε στο Aspose.Words πώς να συμπεριφέρεται όταν αντιμετωπίζει προβλήματα. Από προεπιλογή η βιβλιοθήκη ρίχνει εξαίρεση στην πρώτη ένδειξη προβλήματος, αλλά μπορούμε να της ζητήσουμε να *ανακτήσει με προειδοποιήσεις*.

```java
import com.aspose.words.*;

public class LoadCorruptedDocument {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions and enable recovery with warnings
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
        // (Alternatively, use RECOVER_WITHOUT_WARNINGS to suppress warnings)

        // Step 2: Load the corrupted document using the configured options
        Document corruptedDoc = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);

        // Step 3: Retrieve and display the number of warnings generated during loading
        int warningsCount = corruptedDoc.getWarnings().size();
        System.out.println("Loaded with warnings: " + warningsCount);
    }
}
```

**Γιατί λειτουργεί αυτό:**

*`LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS`* λέει στη μηχανή να συνεχίσει την ανάλυση του αρχείου ακόμη και όταν συναντήσει κατεστραμμένο XML, ελλιπή μέρη ή σπασμένες σχέσεις. Αντί να διακόψει, το Aspose.Words συλλέγει κάθε σφάλμα στη συλλογή `Document.getWarnings()`. Αυτό σας προσφέρει μια εμπειρία **recover word document** που είναι τόσο ασφαλής όσο και διαφανής.

---

## Ορισμός Τρόπου Ανάκτησης – Επιλέξτε τη Σωστή Επιλογή

Υπάρχουν τρεις τρόποι ανάκτησης που μπορείτε να επιλέξετε:

| Mode | Συμπεριφορά | Πότε να το χρησιμοποιήσετε |
|------|-------------|---------------------------|
| `RECOVER_WITH_WARNINGS` | Φορτώνει όσο το δυνατόν περισσότερο **και** καταγράφει κάθε πρόβλημα. | Θέλετε να ελέγξετε τα προβλήματα μετά τη φόρτωση (προεπιλογή για αποσφαλμάτωση). |
| `RECOVER_WITHOUT_WARNINGS` | Παραλείπει σιωπηλά τα προβληματικά τμήματα. | Χρειάζεστε ένα καθαρό, χωρίς προειδοποιήσεις έγγραφο και μπορείτε να ανεχθεί η απώλεια δεδομένων. |
| `NO_RECOVERY` (default) | Ρίχνει εξαίρεση στην πρώτη σφάλμα. | Προτιμάτε μια σκληρή αποτυχία για να εγγυηθείτε την ακεραιότητα του εγγράφου. |

Αν δημιουργείτε μια υπηρεσία **recover word document** που καταγράφει κάθε ανωμαλία, παραμείνετε στο `RECOVER_WITH_WARNINGS`. Για μια εργασία παρτίδας στο παρασκήνιο που ενδιαφέρεται μόνο για ένα χρησιμοποιήσιμο αποτέλεσμα, το `RECOVER_WITHOUT_WARNINGS` μπορεί να είναι η καλύτερη επιλογή.

**Συμβουλή:** Πάντα να καταγράφετε τον αριθμό των προειδοποιήσεων και, όταν είναι δυνατόν, τα μεμονωμένα μηνύματα (`doc.getWarnings().forEach(System.out::println);`). Αυτό το μικρό βήμα σας εξοικονομεί ώρες επίλυσης μυστηρίων αργότερα.

---

## Φόρτωση του Κατεστραμμένου Εγγράφου

Ο κατασκευαστής `Document` που βλέπετε στο απόσπασμα κώδικα κάνει δύο πράγματα ταυτόχρονα:

1. **Διαβάζει το αρχείο** από τη διαδρομή που παρέχετε (`"YOUR_DIRECTORY/corrupted.docx"`).  
2. **Εφαρμόζει το LoadOptions** που διαμορφώσατε νωρίτερα.

Επειδή περάσαμε το αντικείμενο `loadOptions`, το Aspose.Words εσωτερικά αλλάζει στον τρόπο ανάκτησης που ορίσατε. Αν ξεχάσετε να παρέχετε τις επιλογές, η βιβλιοθήκη θα επιστρέψει στην προεπιλογή `NO_RECOVERY` και θα ρίξει εξαίρεση.

**Ακραία περίπτωση:** Μεγάλα αρχεία (εκατοντάδες megabytes) μπορούν να προκαλέσουν σφάλματα έλλειψης μνήμης κατά την ανάκτηση. Για να το μετριάσετε, ενεργοποιήστε τη **memory‑optimized loading**:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setMemoryOptimization(true);
```

Τώρα η μηχανή μεταδίδει το αρχείο αντί να φορτώνει τα πάντα στη μνήμη RAM—ένας χρήσιμος κόλπος όταν **recover a DOCX** που είναι επίσης τεράστιο.

---

## Επιθεώρηση Προειδοποιήσεων και Τελικοί Έλεγχοι

Αφού φορτωθεί το έγγραφο, θα θέλετε να γνωρίζετε αν το ανακτημένο περιεχόμενο είναι χρήσιμο. Το `warningsCount` που εκτυπώσαμε νωρίτερα είναι ένας γρήγορος δείκτης υγείας, αλλά μπορείτε να εμβαθύνετε:

```java
if (warningsCount > 0) {
    System.out.println("Document loaded with warnings. Review details:");
    for (WarningInfo warning : corruptedDoc.getWarnings()) {
        System.out.println("- " + warning.getWarningType() + ": " + warning.getDescription());
    }
} else {
    System.out.println("Document loaded cleanly—no warnings reported.");
}
```

Τυπικές προειδοποιήσεις περιλαμβάνουν:

* **Missing part** – ένα εσωτερικό τμήμα XML δεν βρέθηκε.  
* **Invalid relationship** – ένας υπερσύνδεσμος δείχνει σε ανύπαρκτο στόχο.  
* **Corrupt image data** – μια ενσωματωμένη εικόνα δεν μπόρεσε να αποκωδικοποιηθεί.

Αν οι προειδοποιήσεις είναι ακίνδυνες (π.χ., ένα ελλιπές σχόλιο), μπορείτε με ασφάλεια να αποθηκεύσετε το έγγραφο:

```java
corruptedDoc.save("recovered.docx");
System.out.println("Recovered file saved as recovered.docx");
```

**Τι γίνεται αν ο αριθμός των προειδοποιήσεων είναι τεράστιος;** Μπορεί να αποφασίσετε να επιστρέψετε σε διαφορετική στρατηγική, όπως η μετατροπή του αρχείου πρώτα σε PDF (`Document.save("temp.pdf", SaveFormat.PDF)`) και μετά ξανά σε DOCX, κάτι που μερικές φορές εξαναγκάζει μια καθαρή ανακατασκευή της εσωτερικής δομής.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Εκτέλεση)

Παρακάτω είναι το **πλήρες, εκτελέσιμο πρόγραμμα** που συνδυάζει όλα όσα συζητήσαμε. Απλώς αντικαταστήστε το `"YOUR_DIRECTORY/corrupted.docx"` με τη διαδρομή του κατεστραμμένου αρχείου σας.

```java
import com.aspose.words.*;

public class LoadCorruptedDocument {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and enable recovery with warnings
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);
        // Optional: enable memory‑optimized loading for big files
        // loadOptions.setMemoryOptimization(true);

        // 2️⃣ Load the corrupted DOCX using the configured options
        Document corruptedDoc = new Document("YOUR_DIRECTORY/corrupted.docx", loadOptions);

        // 3️⃣ Check how many warnings were generated
        int warningsCount = corruptedDoc.getWarnings().size();
        System.out.println("Loaded with warnings: " + warningsCount);

        // 4️⃣ If there are warnings, print each one for debugging
        if (warningsCount > 0) {
            System.out.println("Warning details:");
            for (WarningInfo warning : corruptedDoc.getWarnings()) {
                System.out.println("- " + warning.getWarningType() + ": " + warning.getDescription());
            }
        } else {
            System.out.println("Document loaded cleanly—no warnings reported.");
        }

        // 5️⃣ Save the recovered document (you can change the format if needed)
        corruptedDoc.save("recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
Loaded with warnings: 2
Warning details:
- MissingPart: The part 'word/footer1.xml' could not be found.
- InvalidRelationship: Relationship ID 'rId5' points to a non‑existent target.
Recovered file saved as recovered.docx
```

Ακόμη και αν λείπουν δύο τμήματα, το υπόλοιπο του εγγράφου επέζησε και αποθηκεύτηκε επιτυχώς.

---

## Συχνές Ερωτήσεις & Γρήγορες Απαντήσεις

* **Ε: Λειτουργεί αυτό με αρχεία .doc;**  
  Α: Ναι—απλώς αλλάξτε την επέκταση του αρχείου και το Aspose.Words θα ανιχνεύσει αυτόματα τη μορφή. Μπορείτε επίσης να το εξαναγκάσετε με `loadOptions.setLoadFormat(LoadFormat.DOC);`.

* **Ε: Τι γίνεται αν χρειαστεί να καταστέλλω τις προειδοποιήσεις εντελώς;**  
  Α: Μεταβείτε σε `RECOVER_WITHOUT_WARNINGS`. Η μηχανή θα παραλείψει σιωπηλά τα προβληματικά τμήματα.

* **Ε: Μπορώ να ανακτήσω ένα προστατευμένο με κωδικό DOCX;**  
  Α: Πρώτα ξεκλειδώστε το χρησιμοποιώντας `LoadOptions.setPassword("yourPassword");` και μετά εφαρμόστε τον τρόπο ανάκτησης.

* **Ε: Υπάρχει όριο στον αριθμό των προειδοποιήσεων που θα συλλέξει το Aspose.Words;**  
  Α: Δεν υπάρχει σκληρό όριο· ωστόσο, εξαιρετικά κατεστραμμένα αρχεία μπορεί να δημιουργήσουν χιλιάδες καταχωρήσεις, κάτι που μπορεί να επηρεάσει την απόδοση. Σκεφτείτε να καταγράφετε μόνο τις πρώτες 100 προειδοποιήσεις στην παραγωγή.

---

## Συμπέρασμα

Τώρα ξέρετε **πώς να ανακτήσετε DOCX** αρχεία με το Aspose.Words, πώς να **ορίσετε τον τρόπο ανάκτησης** ώστε να ταιριάζει στο σενάριό σας, και πώς να **επιθεωρήσετε τις προειδοποιήσεις** για να αποφασίσετε αν το ανακτημένο έγγραφο πληροί τα πρότυπά σας. Είτε δημιουργείτε έναν επεξεργαστή παρτίδας που **ανακτά έγγραφα word** κάθε νύχτα είτε μια υπηρεσία σε πραγματικό χρόνο για χρήστες, το μοτίβο παραμένει το ίδιο: διαμορφώστε το `LoadOptions`, φορτώστε, ελέγξτε τις προειδοποιήσεις και αποθηκεύστε.

Επόμενα βήματα; Δοκιμάστε να αλλάξετε τη μορφή εξόδου σε PDF, HTML ή ακόμη και απλό κείμενο για να δείτε πώς η ανάκτηση συμπεριφέρεται σε διαφορετικές μετατροπές. Μπορείτε επίσης να εξερευνήσετε την κλάση `DocumentBuilder` για να διορθώσετε προγραμματιστικά κοινά προβλήματα (π.χ., προσθήκη ελλιπών κεφαλίδων) πριν την αποθήκευση.

Νιώστε ελεύθεροι να πειραματιστείτε, να μοιραστείτε τα ευρήματά σας ή να θέσετε περαιτέρω ερωτήσεις στα σχόλια. Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας να παραμείνουν υγιή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}