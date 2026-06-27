---
category: general
date: 2026-06-27
description: Μάθετε πώς να καταγράφετε προειδοποιήσεις αντικατάστασης γραμματοσειρών
  σε Java χρησιμοποιώντας το Aspose.Words. Αυτό το βήμα‑βήμα εκπαιδευτικό υλικό καλύπτει
  επίσης τις κλήσεις επιστροφής προειδοποιήσεων και τη χρήση του LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: el
og_description: Καταγράψτε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών σε Java
  με το Aspose.Words. Ακολουθήστε αυτόν τον οδηγό για να ρυθμίσετε callbacks προειδοποιήσεων,
  να χρησιμοποιήσετε το LoadOptions και να διαχειριστείτε τις ελλείπουσες γραμματοσειρές.
og_title: Καταγραφή Προειδοποιήσεων Υποκατάστασης Γραμματοσειρών σε Java – Εκπαίδευση
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειρών σε Java με το Aspose.Words
  – Πλήρης οδηγός
url: /el/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς σε Java με Aspose.Words – Πλήρης Οδηγός

Χρειάστηκε ποτέ να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** κατά τη φόρτωση ενός DOCX που χρησιμοποιεί εξωτικές γραμματοσειρές; Δεν είστε ο μόνος. Σε πολλά πραγματικά έργα—σκεφτείτε αυτόματους δημιουργούς αναφορών ή μετατροπείς εγγράφων σε παρτίδες—η έλλειψη γραμματοσειρών προκαλεί σιωπηλές αντικαταστάσεις που μπορούν να χαλάσουν την πιστότητα της διάταξης.

Fortunately, Aspose.Words gives you a clean way to listen for those warnings. In this tutorial we'll walk through configuring **LoadOptions**, wiring an **Aspose.Words warning callback**, and printing every *font substitution* notice to the console. By the end you'll know exactly when a font has been swapped and how to react programmatically.

> **Τι θα πάρετε:** ένα πλήρως εκτελέσιμο απόσπασμα Java, μια εξήγηση του *γιατί* κάθε μέρος είναι σημαντικό, και συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως προσαρμοσμένοι φάκελοι γραμματοσειρών.

## Προαπαιτούμενα & Τι Θα Χρειαστείτε

- Java 8 ή νεότερη εγκατεστημένη (ο κώδικας λειτουργεί επίσης με Java 11+).
- Το πιο πρόσφατο Aspose.Words for Java JAR (κατεβάστε από την επίσημη ιστοσελίδα ή το Maven Central).
- Ένα αρχείο DOCX που αναφέρει γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας (π.χ., ένα *font‑rich.docx* που μπορείτε να βρείτε στο σύνολο demo του Aspose).
- Ένα καλό IDE (IntelliJ IDEA, Eclipse ή ακόμη και VS Code με επεκτάσεις Java).

No external libraries beyond Aspose.Words are required, and the example runs in a plain `main` method.

## Βήμα 1: Ρύθμιση LoadOptions – Το Σημείο Εισόδου για Προσαρμοσμένη Φόρτωση

`LoadOptions` is Aspose.Words’ configuration bag that tells the library *how* to read a document. By default it silently substitutes missing fonts, but you can change that behavior with a warning callback.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Γιατί είναι σημαντικό:** Χωρίς `LoadOptions`, το έγγραφο φορτώνεται αθόρυβα και χάνετε την ορατότητα στις ελλιπείς γραμματοσειρές. Δημιουργώντας μια παρουσία κερδίζετε ένα hook για το σύστημα προειδοποιήσεων.

## Βήμα 2: Ορισμός Callback Προειδοποίησης για *Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς*

Aspose.Words pushes warning events through the `IWarningCallback` interface. Implement it inline (or as a separate class) and filter for `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Εξήγηση:**  
- `info.getWarningType()` σας λέει την κατηγορία της προειδοποίησης.  
- `WarningType.FONT_SUBSTITUTION` είναι η τιμή enum που μας ενδιαφέρει.  
- `info.getDescription()` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα, π.χ., *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Με την εκτύπωση της περιγραφής, **καταγράφετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** σε πραγματικό χρόνο.

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Ρυθμισμένες LoadOptions

Now that the callback is in place, load your DOCX. The warning callback fires automatically during parsing.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Replace `YOUR_DIRECTORY` with the actual path to your test file. When the `Document` constructor runs, any missing font triggers the callback defined earlier, and you’ll see the substitution messages on the console.

## Βήμα 4: Επαλήθευση του Φορτωμένου Εγγράφου (Προαιρετικό αλλά Χρήσιμο)

After loading, you might want to confirm the document's integrity—page count, text extraction, etc. This step isn’t required for capturing warnings, but it helps you see the impact of substitutions.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

If a font was substituted, the layout may shift slightly; checking the page count can reveal such changes.

## Βήμα 5: Προχωρημένο – Διαχείριση Αντικαταστημένων Γραμματοσειρών Προγραμματιστικά

Sometimes you don’t just want to log the warning—you might need to embed a fallback font or adjust styling. Below is a quick pattern you can adopt.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

By pointing Aspose.Words to a folder that contains the original fonts, you can *prevent* substitution altogether. If the folder is missing, the warning callback still captures the event, giving you a fallback strategy.

## Πλήρες Παράδειγμα Εργασίας

Putting it all together, here’s the complete, ready‑to‑run program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (όταν εντοπιστεί μια ελλιπής γραμματοσειρά):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

If all fonts are present, the callback remains silent—nothing is printed, which is exactly what you’d expect.

## Κοινά Παράπτωμα & Επαγγελματικές Συμβουλές

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Callback never fires** | Ξεχάσατε να συνδέσετε το callback στο `LoadOptions` **ή** χρησιμοποιήσατε τον προεπιλεγμένο κατασκευαστή του `Document` χωρίς να περάσετε `loadOptions`. | Πάντα καλέστε `loadOptions.setWarningCallback(...)` **και** χρησιμοποιήστε την υπερφόρτωση `new Document(path, loadOptions)`. |
| **Too many warnings clutter the log** | Μεγάλα έγγραφα με πολλές ελλιπείς γραμματοσειρές παράγουν μια προειδοποίηση ανά αντικατάσταση. | Φιλτράρετε περαιτέρω ελέγχοντας `info.getDescription()` για συγκεκριμένα ονόματα γραμματοσειρών, ή συγκεντρώστε τις προειδοποιήσεις σε λίστα για μεταγενέστερη επεξεργασία. |
| **Substituted fonts affect layout** | Η εναλλακτική γραμματοσειρά μπορεί να έχει διαφορετικά μετρικά (μέγεθος, απόσταση). | Παρέχετε φάκελο προσαρμοσμένων γραμματοσειρών (δείτε το Βήμα 5) ή προσαρμόστε το στυλ του εγγράφου μετά τη φόρτωση. |
| **Running on a headless server** | Η προεπιλεγμένη εναλλακτική γραμματοσειρά μπορεί να βασίζεται σε συστημικές γραμματοσειρές που δεν είναι εγκατεστημένες στον διακομιστή. | Συμπεριλάβετε τις απαιτούμενες γραμματοσειρές με την εφαρμογή σας και κατευθύνετε το `FontSettings` σε αυτόν τον φάκελο. |

## Συχνές Ερωτήσεις

**Q: Λειτουργεί αυτό με PDF ή άλλες μορφές;**  
A: Ναι. Το callback προειδοποίησης είναι ανεξάρτητο από τη μορφή· ενεργοποιείται για οποιονδήποτε τύπο εγγράφου που φορτώνει το Aspose.Words (DOC, DOCX, RTF, HTML, κ.λπ.). Η μόνη διαφορά είναι το σύνολο των προειδοποιήσεων που μπορεί να εμφανιστούν.

**Q: Μπορώ να καταγράψω άλλους τύπους προειδοποιήσεων, όπως προειδοποιήσεις *ανάλυσης εικόνας*;**  
A: Απόλυτα. Μέσα στη μέθοδο `warning`, ελέγξτε το `info.getWarningType()` για άλλες τιμές enum όπως `WarningType.IMAGE_RESOLUTION`. Στη συνέχεια χειριστείτε τις ανάλογα.

**Q: Τι γίνεται αν χρειαστώ τη λίστα των αντικαταστημένων γραμματοσειρών μετά τη φόρτωση του εγγράφου;**  
A: Αποθηκεύστε κάθε `info.getDescription()` σε μια `List<String>` μέσα στο callback. Μετά τη φόρτωση, θα έχετε μια συλλογή που μπορείτε να καταγράψετε, να στείλετε σε υπηρεσία παρακολούθησης ή να χρησιμοποιήσετε για να ενεργοποιήσετε μια διαδικασία λήψης γραμματοσειρών.

## Συμπέρασμα

You now know **how to capture font substitution warnings** in Java using Aspose.Words, why each piece of the puzzle matters, and how to extend the solution for real‑world scenarios. By leveraging `LoadOptions`, an `Aspose.Words warning callback`, and optional `FontSettings`, you gain full visibility into missing fonts and can keep your document conversion pipelines reliable.

Ready for the next step? Try swapping out the `System.out.println` with a logger like SLF4J, or integrate the warning list into a UI that alerts users before they finalize a batch conversion. You could also explore the **Aspose.Words warning callback** for other warning types, such as *unsupported features* or *high‑resolution image* alerts.  

Happy coding, and may your PDFs never suffer from unexpected font swaps again! 

![Στιγμιότυπο οθόνης που δείχνει την έξοδο της κονσόλας με τις καταγεγραμμένες προειδοποιήσεις αντικατάστασης γραμματοσειράς](image-placeholder.png "καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειράς")

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Πώς να Ορίσετε LoadOptions στο Aspose.Words για Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Πώς να Δημιουργήσετε PDF Έγγραφα με Aspose.Words για Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}