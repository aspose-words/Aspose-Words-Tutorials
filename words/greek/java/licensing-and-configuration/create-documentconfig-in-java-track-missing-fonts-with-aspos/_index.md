---
category: general
date: 2026-07-06
description: Δημιουργήστε το DocumentConfig σε Java για την παρακολούθηση των ελλιπών
  γραμματοσειρών χρησιμοποιώντας το Aspose.Words – ένας πλήρης, βήμα‑βήμα οδηγός για
  προγραμματιστές.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: el
og_description: Δημιουργήστε το DocumentConfig σε Java για την παρακολούθηση των ελλιπών
  γραμματοσειρών με το Aspose.Words. Μάθετε τη πλήρη ροή εργασίας, από τη ρύθμιση
  έως τη διαχείριση των προειδοποιήσεων.
og_title: Δημιουργία DocumentConfig σε Java – Παρακολούθηση Ελλειπόντων Γραμματοσειρών
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Δημιουργία DocumentConfig σε Java – Παρακολούθηση Ελλειπουσών Γραμματοσειρών
  με το Aspose.Words
url: /el/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία DocumentConfig σε Java – Παρακολούθηση Ελλειπουσών Γραμματοσειρών με Aspose.Words

**Create DocumentConfig in Java** για την παρακολούθηση προειδοποιήσεων αντικατάστασης γραμματοσειρών κατά τη φόρτωση ενός εγγράφου Word. Αναρωτηθήκατε ποτέ γιατί μερικοί χαρακτήρες φαίνονται περίεργοι μετά το άνοιγμα ενός DOCX; Οι πιθανότητες είναι ότι η αρχική γραμματοσειρά δεν υπάρχει στο σύστημα, και το Aspose.Words την αντικαθιστά σιωπηρά. Σε αυτό το tutorial θα σας δείξουμε ακριβώς πώς να **παρακολουθείτε τις ελλειπούσες γραμματοσειρές** ώστε να μην εκπλαγείτε ξανά από κάποιο ανεπιθύμητο σύμβολο.

Θα περάσουμε από όλα όσα χρειάζεστε: τη ρύθμιση Maven/Gradle, τον κώδικα που δημιουργεί ένα `DocumentConfig`, ένα προσαρμοσμένο `IWarningCallback` που φιλτράρει μόνο τις προειδοποιήσεις αντικατάστασης γραμματοσειρών, και έναν γρήγορο τρόπο καταγραφής των μηνυμάτων. Στο τέλος θα έχετε ένα εκτελέσιμο παράδειγμα που εκτυπώνει κάθε προειδοποίηση ελλειπούσας γραμματοσειράς στην κονσόλα (ή σε αρχείο, αν προτιμάτε).

---

## Τι Θα Μάθετε

- Γιατί ένα `DocumentConfig` είναι το σωστό σημείο για την παρέμβαση σε γεγονότα αντικατάστασης γραμματοσειρών.  
- Πώς να **παρακολουθείτε τις ελλειπούσες γραμματοσειρές** χωρίς να μολύνουν τα αρχεία καταγραφής σας με άσχετες προειδοποιήσεις.  
- Ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση πρόγραμμα Java που δείχνει την τεχνική.  
- Συμβουλές για επέκταση της λύσης—π.χ., εγγραφή προειδοποιήσεων σε βάση δεδομένων ή αποστολή ειδοποιήσεων μέσω email.

### Προαπαιτήσεις

| Απαίτηση | Αιτιολογία |
|----------|------------|
| Java 8 ή νεότερη | Το Aspose.Words for Java υποστηρίζει JDK 8+. |
| Βιβλιοθήκη Aspose.Words for Java (τελευταία έκδοση) | Παρέχει `DocumentConfig`, `IWarningCallback`, κ.λπ. |
| IDE ή εργαλείο κατασκευής (IntelliJ, Eclipse, Maven/Gradle) | Για τη μεταγλώττιση και εκτέλεση του δείγματος. |
| Αρχείο DOCX που αναφέρεται σε γραμματοσειρές που δεν έχετε εγκατεστημένες | Για να δείτε την προειδοποίηση σε δράση. |

Αν έχετε ήδη ένα έργο, απλώς προσθέστε την εξάρτηση Aspose και είστε έτοιμοι.

---

## Βήμα 1: Προσθήκη Aspose.Words στο Build σας

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro tip:** Η δωρεάν δοκιμαστική έκδοση λειτουργεί τέλεια για δοκιμές, αλλά θυμηθείτε να εφαρμόσετε άδεια για παραγωγή ώστε να αφαιρεθεί το υδατογράφημα αξιολόγησης.

---

## Βήμα 2: Δημιουργία DocumentConfig και Καταχώρηση Callback Προειδοποιήσεων

Η καρδιά της λύσης βρίσκεται σε αυτό το απόσπασμα. **Δημιουργούμε ένα DocumentConfig**, συνδέουμε ένα προσαρμοσμένο `IWarningCallback` και του λέμε να **παρακολουθεί μόνο τις ελλειπούσες γραμματοσειρές**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Γιατί λειτουργεί:** Όταν το Aspose.Words αναλύει ένα έγγραφο, εκπέμπει αντικείμενα `WarningInfo` για οποιεσδήποτε ανωμαλίες. Παρέχοντας ένα callback, παρεμβαίνετε σε αυτές τις προειδοποιήσεις *πριν* εξαφανιστούν. Ο έλεγχος `if` εγγυάται ότι παρακολουθούμε μόνο **ελλειπούσες γραμματοσειρές**, αγνοώντας άλλες προειδοποιήσεις όπως παρωχημένες ετικέτες ή μη υποστηριζόμενες δυνατότητες.

---

## Βήμα 3: Εκτέλεση του Παραδείγματος και Παρατήρηση του Αποτελέσματος

Τοποθετήστε ένα DOCX που αναφέρεται σε γραμματοσειρά που δεν έχετε (π.χ., “Comic Sans MS” σε Linux). Εκτελέστε το πρόγραμμα:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Θα πρέπει να δείτε κάτι παρόμοιο με:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Κάθε γραμμή αντιστοιχεί σε μια ελλειπούσα γραμματοσειρά που το Aspose αντικατέστησε αυτόματα. Αν δεν υπάρχουν ελλειπούσες γραμματοσειρές, το πρόγραμμα παραμένει σιωπηλό—ακριβώς αυτό που θέλετε για καθαρό log.

---

## Βήμα 4: Αποθήκευση της Λίστας Ελλειπουσών Γραμματοσειρών (Προαιρετικό)

Η εκτύπωση στην κονσόλα είναι χρήσιμη για demos, αλλά σε πραγματική υπηρεσία πιθανότατα θα θέλετε να αποθηκεύσετε τα δεδομένα. Εδώ είναι ένας γρήγορος τρόπος να γράψετε τις προειδοποιήσεις σε αρχείο κειμένου.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Τώρα κάθε συμβάν ελλειπούσας γραμματοσειράς προσθέτει μια γραμμή στο `missing-fonts.log`. Μπορείτε αργότερα να αναλύσετε το αρχείο, να το τροφοδοτήσετε σε πίνακα παρακολούθησης ή ακόμη και να ενεργοποιήσετε μια ειδοποίηση αν μια κρίσιμη γραμματοσειρά εξαφανιστεί από τον διακομιστή σας.

---

## Βήμα 5: Συνηθισμένα Προβλήματα και Πώς να τα Αποφύγετε

| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|----------|--------------|----------|
| Δεν εμφανίζονται προειδοποιήσεις παρόλο που το DOCX χρησιμοποιεί άγνωστες γραμματοσειρές | Το callback δεν έχει καταχωρηθεί ή το `setWarningCallback` κλήθηκε μετά τη φόρτωση του εγγράφου | Βεβαιωθείτε ότι το `config.setWarningCallback(...)` εκτελείται **πριν** δημιουργηθεί η παρουσία `Document`. |
| Η εφαρμογή καταρρέει με `NullPointerException` | Το `info.getDescription()` επιστρέφει `null` για ορισμένους σπάνιους τύπους προειδοποιήσεων | Προστατέψτε το από null: `String desc = info.getDescription(); if (desc != null) …` |
| Πάρα πολλές άσχετες προειδοποιήσεις πλημμυρίζουν την κονσόλα | Το callback φιλτράρει μόνο `FONT_SUBSTITUTION`; | Ελέγξτε ξανά τη συνθήκη `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Μείωση απόδοσης σε μεγάλες παρτίδες | Συγγραφή σε αρχείο συγχρονισμένα για κάθε προειδοποίηση | Γράψτε σε παρτίδες ή χρησιμοποιήστε `BufferedWriter` για μείωση του I/O. |

---

## Βήμα 6: Επέκταση της Λύσης – Από την Κονσόλα στην Επιχείρηση

- **Καταγραφή σε βάση δεδομένων:** Αντικαταστήστε το `FileWriter` με μια εντολή JDBC insert· αποθηκεύστε `documentName`, `missingFont` και `timestamp`.  
- **Ειδοποιήσεις μέσω email:** Συνδέστε το JavaMail· στείλτε μια σύνοψη μετά την επεξεργασία μιας παρτίδας εγγράφων.  
- **Προσαρμοσμένη λογική αντικατάστασης:** Αντί να αφήνετε το Aspose να επιλέξει εφεδρική γραμματοσειρά, μπορείτε να φορτώσετε τοπική συλλογή γραμματοσειρών μέσω `FontSettings.setFontsFolder()` και να ξανατρέξετε τη φόρτωση αν συμβεί αντικατάσταση.

Αυτές οι επεκτάσεις διατηρούν την κύρια ιδέα—**create documentconfig** και **track missing fonts**—ακέραια ενώ κλιμακώνονται στις ανάγκες παραγωγής.

---

## Συμπέρασμα

Τώρα έχετε ένα σταθερό, έτοιμο για αντιγραφή‑επικόλληση μοτίβο για **δημιουργία DocumentConfig** σε Java και χρήση του για **παρακολούθηση ελλειπούσων γραμματοσειρών** με Aspose.Words. Η προσέγγιση είναι ελαφριά, απαιτεί μόνο λίγες γραμμές κώδικα και σας δίνει πλήρη έλεγχο στο πώς διαχειρίζεστε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών. Είτε χτίζετε μια υπηρεσία μετατροπής εγγράφων, έναν αυτόματο δημιουργό αναφορών, είτε ένα εργαλείο ελέγχου συμμόρφωσης, η ακριβής γνώση των ελλειπούσων γραμματοσειρών μπορεί να εξοικονομήσει ώρες εντοπισμού σφαλμάτων.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αντικαταστήσετε την έξοδο της κονσόλας με ένα δομημένο JSON log, ή ενσωματώστε το callback σε μια μικροϋπηρεσία Spring Boot που επεξεργάζεται ανεβάσματα σε πραγματικό χρόνο. Και αν συναντήσετε ειδικές περιπτώσεις—π.χ., μια προσαρμοσμένη γραμματοσειρά OpenType που το Aspose δεν μπορεί να αναλύσει—αφήστε ένα σχόλιο παρακάτω· θα το αντιμετωπίσουμε μαζί.

Καλή προγραμματιστική, και εύχομαι τα PDF σας να αποδίδουν πάντα με τις γραμματοσειρές που περιμένετε!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Χρήση Γραμματοσειρών στο Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Προσαρμογή Χρωμάτων Θέματος & Γραμματοσειρών στο Aspose.Words Java: Ένας Πλήρης Οδηγός](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Πώς να Δημιουργήσετε PDF Έγγραφα με Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}