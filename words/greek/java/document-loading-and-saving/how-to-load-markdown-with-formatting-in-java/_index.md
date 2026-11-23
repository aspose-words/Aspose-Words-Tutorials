---
category: general
date: 2026-11-22
description: Μάθετε πώς να φορτώνετε markdown με μορφοποίηση σε Java. Αυτός ο οδηγός
  σας δείχνει πώς να διαβάζετε markdown με μορφοποίηση χρησιμοποιώντας το LoadOptions
  και το Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: el
lastmod: 2026-11-22
og_description: Πώς να φορτώσετε markdown με μορφοποίηση στη Java. Ακολουθήστε αυτόν
  τον πλήρη οδηγό για να διαβάσετε markdown με μορφοποίηση, να διατηρήσετε τα στυλ
  υπογράμμισης και να εργαστείτε με αντικείμενα Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Πώς να φορτώσετε markdown με μορφοποίηση στη Java – βήμα‑βήμα οδηγός
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Πώς να φορτώσετε markdown με μορφοποίηση σε Java
url: /el/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε markdown με μορφοποίηση σε Java

Εάν χρειάζεστε **πώς να φορτώσετε markdown** διατηρώντας τα οπτικά του στυλ, αυτό το tutorial σας παρέχει μια έτοιμη λύση εκτέλεσης. Θα δείτε ακριβώς πώς να **διαβάσετε markdown με μορφοποίηση** όπως υπογραμμισμένο κείμενο, ώστε το παραγόμενο έγγραφο να ταιριάζει με την αρχική πηγή.

Ο οδηγός καλύπτει κάθε βήμα, από τη διαμόρφωση του φορτωτή μέχρι την επαλήθευση ότι η μορφοποίηση επιβίωσε στην εισαγωγή. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη στάνταρ βιβλιοθήκη GroupDocs.Viewer (ή οποιοδήποτε συμβατό API που παρέχει `LoadOptions` και `Document`). Στο τέλος, θα μπορείτε να ενσωματώσετε τη φόρτωση markdown σε οποιοδήποτε backend Java, web service ή desktop εφαρμογή.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Πρόσβαση στο JAR του GroupDocs.Viewer (ή ισοδύναμο) που περιέχει `LoadOptions` και `Document`.
* Ένα δείγμα αρχείου markdown (`sample.md`) που περιλαμβάνει σήμανση υπογράμμισης (π.χ., `<u>υπογραμμισμένο κείμενο</u>` ή `_υπογραμμισμένο_` ανάλογα με τον parser).

## Βήμα 1: Προσθέστε την απαιτούμενη εξάρτηση

Αν χρησιμοποιείτε Maven, προσθέστε το παρακάτω στο `pom.xml`. Προσαρμόστε την έκδοση στην πιο πρόσφατη σταθερή έκδοση.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Οι χρήστες Gradle μπορούν να προσθέσουν:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Η προσθήκη της βιβλιοθήκης κάνει διαθέσιμες τις κλάσεις `LoadOptions` και `Document` κατά τη μεταγλώττιση.

## Βήμα 2: Διαμορφώστε το LoadOptions για εισαγωγή μορφοποίησης υπογράμμισης

Το αντικείμενο `LoadOptions` ενημερώνει τον parser ποιες δυνατότητες markdown πρέπει να διατηρηθούν. Η ενεργοποίηση της μορφοποίησης υπογράμμισης εξασφαλίζει ότι το οπτικό στυλ εμφανίζεται στο προκύπτον `Document`.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Γιατί είναι σημαντικό:**  
Χωρίς το `setImportUnderlineFormatting(true)`, ο parser αφαιρεί τις ετικέτες υπογράμμισης, αφήνοντας απλό κείμενο. Η ενεργοποίηση της σημαίας διατηρεί το στυλ αμετάβλητο, κάτι που είναι κρίσιμο όταν ο επόμενος καταναλωτής (π.χ., ένας δημιουργός PDF) βασίζεται σε οπτικές ενδείξεις.

## Βήμα 3: Φορτώστε το έγγραφο markdown χρησιμοποιώντας τις διαμορφωμένες επιλογές

Τώρα μπορείτε να διαβάσετε το αρχείο markdown. Ο κατασκευαστής `Document` δέχεται τη διαδρομή του αρχείου και το `LoadOptions` που μόλις προετοιμάσατε.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Γιατί είναι σημαντικό:**  
Η μεταβίβαση του `LoadOptions` στον κατασκευαστή `Document` εγγυάται ότι ο parser σέβεται τη σημαία υπογράμμισης καθ' όλη τη διάρκεια της εισαγωγής. Το προκύπτον αντικείμενο `Document` μπορεί να αποδοθεί, να μετατραπεί ή να εξεταστεί με πλήρη μορφοποίηση.

## Βήμα 4: Επαληθεύστε ότι η μορφοποίηση υπογράμμισης επιβίωσε

Ένας γρήγορος τρόπος να επιβεβαιώσετε ότι η υπογράμμιση υπάρχει είναι να αποδώσετε το έγγραφο σε HTML και να εκτυπώσετε το αποτέλεσμα. Το HTML θα περιέχει ετικέτες `<u>` εάν η εισαγωγή ήταν επιτυχής.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Η εκτέλεση του πλήρους προγράμματος θα πρέπει να εμφανίσει ένα απόσπασμα HTML που περιλαμβάνει `<u>υπογραμμισμένο κείμενο</u>`. Αν λείπει η ετικέτα, ελέγξτε ξανά ότι κλήθηκε το `setImportUnderlineFormatting(true)` πριν τη φόρτωση του αρχείου.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη κλάση Java που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Αναμενόμενο αποτέλεσμα (κομμένο για συντομία):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Αν εμφανιστεί η ετικέτα `<u>`, το markdown φορτώθηκε με τη μορφοποίηση ακεραιότητα.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση                              | Τι πρέπει να αλλάξετε                                          |
|----------------------------------------|---------------------------------------------------------------|
| **Διαφορετικές επεκτάσεις markdown**   | Χρησιμοποιήστε `loadOptions.setImportBoldFormatting(true)` για **bold**. |
| **Μεγάλα αρχεία (> 10 MB)**            | Διαβάστε το αρχείο με `FileInputStream` και περάστε το stream στο `Document`. |
| **Απαίτηση εξόδου PDF**                | Μετά τη φόρτωση, χρησιμοποιήστε `PdfViewOptions` με `Viewer` για δημιουργία PDF που διατηρεί τα στυλ υπογράμμισης. |
| **Εκτέλεση σε servlet container**      | Αποθηκεύστε το `Document` στο scope του request και αποδώστε σε HTML άμεσα. |

**Pro tip:** Δημιουργείτε πάντα ένα νέο αντικείμενο `LoadOptions` για κάθε λειτουργία φόρτωσης. Η επαναχρησιμοποίηση του ίδιου αντικειμένου μεταξύ νημάτων μπορεί να οδηγήσει σε ανεπιθύμητη διαρροή κατάστασης.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να φορτώσετε markdown με μορφοποίηση σε Java** και πώς να **διαβάσετε markdown με μορφοποίηση** χρησιμοποιώντας `LoadOptions`. Το πλήρες παράδειγμα δείχνει τη διαμόρφωση, τη φόρτωση και την επαλήθευση, ώστε να μπορείτε να ενσωματώσετε αυτό το μοτίβο σε οποιοδήποτε έργο Java που επεξεργάζεται αρχεία markdown.  

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **ανάγνωση markdown με εικόνες**, **μετατροπή markdown σε PDF**, ή **προσαρμογή άλλων εισαγωγών στυλ** (bold, italic, strikethrough). Κάθε μία από αυτές τις επεκτάσεις ακολουθεί το ίδιο μοτίβο: ρυθμίστε τις σημαίες του `LoadOptions`, φορτώστε το `Document` και αποδώστε στη μορφή που επιθυμείτε.

Καλό κώδικα!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to load markdown document in Java with custom import options](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [How to read and load a Markdown file in Java with Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [How to Load Markdown in Java – Complete Guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}