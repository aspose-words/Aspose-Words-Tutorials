---
category: general
date: 2026-06-05
description: Ανίχνευση αντικατάστασης ελλιπών γραμματοσειρών σε Java με χρήση του
  Aspose.Words. Μάθετε πώς να ρυθμίσετε το LoadOptions, το FontSettings και τις κλήσεις
  προειδοποίησης για αξιόπιστη επεξεργασία εγγράφων.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: el
og_description: Ανιχνεύστε την αντικατάσταση ελλιπούς γραμματοσειράς σε Java με το
  Aspose.Words. Αυτός ο οδηγός δείχνει βήμα‑βήμα πώς να ρυθμίσετε το LoadOptions,
  το FontSettings και μια κλήση προειδοποίησης για να εντοπίσετε τις ελλιπείς γραμματοσειρές.
og_title: Ανίχνευση έλλειψης αντικατάστασης γραμματοσειράς σε Java – Πλήρη Εκπαίδευση
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Ανίχνευση έλλειψης αντικατάστασης γραμματοσειράς σε Java – Πλήρης Οδηγός Aspose.Words
url: /el/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανίχνευση ελλιπών αντικαταστάσεων γραμματοσειρών σε Java – Πλήρης Οδηγός Aspose.Words

Αναρωτηθήκατε ποτέ πώς να **ανιχνεύσετε ελλιπείς αντικαταστάσεις γραμματοσειρών** κατά τη φόρτωση ενός εγγράφου Word σε Java; Δεν είστε ο μόνος. Οι ελλιπείς γραμματοσειρές μπορούν σιωπηρά να χαλάσουν τα PDF ή τις αποδομένες σελίδες, και η έγκαιρη ανίχνευσή τους εξοικονομεί ώρες εντοπισμού σφαλμάτων. Σε αυτό το tutorial θα περάσουμε από μια πρακτική λύση που όχι μόνο φορτώνει ένα έγγραφο αλλά και σας λέει ακριβώς πότε συμβαίνει μια αντικατάσταση γραμματοσειράς.

Θα καλύψουμε τα πάντα, από τη δημιουργία του `LoadOptions` μέχρι τη σύνδεση ενός `WarningCallback` που εκτυπώνει ένα σαφές μήνυμα κάθε φορά που το Aspose.Words αντικαθιστά μια ελλιπή γραμματοσειρά. Στο τέλος, θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που λειτουργεί με οποιοδήποτε αρχείο `.docx`, και θα κατανοήσετε *γιατί* κάθε μέρος είναι σημαντικό. Χωρίς πρόσθετες βιβλιοθήκες, μόνο απλή Java και Aspose.Words.

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το **LoadOptions** για χρήση προσαρμοσμένων **FontSettings**.  
- Πώς να υλοποιήσετε ένα **IWarningCallback** που καταγράφει προειδοποιήσεις `FONT_SUBstitution`.  
- Πώς να φορτώσετε ένα έγγραφο ενώ παρακολουθείτε με ασφάλεια τις ελλιπείς γραμματοσειρές.  
- Αναμενόμενη έξοδος κονσόλας και πώς να προσαρμόσετε τον κώδικα για πλαίσια καταγραφής.  

**Προαπαιτούμενα**: Java 8+ εγκατεστημένη, Aspose.Words for Java (v23.12 ή νεότερη) στο classpath σας, και ένα δείγμα `.docx` που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη. Αυτό είναι όλο—δεν απαιτούνται πρόσθετα εργαλεία κατασκευής.

---

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη του Aspose.Words

Πριν βουτήξουμε στον κώδικα, βεβαιωθείτε ότι το Aspose.Words είναι διαθέσιμο. Αν χρησιμοποιείτε Maven, προσθέστε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Μόλις η βιβλιοθήκη είναι στο classpath, είστε έτοιμοι να **ανιχνεύσετε ελλιπείς αντικαταστάσεις γραμματοσειρών** με μία μόνο κλήση μεθόδου.

## Βήμα 2: Δημιουργία LoadOptions και Σύνδεση FontSettings

Η καρδιά της λύσης βρίσκεται στην προετοιμασία μιας παρουσίας `LoadOptions` που γνωρίζει πώς να παρακολουθεί προβλήματα γραμματοσειρών. Ακολουθεί ο κώδικας αναλυτικά γραμμή‑με‑γραμμή.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Γιατί είναι σημαντικό**: Το `LoadOptions` λέει στο Aspose.Words *πώς* να ερμηνεύσει το εισερχόμενο αρχείο. Ενσωματώνοντας προσαρμοσμένα `FontSettings`, δίνουμε στον φορτωτή ένα hook (`IWarningCallback`) που ενεργοποιείται **ακριβώς όταν αντικαθίσταται μια ελλιπής γραμματοσειρά**. Χωρίς αυτό το callback, το Aspose.Words θα αντικαθιστούσε σιωπηρά τη γραμματοσειρά και δεν θα το γνωρίζατε ποτέ.

## Βήμα 3: Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές

Τώρα που το σύστημα προειδοποιήσεων είναι σε θέση, η φόρτωση του εγγράφου γίνεται απλή.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Όταν εκτελείται η κλήση `new Document(...)`, το Aspose.Words διαβάζει το αρχείο, ελέγχει κάθε αναφορά γραμματοσειράς και αν δεν βρει μια αντίστοιχη γραμματοσειρά στο σύστημα, ενεργοποιεί τη μέθοδο `warning` που ορίσαμε νωρίτερα. Η κονσόλα θα εμφανίσει αμέσως μια γραμμή όπως:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Αυτή η γραμμή είναι η έξοδος **ανίχνευσης ελλιπών αντικαταστάσεων γραμματοσειρών** που ψάχνατε.

## Βήμα 4: Επαλήθευση του Αποτελέσματος και Ρύθμιση του Callback (Για Προχωρημένους)

### 4.1 Γρήγορη επαλήθευση

Εκτελέστε το πρόγραμμα από το IDE σας ή μέσω `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Αν το έγγραφο αναφέρει μια γραμματοσειρά που δεν έχετε, θα δείτε το μήνυμα προειδοποίησης να εκτυπώνεται. Αν η κονσόλα παραμείνει σιωπηλή, είτε η γραμματοσειρά υπάρχει στο σύστημά σας είτε το έγγραφο δεν ζητά ελλιπείς γραμματοσειρές.

### 4.2 Καταγραφή αντί για `System.out`

Σε κώδικα παραγωγής πιθανότατα θέλετε έναν logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Αυτή η μικρή αλλαγή κάνει τον μηχανισμό **ανίχνευσης ελλιπών αντικαταστάσεων γραμματοσειρών** να λειτουργεί ομαλά με υπάρχουσες γραμμές καταγραφής.

### 4.3 Διαχείριση άλλων τύπων προειδοποιήσεων

Το callback λαμβάνει *όλες* τις προειδοποιήσεις, όχι μόνο προβλήματα γραμματοσειρών. Αν θέλετε να παρακολουθείτε και άλλα προβλήματα (π.χ., `UNKNOWN_STYLE`), προσθέστε επιπλέον κλάδους `if`. Εδώ είναι ένα γρήγορο παράδειγμα:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

## Βήμα 5: Συνηθισμένα Πιθανά Σφάλματα και Συμβουλές Επαγγελματία

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Δεν εμφανίζεται προειδοποίηση** | Η γραμματοσειρά υπάρχει πραγματικά στο λειτουργικό σύστημα, ή το έγγραφο χρησιμοποιεί εναλλακτική που το Aspose.Words θεωρεί ως “βρέθηκε”. | Διαγράψτε προσωρινά τη γραμματοσειρά από το σύστημα ή χρησιμοποιήστε ένα πραγματικά ελλιπές όνομα γραμματοσειράς στο πηγαίο έγγραφο. |
| **Το callback δεν καλείται ποτέ** | `setWarningCallback` κλήθηκε σε μια *διαφορετική* παρουσία `FontSettings` από αυτή που συνδέθηκε στο `LoadOptions`. | Βεβαιωθείτε ότι καλείτε `loadOptions.setFontSettings(fontSettings)` **μετά** τη διαμόρφωση του callback. |
| **Μείωση απόδοσης** | Η φόρτωση πολλών μεγάλων εγγράφων με callbacks μπορεί να προσθέσει επιπλέον φόρτο. | Αποθηκεύστε στην cache μια μόνο παρουσία `FontSettings` και επαναχρησιμοποιήστε την σε πολλαπλές φορτώσεις αν επεξεργάζεστε παρτίδες. |
| **Πολλαπλά νήματα** | `FontSettings` δεν είναι ασφαλές για νήματα από προεπιλογή. | Δημιουργήστε ξεχωριστό `FontSettings` ανά νήμα ή συγχρονίστε την πρόσβαση. |

**Συμβουλή επαγγελματία**: Αν δημιουργείτε PDF για μια υπηρεσία web, ίσως θέλετε να συλλέξετε όλες τις προειδοποιήσεις αντικατάστασης σε μια λίστα και να τις επιστρέψετε στην απόκριση του API, αντί να τις εκτυπώνετε στην κονσόλα.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (υποθέτοντας ότι το αρχείο αναφέρει μια ελλιπή γραμματοσειρά):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Αν δεν υπάρχουν ελλιπείς γραμματοσειρές, θα δείτε μόνο την τελική γραμμή “Document loaded successfully.”.

## Συμπέρασμα

Μόλις δείξαμε πώς να **ανιχνεύσετε ελλιπείς αντικαταστάσεις γραμματοσειρών** σε Java χρησιμοποιώντας το Aspose.Words. Διαμορφώνοντας το `LoadOptions`, δημιουργώντας μια παρουσία `FontSettings` και συνδέοντας ένα `IWarningCallback`, αποκτάτε πλήρη ορατότητα σε κάθε γραμματοσειρά που η βιβλιοθήκη αντικαθιστά στο παρασκήνιο. Αυτή η προσέγγιση όχι μόνο αποτρέπει σιωπηλές δυσλειτουργίες απόδοσης, αλλά σας παρέχει επίσης ένα hook για καταγραφή, ειδοποίηση ή ακόμη και αυτόματη ενσωμάτωση εναλλακτικών γραμματοσειρών.

Από εδώ μπορείτε να:

- Επεκτείνετε το callback για να συλλέγετε προειδοποιήσεις σε μια λίστα για απαντήσεις API.  
- Συνδυάσετε αυτήν την τεχνική με τη **διαμόρφωση LoadOptions** για άλλες περιπτώσεις (π.χ., προσαρμοσμένη φόρτωση πόρων).  
- Εξερευνήσετε το ευρύτερο οικοσύστημα **Java Aspose.Words**: μετατροπή σε PDF, εξαγωγή κειμένου ή εκτέλεση mail merges.

Δοκιμάστε το, προσαρμόστε τον logger, και αφήστε τις εφαρμογές σας να προειδοποιούν όταν λείπει μια γραμματοσειρά. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}