---
category: general
date: 2026-04-28
description: Επανάληψη των προειδοποιήσεων εγγράφου σε ένα αρχείο Word για τον εντοπισμό
  ελλιπών γραμματοσειρών, ανάκτηση των ονομάτων των ελλιπών γραμματοσειρών και εκτύπωση
  των λεπτομερειών των ελλιπών γραμματοσειρών χρησιμοποιώντας το Aspose.Words for
  Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: el
og_description: Διατρέξτε τις προειδοποιήσεις του εγγράφου για να βρείτε τις ελλιπείς
  γραμματοσειρές, ανακτήστε τα ονόματα των ελλιπών γραμματοσειρών και εκτυπώστε τις
  λεπτομέρειες των ελλιπών γραμματοσειρών με ένα πλήρες παράδειγμα Java.
og_title: 'Επανάληψη προειδοποιήσεων εγγράφου: Εντοπισμός ελλειπόντων γραμματοσειρών
  σε Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Επανάληψη προειδοποιήσεων εγγράφου: Εντοπισμός ελλειπόντων γραμματοσειρών
  σε Java'
url: /el/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Επανάληψη προειδοποιήσεων εγγράφου – Ανίχνευση ελλιπών γραμματοσειρών σε Java

Έχετε ποτέ χρειαστεί να **iterate document warnings** κατά το άνοιγμα ενός αρχείου Word και να αναρωτηθείτε ποιες γραμματοσειρές λείπουν; Δεν είστε ο μόνος. Οι ελλιπείς γραμματοσειρές μπορούν να χαλάσουν την εμφάνιση μιας αναφοράς, και χωρίς τρόπο να τις εντοπίσετε μπορεί να στείλετε ένα έγγραφο που δεν μοιάζει καθόλου με το πρωτότυπο.  

Σε αυτό το tutorial θα σας δείξουμε πώς να **detect missing fonts** φορτώνοντας ένα έγγραφο Word, επαναλαμβάνοντας τις προειδοποιήσεις του, ανακτώντας τα ονόματα των ελλιπών γραμματοσειρών και τελικά εκτυπώνοντας τις πληροφορίες των ελλιπών γραμματοσειρών — όλα με το Aspose.Words for Java.  

Θα καλύψουμε τα πάντα, από την πρώτη γραμμή κώδικα μέχρι την αναμενόμενη έξοδο της κονσόλας, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε μια λειτουργική λύση στο έργο σας αμέσως. Δεν απαιτούνται επιπλέον έγγραφα.

## Προαπαιτούμενα

- Java 8 ή νεότερη εγκατεστημένη.
- Βιβλιοθήκη Aspose.Words for Java (η τελευταία έκδοση μέχρι 2026‑04‑28).
- Ένα αρχείο Word που ενδέχεται να περιέχει γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας (π.χ., `doc-with-missing-font.docx`).

Αν έχετε ήδη αυτά, υπέροχα—είστε έτοιμοι να **load word document** και να ξεκινήσετε την επανάληψη.

## Βήμα 1 – Φόρτωση εγγράφου Word με προεπιλεγμένες επιλογές

Πριν μπορέσουμε να **iterate document warnings**, το αρχείο πρέπει να φορτωθεί στη μνήμη. Το Aspose.Words σας επιτρέπει να το κάνετε αυτό με μία κλήση κατασκευής. Η χρήση των προεπιλεγμένων `LoadOptions` είναι συνήθως αρκετή, αλλά θα δείξουμε τη ρητή δημιουργία για σαφήνεια.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Γιατί είναι σημαντικό:**  
> Η φόρτωση του εγγράφου προκαλεί το Aspose.Words να σαρώσει το αρχείο για οποιουσδήποτε πόρους που δεν μπορεί να επιλύσει, όπως γραμματοσειρές που δεν είναι εγκατεστημένες τοπικά. Αυτά τα προβλήματα αποθηκεύονται ως **warnings**, τα οποία θα **iterate document warnings** στο επόμενο βήμα.

## Βήμα 2 – Επανάληψη προειδοποιήσεων εγγράφου για εντοπισμό προβλημάτων γραμματοσειρών

Τώρα έρχεται η καρδιά της λύσης: διατρέχουμε κάθε προειδοποίηση που συνέλεξε η βιβλιοθήκη κατά τη φόρτωση. Τα αντικείμενα `WarningInfo` μας λένε τι πήγε στραβά, και μπορούμε να φιλτράρουμε για `FontSubstitutionWarning` ώστε να **detect missing fonts**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Συμβουλή:** Ο έλεγχος `instanceof` εξασφαλίζει ότι χειριζόμαστε μόνο προειδοποιήσεις σχετικές με γραμματοσειρές, αγνοώντας άλλες όπως προβλήματα φόρτωσης εικόνας. Αυτό κάνει τη βρόχο αποδοτικό και διατηρεί την έξοδο εστιασμένη στις γραμματοσειρές για τις οποίες πραγματικά χρειάζεστε πληροφορίες **retrieve missing font**.

### Αναμενόμενη έξοδος κονσόλας

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Αν το έγγραφο δεν περιέχει ελλιπείς γραμματοσειρές, η βρόχος ολοκληρώνεται σιωπηλά—τίποτα για **print missing font**.

## Βήμα 3 – Γιατί να μην πιάσουμε απλώς μια εξαίρεση;

Μπορεί να αναρωτιέστε, “Γιατί να μην τυλίξουμε την κλήση `new Document(...)` σε try‑catch και να ψάξουμε για εξαίρεση?” Η απάντηση είναι διπλή:

1. **Λεπτομερείς πληροφορίες:** Οι εξαιρέσεις σας λένε μόνο ότι κάτι απέτυχε. Οι προειδοποιήσεις σας δίνουν το ακριβές όνομα της γραμματοσειράς και το εναλλακτικό που επέλεξε το Aspose.Words.
2. **Μη‑θανάσιμα ζητήματα:** Οι ελλιπείς γραμματοσειρές είναι συνήθως μη‑θανάσιμες· το έγγραφο φορτώνεται, αλλά η οπτική πιστότητα επηρεάζεται. Με το **iterating document warnings**, διατηρείτε τη δυνατότητα επεξεργασίας του υπόλοιπου αρχείου.

## Βήμα 4 – Επέκταση του παραδείγματος: Συλλογή ελλιπών γραμματοσειρών σε λίστα

Μερικές φορές χρειάζεστε τις ελλιπείς γραμματοσειρές για περαιτέρω επεξεργασία—ίσως να τις ενσωματώσετε ή να ειδοποιήσετε έναν χρήστη μέσω UI. Εδώ είναι μια γρήγορη τροποποίηση που συγκεντρώνει τα ονόματα σε ένα `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Τώρα έχετε έναν καθαρό τρόπο για να **retrieve missing font** δεδομένα προγραμματιστικά, τα οποία μπορείτε να περάσετε σε ένα μοντέλο αναφοράς ή σε έναν οδηγό εγκατάστασης γραμματοσειρών.

## Βήμα 5 – Πρακτικές Σκέψεις

- **Πολλαπλές αντικαταστάσεις:** Μια ελλιπής γραμματοσειρά μπορεί να αντικατασταθεί από διαφορετικές γραμματοσειρές σε διαφορετικά τμήματα του εγγράφου. Η λίστα προειδοποιήσεων θα περιέχει κάθε εμφάνιση, έτσι μπορεί να δείτε διπλότυπες καταχωρήσεις ελλιπών γραμματοσειρών.
- **Απόδοση:** Η φόρτωση πολύ μεγάλων εγγράφων μπορεί να δημιουργήσει χιλιάδες προειδοποιήσεις. Αν σας ενδιαφέρουν μόνο οι γραμματοσειρές, φιλτράρετε νωρίς όπως φαίνεται για να διατηρήσετε τη βρόχο γρήγορη.
- **Γραμματοσειρές διαφόρων πλατφορμών:** Σε Linux, η προεπιλεγμένη γραμματοσειρά αντικατάστασης είναι συχνά *Liberation Sans*. Σε Windows, μπορεί να είναι *Arial*. Η γνώση του εναλλακτικού σας βοηθά να αποφασίσετε αν χρειάζεται να συμπεριλάβετε προσαρμοσμένες γραμματοσειρές στην εφαρμογή σας.

## Βήμα 6 – Οπτική Βοήθεια

Παρακάτω υπάρχει ένα στιγμιότυπο οθόνης της εξόδου της κονσόλας (το alt text περιλαμβάνει τη βασική λέξη-κλειδί για SEO).

![Έξοδος κονσόλας με επανάληψη προειδοποιήσεων εγγράφου που εμφανίζει ελλιπείς γραμματοσειρές και τις αντικαταστάσεις τους](/images/iterate-document-warnings.png)

*Alt text:* *παράδειγμα επανάληψης προειδοποιήσεων εγγράφου που εμφανίζει ονόματα ελλιπών γραμματοσειρών και λεπτομέρειες αντικατάστασης.*

## Συμπέρασμα

Μόλις μάθατε πώς να **iterate document warnings** στο Aspose.Words for Java, **detect missing fonts**, **load word document** με ασφάλεια, **retrieve missing font** πληροφορίες, και **print missing font** λεπτομέρειες στην κονσόλα. Το πλήρες απόσπασμα κώδικα εκτελείται όπως είναι, και μπορείτε να το προσαρμόσετε για να καταγράψετε σε αρχείο, να εμφανίσετε διάλογο UI, ή ακόμη και να ενσωματώσετε αυτόματα τις ελλιπείς γραμματοσειρές.

Στη συνέχεια, ίσως θέλετε να εξερευνήσετε πώς να **load word document** με προσαρμοσμένες πηγές γραμματοσειρών (π.χ., προσθέτοντας έναν φάκελο εταιρικών γραμματοσειρών) ή πώς να ενσωματώσετε τις ελλιπείς γραμματοσειρές απευθείας στο αρχείο για να διατηρήσετε τη διάταξη σε διαφορετικές μηχανές. Και τα δύο θέματα βασίζονται φυσικά σε ό,τι καλύψαμε εδώ.

Καλό κώδικα, και εύχομαι τα PDF σας να φαίνονται πάντα ακριβώς όπως θέλετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}