---
category: general
date: 2026-02-28
description: Πώς να εντοπίσετε τις γραμματοσειρές σε έγγραφα Word Java και να ελέγξετε
  τις ελλιπείς γραμματοσειρές ενεργοποιώντας τις προειδοποιήσεις. Μάθετε πώς να ενεργοποιείτε
  τις προειδοποιήσεις, να διαβάζετε τις προειδοποιήσεις και να φορτώνετε ένα έγγραφο
  Word σε Java.
draft: false
keywords:
- how to detect fonts
- check missing fonts
- how to enable warnings
- how to read warnings
- load word document java
language: el
og_description: Πώς να εντοπίζετε γρήγορα τις γραμματοσειρές σε έγγραφα Word με Java.
  Αυτός ο οδηγός δείχνει πώς να ενεργοποιείτε προειδοποιήσεις, να διαβάζετε προειδοποιήσεις
  και να ελέγχετε τις ελλιπείς γραμματοσειρές όταν φορτώνετε ένα έγγραφο Word σε Java.
og_title: Πώς να εντοπίσετε τις γραμματοσειρές σε έγγραφα Word με Java – Πλήρης οδηγός
tags:
- Java
- Aspose.Words
- Font Detection
title: Πώς να ανιχνεύσετε τις γραμματοσειρές σε έγγραφα Word με Java – Πλήρης οδηγός
url: /el/java/document-styling/how-to-detect-fonts-in-java-word-documents-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εντοπίσετε τις Γραμματοσειρές σε Έγγραφα Word Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να εντοπίσετε τις γραμματοσειρές** σε ένα αρχείο Word ενώ γράφετε κώδικα Java; Δεν είστε μόνοι—οι ελλιπείς γραμματοσειρές μπορούν να μετατρέψουν μια τέλεια μορφοποιημένη αναφορά σε ένα ακατάστατο μπερδεμένο κείμενο, και οι περισσότεροι προγραμματιστές ανακαλύπτουν το πρόβλημα μόνο αφού το έγγραφο έχει ήδη κυκλοφορήσει.  

Τα καλά νέα; Ενεργοποιώντας μια μόνο σημαία προειδοποίησης μπορείτε **να ελέγξετε τις ελλιπείς γραμματοσειρές** πριν γίνουν πρόβλημα. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα **πώς να ενεργοποιήσετε τις προειδοποιήσεις**, πώς να φορτώσετε ένα αρχείο DOCX, και στη συνέχεια **πώς να διαβάσετε τις προειδοποιήσεις** ώστε να γνωρίζετε πάντα ποιες γλύφες αντικαθίστανται.

Θα προσθέσουμε επίσης μερικές επιπλέον συμβουλές για τις **καλύτερες πρακτικές load word document java**, επειδή μια καθαρή φόρτωση είναι το θεμέλιο για αξιόπιστη ανίχνευση γραμματοσειρών. Έτοιμοι; Ας βουτήξουμε.

---

## Τι Θα Μάθετε

- **Ενεργοποίηση προειδοποιήσεων αντικατάστασης γραμματοσειρών** ώστε το Aspose.Words να σας ενημερώνει όταν δεν βρεθεί μια γραμματοσειρά.  
- **Φόρτωση εγγράφου Word σε Java** χρησιμοποιώντας το πιο πρόσφατο Aspose.Words for Java API.  
- **Ανάγνωση και ερμηνεία των μηνυμάτων προειδοποίησης** για να εντοπίσετε ακριβώς ποιες γραμματοσειρές λείπουν.  
- Ένα γρήγορο **utility ελέγχου ελλιπών γραμματοσειρών** που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο.  

Χωρίς εξωτερικά εργαλεία, χωρίς εικασίες—απλός κώδικας Java που μπορείτε να αντιγράψετε‑επικολλήσετε και να τρέξετε.

---

## Προαπαιτούμενα

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο στο σύστημά σας.  
- Maven ή Gradle για να κατεβάσετε την εξάρτηση Aspose.Words for Java.  
- Ένα αρχείο DOCX που ενδέχεται να αναφέρει γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας (θα το ονομάσουμε `input.docx`).  

Αν ήδη χρησιμοποιείτε Aspose.Words, τέλεια—παραλείψτε το βήμα της εξάρτησης. Διαφορετικά, προσθέστε αυτό στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- check for the latest version -->
</dependency>
```

Ή, για Gradle:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

---

## Βήμα 1 – Πώς να Εντοπίσετε τις Γραμματοσειρές Ενεργοποιώντας Προειδοποιήσεις Αντικατάστασης Γραμματοσειρών

Πριν ανοίξετε το έγγραφο, πείτε στο Aspose.Words **πώς να ενεργοποιήσετε προειδοποιήσεις** για ελλιπείς γραμματοσειρές. Είναι μια μιά γραμμή κώδικα, αλλά κάνει πολύ δουλειά στο παρασκήνιο.

```java
import com.aspose.words.*;

public class FontDetectionDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Enable font‑substitution warnings so missing fonts are reported
        FontSettings.getDefaultInstance()
                    .setWarnings(WarningSource.FONT_SUBSTITUTION, true);
        
        // The rest of the steps follow...
    }
}
```

**Γιατί είναι σημαντικό:**  
Το Aspose.Words αντικαθιστά σιωπηρά μια εναλλακτική γραμματοσειρά όταν η αρχική δεν είναι διαθέσιμη, εκτός αν ζητήσετε ρητά μια προειδοποίηση. Ορίζοντας το `WarningSource.FONT_SUBSTITUTION` σε `true`, κάθε φορά που η μηχανή δεν μπορεί να εντοπίσει τη ζητούμενη γραμματοσειρά θα προσθέτει ένα αντικείμενο `WarningInfo` στη συλλογή προειδοποιήσεων του εγγράφου. Αυτό είναι το θεμέλιο για **πώς να εντοπίσετε τις γραμματοσειρές** που λείπουν.

> **Συμβουλή επαγγελματία:** Αν σας ενδιαφέρουν μόνο συγκεκριμένες γραμματοσειρές, μπορείτε αργότερα να φιλτράρετε τις προειδοποιήσεις με βάση το `warningInfo.getDescription()`.

---

## Βήμα 2 – Φόρτωση Εγγράφου Word σε Java

Τώρα που το σύστημα προειδοποιήσεων είναι έτοιμο, φορτώστε το έγγραφο που θέλετε να ελέγξετε. Ο κατασκευαστής `Document` κάνει το βαρέως τύπου έργο, αλλά θυμηθείτε να το τυλίξετε σε `try‑catch` αν δουλεύετε με διαδρομές που παρέχονται από χρήστη.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Τι συμβαίνει στο παρασκήνιο;**  
Το Aspose.Words αναλύει το πακέτο DOCX, δημιουργεί ένα μοντέλο DOM‑όμοιο και—στην περίπτωσή μας—συλλέγει τυχόν προειδοποιήσεις αντικατάστασης γραμματοσειρών κατά τη φάση φόρτωσης. Αν το αρχείο είναι κατεστραμμένο, ρίχνεται εξαίρεση, την οποία μπορείτε να διαχειριστείτε για να εμφανίσετε φιλικό μήνυμα σφάλματος.

---

## Βήμα 3 – Ανάγνωση των Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Μετά τη φόρτωση, η συλλογή `document.getWarnings()` περιέχει κάθε προειδοποίηση που δημιουργήθηκε. Περάστε τη με βρόχο και θα έχετε μια σαφή λίστα με τις γραμματοσειρές που λείπουν.

```java
        // Step 3: Retrieve and display any font‑substitution warnings
        for (WarningInfo warningInfo : document.getWarnings()) {
            System.out.println("Font substitution: " + warningInfo.getDescription());
        }
    }
}
```

**Δείγμα εξόδου** (η κονσόλα σας μπορεί να φαίνεται έτσι):

```
Font substitution: Font 'Calibri' not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria Math' not found. Substituted with 'Times New Roman'.
```

Αυτή είναι η **διαδικασία ανάγνωσης προειδοποιήσεων** σε δράση—κάθε γραμμή σας λέει το όνομα της αρχικής γραμματοσειράς και την εναλλακτική που χρησιμοποιήθηκε.

![How to detect fonts output screenshot](https://example.com/images/font-warning-output.png "Console output showing how to detect fonts in Java")

*Κείμενο alt εικόνας:* *Έξοδος κονσόλας που δείχνει πώς να εντοπίσετε γραμματοσειρές σε έγγραφα Java Word.*

---

## Bonus – Πώς να Ελέγξετε Προγραμματιστικά τις Ελλιπείς Γραμματοσειρές

Αν χρειάζεστε μια επαναχρησιμοποιήσιμη μέθοδο που επιστρέφει μια λίστα με τις ελλιπείς γραμματοσειρές, τυλίξτε τον βρόχο σε μια βοηθητική συνάρτηση:

```java
import java.util.*;
import com.aspose.words.*;

public class FontUtils {

    /**
     * Returns a set of font names that were not found during document load.
     *
     * @param docPath path to the DOCX file
     * @return Set of missing font names (empty if all fonts are present)
     * @throws Exception if the file cannot be opened
     */
    public static Set<String> getMissingFonts(String docPath) throws Exception {
        // Ensure warnings are turned on (idempotent call)
        FontSettings.getDefaultInstance()
                    .setWarnings(WarningSource.FONT_SUBSTITUTION, true);

        Document doc = new Document(docPath);
        Set<String> missing = new HashSet<>();

        for (WarningInfo wi : doc.getWarnings()) {
            // Extract the original font name from the warning description
            // Typical format: "Font 'Calibri' not found..."
            String desc = wi.getDescription();
            int start = desc.indexOf('\'') + 1;
            int end   = desc.indexOf('\'', start);
            if (start > 0 && end > start) {
                missing.add(desc.substring(start, end));
            }
        }
        return missing;
    }

    // Quick demo
    public static void main(String[] args) throws Exception {
        Set<String> missing = getMissingFonts("YOUR_DIRECTORY/input.docx");
        if (missing.isEmpty()) {
            System.out.println("All fonts are available – no substitutions needed.");
        } else {
            System.out.println("Missing fonts detected: " + missing);
        }
    }
}
```

**Γιατί να το τυλίξετε;**  
Τώρα έχετε μια ενιαία κλήση που μπορείτε να ενσωματώσετε σε μονάδες δοκιμών, pipelines CI, ή σε μια μεγαλύτερη υπηρεσία δημιουργίας εγγράφων. Επίσης, δείχνει τη λογική **check missing fonts** χωρίς να χρειάζεται να ξαναγράψετε τον βρόχο προειδοποιήσεων κάθε φορά.

---

## Διαχείριση Ακραίων Περιπτώσεων

| Κατάσταση | Τι Πρέπει Να Κάνετε |
|-----------|----------------------|
| **Το έγγραφο χρησιμοποιεί προσαρμοσμένες ενσωματωμένες γραμματοσειρές** | Το Aspose.Words θα εξακολουθήσει να εκδίδει προειδοποίηση αν η ενσωματωμένη γραμματοσειρά δεν αναγνωρίζεται. Σκεφτείτε να ενσωματώσετε τη γραμματοσειρά απευθείας στο DOCX ή να διανείμετε το αρχείο γραμματοσειράς με την εφαρμογή σας. |
| **Μεγάλα έγγραφα (εκατοντάδες σελίδες)** | Η συλλογή προειδοποιήσεων μπορεί να μεγαλώσει· χρησιμοποιήστε `document.getWarnings().size()` για να εκτιμήσετε την επίπτωση στη μνήμη. |
| **Εκτέλεση σε headless server** | Δεν απαιτείται UI—οι προειδοποιήσεις είναι καθαρά κειμενικές, οπότε ο κώδικας λειτουργεί άψογα σε Docker containers ή agents CI. |
| **Πολλαπλά νήματα που φορτώνουν έγγραφα** | Το `FontSettings.getDefaultInstance()` είναι thread‑safe, αλλά μπορείτε να δημιουργήσετε ξεχωριστό `FontSettings` ανά νήμα για απομόνωση. |

---

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με αρχεία .doc (δυαδικά) ;**  
Α: Απόλυτα. Ο ίδιος κατασκευαστής `Document` διαχειρίζεται τόσο `.doc` όσο και `.docx`. Ο μηχανισμός προειδοποίησης είναι ανεξάρτητος από τη μορφή.

**Ε: Μπορώ να καταστείλω τις προειδοποιήσεις για γραμματοσειρές που ξέρω ότι θα αντικαταστήσω αργότερα;**  
Α: Ναι—καλέστε `FontSettings.getDefaultInstance().setWarnings(WarningSource.FONT_SUBSTITUTION, false)` μετά την καταγραφή των πληροφοριών που χρειάζεστε.

**Ε: Τι γίνεται αν θέλω να αντικαταστήσω αυτόματα μια ελλιπή γραμματοσειρά;**  
Α: Χρησιμοποιήστε `FontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MissingFont", "Arial")` πριν φορτώσετε το έγγραφο.

---

## Συμπέρασμα

Τώρα ξέρετε **πώς να εντοπίσετε τις γραμματοσειρές** σε έγγραφα Word Java, πώς να **ελέγξετε τις ελλιπείς γραμματοσειρές**, τα ακριβή βήματα για **πώς να ενεργοποιήσετε τις προειδοποιήσεις**, και τον πιο απλό τρόπο για **πώς να διαβάσετε τις προειδοποιήσεις** μετά το **load word document java**. Ενεργοποιώντας τη σημαία προειδοποίησης αντικατάστασης γραμματοσειρών, φορτώνοντας το DOCX και εξετάζοντας τη συλλογή προειδοποιήσεων, αποκτάτε πλήρη ορατότητα σε τυχόν κενά γραμματοσειρών πριν επηρεάσουν τους τελικούς χρήστες.

Στη συνέχεια, δοκιμάστε να επεκτείνετε τη βοηθητική μέθοδο ώστε να ενσωματώνει αυτόματα εναλλακτικές γραμματοσειρές ή να δημιουργεί αναφορά για την ομάδα QA. Μπορείτε επίσης να εξερευνήσετε τους **πίνακες αντικατάστασης γραμματοσειρών** του Aspose.Words για πιο λεπτομερή έλεγχο.  

Καλή προγραμματιστική δουλειά, και εύχομαι όλα τα έγγραφά σας να αποδίδουν ακριβώς όπως το θέλετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}