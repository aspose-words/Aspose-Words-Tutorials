---
category: general
date: 2026-03-25
description: Εκπαιδευτικό σεμινάριο για την κλήση προειδοποίησης κατά τη φόρτωση ενός
  εγγράφου Word σε Java και τη διαχείριση ελλιπών γραμματοσειρών. Μάθετε την προσέγγιση
  φόρτωσης εγγράφου Word σε Java με προσαρμοσμένη κλήση προειδοποίησης.
draft: false
keywords:
- warning callback tutorial
- load word document java
- handle missing fonts
language: el
og_description: Το tutorial για το callback προειδοποίησης δείχνει πώς να φορτώσετε
  ένα έγγραφο Word σε Java, διαχειριζόμενοι τις ελλείπουσες γραμματοσειρές με προσαρμοσμένο
  callback προειδοποίησης.
og_title: Οδηγός callback προειδοποίησης – Φόρτωση εγγράφου Word σε Java
tags:
- java
- aspose-words
- document-processing
title: Οδηγός προειδοποίησης callback – Φόρτωση εγγράφου Word σε Java
url: /el/java/document-loading-and-saving/warning-callback-tutorial-load-word-document-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# warning callback tutorial – Load Word Document in Java

Ποτέ προσπαθήσατε να φορτώσετε ένα αρχείο **.docx** σε Java μόνο για να δείτε μια ακατανόητη προειδοποίηση για ελλιπείς γραμματοσειρές; Δεν είστε μόνοι. Σε αυτό το **warning callback tutorial**, θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο φορτώνει ένα έγγραφο Word αλλά και συλλαμβάνει προειδοποιήσεις αντικατάστασης γραμματοσειρών ώστε να μπορείτε να αντιδράτε προγραμματιστικά.

Αν αναρωτιέστε πώς να **load word document java** ενώ παρακολουθείτε εκείνες τις ειδοποιήσεις *handle missing fonts*, βρίσκεστε στο σωστό μέρος. Στο τέλος αυτού του οδηγού θα έχετε ένα επαναχρησιμοποιήσιμο μοτίβο που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java που χρησιμοποιεί Aspose.Words (ή παρόμοια βιβλιοθήκη) και θα καταλάβετε γιατί ένα warning callback είναι ο πιο καθαρός τρόπος για να παραμένετε ενήμεροι για προβλήματα γραμματοσειρών.

---

## What You’ll Learn

- Ο ακριβής κώδικας που απαιτείται για τη ρύθμιση ενός warning callback σε Java.  
- Πώς το callback διακρίνει προειδοποιήσεις αντικατάστασης γραμματοσειρών από άλλους τύπους μηνυμάτων.  
- Τρόποι για καταγραφή, καταστολή ή ακόμη και αντικατάσταση ελλιπών γραμματοσειρών σε πραγματικό χρόνο.  
- Συμβουλές για την αντιμετώπιση κοινών παγίδων κατά τη φόρτωση εγγράφων Word που αναφέρονται σε μη διαθέσιμες γραμματοσειρές.

### Prerequisites

- Java 17 (ή νεότερη) εγκατεστημένη στο σύστημά σας.  
- Ένα εργαλείο κατασκευής όπως Maven ή Gradle (θα δείξουμε αποσπάσματα Maven).  
- Βιβλιοθήκη Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για δοκιμές).  
- Ένα δείγμα **input.docx** που χρησιμοποιεί μια γραμματοσειρά που δεν έχετε εγκατεστημένη (για να ενεργοποιήσετε την προειδοποίηση).

> **Pro tip:** Αν δεν έχετε ακόμη Aspose.Words, προσθέστε την εξάρτηση που φαίνεται παρακάτω και αφήστε το Maven να την κατεβάσει για εσάς—χωρίς χειροκίνητη διαχείριση JAR.

---

## Step 1: Set Up Your Project and Import Required Classes

Πρώτα, χρειαζόμαστε τις σωστές συντεταγμένες Maven. Προσθέστε αυτό στο `pom.xml` σας:

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Τώρα δημιουργήστε μια νέα κλάση Java, π.χ. `WordLoader.java`, και εισάγετε τους απαραίτητους τύπους:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import com.aspose.words.WarningType;
```

Αυτές οι εισαγωγές μας δίνουν πρόσβαση στο `LoadOptions`, στη διεπαφή `IWarningCallback` και στο αντικείμενο `WarningInfo` που μας λέει *τι* πήγε στραβά.

---

## Step 2: Define the Warning Callback – The Heart of the Tutorial

Το **warning callback tutorial** στηρίζεται στην παρέμβαση σε γεγονότα αντικατάστασης γραμματοσειρών. Ακολουθεί μια σύντομη αλλά πλήρως λειτουργική υλοποίηση:

```java
// Step 2: Create a warning callback that prints font substitution messages
class FontSubstitutionCallback implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("⚠️ Font substituted: " + info.getDescription());
        }
    }
}
```

**Γιατί είναι σημαντικό:**  
- Το `IWarningCallback` καλείται *κάθε* φορά που το Aspose.Words συναντά μια κατάσταση που θεωρεί αξιοσημείωτη.  
- Ελέγχοντας το `info.getWarningType()`, φιλτράρουμε τις ανεξάρτητες προειδοποιήσεις (όπως παρωχημένες δυνατότητες) και εστιάζουμε αποκλειστικά στο σενάριο **handle missing fonts**.  
- Η καταγραφή της περιγραφής σας δίνει το αρχικό όνομα της γραμματοσειράς και το εναλλακτικό που χρησιμοποιήθηκε, κάτι κρίσιμο για επακόλουθους ελέγχους διάταξης.

---

## Step 3: Wire the Callback into LoadOptions

Τώρα συνδέουμε το callback με ένα αντικείμενο `LoadOptions`. Αυτό είναι το σημείο όπου η διαδικασία **load word document java** γίνεται ενήμερη για τον προσαρμοσμένο μας χειριστή.

```java
// Step 3: Prepare LoadOptions with the custom warning callback
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontSubstitutionCallback());
```

Μπορείτε επίσης να ορίσετε άλλες επιλογές εδώ—όπως `setPassword` για κρυπτογραφημένα αρχεία ή `setLoadFormat` αν χρειάζεται να εξαναγκάσετε συγκεκριμένη μορφή. Το callback λειτουργεί ανεξάρτητα από αυτές τις ρυθμίσεις.

---

## Step 4: Load the Document and Observe the Callback in Action

Με όλα συνδεδεμένα, η φόρτωση του εγγράφου γίνεται με μια μόνο γραμμή:

```java
// Step 4: Load the .docx file using the configured LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Όταν το αρχείο αναφέρει μια ελλιπή γραμματοσειρά, θα δείτε έξοδο παρόμοια με:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Αν όλες οι γραμματοσειρές του εγγράφου είναι παρούσες, το callback παραμένει σιωπηλό—ακριβώς όπως θα περιμένατε όταν **handling missing fonts** με χάρη.

---

## Step 5: Verify the Result and Optional Post‑Processing

Μετά τη φόρτωση, ίσως θέλετε να επιβεβαιώσετε ότι το έγγραφο είναι χρησιμοποιήσιμο, ίσως μετατρέποντάς το σε PDF ή εξάγοντας απλό κείμενο:

```java
// Optional: Save as PDF to verify visual fidelity
document.save("output.pdf");

// Or extract plain text to a console for quick inspection
System.out.println(document.getText());
```

Και οι δύο ενέργειες θα σεβαστούν την αντικατάσταση που πραγματοποιήθηκε νωρίτερα, ώστε να δείτε την πραγματική επίδραση της ελλιπής γραμματοσειράς στο τελικό αποτέλεσμα.

---

## Edge Cases & Common Pitfalls

| Situation | What Happens | How to Handle |
|-----------|--------------|---------------|
| **Multiple missing fonts** | Το callback ενεργοποιείται μία φορά ανά ελλιπής γραμματοσειρά. | Κρατήστε το callback ελαφρύ· αποφύγετε βαριές λειτουργίες I/O μέσα στο `warning()`. |
| **Custom font directory** | Το Aspose.Words εξακολουθεί να αναφέρει αντικατάσταση αν η γραμματοσειρά δεν βρίσκεται στο προεπιλεγμένο μονοπάτι αναζήτησης. | Χρησιμοποιήστε `loadOptions.setFontSettings(FontSettings.getDefaultInstance())` και προσθέστε το φάκελο γραμματοσειρών μέσω `FontSettings.getDefaultInstance().setFontsFolder("path", true)`. |
| **Performance‑critical apps** | Η υπερβολική καταγραφή μπορεί να επιβραδύνει την επεξεργασία παρτίδας. | Μεταβείτε σε logger με επίπεδο `WARN` και απενεργοποιήστε την εκτύπωση στην κονσόλα σε παραγωγή. |
| **Non‑font warnings** | Το callback λαμβάνει πολλούς τύπους προειδοποιήσεων (π.χ., `DEPRECATED_FEATURE`). | Φιλτράρετε με `WarningType` όπως φαίνεται· μπορείτε επίσης να συλλέξετε άλλες προειδοποιήσεις για διαγνωστικές αναφορές. |

---

## Full Working Example

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο IDE σας. Περιλαμβάνει όλες τις εισαγωγές, την κλάση callback και μια απλή μέθοδο `main`.

```java
import com.aspose.words.*;

public class WordLoader {
    // Custom warning callback – only cares about font substitution
    static class FontSubstitutionCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("⚠️ Font substituted: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with our callback
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setWarningCallback(new FontSubstitutionCallback());

            // 2️⃣ Load the document – this triggers the callback if needed
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 3️⃣ Optional verification – save as PDF and print text
            doc.save("output.pdf");                     // visual check
            System.out.println("--- Extracted Text ---");
            System.out.println(doc.getText());          // quick sanity check
        } catch (Exception e) {
            // In real apps, use proper logging instead of printStackTrace
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (όταν εντοπιστεί ελλιπής γραμματοσειρά):

```
⚠️ Font substituted: Font 'Times New Roman' was not found. Substituted with 'Liberation Serif'.
--- Extracted Text ---
[Document text appears here...]
```

Αν δεν υπάρχουν ελλιπείς γραμματοσειρές, θα δείτε μόνο την κεφαλίδα του εξαγόμενου κειμένου.

---

## Visual Overview

![Διάγραμμα tutorial warning callback που δείχνει τη ροή από LoadOptions → IWarningCallback → έξοδο κονσόλας](/images/warning-callback-tutorial.png "Διάγραμμα tutorial warning callback")

*Το διάγραμμα απεικονίζει πώς το warning callback παρεμβάλλεται σε γεγονότα αντικατάστασης γραμματοσειρών κατά τη διαδικασία φόρτωσης του εγγράφου.*

---

## Recap & Next Steps

Μόλις ολοκληρώσαμε ένα **warning callback tutorial** που σας δείχνει πώς να **load word document java** ενώ **handle missing fonts** με κομψότητα. Τα βασικά σημεία είναι:

1. Υλοποιήστε το `IWarningCallback` και φιλτράρετε για `WarningType.FONT_SUBSTITUTION`.  
2. Συνδέστε το callback στο `LoadOptions` πριν φορτώσετε το έγγραφο.  
3. Επαληθεύστε το αποτέλεσμα αποθηκεύοντας ή εξάγοντας κείμενο, και προαιρετικά βελτιστοποιήστε τις διαδρομές αναζήτησης γραμματοσειρών.

Από εδώ μπορείτε να εξερευνήσετε:

- **Custom font substitution**: Αντικαταστήστε προγραμματιστικά τη λείπουσα γραμματοσειρά με μια της επιλογής σας.  
- **Batch processing**: Περάστε από έναν φάκελο εγγράφων, συλλέγοντας όλες τις προειδοποιήσεις αντικατάστασης σε αναφορά CSV.  
- **Integration with logging frameworks**: Κατευθύνετε τις προειδοποιήσεις σε Log4j ή SLF4J για διαγνωστικά επιπέδου παραγωγής.

Δοκιμάστε αυτές τις ιδέες και θα δείτε πόσο ισχυρό μπορεί να είναι ένα καλά τοποθετημένο warning callback σε πραγματικές ροές επεξεργασίας εγγράφων.

---

### Got Questions?

Μη διστάσετε να αφήσετε ένα σχόλιο παρακάτω ή να με ping στο GitHub. Καλό coding, και εύχομαι τα έγγραφά σας να εμφανίζονται πάντα με τις γραμματοσειρές που περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}