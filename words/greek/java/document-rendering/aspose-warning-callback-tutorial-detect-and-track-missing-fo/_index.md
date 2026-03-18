---
category: general
date: 2026-03-17
description: Μάθετε το tutorial του aspose warning callback για την ανίχνευση ελλιπών
  γραμματοσειρών και την παρακολούθησή τους σε έγγραφα Java, με ένα πλήρες, εκτελέσιμο
  παράδειγμα.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: el
og_description: Κατακτήστε το tutorial για το aspose warning callback ώστε να εντοπίζετε
  ελλείπουσες γραμματοσειρές και να παρακολουθείτε τις ελλείπουσες γραμματοσειρές
  στη ροή εργασίας επεξεργασίας κειμένου Java.
og_title: Οδηγός κλήσης προειδοποίησης Aspose – Ανίχνευση ελλειπόντων γραμματοσειρών
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Οδηγός προειδοποίησης callback του Aspose – Εντοπισμός και παρακολούθηση ελλιπών
  γραμματοσειρών
url: /el/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Ανίχνευση και Παρακολούθηση Ελλειπουσών Γραμματοσειρών

Έχετε αναρωτηθεί ποτέ πώς να **ανιχνεύσετε ελλειπούσες γραμματοσειρές** όταν μετατρέπετε ή επεξεργάζεστε αρχεία Word με το Aspose.Words; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, μια εσφαλμένη γραμματοσειρά μπορεί να προκαλέσει προβλήματα διάταξης, και χρειάζεστε έναν αξιόπιστο τρόπο για **να παρακολουθείτε ελλειπούσες γραμματοσειρές** πριν σας δημιουργήσουν προβλήματα αργότερα.  

Τα καλά νέα; Το **aspose warning callback tutorial** σας παρέχει ένα καθαρό, προγραμματιζόμενο hook που εκτυπώνει ακριβώς τις προειδοποιήσεις αντικατάστασης γραμματοσειρών καθώς συμβαίνουν. Σε αυτόν τον οδηγό θα περάσουμε από τη ρύθμιση του callback, τη φόρτωση ενός εγγράφου και την παρακολούθηση των προειδοποιήσεων σε δράση — όλα σε Java.

Στο τέλος αυτού του άρθρου θα μπορείτε να εντοπίζετε ελλειπούσες γραμματοσειρές αυτόματα, να τις καταγράφετε και να αποφασίζετε αν θα ενσωματώσετε μια εναλλακτική ή θα προσαρμόσετε τα αρχεία πηγής σας. Δεν απαιτούνται εξωτερικά εργαλεία.

## Προαπαιτούμενα

- **Java 8+** (ο κώδικας μεταγλωττίζεται με οποιοδήποτε πρόσφατο JDK)
- **Aspose.Words for Java** έκδοση 23.10 ή νεότερη — κατεβάστε από το portal του Aspose ή προσθέστε την εξάρτηση Maven.
- Ένα δείγμα DOCX που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., “Comic Sans MS” σε Linux μηχάνημα).

Αυτό είναι όλο — χωρίς επιπλέον βιβλιοθήκες, χωρίς σύνθετα βήματα κατασκευής.

## Βήμα 1: Καταχώρηση Callback Προειδοποίησης — Ο Πυρήνας του aspose warning callback tutorial

Το πρώτο πράγμα που σας διδάσκει ο οδηγός είναι πώς να συνδέσετε έναν ακροατή προειδοποίησης. Το Aspose.Words δημιουργεί ένα αντικείμενο `WarningInfo` για κάθε πρόβλημα που εντοπίζει, και η σημαία `WarningSource.FONT_SUBSTITUTION` μας λέει ακριβώς πότε γίνεται αντικατάσταση μιας γραμματοσειράς.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Γιατί είναι σημαντικό:** Χωρίς το callback, το Aspose αντικαθιστά σιωπηλά τις ελλειπούσες γραμματοσειρές, και δεν ξέρετε ποτέ ποιοι χαρακτήρες μπορεί να εμφανίζονται λανθασμένα. Καταγράφοντας την προειδοποίηση, μπορείτε να **ανιχνεύσετε ελλειπούσες γραμματοσειρές** νωρίς και να αποφασίσετε αν θα ενσωματώσετε τη σωστή.

> **Συμβουλή:** Αν χρειάζεστε να συλλέξετε προειδοποιήσεις για μεταγενέστερη αναφορά, αποθηκεύστε τις σε μια `List<WarningInfo>` αντί να τις εκτυπώνετε απευθείας.

## Βήμα 2: Φόρτωση Εγγράφου — Όπου οι ελλειπούσες γραμματοσειρές μπορεί να κρύβονται

Τώρα φορτώνουμε το DOCX που μπορεί να αναφέρει γραμματοσειρές που δεν υπάρχουν στο σύστημα. Η διαδικασία φόρτωσης ενεργοποιεί το callback προειδοποίησης εάν λείπουν γραμματοσειρές.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Τι συμβαίνει στο παρασκήνιο;** Το Aspose αναλύει τους ορισμούς στυλ του εγγράφου, σαρώνει κάθε τμήμα κειμένου και ελέγχει το αποθετήριο γραμματοσειρών του συστήματος. Όταν δεν βρίσκει την ακριβή αντιστοιχία, επιστρέφει σε εναλλακτική και εκκινεί την προειδοποίηση που μόλις συνδέσαμε.

## Βήμα 3: Αποθήκευση Εγγράφου — Εκκαθάριση των προειδοποιήσεων

Τέλος, αποθηκεύουμε το έγγραφο. Η λειτουργία αποθήκευσης επίσης επανεξετάζει τις γραμματοσειρές, έτσι οποιεσδήποτε προειδοποιήσεις που δεν εκδόθηκαν κατά τη φόρτωση θα εμφανιστούν τώρα.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Όταν εκτελέσετε το πρόγραμμα, θα δείτε έξοδο κονσόλας παρόμοια με:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Αυτή η έξοδος αποδεικνύει ότι το **aspose warning callback tutorial** λειτουργεί, και έχετε επιτυχώς **ανιχνεύσει ελλειπούσες γραμματοσειρές** και τώρα **παρακολουθείτε ελλειπούσες γραμματοσειρές** μέσω του αρχείου καταγραφής.

## Πώς να Ανιχνεύσετε Ελλειπούσες Γραμματοσειρές σε Έγγραφο Word — Πέρα από τα Βασικά

Η προσέγγιση με callback είναι εξαιρετική για μεμονωμένες εκτελέσεις, αλλά κάποιες φορές χρειάζεστε ένα επαναχρησιμοποιήσιμο εργαλείο. Εδώ είναι ένας γρήγορος wrapper που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Κλήστε το ως εξής:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Τώρα έχετε μια επαναχρησιμοποιήσιμη μέθοδο **detect missing fonts** που επιστρέφει μια λίστα που μπορείτε να τροφοδοτήσετε σε μια CI pipeline ή σε UI.

## Παρακολούθηση Ελλειπουσών Γραμματοσειρών με Aspose.Words — Αναφορά για Ομάδες

Σε μεγαλύτερη ομάδα, ίσως θέλετε να δημιουργήσετε μια αναφορά CSV με όλες τις ελλειπούσες γραμματοσειρές σε πολλά έγγραφα. Συνδυάστε το προηγούμενο εργαλείο με απλή επανάληψη αρχείων:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Η εκτέλεση αυτού του script θα σας δώσει ένα CSV **track missing fonts** που κάθε προγραμματιστής μπορεί να ρίξει μια ματιά πριν υποβάλει ένα έγγραφο στην παραγωγή.

## Συνηθισμένα Παγίδες & Πώς να τις Αποφύγετε

| Παγίδα | Γιατί συμβαίνει | Διόρθωση |
|--------|----------------|----------|
| **Callback not firing** | Ξεχάσατε να ορίσετε το callback **πριν** τη φόρτωση του εγγράφου. | Τοποθετήστε `Document.setWarningCallback` στην κορυφή του `main`. |
| **Only first warning appears** | Το Aspose αποθηκεύει στην κρυφή μνήμη (cache) τις προειδοποιήσεις ανά αντικείμενο `Document`. | Χρησιμοποιήστε νέο αντικείμενο `Document` για κάθε αρχείο ή επαναφέρετε το callback μεταξύ των εκτελέσεων. |
| **Wrong font name in log** | Η περιγραφή περιέχει επιπλέον κείμενο (“Font … not found”). | Αφαιρέστε το με regex όπως φαίνεται στο παράδειγμα CSV. |
| **Performance hit on large batches** | Το callback εκτελείται σε κάθε τμήμα κειμένου, κάτι που μπορεί να είναι δαπανηρό. | Περιορίστε τον έλεγχο σε ένα βήμα προπτήρησης· παραλείψτε την αποθήκευση αν χρειάζεστε μόνο ανίχνευση. |

## Αναμενόμενα Αποτελέσματα & Επαλήθευση

1. **Έξοδος κονσόλας** – Θα πρέπει να δείτε τουλάχιστον μία γραμμή “Font substitution warning” για κάθε ελλειπούσα γραμματοσειρά.  
2. **Αναφορά CSV** – Μετά το τέλος του script μαζικής επεξεργασίας, ανοίξτε το `missing-fonts-report.csv` και ελέγξτε ότι κάθε γραμμή περιλαμβάνει το όνομα του εγγράφου και τη συγκεκριμένη ελλειπούσα γραμματοσειρά.  
3. **Αποθηκευμένο έγγραφο** – Το παραγόμενο DOCX θα εμφανίζεται με τις εναλλακτικές γραμματοσειρές, αλλά η οπτική διάταξη μπορεί να διαφέρει από το αρχικό.

Αν κάποιο από αυτά τα βήματα δεν συμπεριφέρεται όπως περιγράφεται, ελέγξτε ξανά ότι το Aspose.Words JAR βρίσκεται στο classpath σας και ότι το `input.docx` πραγματικά αναφέρει μια γραμματοσειρά που λείπει από το λειτουργικό σας σύστημα.

## Συμπέρασμα

Μόλις ολοκληρώσατε ένα **aspose warning callback tutorial** που δείχνει πώς να **ανιχνεύσετε ελλειπούσες γραμματοσειρές** και **να παρακολουθείτε ελλειπούσες γραμματοσειρές** σε εφαρμογές Java. Καταγράφοντας έναν ακροατή προειδοποίησης, φορτώνοντας το έγγραφο και προαιρετικά εξάγοντας τα αποτελέσματα, αποκτάτε πλήρη ορατότητα στα ζητήματα γραμματοσειρών πριν εμφανιστούν στην παραγωγή.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

- Ενσωμάτωση της ελλειπούσας γραμματοσειράς απευθείας με `LoadOptions.setFontSubstitution`.  
- Χρήση της κλάσης `FontSettings` για αντιστοίχιση ελλειπούσων γραμματοσειρών σε συγκεκριμένες εναλλακτικές.  
- Ενσωμάτωση της αναφοράς CSV σε pipeline CI/CD ώστε να αποτυγχάνουν οι builds όταν εμφανίζονται αδόμητες γραμματοσειρές.

Δοκιμάστε το, προσαρμόστε τα callbacks ώστε να ταιριάζουν με το σύστημα καταγραφής σας, και παρακολουθήστε τη ροή εργασίας των εγγράφων σας να γίνεται πολύ πιο ανθεκτική. Καλό προγραμματισμό!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}