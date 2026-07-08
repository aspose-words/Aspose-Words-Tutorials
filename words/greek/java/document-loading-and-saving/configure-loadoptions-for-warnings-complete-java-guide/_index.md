---
category: general
date: 2026-06-30
description: Διαμορφώστε τις LoadOptions για προειδοποιήσεις στο Aspose.Words Java.
  Μάθετε πώς να ρυθμίσετε μια κλήση επιστροφής προειδοποίησης για αντικατάσταση γραμματοσειρών
  και άλλες προειδοποιήσεις επιλογών φόρτωσης.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: el
og_description: Διαμορφώστε τις LoadOptions για προειδοποιήσεις στο Aspose.Words Java.
  Αυτός ο οδηγός δείχνει πώς να καταγράψετε τις ειδοποιήσεις αντικατάστασης γραμματοσειράς
  με μια κλήση επιστροφής προειδοποίησης.
og_title: Διαμόρφωση LoadOptions για Προειδοποιήσεις – Μάθημα Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Διαμόρφωση LoadOptions για Προειδοποιήσεις – Πλήρης Οδηγός Java
url: /el/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαμόρφωση LoadOptions για Προειδοποιήσεις – Πλήρης Οδηγός Java

Έχετε χρειαστεί ποτέ να **διαμορφώσετε LoadOptions για προειδοποιήσεις** όταν ανοίγετε ένα έγγραφο Word με το Aspose.Words for Java; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν το πρόβλημα όταν μια ελλιπής γραμματοσειρά αντικαθίσταται σιωπηρά, αφήνοντας το τελικό PDF να φαίνεται εκτός μάρκας. Το καλό νέο; Με την προσθήκη μιας **Java warning callback** στα `LoadOptions` σας, μπορείτε να πιάσετε κάθε ειδοποίηση αντικατάστασης γραμματοσειράς τη στιγμή που συμβαίνει.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που όχι μόνο δείχνει πώς να ρυθμίσετε το callback, αλλά εξηγεί και *γιατί* κάθε στοιχείο είναι σημαντικό. Στο τέλος θα μπορείτε να **χειριστείτε προειδοποιήσεις γραμματοσειρών**, να τις καταγράψετε ή ακόμη και να αντικαταστήσετε γραμματοσειρές εν κινήσει—χωρίς εικασίες.

## Τι Θα Κερδίσετε

- Ένα πλήρως εκτελέσιμο πρόγραμμα Java που εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς.  
- Κατανόηση των μηχανισμών **Aspose.Words font substitution**.  
- Συμβουλές για προσαρμογή του χειρισμού προειδοποιήσεων σε μεγαλύτερα έργα.  
- Επισκόπηση των **document loading options** και πότε να τις τροποποιήσετε.

> **Προαπαιτούμενο:** Java 8+ και η βιβλιοθήκη Aspose.Words for Java (έκδοση 23.9 ή νεότερη). Δεν απαιτούνται άλλες εξωτερικές εξαρτήσεις.

---

## Βήμα 1: Διαμόρφωση LoadOptions για Προειδοποιήσεις

Το πρώτο που χρειάζεστε είναι μια παρουσία `LoadOptions` που ξέρει ότι πρέπει να αναφέρει προειδοποιήσεις. Σκεφτείτε το `LoadOptions` ως το κουτί εργαλείων που δίνετε στο Aspose.Words πριν ακόμη ανοίξει το αρχείο.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Γιατί είναι σημαντικό:**  
`LoadOptions` ελέγχει πώς η βιβλιοθήκη διαβάζει το έγγραφο. Αναθέτοντας ένα `IWarningCallback`, λέτε στο Aspose.Words να καλέσει τον κώδικά σας όποτε συναντήσει κάτι αξιοσημείωτο—όπως μια ελλιπή γραμματοσειρά. Χωρίς αυτό, η βιβλιοθήκη θα αντικαθιστούσε σιωπηρά τη γραμματοσειρά και δεν θα το γνωρίζατε.

> **Pro tip:** Αν θέλετε να συλλάβετε *όλες* τις προειδοποιήσεις, αφαιρέστε τον έλεγχο `if`. Για τώρα εστιάζουμε στα προβλήματα γραμματοσειρών επειδή είναι η πιο συχνή πηγή απρόσμενων αλλαγών διάταξης.

---

## Βήμα 2: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Τώρα που το callback είναι έτοιμο, φορτώστε το `.docx` (ή οποιαδήποτε υποστηριζόμενη μορφή) με τα ίδια `LoadOptions`. Εδώ οι **document loading options** παίρνουν πραγματικά ισχύ.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Πίσω από τη σκηνή:**  
Καθώς το Aspose.Words αναλύει το `input.docx`, σαρώνει τους πίνακες γραμματοσειρών. Αν μια γραμματοσειρά που αναφέρεται στο έγγραφο δεν είναι εγκατεστημένη στο σύστημα, η μηχανή δημιουργεί μια προειδοποίηση `FONT_SUBSTITUTION`, η οποία ενεργοποιεί αμέσως το callback που ορίσαμε νωρίτερα.

---

## Βήμα 3: Αποθήκευση του Εγγράφου – Οι Προειδοποιήσεις Έχουν Ήδη Εκτυπωθεί

Η αποθήκευση του εγγράφου είναι απλή, αλλά είναι η στιγμή που μπορείτε να επαληθεύσετε ότι το callback εκτελέστηκε σωστά. Όλες οι προειδοποιήσεις εκτυπώνονται κατά το βήμα φόρτωσης, οπότε η λειτουργία αποθήκευσης είναι απλώς καθαριστική.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Αναμενόμενη έξοδος κονσόλας:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Αν δεν δείτε τίποτα, είτε το έγγραφο χρησιμοποίησε μόνο εγκατεστημένες γραμματοσειρές, είτε το callback δεν συνδέθηκε σωστά—ελέγξτε ξανά το Βήμα 1.

---

## Βήμα 4: Επέκταση του Callback για **Χειρισμό Προειδοποιήσεων Γραμματοσειρών** με Ευγένεια

Η εκτύπωση στην κονσόλα είναι αποδεκτή για demos, αλλά ο κώδικας παραγωγής συχνά χρειάζεται πιο πλούσιο χειρισμό: καταγραφή σε αρχείο, αποστολή ειδοποιήσεων ή ακόμη και αντικατάσταση γραμματοσειρών προγραμματιστικά.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Γιατί θα το κάνατε:**  
Ένα αρχείο καταγραφής σας δίνει μετα‑ανάλυση, ειδικά όταν επεξεργάζεστε δέσμες εγγράφων. Το προαιρετικό τμήμα αντικατάστασης δείχνει πώς να **διαμορφώσετε LoadOptions για προειδοποιήσεις** *και* να παρέμβετε για να επιβάλλετε μια εταιρική πολιτική γραμματοσειρών.

---

## Προχωρημένα: Έλεγχος Άλλων Σεναρίων **Aspose.Words Font Substitution**

Το callback προειδοποιήσεων δεν περιορίζεται μόνο σε ελλιπείς γραμματοσειρές. Μπορείτε επίσης να πιάσετε:

- **Μη υποστηριζόμενους Unicode χαρακτήρες** (`WarningType.UNSUPPORTED_CHAR`).  
- **Θέματα σύνθετων γραφών** (`WarningType.COMPLEX_SCRIPT`).

Απλώς επεκτείνετε την εντολή `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Αυτό κάνει τη λύση σας ανθεκτική για πολυγλωσσικά έγγραφα, ένα κοινό edge case σε παγκόσμιες εφαρμογές.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Επικολλήστε το σε οποιοδήποτε IDE Java, αντικαταστήστε τα placeholders `YOUR_DIRECTORY` και πατήστε *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Η κονσόλα εκτυπώνει τυχόν προειδοποιήσεις αντικατάστασης γραμματοσειράς.  
- Το `font-warnings.log` περιέχει μια λίστα με χρονική σήμανση (αν διατηρήσατε την προαιρετική καταγραφή).  
- Το `output.docx` αποθηκεύεται με τις αντικατεστημένες γραμματοσειρές, ταιριάζοντας στην εναλλακτική που ορίσατε.

---

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Λύση |
|----------|----------------|------|
| **Δεν εμφανίζονται προειδοποιήσεις** | Το callback δεν συνδέθηκε, ή το έγγραφο χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές. | Βεβαιωθείτε ότι το `loadOptions.setWarningCallback(...)` καλείται *πριν* τη φόρτωση του εγγράφου. |
| **FileNotFoundException** στο `input.docx` | Λάθος διαδρομή ή το αρχείο δεν περιλαμβάνεται στο project. | Χρησιμοποιήστε απόλυτη διαδρομή ή τοποθετήστε το αρχείο στον φάκελο resources του project. |
| **Μείωση απόδοσης** όταν επεξεργάζεστε χιλιάδες έγγραφα | Υπερβολική καταγραφή σε δίσκο για κάθε προειδοποίηση. | Συγκεντρώστε τις καταγραφές σε παρτίδες ή περιορίστε την καταγραφή σε κρίσιμες προειδοποιήσεις. |
| **Απρόσμενη αντικατάσταση γραμματοσειράς** παρά την εναλλακτική | Ο πίνακας αντικατάστασης δεν εφαρμόστηκε έγκαιρα. | Ορίστε τις ρυθμίσεις αντικατάστασης **πριν** τη φόρτωση του εγγράφου, ή χρησιμοποιήστε `FontSettings.setSubstitutionSettings` παγκοσμίως. |

---

## Επόμενα Βήματα

Τώρα που έχετε κυριαρχήσει στη **διαμόρφωση LoadOptions για προειδοποιήσεις**, σκεφτείτε τα εξής θέματα:

- **Batch processing**: Επανάληψη σε κατάλογο εγγράφων, συγκεντρώνοντας όλες τις προειδοποιήσεις γραμματοσειρών σε μια ενιαία αναφορά.  
- **Custom font providers**: Φόρτωση γραμματοσειρών από δικτυακό χώρο ή ενσωματωμένους πόρους αντί για το τοπικό OS.  
- **Ενσωμάτωση με πλαίσια καταγραφής** όπως Log4j για επιχειρησιακό επίπεδο traceability.  
- Εξερευνήστε άλλες **document loading options** όπως ανίχνευση `LoadFormat` ή διαχείριση `Password` για προστατευμένα αρχεία.

Κάθε ένα από αυτά βασίζεται στο ίδιο μοτίβο—δημιουργήστε ένα αντικείμενο `LoadOptions`, συνδέστε τα κατάλληλα callbacks, και αφήστε το Aspose.Words να κάνει το σκληρό έργο.

---

## Συμπέρασμα

Καταπιάσαμε σε βάθος πώς να **διαμορφώσετε LoadOptions για προειδοποιήσεις** στο Aspose.Words for Java, να ρυθμίσουμε ένα **Java warning callback**, και να χρησιμοποιήσουμε αυτές τις πληροφορίες για **έξυπνο χειρισμό προειδοποιήσεων γραμματοσειρών**. Ο κώδικας είναι σύντομος, οι έννοιες σαφείς, και έχετε τώρα μια σταθερή βάση για να επεκτείνετε τον χειρισμό προειδοποιήσεων σε άλλα σενάρια όπως μη υποστηριζόμενοι χαρακτήρες ή σύνθετες γραφές.

Δοκιμάστε το, προσαρμόστε τον πίνακα αντικατάστασης ώστε να ταιριάζει στις εταιρικές σας γραμματοσειρές, και παρακολουθήστε τις σιωπηλές αντικαταστάσεις γραμματοσειρών να εξαφανίζονται. Καλό coding!

--- 

![Διάγραμμα που δείχνει τη ροή διαμόρφωσης LoadOptions για προειδοποιήσεις, φόρτωσης εγγράφου, σύλληψης συμβάντων αντικατάστασης γραμματοσειράς, και αποθήκευσης του αποτελέσματος](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}