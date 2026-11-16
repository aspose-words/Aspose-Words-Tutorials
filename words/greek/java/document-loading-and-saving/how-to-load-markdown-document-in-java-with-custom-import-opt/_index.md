---
category: general
date: 2026-11-15
description: Μάθετε πώς να φορτώνετε έγγραφο markdown σε Java χρησιμοποιώντας το LoadOptions
  για να διατηρήσετε τη μορφοποίηση υπογράμμισης και να ελέγχετε τη συμπεριφορά εισαγωγής.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown document
- LoadOptions
- import underline formatting
- Document class
- custom import behavior
language: el
lastmod: 2026-11-15
og_description: Φορτώστε έγγραφο markdown σε Java με το LoadOptions. Διατηρήστε τη
  μορφοποίηση υπογράμμισης και ρυθμίστε λεπτομερώς τη συμπεριφορά εισαγωγής με λίγες
  μόνο γραμμές κώδικα.
og_image_alt: Screenshot of Java code loading a markdown document with custom LoadOptions
og_title: Φόρτωση εγγράφου markdown στην Java – οδηγός προσαρμοσμένων επιλογών εισαγωγής
schemas:
- author: GroupDocs
  dateModified: '2026-11-15'
  description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  headline: How to load markdown document in Java with custom import options
  type: TechArticle
- description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  name: How to load markdown document in Java with custom import options
  steps:
  - name: Why you need a `LoadOptions` instance
    text: '* **Predictable results** – Without explicit options the parser may drop
      or change formatting. * **Future‑proofing** – Adding new flags later (e.g.,
      handling tables or code blocks) is as simple as setting another property.'
  - name: When to enable this flag
    text: '* Your markdown contains emphasis that relies on underlining (common in
      technical documentation). * You are generating PDFs or HTML where visual fidelity
      matters.'
  - name: Verifying the load
    text: 'You can quickly confirm that the document loaded correctly:'
  - name: Pro tip
    text: 'Always log the effective `LoadOptions` before loading the file. This makes
      debugging easier when the document doesn’t look as expected:'
  type: HowTo
tags:
- Java
- Markdown
- File I/O
title: Πώς να φορτώσετε έγγραφο markdown σε Java με προσαρμοσμένες επιλογές εισαγωγής
url: /el/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε έγγραφο markdown σε Java με προσαρμοσμένες επιλογές εισαγωγής

Αν χρειάζεται να **φορτώσετε έγγραφο markdown** διατηρώντας συγκεκριμένη μορφοποίηση, αυτός ο οδηγός σας παρουσιάζει μια σύντομη, έτοιμη για παραγωγή λύση. Με τη διαμόρφωση ενός αντικειμένου `LoadOptions` μπορείτε να ελέγξετε πώς εισάγεται η υπογράμμιση και άλλα χαρακτηριστικά από το αρχείο προέλευσης.

Το tutorial καλύπτει όλα όσα χρειάζεστε: απαιτούμενες εισαγωγές, κώδικας βήμα‑βήμα, γιατί κάθε ρύθμιση είναι σημαντική και κοινά λάθη που πρέπει να αποφύγετε. Δεν απαιτείται εξωτερική τεκμηρίωση — απλώς αντιγράψτε, επικολλήστε και εκτελέστε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Τη βιβλιοθήκη που παρέχει `Document` και `LoadOptions` (π.χ. ένα SDK επεξεργασίας markdown όπως **GroupDocs.Viewer** ή **Aspose.Words**). Προσαρμόστε τις δηλώσεις εισαγωγής αν χρησιμοποιείτε διαφορετικό πακέτο.
* Ένα αρχείο markdown (`input.md`) τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε από τον κώδικά σας.

## Βήμα 1: Δημιουργήστε ένα αντικείμενο `LoadOptions` για προσαρμογή της συμπεριφοράς εισαγωγής

```java
// Import the necessary classes from the SDK
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

// Step 1: Instantiate LoadOptions for fine‑grained control
LoadOptions loadOptions = new LoadOptions();
```

Το `LoadOptions` είναι η κεντρική κλάση που λέει στην **κλάση Document** πώς να ερμηνεύσει το αρχείο προέλευσης. Δημιουργώντας μια παρουσία, αποκτάτε πρόσβαση σε δεκάδες σημαίες — μία από αυτές είναι η δυνατότητα εισαγωγής της μορφοποίησης υπογράμμισης.

### Γιατί χρειάζεστε μια παρουσία `LoadOptions`

* **Προβλέψιμα αποτελέσματα** — Χωρίς ρητές επιλογές, ο parser μπορεί να αφαιρέσει ή να αλλάξει τη μορφοποίηση.
* **Μελλοντική προσαρμοστικότητα** — Η προσθήκη νέων σηματών αργότερα (π.χ. διαχείριση πινάκων ή κώδικα) είναι τόσο απλή όσο το να ορίσετε μια ακόμη ιδιότητα.

## Βήμα 2: Ενεργοποιήστε την εισαγωγή μορφοποίησης υπογράμμισης

```java
// Step 2: Turn on underline import
loadOptions.setImportUnderlineFormatting(true);
```

Η κλήση `setImportUnderlineFormatting(true)` ενεργοποιεί τη σημαία **import underline formatting**. Όταν αυτή η σημαία είναι `true`, οποιοδήποτε κείμενο που ήταν υπογραμμισμένο στο αρχικό markdown θα διατηρήσει αυτό το στυλ στο παραγόμενο αντικείμενο `Document`.

### Πότε να ενεργοποιήσετε αυτή τη σημαία

* Το markdown σας περιέχει έμφαση που βασίζεται στην υπογράμμιση (συνηθισμένο σε τεχνική τεκμηρίωση).
* Δημιουργείτε PDF ή HTML όπου η οπτική πιστότητα είναι σημαντική.

Αν παραλείψετε αυτό το βήμα, το υπογραμμισμένο κείμενο θα εμφανιστεί ως απλό κείμενο, κάτι που μπορεί να μπερδέψει τους αναγνώστες που βασίζονται σε οπτικά σήματα.

## Βήμα 3: Φορτώστε το αρχείο markdown χρησιμοποιώντας το διαμορφωμένο `LoadOptions`

```java
// Step 3: Load the markdown document with the custom options
Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
```

Π Passing the `loadOptions` instance to the `Document` constructor instructs the **Document class** to apply the custom import rules while reading `input.md`.

### Επαλήθευση της φόρτωσης

Μπορείτε γρήγορα να επιβεβαιώσετε ότι το έγγραφο φορτώθηκε σωστά:

```java
System.out.println("Document loaded. Page count: " + markdownDoc.getPageCount());
```

Αν το αρχείο λείπει ή η διαδρομή είναι λανθασμένη, ο κατασκευαστής ρίχνει μια περιγραφική εξαίρεση, επιτρέποντάς σας να χειριστείτε το σφάλμα με χάρη.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε όπως είναι (αντικαταστήστε το όνομα πακέτου με αυτό που ταιριάζει στο SDK σας).

```java
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

public class LoadMarkdownExample {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions to customize import behavior
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable importing of underline formatting from the source
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the markdown document using the configured options
        try {
            Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
            System.out.println("Markdown document loaded successfully.");
            System.out.println("Page count: " + markdownDoc.getPageCount());
        } catch (Exception e) {
            System.err.println("Failed to load markdown document: " + e.getMessage());
        }
    }
}
```

**Αναμενόμενη έξοδος (υπόθεση ότι το αρχείο υπάρχει και περιέχει τουλάχιστον μία σελίδα περιεχομένου):**

```
Markdown document loaded successfully.
Page count: 1
```

Αν το αρχείο δεν βρεθεί, θα δείτε ένα μήνυμα σφάλματος όπως:

```
Failed to load markdown document: File not found: YOUR_DIRECTORY/input.md
```

## Περιπτώσεις άκρων και συμβουλές βέλτιστης πρακτικής

| Κατάσταση | Σε τι πρέπει να προσέξετε | Προτεινόμενη προσέγγιση |
|-----------|---------------------------|--------------------------|
| **Διαδρομή αρχείου με κενά** | `new Document("C:/My Docs/input.md", ...)` μπορεί να αποτύχει σε ορισμένα λειτουργικά συστήματα. | Χρησιμοποιήστε `java.nio.file.Paths` για ασφαλή κατασκευή της διαδρομής: `Paths.get("C:", "My Docs", "input.md").toString()` |
| **Μεγάλα αρχεία markdown** | Η φόρτωση πολύ μεγάλων αρχείων μπορεί να καταναλώσει μνήμη. | Ενεργοποιήστε επιλογές streaming αν το SDK τις παρέχει, ή αυξήστε το heap της JVM (`-Xmx`). |
| **Απουσία υποστήριξης υπογράμμισης** | Κάποιες εκδόσεις SDK αγνοούν τη σημαία υπογράμμισης. | Βεβαιωθείτε ότι χρησιμοποιείτε έκδοση που υλοποιεί `setImportUnderlineFormatting`. Ελέγξτε τις σημειώσεις έκδοσης. |
| **Απαιτούνται πολλαπλές σημαίες εισαγωγής** | Μπορεί να χρειαστεί επίσης η διατήρηση πινάκων, κώδικα κ.λπ. | Συνδυάστε επιπλέον setters στο `loadOptions`, π.χ. `loadOptions.setImportTables(true);` |

### Pro tip

Καταγράψτε πάντα τις ενεργές `LoadOptions` πριν φορτώσετε το αρχείο. Αυτό διευκολύνει τον εντοπισμό σφαλμάτων όταν το έγγραφο δεν εμφανίζεται όπως αναμένεται:

```java
System.out.println("Import underline formatting: " + loadOptions.isImportUnderlineFormatting());
```

## Οπτική επισκόπηση

![Screenshot of Java code loading a markdown document with custom LoadOptions](load-markdown.png)

*Alt text: Στιγμιότυπο κώδικα Java που φορτώνει ένα έγγραφο markdown με προσαρμοσμένες LoadOptions.*

## Συμπέρασμα

Τώρα ξέρετε πώς να **φορτώνετε έγγραφο markdown** σε Java διατηρώντας τη μορφοποίηση υπογράμμισης και εφαρμόζοντας **προσαρμοσμένη συμπεριφορά εισαγωγής** μέσω του `LoadOptions`. Το μοτίβο τριών βημάτων — δημιουργία `LoadOptions`, ενεργοποίηση των επιθυμητών σηματών, και πέρασμα των επιλογών στον κατασκευαστή `Document` — ισχύει και για πολλές άλλες ρυθμίσεις εισαγωγής.

Από εδώ μπορείτε να εξερευνήσετε πρόσθετες σημαίες όπως `setImportTables`, να συνδυάσετε το φορτωμένο `Document` με έναν μετατροπέα PDF, ή να ενσωματώσετε το έγγραφο σε έναν web viewer. Η ίδια προσέγγιση λειτουργεί για άλλους τύπους αρχείων που υποστηρίζει το SDK, καθιστώντας αυτό το μοτίβο ένα ευέλικτο εργαλείο στο Java toolkit σας.

--- 

*Επόμενα βήματα:*  

* Μάθετε πώς να **εξάγετε το φορτωμένο Document σε PDF** ή HTML.  
* Εξερευνήστε τη πλήρη λίστα ιδιοτήτων `LoadOptions` για λεπτομερή ρύθμιση της ανάλυσης markdown.  
* Ενσωματώστε διαχείριση σφαλμάτων και logging για εφαρμογές παραγωγικού επιπέδου.

## What Should You Learn Next?

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Load markdown underline in Java – complete programming guide](/words/english/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/)
- [How to Load Markdown in Java – Complete Guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)
- [How to read and load a Markdown file in Java with Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}