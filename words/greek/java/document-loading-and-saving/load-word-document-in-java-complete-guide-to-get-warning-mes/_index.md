---
category: general
date: 2025-12-22
description: Φορτώστε έγγραφο Word σε Java και μάθετε πώς να λαμβάνετε μηνύματα προειδοποίησης,
  ειδικά για τη διαχείριση ελλιπών γραμματοσειρών. Αυτό το βήμα‑βήμα tutorial καλύπτει
  τις προειδοποιήσεις, την αντικατάσταση γραμματοσειρών και τις βέλτιστες πρακτικές.
draft: false
keywords:
- load word document
- get warning messages
- handle missing fonts
- Aspose.Words warnings
- font substitution warning
language: el
og_description: Φορτώστε έγγραφο Word σε Java και λάβετε αμέσως μηνύματα προειδοποίησης.
  Μάθετε πώς να διαχειρίζεστε τις ελλείπουσες γραμματοσειρές με πρακτικά παραδείγματα
  κώδικα.
og_title: Φόρτωση εγγράφου Word σε Java – Λήψη προειδοποιήσεων & Διαχείριση ελλιπών
  γραμματοσειρών
tags:
- Java
- Aspose.Words
- Document Processing
title: Φόρτωση εγγράφου Word σε Java – Πλήρης οδηγός για λήψη προειδοποιητικών μηνυμάτων
  & διαχείριση ελλιπών γραμματοσειρών
url: /el/java/document-loading-and-saving/load-word-document-in-java-complete-guide-to-get-warning-mes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Φόρτωση Εγγράφου Word σε Java – Πλήρης Οδηγός για Λήψη Μηνυμάτων Προειδοποίησης & Διαχείριση Ελλιπών Γραμματοσειρών

Έχετε ποτέ χρειαστεί να **φορτώσετε ένα έγγραφο Word σε Java** και αναρωτηθήκατε γιατί κάποιες γραμματοσειρές εξαφανίζονται ή γιατί συνεχίζετε να βλέπετε μυστηριώδεις προειδοποιήσεις; Δεν είστε μόνοι. Σε πολλά έργα, ειδικά όταν τα έγγραφα μεταφέρονται μεταξύ μηχανών, οι ελλιπείς γραμματοσειρές προκαλούν μηνύματα `FontSubstitutionWarning` που μπορούν να διαταράξουν τις προσδοκίες διάταξης.

Σε αυτό το tutorial θα σας δείξουμε **πώς να φορτώσετε ένα έγγραφο Word**, **να ανακτήσετε μηνύματα προειδοποίησης**, και **να διαχειριστείτε ελλιπείς γραμματοσειρές** με χάρη. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα που εκτυπώνει κάθε προειδοποίηση, ώστε να μπορείτε να αποφασίσετε αν θα ενσωματώσετε τις γραμματοσειρές, θα τις αντικαταστήσετε ή θα καταγράψετε το ζήτημα για μελλοντική ανασκόπηση.

> **Τι θα μάθετε**
> - Ο ακριβής κώδικας που απαιτείται για **φόρτωση εγγράφου word** χρησιμοποιώντας το Aspose.Words for Java.  
> - Πώς να επαναλάβετε το `document.getWarnings()` και να φιλτράρετε το `FontSubstitutionWarning`.  
> - Συμβουλές για την αντιμετώπιση ελλιπών γραμματοσειρών, συμπεριλαμβανομένης της ενσωμάτωσης γραμματοσειρών ή της παροχής εναλλακτικών.

## Προαπαιτούμενα

- Εγκατεστημένο Java 8 ή νεότερο.  
- Maven (ή Gradle) για διαχείριση εξαρτήσεων.  
- Βιβλιοθήκη Aspose.Words for Java (η δωρεάν δοκιμαστική έκδοση λειτουργεί για αυτήν την επίδειξη).

Αν δεν έχετε προσθέσει ακόμη το Aspose.Words στο έργο σας, προσθέστε αυτήν την εξάρτηση Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

*(Μπορείτε επίσης να χρησιμοποιήσετε το ισοδύναμο Gradle – το API είναι ταυτόσημο.)*

## Βήμα 1: Προετοιμασία Load Options – Το Αρχικό Σημείο για τη Φόρτωση Εγγράφου Word

Πριν πραγματικά **φορτώσετε το έγγραφο word**, ίσως θέλετε να ρυθμίσετε πώς η βιβλιοθήκη διαχειρίζεται τα ελλιπή πόρους. Το `LoadOptions` σας δίνει έλεγχο πάνω στην αντικατάσταση γραμματοσειρών, τη φόρτωση εικόνων και άλλα.

```java
import com.aspose.words.*;

public class LoadDocumentDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Prepare load options (default options are fine for most cases)
        LoadOptions loadOptions = new LoadOptions();

        // Optional: Force the library to use a specific font folder
        // loadOptions.setFontSettings(new FontSettings());
        // loadOptions.getFontSettings().setFontsFolder("C:/MyFonts", true);
```

> **Γιατί είναι σημαντικό:**  
> Η χρήση του `LoadOptions` εξασφαλίζει ότι όταν η λειτουργία **φόρτωσης εγγράφου word** αντιμετωπίζει μια ελλιπή γραμματοσειρά, η βιβλιοθήκη ξέρει πού να ψάξει για υποκατάστατα. Αν παραλείψετε αυτό το βήμα, μπορεί να λάβετε μια πλημμύρα μηνυμάτων `FontSubstitutionWarning` που δεν προέβλεψατε.

## Βήμα 2: Φόρτωση του Εγγράφου Word με τις Καθορισμένες Επιλογές

Τώρα πραγματικά **φορτώνουμε το έγγραφο word** από το δίσκο. Ο κατασκευαστής δέχεται τη διαδρομή του αρχείου και το `LoadOptions` που μόλις διαμορφώσαμε.

```java
        // Step 2: Load the Word document with the specified options
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

> **Συμβουλή:**  
> Εάν το αρχείο είναι ενσωματωμένο σε ένα JAR ή προέρχεται από ροή δικτύου, χρησιμοποιήστε την υπερφόρτωση `InputStream` του κατασκευαστή `Document`. Η λογική διαχείρισης προειδοποιήσεων παραμένει η ίδια.

## Βήμα 3: Ανάκτηση και Φιλτράρισμα Μηνυμάτων Προειδοποίησης – Εστίαση στις Ελλιπείς Γραμματοσειρές

Το Aspose.Words αποθηκεύει τυχόν προβλήματα που συναντά κατά τη φόρτωση σε ένα `WarningInfoCollection`. Θα το διατρέξουμε, θα ψάξουμε για `FontSubstitutionWarning` και θα εκτυπώσουμε κάθε μήνυμα.

```java
        // Step 3: Retrieve any warnings generated during loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 4: Identify font substitution warnings and display their messages
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
            } else {
                // Optionally handle other warning types
                System.out.println("[Other Warning] " + warning.getMessage());
            }
        }
    }
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
[Font Warning] Font 'Calibri' not found. Substituted with 'Arial'.
[Font Warning] Font 'Times New Roman' not found. Substituted with 'Liberation Serif'.
```

Τώρα έχετε μια σαφή εικόνα των **μηνυμάτων προειδοποίησης** που σχετίζονται με ελλιπείς γραμματοσειρές, και μπορείτε να αποφασίσετε τι θα κάνετε στη συνέχεια.

## Βήμα 4: Διαχείριση Ελλιπών Γραμματοσειρών – Πρακτικές Στρατηγικές

Η εμφάνιση προειδοποιήσεων γραμματοσειρών είναι χρήσιμη, αλλά πιθανότατα θέλετε να **διαχειριστείτε ελλιπείς γραμματοσειρές** ώστε το τελικό έγγραφο να φαίνεται ακριβώς όπως προοριζόταν από τον δημιουργό.

### 4.1 Ενσωμάτωση Γραμματοσειρών Απευθείας στο Έγγραφο

Εάν ελέγχετε το πηγαίο `.docx`, ενεργοποιήστε την ενσωμάτωση γραμματοσειρών κατά την αποθήκευση:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setEmbedTrueTypeFonts(true);
document.setFontSettings(fontSettings);
document.save("output.docx");
```

> **Αποτέλεσμα:** Το παραγόμενο `output.docx` περιέχει τις απαιτούμενες γραμματοσειρές, εξαλείφοντας τις περισσότερες προειδοποιήσεις αντικατάστασης σε μεταγενέστερες μηχανές.

### 4.2 Παροχή Προσαρμοσμένου Φακέλου Γραμματοσειρών

Εάν η ενσωμάτωση δεν είναι δυνατή (π.χ., περιορισμοί αδειοδότησης), κατευθύνετε το Aspose.Words σε έναν φάκελο που περιέχει τις ελλιπείς γραμματοσειρές:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setFontsFolder("C:/SharedFonts", true); // true = scan subfolders
loadOptions.setFontSettings(fontSettings);
```

Τώρα όταν **φορτώνετε το έγγραφο word**, η βιβλιοθήκη θα βρει τις ελλιπείς γραμματοσειρές και θα σταματήσει να εκδίδει προειδοποιήσεις.

### 4.3 Καταγραφή Προειδοποιήσεων για Έλεγχο

Σε παραγωγή, ίσως θέλετε να καταγράψετε τις προειδοποιήσεις σε αρχείο καταγραφής αντί για εκτύπωση στην κονσόλα:

```java
import java.io.FileWriter;
import java.io.PrintWriter;

PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));
for (WarningInfo warning : document.getWarnings()) {
    logger.println("[Warning] " + warning.getMessage());
}
logger.close();
```

Αυτή η προσέγγιση ικανοποιεί τις απαιτήσεις συμμόρφωσης όπου πρέπει να αποδείξετε ότι οι ελλιπείς γραμματοσειρές εντοπίστηκαν και διαχειρίστηκαν.

## Βήμα 5: Πλήρες Παράδειγμα Λειτουργίας – Όλα τα Μέρη Μαζί

Παρακάτω βρίσκεται η πλήρης, έτοιμη‑για‑εκτέλεση κλάση που δείχνει **φόρτωση εγγράφου word**, **λήψη μηνυμάτων προειδοποίησης**, και **διαχείριση ελλιπών γραμματοσειρών** χρησιμοποιώντας έναν προσαρμοσμένο φάκελο γραμματοσειρών.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.PrintWriter;

public class WordLoadWithWarnings {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // 👉 Optional: point to a custom font folder
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("C:/SharedFonts", true);
        loadOptions.setFontSettings(fontSettings);

        // 2️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Open a log file for warning capture
        PrintWriter logger = new PrintWriter(new FileWriter("load-warnings.log", true));

        // 4️⃣ Iterate through warnings
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                System.out.println("[Font Warning] " + warning.getMessage());
                logger.println("[Font Warning] " + warning.getMessage());
            } else {
                System.out.println("[Other Warning] " + warning.getMessage());
                logger.println("[Other Warning] " + warning.getMessage());
            }
        }

        // 5️⃣ (Optional) Save with embedded fonts
        FontSettings embedSettings = new FontSettings();
        embedSettings.setEmbedTrueTypeFonts(true);
        doc.setFontSettings(embedSettings);
        doc.save("output-with-embedded-fonts.docx");

        logger.close();
    }
}
```

**Τι κάνει αυτό:**
1. Διαμορφώνει το `LoadOptions` και κατευθύνει τη μηχανή σε έναν φάκελο όπου βρίσκονται οι ελλιπείς γραμματοσειρές.  
2. **Φορτώνει το έγγραφο Word** ενώ συλλέγει τυχόν προειδοποιήσεις.  
3. Εκτυπώνει και καταγράφει κάθε προειδοποίηση, εστιάζοντας στο `FontSubstitutionWarning`.  
4. Αποθηκεύει ένα νέο αντίγραφο με ενσωματωμένες γραμματοσειρές, εξαλείφοντας μελλοντικές προειδοποιήσεις.

## Συχνές Ερωτήσεις (FAQ)

**Ε: Λειτουργεί αυτό με παλαιότερα αρχεία `.doc`;**  
Α: Ναι. Το Aspose.Words υποστηρίζει τόσο `.doc` όσο και `.docx`. Η ίδια λογική διαχείρισης προειδοποιήσεων ισχύει.

**Ε: Τι γίνεται αν δεν μπορώ να ενσωματώσω γραμματοσειρές λόγω αδειοδότησης;**  
Α: Χρησιμοποιήστε την προσέγγιση του προσαρμοσμένου φακέλου γραμματοσειρών (Βήμα 4.2). Σεβόμενη την αδειοδότηση, παρέχει την οπτική πιστότητα που χρειάζεστε.

**Ε: Θα επηρεάσει η συλλογή προειδοποιήσεων την απόδοση;**  
Α: Παραπλανητικά. Οι προειδοποιήσεις αποθηκεύονται σε μια ελαφριά συλλογή. Εάν έχετε χιλιάδες έγγραφα, μπορείτε να απενεργοποιήσετε τις προειδοποιήσεις στο `LoadOptions` (`loadOptions.setWarningCallback(null)`) αλλά θα χάσετε τη δυνατότητα **λήψης μηνυμάτων προειδοποίησης**.

## Συμπέρασμα

Διασχίσαμε κάθε βήμα που απαιτείται για **φόρτωση εγγράφου word** σε Java, **λήψη μηνυμάτων προειδοποίησης**, και **διαχείριση ελλιπών γραμματοσειρών** αποτελεσματικά. Με τη διαμόρφωση του `LoadOptions`, την επανάληψη του `document.getWarnings()` και την εφαρμογή είτε ενσωμάτωσης γραμματοσειρών είτε προσαρμοσμένου φακέλου γραμματοσειρών, αποκτάτε πλήρη έλεγχο πάνω στο πώς οι ελλιπείς γραμματοσειρές επηρεάζουν το αποτέλεσμα.

Τώρα μπορείτε με σιγουριά να επεξεργάζεστε αρχεία Word σε οποιαδήποτε εφαρμογή Java — είτε πρόκειται για υπηρεσία μαζικής μετατροπής, προβολέα εγγράφων ή δημιουργό αναφορών στο διακομιστή. Στο επόμενο βήμα, μπορείτε να εξερευνήσετε **πώς να αντικαταστήσετε ελλιπείς γραμματοσειρές προγραμματιστικά** ή **να μετατρέψετε το έγγραφο σε PDF διατηρώντας τη διάταξη**. Οι δυνατότητες είναι απεριόριστες.

*Καλό κώδικα, και εύχομαι τα έγγραφά σας ποτέ ξανά να μην χάνουν γραμματοσειρά!*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}