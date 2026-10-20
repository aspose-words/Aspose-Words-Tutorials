---
category: general
date: 2026-04-24
description: Μάθετε πώς να αποθηκεύσετε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words,
  ρυθμίζοντας τις ρυθμίσεις γραμματοσειράς και αντιμετωπίζοντας τις ελλείπουσες γραμματοσειρές
  με εύκολο στην κατανόηση κώδικα Java.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: el
og_description: Αποθήκευση εγγράφου Word με το Aspose.Words ενώ ορίζετε ρυθμίσεις
  γραμματοσειράς και διαχειρίζεστε τις ελλείπουσες γραμματοσειρές. Πλήρης οδηγός Java
  για προγραμματιστές.
og_title: Αποθήκευση εγγράφου Word – Ορισμός ρυθμίσεων γραμματοσειράς, Διαχείριση
  ελλιπών γραμματοσειρών
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Αποθήκευση εγγράφου Word – Ορισμός ρυθμίσεων γραμματοσειράς, Διαχείριση ελλιπών
  γραμματοσειρών
url: /el/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφου Word – Ορισμός ρυθμίσεων γραμματοσειράς, Διαχείριση ελλιπών γραμματοσειρών

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε έγγραφο Word** αλλά το αρχείο προέλευσης χρησιμοποιεί γραμματοσειρές που δεν υπάρχουν στον διακομιστή σας; Είναι ένα συχνό πρόβλημα που μπορεί να μετατρέψει μια ομαλή διαδικασία αυτοματοποίησης σε πονοκέφαλο.  

Τα καλά νέα; Με το Aspose.Words μπορείτε να **ορίσετε ρυθμίσεις γραμματοσειράς** εν κινήσει, να εντοπίσετε προειδοποιήσεις ελλιπών γραμματοσειρών και να καταλήξετε σε ένα τέλεια αποθηκευμένο έγγραφο Word. Σε αυτό το tutorial θα περάσουμε από ένα πλήρες παράδειγμα Java που δείχνει **πώς να ορίσετε ρυθμίσεις γραμματοσειράς**, να διαχειριστείτε τις ενοχλητικές προειδοποιήσεις *αντικατάστασης γραμματοσειράς* και τελικά να **αποθηκεύσετε έγγραφο Word** χωρίς εκπλήξεις.

## Τι θα μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` με ένα προσαρμοσμένο αντικείμενο `FontSettings`.  
- Πώς να καταχωρίσετε μια callback προειδοποίησης που αναφέρει γεγονότα **aspose words font substitution**.  
- Πώς να φορτώσετε ένα DOCX, να αφήσετε το Aspose να αντικαταστήσει τις ελλιπείς γραμματοσειρές και να **αποθηκεύσετε έγγραφο Word** σε νέα τοποθεσία.  
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως κρυπτογραφημένα αρχεία ή έγγραφα με ενσωματωμένες γραμματοσειρές.  

Δεν απαιτούνται επιπλέον βιβλιοθήκες πέρα από το Aspose.Words, και ο κώδικας λειτουργεί με την πιο πρόσφατη έκδοση 24.x (απρίλιος 2026).  

---

![Διάγραμμα που απεικονίζει τη ροή αποθήκευσης εγγράφου Word με ρυθμίσεις γραμματοσειράς και callback προειδοποίησης](font-workflow.png "Διάγραμμα που δείχνει τη ροή αποθήκευσης εγγράφου Word")

## Αποθήκευση εγγράφου Word με προσαρμοσμένες ρυθμίσεις γραμματοσειράς

Το πρώτο βήμα είναι να πείτε στο Aspose.Words τι πρέπει να κάνει όταν δεν μπορεί να βρει μια γραμματοσειρά που αναφέρεται στο έγγραφο προέλευσης. Εδώ έρχεται σε παιχνίδι η **set font settings**.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Γιατί λειτουργεί αυτό:**  
- Το `LoadOptions` λέει στο Aspose.Words να χρησιμοποιήσει το παρεχόμενο `FontSettings` κατά την ανάλυση του αρχείου.  
- Το `IWarningCallback` παρεμβάλλεται σε οποιαδήποτε μηνύματα **aspose words font substitution**, παρέχοντάς σας ένα ζωντανό αρχείο καταγραφής των γραμματοσειρών που λείπουν.  
- Όταν καλείτε `document.save(...)`, το Aspose αντικαθιστά αυτόματα τις ελλιπείς γραμματοσειρές με τις πιο κοντινές αντιστοιχίες από το σύστημα ή τους φακέλους που προσθέσατε στο `FontSettings`.

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος εκτυπώνει γραμμές όπως:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

Και καταλήγετε με το `output.docx` που φαίνεται ακριβώς όπως το αρχικό—εκτός από το ότι οι ελλιπείς γραμματοσειρές έχουν αντικατασταθεί, και το αρχείο έχει **saved word document** επιτυχώς στο δίσκο.

## Πώς να ορίσετε ρυθμίσεις γραμματοσειράς στο Aspose.Words

Αν χρειάζεστε μεγαλύτερο έλεγχο—π.χ. θέλετε να κατευθύνετε το Aspose σε έναν προσαρμοσμένο φάκελο γραμματοσειρών ή να ενσωματώσετε μια εφεδρική γραμματοσειρά—απλώς τροποποιήστε το αντικείμενο `FontSettings` πριν το αναθέσετε στο `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**Πότε να το χρησιμοποιήσετε:**  
- Η εφαρμογή σας εκτελείται σε κοντέινερ που περιλαμβάνει μόνο ένα ελάχιστο σύνολο συστημικών γραμματοσειρών.  
- Διαθέτετε εταιρικές γραμματοσειρές branding που βρίσκονται σε ασφαλή δικτυακή κοινή χρήση.  
- Θέλετε να εγγυηθείτε ότι μια συγκεκριμένη εφεδρική γραμματοσειρά (π.χ. “Arial”) χρησιμοποιείται πάντα, αποφεύγοντας απρόβλεπτες αντικαταστάσεις.

## Διαχείριση ελλιπών γραμματοσειρών – Callback αντικατάστασης γραμματοσειράς

Η callback προειδοποίησης που καταχωρίσαμε νωρίτερα αποτελεί την καρδιά της λογικής **handle missing fonts**. Μπορείτε να την επεκτείνετε ώστε:

1. **Συλλέξετε προειδοποιήσεις** σε λίστα για μεταγενέστερη αναφορά.  
2. **Ρίξετε εξαίρεση** αν λείπει μια κρίσιμη γραμματοσειρά (π.χ. γραμματοσειρά λογότυπου).  
3. **Καταγράψετε σε σύστημα παρακολούθησης** (Splunk, ELK, κ.λπ.) για αρχεία ελέγχου.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**Συμβουλή επαγγελματία:** Αν χρειάζεται να διακόψετε τη λειτουργία όταν λείπει μια συγκεκριμένη γραμματοσειρά, συγκρίνετε το `info.getDescription()` με μια λευκή λίστα και ρίξτε `RuntimeException` όταν η σύγκριση αποτύχει.

## Πλήρες παράδειγμα Java – Από την αρχή μέχρι το τέλος

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο IDE σας. Βεβαιωθείτε ότι έχετε το Aspose.Words for Java JAR στο classpath.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Εκτελέστε το πρόγραμμα, παρακολουθήστε την κονσόλα για τυχόν **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}