---
category: general
date: 2026-08-04
description: Φορτώστε το markdown με υπογράμμιση σε Java και διατηρήστε τη μορφοποίηση
  markdown κατά τη φόρτωση του markdown στο έγγραφο. Ακολουθήστε αυτόν τον βήμα‑βήμα
  οδηγό.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: el
lastmod: 2026-08-04
og_description: Φορτώστε υπογράμμιση markdown στην Java και διατηρήστε τη μορφοποίηση
  markdown. Μάθετε πώς να φορτώνετε markdown σε έγγραφο με πλήρη υποστήριξη υπογράμμισης.
og_image_alt: Diagram showing load markdown underline process
og_title: Φόρτωση υπογράμμισης markdown σε Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Φόρτωση υπογράμμισης markdown σε Java – πλήρης οδηγός προγραμματισμού
url: /el/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Φόρτωση υπογράμμισης markdown σε Java – πλήρης οδηγός προγραμματισμού

Αν χρειάζεστε να **φορτώσετε υπογράμμιση markdown** κατά τη μετατροπή ενός αρχείου Markdown σε αντικείμενο `Document`, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα μάθετε επίσης πώς να **φορτώσετε markdown σε έγγραφο** χωρίς να χάσετε οποιοδήποτε στυλ υπογράμμισης, εξασφαλίζοντας ότι η αρχική μορφοποίηση του Markdown διατηρείται πλήρως.

Το σεμινάριο καλύπτει όλα όσα χρειάζεστε: τις απαιτούμενες βιβλιοθήκες, κάθε βήμα διαμόρφωσης και πώς να επαληθεύσετε ότι η μορφοποίηση υπογράμμισης επέζησε της εισαγωγής. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java.

## Προαπαιτούμενα

- Java 17 ή νεότερη εγκατεστημένη (το παράδειγμα χρησιμοποιεί το σύγχρονο σύστημα μονάδων)
- Την πιο πρόσφατη έκδοση του **GroupDocs.Viewer** (ή μια συμβατή βιβλιοθήκη που παρέχει `LoadOptions` και `Document`)
- Ένα αρχείο Markdown (`sample.md`) που περιέχει υπογραμμισμένο κείμενο, π.χ., `<u>underlined</u>` ή τη σύνταξη τύπου GitHub `__underlined__`
- Ένα IDE όπως το IntelliJ IDEA ή το VS Code, αν και οποιοσδήποτε επεξεργαστής κειμένου λειτουργεί

Αυτές οι απαιτήσεις εγγυώνται ότι ο κώδικας εκτελείται χωρίς πρόσθετη διαμόρφωση.

## Φόρτωση υπογράμμισης markdown – οδηγός βήμα‑βήμα

Η διαδικασία αποτελείται από τρεις βασικές ενέργειες: δημιουργία ενός αντικειμένου `LoadOptions`, ενεργοποίηση της ανίχνευσης υπογράμμισης και, τέλος, φόρτωση του αρχείου Markdown με αυτές τις επιλογές. Κάθε βήμα εξηγείται παρακάτω.

### Βήμα 1: Δημιουργία `LoadOptions` για το έγγραφο

`LoadOptions` σας επιτρέπει να προσαρμόσετε τον τρόπο που η βιβλιοθήκη αναλύει το αρχείο προέλευσης. Η δημιουργία μιας νέας παρουσίας σας παρέχει ένα καθαρό ξεκίνημα για τις επόμενες ρυθμίσεις.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

Το αντικείμενο `LoadOptions` είναι το σημείο εισόδου για όλες τις ρυθμίσεις που σχετίζονται με την εισαγωγή. Θα το χρησιμοποιήσετε στο επόμενο βήμα για να ενεργοποιήσετε την ανίχνευση υπογράμμισης.

### Βήμα 2: Ενεργοποίηση ανίχνευσης μορφοποίησης υπογράμμισης κατά τη φόρτωση

Από προεπιλογή, ο προβολέας μπορεί να αγνοεί τις ετικέτες υπογράμμισης επειδή είναι λιγότερο συνηθισμένες στο Markdown. Η ενεργοποίηση αυτής της σημαίας λέει στον αναλυτή να διατηρήσει τα τμήματα υπογράμμισης αμετάβλητα.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Η ρύθμιση `setImportUnderlineFormatting(true)` εξασφαλίζει ότι οποιαδήποτε ετικέτα HTML `<u>` ή η σύνταξη υπογράμμισης τύπου GitHub μετατρέπεται στο μοντέλο `Document` ως στυλ υπογράμμισης. Αυτή είναι η βασική ενέργεια που κάνει τη **φόρτωση υπογράμμισης markdown** να λειτουργεί όπως αναμένεται.

### Βήμα 3: Φόρτωση του αρχείου Markdown χρησιμοποιώντας τις διαμορφωμένες επιλογές

Τώρα μπορείτε να φορτώσετε το αρχείο. Περνάτε το αντικείμενο `loadOptions` στον κατασκευαστή `Document` ώστε ο αναλυτής να σέβεται τη σημαία υπογράμμισης.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Όταν ολοκληρωθεί ο κατασκευαστής, το `markdownDoc` περιέχει μια πλήρη αναπαράσταση στη μνήμη της πηγής Markdown, με πλήρη υπογράμμιση.

### Βήμα 4: Επαλήθευση ότι η μορφοποίηση υπογράμμισης διατηρείται

Μια γρήγορη έλεγχος λογικής σας βοηθά να επιβεβαιώσετε ότι η **διατήρηση μορφοποίησης markdown** λειτούργησε. Το παρακάτω απόσπασμα εκτυπώνει το κείμενο κάθε παραγράφου και σημειώνει τα υπογραμμισμένα τμήματα με μια tilde (`~`) για ορατότητα.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Αναμενόμενη έξοδος** (υποθέτοντας ότι το `sample.md` περιέχει `This is __underlined__ text`):

```
This is ~underlined~ text
```

Οι tilde υποδεικνύουν ότι το στυλ υπογράμμισης επέζησε της εισαγωγής, επιβεβαιώνοντας ότι η λειτουργία **φόρτωσης markdown σε έγγραφο** διατήρησε την αρχική μορφοποίηση.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Αιτία | Διόρθωση |
|---|---|---|
| Η υπογράμμιση εξαφανίζεται μετά τη φόρτωση | `setImportUnderlineFormatting` παραμένει στην προεπιλογή `false` | Βεβαιωθείτε ότι καλείτε `loadOptions.setImportUnderlineFormatting(true)` πριν δημιουργήσετε το `Document`. |
| Μόνο μέρος του κειμένου είναι υπογραμμισμένο | Μικτή σύνταξη Markdown (π.χ., HTML `<u>` αναμεμειγμένο με `__underline__`) | Η βιβλιοθήκη υποστηρίζει και τα δύο· βεβαιωθείτε ότι το αρχείο προέλευσης χρησιμοποιεί ένα συνεπές σύμβολο υπογράμμισης. |
| Το έγγραφο αποτυγχάνει να φορτωθεί | Λανθασμένη διαδρομή αρχείου ή ελλείψεις εξαρτήσεων βιβλιοθήκης | Χρησιμοποιήστε απόλυτη διαδρομή ή τοποθετήστε το `sample.md` σχετικό με τον τρέχοντα φάκελο εργασίας· συμπεριλάβετε τα JAR του viewer στο classpath. |

**Συμβουλή:** Εάν χρειάζεται επίσης να διατηρήσετε τα στυλ έντονου ή πλάγιου, ενεργοποιήστε τα με `setImportBoldFormatting(true)` και `setImportItalicFormatting(true)` αντίστοιχα. Ο συνδυασμός αυτών των σημαιών σας παρέχει μια πλήρως πιστή εισαγωγή των πιο κοινών στυλ Markdown.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα Java που συνδυάζει όλα. Αντιγράψτε τον κώδικα σε ένα αρχείο με όνομα `LoadMarkdownUnderlineDemo.java`, προσαρμόστε τη διαδρομή του αρχείου και εκτελέστε το με `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Η εκτέλεση του προγράμματος εκτυπώνει το περιεχόμενο του εγγράφου με δείκτες υπογράμμισης, αποδεικνύοντας ότι η δυνατότητα **φόρτωσης υπογράμμισης markdown** λειτουργεί και ότι μπορείτε να **διατηρήσετε τη μορφοποίηση markdown** καθ' όλη τη διαδικασία εισαγωγής.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **φορτώνετε υπογράμμιση markdown** σε Java, πώς να **φορτώνετε markdown σε έγγραφο** διατηρώντας το αρχικό στυλ, και πώς να επαληθεύετε ότι η μορφοποίηση υπογράμμισής είναι αμετάβλητη. Αυτή η προσέγγιση λειτουργεί με τις πιο πρόσφατες εκδόσεις του GroupDocs.Viewer και μπορεί να επεκταθεί για να υποστηρίξει πρόσθετες δυνατότητες του Markdown όπως έντονο, πλάγιο και πίνακες.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **διατήρηση μορφοποίησης markdown για πίνακες**, **απόδοση Markdown σε PDF**, ή **προσαρμοσμένο στυλ των εισαγόμενων στοιχείων Markdown**. Προσαρμόστε τις σημαίες `LoadOptions` ώστε να ταιριάζουν με τις ακριβείς απαιτήσεις μορφοποίησης της εφαρμογής σας, και θα έχετε λεπτομερή έλεγχο σε κάθε βήμα εισαγωγής. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω σεμινάρια καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Κατακτήστε τις Επιλογές Φόρτωσης Markdown με Aspose.Words για Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Κατακτήστε τις Επιλογές Φόρτωσης Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}