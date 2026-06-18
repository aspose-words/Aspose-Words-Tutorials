---
category: general
date: 2026-06-17
description: Καταγράψτε προειδοποιήσεις αντικατάστασης γραμματοσειρών σε Java με τη
  χρήση του Aspose.Words – εντοπίστε τις ελλείπουσες γραμματοσειρές κατά τη φόρτωση
  του εγγράφου και διατηρήστε το αποτέλεσμα σας συνεπές.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: el
og_description: Καταγράψτε προειδοποιήσεις αντικατάστασης γραμματοσειρών σε Java με
  το Aspose.Words. Μάθετε πώς να συλλαμβάνετε ειδοποιήσεις για ελλιπείς γραμματοσειρές
  κατά τη φόρτωση του εγγράφου και να διατηρείτε τα PDF σας άψογα.
og_title: Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε Java – Πλήρης
  Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειράς σε Java με το Aspose.Words
url: /el/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς σε Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** όταν ένα έγγραφο Word φορτώνει μια γραμματοσειρά που δεν υπάρχει στον διακομιστή; Δεν είστε οι μόνοι που σκεπάζονται τις ελλείψεις γραμματοσειρών που αντικαθίστανται σιωπηρά. Το καλό νέο; Η Aspose.Words for Java παρέχει έναν καθαρό τρόπο για να πιάσετε αυτές τις αντικαταστάσεις τη στιγμή που φορτώνεται το έγγραφο.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που δείχνει ακριβώς πώς να καταχωρίσετε μια callback προειδοποίησης, να φιλτράρετε τις ειδοποιήσεις αντικατάστασης γραμματοσειράς και να τις γράψετε στην κονσόλα (ή σε οποιονδήποτε logger προτιμάτε). Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java που χρησιμοποιεί **Aspose.Words Java**.

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το **LoadOptions** ώστε να καταγράφει προειδοποιήσεις.
- Πώς να υλοποιήσετε ένα **IWarningCallback** που αντιδρά μόνο σε συμβάντα **font substitution**.
- Πώς να φορτώσετε ένα έγγραφο με ασφάλεια διατηρώντας ένα σαφές αποτύπωμα των ελλιπών γραμματοσειρών.
- Συμβουλές για την επέκταση της λύσης σε αρχεία καταγραφής ή συστήματα παρακολούθησης.

### Προαπαιτούμενα

- Java 8 ή νεότερη (ο κώδικας λειτουργεί επίσης με Java 11+).
- Βιβλιοθήκη Aspose.Words for Java (συνιστάται η έκδοση 23.10 ή νεότερη).
- Ένα δείγμα `.docx` που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας (π.χ., `MissingFont.docx`).

Δεν απαιτούνται επιπλέον frameworks—απλώς καθαρή Java και τα Aspose.JARs.

---

## Βήμα 1: Διαμόρφωση LoadOptions για Aspose.Words Java

Πριν μπορέσετε να παγιδεύσετε οποιεσδήποτε προειδοποιήσεις, χρειάζεστε μια παρουσία **LoadOptions**. Αυτό το αντικείμενο λέει στην Aspose.Words πώς να συμπεριφέρεται κατά την ανάλυση του εισερχόμενου αρχείου.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Γιατί είναι κρίσιμο αυτό το βήμα; Χωρίς ένα αντικείμενο `LoadOptions`, η βιβλιοθήκη αντικαθιστά σιωπηρά τις ελλιπείς γραμματοσειρές και δεν βλέπετε κανένα ίχνος. Δημιουργώντας το ρητά, ανοίγετε την πόρτα σε μια προσαρμοσμένη **warning callback** που μπορεί να καταγράψει ακριβώς ό,τι σας ενδιαφέρει.

> **Pro tip:** Αν φορτώνετε πολλά έγγραφα σε batch, επαναχρησιμοποιήστε μία μόνο παρουσία `LoadOptions` για να αποφύγετε περιττές δημιουργίες αντικειμένων.

---

## Βήμα 2: Υλοποίηση Callback Προειδοποίησης για Αντικατάσταση Γραμματοσειράς

Η Aspose.Words παρέχει το interface `IWarningCallback`. Η υλοποίησή του σας επιτρέπει να αποφασίσετε τι θα κάνετε όταν η μηχανή εκδώσει ένα `WarningInfo`. Στην περίπτωσή μας, θέλουμε να αντιδράσουμε μόνο σε `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Μερικά σημεία που πρέπει να σημειώσετε:

1. **Φιλτράρισμα** – Η δήλωση `if` εξασφαλίζει ότι αγνοούμε άσχετες προειδοποιήσεις (όπως προβλήματα διάταξης) και διατηρούμε το log καθαρό.
2. **Ασφάλεια νήματος** – Η callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο, οπότε δεν χρειάζεστε επιπλέον συγχρονισμό για απλή έξοδο στην κονσόλα. Αν γράφετε σε κοινό logger, βεβαιωθείτε ότι είναι thread‑safe.
3. **Επεκτασιμότητα** – Θέλετε να γράψετε σε αρχείο; Αντικαταστήστε το `System.out.println` με `java.util.logging.Logger` ή κάποιο τρίτο framework καταγραφής.

---

## Βήμα 3: Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές

Τώρα που η callback είναι σε θέση, φορτώστε το αρχείο Word. Τη στιγμή που η Aspose.Words αναλύει το έγγραφο, οποιαδήποτε ελλιπής γραμματοσειρά θα ενεργοποιήσει την παραπάνω callback.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Αν το πηγαίο αρχείο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, θα δείτε έξοδο παρόμοια με:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Αυτή η γραμμή είναι η **καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειράς** που ψάχνατε. Τώρα μπορείτε να δράσετε—ίσως να ειδοποιήσετε έναν χρήστη, να αλλάξετε σε εναλλακτικό stylesheet, ή απλώς να κρατήσετε ένα αρχείο για συμμόρφωση.

---

## Βήμα 4: Συνέχιση Κανονικής Επεξεργασίας

Μετά τη φόρτωση, το έγγραφο συμπεριφέρεται όπως οποιοδήποτε άλλο αντικείμενο `Document`. Μπορείτε να ελέγξετε ενότητες, να εξάγετε κείμενο ή να το μετατρέψετε σε PDF. Η καταγραφή προειδοποιήσεων γίνεται αυτόματα κατά το βήμα φόρτωσης, οπότε δεν χρειάζεστε επιπλέον κώδικα.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Η κονσόλα θα εμφανίσει τώρα τόσο την προειδοποίηση αντικατάστασης γραμματοσειράς (αν υπάρχει) **και** τον αριθμό των ενοτήτων, επιβεβαιώνοντας ότι το έγγραφο είναι πλήρως λειτουργικό.

---

## Προχωρημένες Συμβουλές & Ακραίες Περιπτώσεις

### Καταγραφή σε Αρχείο Αντί για Κονσόλα

Αν προτιμάτε μόνιμο log, αντικαταστήστε την κλήση `System.out.println` με έναν `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Θυμηθείτε να διαχειριστείτε το `IOException` σωστά σε κώδικα παραγωγής.

### Καταγραφή Πολλαπλών Εγγράφων σε Βρόχο

Όταν επεξεργάζεστε έναν φάκελο εγγράφων, μπορείτε να επαναχρησιμοποιήσετε την ίδια callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Καθώς η callback είναι συνδεδεμένη με το `loadOptions`, κάθε επανάληψη καταγράφει αυτόματα τυχόν συμβάντα αντικατάστασης γραμματοσειράς.

### Διαχείριση Ενσωματωμένων Γραμματοσειρών

Η Aspose.Words μπορεί να ενσωματώσει τις ελλιπείς γραμματοσειρές αν το ενεργοποιήσετε:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Ακόμη και με την ενσωμάτωση ενεργοποιημένη, η callback προειδοποίησης εξακολουθεί να εκτελείται, δίνοντάς σας ορατότητα σε ό,τι αντικαταστάθηκε.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε το σε μια κλάση με όνομα `FontSubstitutionDiagnostics.java`, προσαρμόστε τη διαδρομή του αρχείου και τρέξτε το.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Αναμενόμενη έξοδος** (υπόθεση ότι το πηγαίο έγγραφο αναφέρει μια ελλιπής γραμματοσειρά):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Τόσο η κονσόλα όσο και το `font_substitution_log.txt` θα περιέχουν την προειδοποίηση, παρέχοντας ένα αξιόπιστο αποτύπωμα.

---

## Συμπέρασμα

Σας δείξαμε πώς να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** σε Java χρησιμοποιώντας την Aspose.Words. Με τη διαμόρφωση του `LoadOptions`, τη σύνδεση ενός `IWarningCallback` και τη φόρτωση του εγγράφου, αποκτάτε πλήρη ορατότητα σε οποιαδήποτε γεγονότα ελλιπών γραμματοσειρών που διαφορετικά θα περνούσαν απαρατήρητα. Από εδώ μπορείτε:

- Να κατευθύνετε τις προειδοποιήσεις σε μια κεντρική υπηρεσία logging.
- Να ενεργοποιήσετε ειδοποιήσεις για pipelines ελέγχου ποιότητας.
- Να συνδυάσετε αυτήν την τεχνική με άλλες στρατηγικές **document loading**, όπως μετατροπή σε PDF ή mail‑merge.

Πειραματιστείτε—αντικαταστήστε τον console logger με SLF4J, προσθέστε timestamps, ή ακόμη στείλτε ειδοποιήσεις σε έναν πίνακα παρακολούθησης. Το βασικό μοτίβο παραμένει το ίδιο, και τώρα έχετε μια σταθερή βάση για αξιόπιστη διαχείριση γραμματοσειρών σε οποιαδήποτε ροή εργασίας εγγράφων Java.

Έχετε κάποιο δικό σας twist να μοιραστείτε; Ίσως το έχετε ενσωματώσει σε Spring Boot ή σε cloud function. Αφήστε ένα σχόλιο παρακάτω και ας συνεχίσουμε τη συζήτηση. Καλό coding!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας projects.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}