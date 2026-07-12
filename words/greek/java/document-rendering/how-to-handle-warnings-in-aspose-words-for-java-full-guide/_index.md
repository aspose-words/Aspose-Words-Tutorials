---
category: general
date: 2026-06-24
description: Πώς να διαχειρίζεστε τις προειδοποιήσεις κατά την επεξεργασία αρχείων
  Word σε Java. Μάθετε πώς να καταγράφετε τις γραμματοσειρές, να εκτυπώνετε μηνύματα
  γραμματοσειρών και να αντιμετωπίζετε ομαλά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: el
og_description: πώς να αντιμετωπίζετε τις προειδοποιήσεις στο Aspose.Words for Java.
  Αυτός ο οδηγός δείχνει πώς να καταγράφετε τις γραμματοσειρές, να εκτυπώνετε μηνύματα
  γραμματοσειρών και να διαχειρίζεστε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
og_title: Πώς να διαχειριστείτε τις προειδοποιήσεις στο Aspose.Words – Πλήρης οδηγός
  Java
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Πώς να διαχειριστείτε τις προειδοποιήσεις στο Aspose.Words for Java – Πλήρης
  Οδηγός
url: /el/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να διαχειριστείτε τις προειδοποιήσεις στο Aspose.Words for Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να διαχειριστείτε τις προειδοποιήσεις** που εμφανίζονται όταν φορτώνετε ένα έγγραφο Word με το Aspose.Words; Ίσως έχετε δει ασαφείς μηνύματα σχετικά με ελλείπουσες γραμματοσειρές και σκεφτείτε, “Τέλεια, το PDF μου είναι εκτός κέντρου—τι κάνω τώρα;” Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, οι προειδοποιήσεις αντικατάστασης γραμματοσειρών είναι οι σιωπηλοί ένοχοι που χαλούν την πιστότητα της διάταξης.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα μια πρακτική λύση: την καταχώρηση ενός callback προειδοποίησης, την ανίχνευση ειδοποιήσεων σχετικών με γραμματοσειρές, και **εκτύπωση μηνυμάτων γραμματοσειρών** ώστε να μπορείτε να αποφασίσετε αν θα ενσωματώσετε μια εναλλακτική ή θα παρέχετε ένα προσαρμοσμένο αρχείο γραμματοσειράς. Στο τέλος θα γνωρίζετε **πώς να συλλάβετε γραμματοσειρές**, να **διαχειριστείτε κομμένες γραμματοσειρές** με χάρη, και να διατηρήσετε την αλυσίδα μετατροπής εγγράφων σας ακαταμάχητη.

## Τι Θα Μάθετε

- Ο σκοπός των callbacks προειδοποίησης του Aspose.Words.
- Πώς να ανιχνεύσετε και να φιλτράρετε προειδοποιήσεις *font substitution*.
- Τρόποι καταγραφής ή εμφάνισης **print font messages** για αποσφαλμάτωση.
- Στρατηγικές για **handling missing fonts** σε περιβάλλοντα παραγωγής.
- Ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

### Προαπαιτούμενα

- Java 8 ή νεότερη (ο κώδικας λειτουργεί επίσης με JDK 11).
- Βιβλιοθήκη Aspose.Words for Java (κατεβάστε από την ιστοσελίδα Aspose ή προσθέστε την εξάρτηση Maven/Gradle).
- Ένα δείγμα `input.docx` που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη τοπικά (τέλειο για δοκιμή του callback).

---

## Βήμα 1: Ρυθμίστε το Έργο σας και Εισάγετε το Aspose.Words

Πριν μπορέσετε να **διαχειριστείτε προειδοποιήσεις**, χρειάζεστε ένα έργο Java που να γνωρίζει το Aspose.Words. Αν χρησιμοποιείτε Maven, προσθέστε αυτό το απόσπασμα στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Για Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

Μόλις επιλυθεί η εξάρτηση, εισάγετε τις απαραίτητες κλάσεις στο αρχείο πηγαίου κώδικα Java σας:

```java
import com.aspose.words.*;
```

> **Συμβουλή:** Διατηρήστε τις βιβλιοθήκες Aspose ενημερωμένες. Οι νέες εκδόσεις συχνά βελτιώνουν τη διαχείριση προειδοποιήσεων και προσθέτουν πιο πλούσιες λεπτομέρειες στο `WarningInfo`.

---

## Βήμα 2: Φορτώστε το Έγγραφο Word και Καταχωρήστε ένα Callback Προειδοποίησης

Τώρα που η βιβλιοθήκη βρίσκεται στο classpath, μπορούμε να **συλλάβουμε τις γραμματοσειρές** που η μηχανή αντικαθιστά. Το κλειδί είναι το `Document.setWarningCallback`, το οποίο δέχεται οποιαδήποτε υλοποίηση του `IWarningCallback`. Παρακάτω υπάρχει ένα σύντομο αλλά πλήρες παράδειγμα που εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς στην κονσόλα.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Γιατί Λειτουργεί Αυτό

- **`Document.setWarningCallback`** ενημερώνει το Aspose.Words να καλέσει τον κώδικά σας κάθε φορά που συναντά μια κατάσταση που απαιτεί προειδοποίηση.
- **`WarningInfo.getWarningType()`** μας επιτρέπει να διακρίνουμε μεταξύ διαφορετικών κατηγοριών (π.χ., `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Εστιάζοντας στο `FONT_SUBSTITUTION` **διαχειριζόμαστε τις ελλείπουσες γραμματοσειρές** χωρίς να γεμίζει το αρχείο καταγραφής.
- Η γραμμή `System.out.println` **εκτυπώνει μηνύματα γραμματοσειρών** σε πραγματικό χρόνο, κάτι ανεκτίμητο κατά την ανάπτυξη ή όταν αντιμετωπίζετε προβλήματα σε μια παραγωγική αλυσίδα.

---

## Βήμα 3: Δοκιμάστε το Callback με Μια Ελλείπουσα Γραμματοσειρά

Για να επιβεβαιώσετε ότι το callback μας πραγματικά **συλλάβει γραμματοσειρές**, δημιουργήστε ένα αρχείο Word που χρησιμοποιεί μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας—π.χ., “Comic Sans MS” σε έναν διακομιστή Linux που έχει μόνο “DejaVu Sans”. Όταν εκτελέσετε τη demo, θα πρέπει να δείτε έξοδο παρόμοια με:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Αν δεν δείτε κανένα μήνυμα, ελέγξτε ξανά:

1. Το έγγραφο πράγματι αναφέρει μια ελλείπουσα γραμματοσειρά.
2. Η διαδρομή προς το `input.docx` είναι σωστή.
3. Χρησιμοποιείτε μια πρόσφατη έκδοση του Aspose.Words (παλαιότερες εκδόσεις μερικές φορές καταστέλλουν ορισμένες προειδοποιήσεις).

---

## Βήμα 4: Προχωρημένη Διαχείριση – Ενσωμάτωση Εναλλακτικών Γραμματοσειρών

Η εκτύπωση μιας προειδοποίησης είναι εξαιρετική, αλλά σε ένα παραγωγικό σύστημα ίσως θέλετε να **διαχειριστείτε τις ελλείπουσες γραμματοσειρές** αυτόματα. Μία κοινή προσέγγιση είναι η ενσωμάτωση μιας εναλλακτικής γραμματοσειράς (π.χ., “Liberation Sans”) πριν από την αποθήκευση. Ακολουθεί πώς μπορείτε να επεκτείνετε το callback ώστε να αντικαθιστά τη χαμένη γραμματοσειρά προγραμματιστικά:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**Τι συμβαίνει;**

- Αναλύουμε την περιγραφή της προειδοποίησης για να εξάγουμε το όνομα της ελλείπουσας γραμματοσειράς.
- Χρησιμοποιώντας το `FontSettings`, λέμε στο Aspose.Words να αντικαταστήσει *οποιαδήποτε* εμφάνιση εκείνης της γραμματοσειράς με το “Liberation Sans”.
- Την επόμενη φορά που το έγγραφο θα αποδοθεί ή θα αποθηκευτεί, η εναλλακτική εφαρμόζεται σιωπηρά.

> **Προειδοποίηση:** Η υπερβολική χρήση αυτόματης αντικατάστασης μπορεί να κρύψει πραγματικά προβλήματα σχεδίασης. Είναι καλύτερο να καταγράφετε την αντικατάσταση (καθώς ήδη **εκτυπώνετε μηνύματα γραμματοσειρών**) και να ελέγχετε το αποτέλεσμα χειροκίνητα κατά τη QA.

---

## Βήμα 5: Καταγραφή Αντί Εκτύπωσης – Κατάλληλο για Παραγωγή

Σε μια αλυσίδα CI/CD πιθανότατα δεν θέλετε έξοδο στην κονσόλα. Αντικαταστήστε το `System.out.println` με έναν κατάλληλο logger (π.χ., SLF4J). Ακολουθεί μια γρήγορη προσαρμογή:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Τώρα οι προειδοποιήσεις σας ενσωματώνονται με τα υπάρχοντα εργαλεία συγκέντρωσης καταγραφών (ELK, Splunk κ.λπ.), καθιστώντας πιο εύκολο το **handle missing fonts** σε πολλές εργασίες.

---

## Βήμα 6: Συνηθισμένα Πάγια & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Δεν εμφανίζονται προειδοποιήσεις | Η γραμματοσειρά υπάρχει πραγματικά στο σύστημα, ή το έγγραφο χρησιμοποιεί ενσωματωμένες γραμματοσειρές. | Επιβεβαιώστε ότι το δοκιμαστικό έγγραφο αναφέρει πραγματικά μια μη διαθέσιμη γραμματοσειρά. |
| Το callback δεν καλείται | `setWarningCallback` κλήθηκε **μετά** το έγγραφο να έχει ήδη φορτωθεί. | Καταχωρήστε το callback **πριν** οποιαδήποτε ενέργεια που μπορεί να προκαλέσει προειδοποιήσεις (π.χ., πριν το `Document.save`). |
| Πολλές προειδοποιήσεις κατακλύζουν το log | Μεγάλα έγγραφα προκαλούν πολλές αντικαταστάσεις. | Προσθέστε μηχανισμό περιορισμού ή συγκεντρώστε τα μηνύματα πριν την καταγραφή. |
| Η αντικατάσταση δεν εφαρμόζεται | `FontSettings` δεν συνδέεται με το αντικείμενο του εγγράφου. | Βεβαιωθείτε ότι έχετε ορίσει το `FontSettings` στο ίδιο αντικείμενο `Document` που αποθηκεύετε. |

---

## Βήμα 7: Πλήρες, Έτοιμο‑για‑Εκτέλεση Παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση. Περιλαμβάνει τις εισαγωγές, το callback, την καταγραφή και μια στρατηγική εναλλακτικής γραμματοσειράς.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας/καταγραφής** (υποθέτοντας ότι το “Comic Sans MS” λείπει):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

Το παραγόμενο `output.pdf` θα χρησιμοποιεί το “Liberation Sans” όπου και αν είχε αναφερθεί το “Comic Sans MS”, χάρη στην αυτόματη αντικατάσταση που προσθέσαμε.

---

## Συμπέρασμα

Μόλις καλύψαμε **πώς να διαχειριστείτε προειδοποιήσεις** στο Aspose.Words for Java από την αρχή μέχρι το τέλος. Καταχωρώντας ένα callback προειδοποίησης, φιλτράροντας τις ειδοποιήσεις **font substitution** και **εκτυπώνοντας μηνύματα γραμματοσειρών**, αποκτάτε πλήρη ορατότητα στις περιπτώσεις ελλείπουσας γραμματοσειράς. Η προσθήκη εναλλακτικής μέσω `FontSettings` σας επιτρέπει να **handle missing fonts** χωρίς χειροκίνητη παρέμβαση, ενώ ένα κατάλληλο πλαίσιο καταγραφής κάνει τη λύση έτοιμη για παραγωγή.

Επόμενα βήματα; Δοκιμάστε να συνδυάσετε αυτήν την προσέγγιση με το Aspose.PDF για να επαληθεύσετε ότι οι ενσωματωμένες γραμματοσειρές διατηρούνται κατά τη μετατροπή, ή εξερευνήστε άλλους τύπους προειδοποιήσεων (π.χ., `DEPRECATED_FEATURE`) για να προστατέψετε τον κώδικά σας στο μέλλον. Και αν σας ενδιαφέρει **πώς να συλλάβετε γραμματοσειρές** από έναν απομακρυσμένο κάδο αποθήκευσης

## Τι Θα Πρέπει να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}