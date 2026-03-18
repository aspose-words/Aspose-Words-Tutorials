---
category: general
date: 2026-03-17
description: Εξαγωγή Word σε markdown σε Java με το Aspose.Words. Μάθετε πώς να μετατρέπετε
  docx σε markdown, να ελέγχετε την ανάλυση των εικόνων στο markdown και να επαναφέρετε
  κατεστραμμένα αρχεία docx.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- markdown image resolution
- save word as markdown
- recover corrupted docx
language: el
og_description: Εξαγωγή Word σε markdown σε Java με το Aspose.Words. Μάθετε πώς να
  μετατρέπετε docx σε markdown, να ρυθμίζετε την ανάλυση των εικόνων markdown και
  να επαναφέρετε κατεστραμμένα αρχεία docx.
og_title: Εξαγωγή Word σε Markdown – Οδηγός Java με χρήση Aspose.Words
tags:
- Aspose.Words
- Java
- Document Conversion
title: Εξαγωγή Word σε Markdown – Οδηγός Java με χρήση Aspose.Words
url: /el/java/document-conversion-and-export/export-word-to-markdown-java-guide-using-aspose-words/
---

preserve markdown formatting exactly.

Let's craft Greek translation.

Will use appropriate Greek punctuation.

Proceed.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή Word σε Markdown – Οδηγός Java με Aspose.Words

Κάποτε χρειάστηκε να **εξάγετε Word σε markdown** αλλά αντιμετωπίσατε προβλήματα με εικόνες ή κατεστραμμένα αρχεία; Δεν είστε μόνοι. Σε πολλά έργα, οι προγραμματιστές πρέπει να μετατρέψουν ένα `.docx` σε καθαρό markdown για γεννήτριες στατικών ιστοσελίδων, pipelines τεκμηρίωσης ή ακόμη και βάσεις γνώσεων chatbot.

Τα καλά νέα; Με το Aspose.Words για Java μπορείτε να **μετατρέψετε docx σε markdown**, να ρυθμίσετε την **ανάλυση εικόνας στο markdown** και ακόμη να **ανακτήσετε κατεστραμμένα docx** αρχεία — όλα σε λίγες γραμμές κώδικα. Σε αυτό το tutorial θα περάσουμε από ένα πλήρες, εκτελέσιμο παράδειγμα, θα εξηγήσουμε γιατί κάθε ρύθμιση είναι σημαντική και θα σας δείξουμε πώς να έχετε αξιόπιστα αποτελέσματα χωρίς να θυσιάζετε την απόδοση.

## Τι θα χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) – το Aspose.Words λειτουργεί με Java 8+ αλλά οι νεότερες εκδόσεις προσφέρουν καλύτερη διαχείριση μνήμης.
- Το πιο πρόσφατο Aspose.Words for Java JAR (κατεβάστε το από την ιστοσελίδα της Aspose ή πάρτε το από το Maven Central).
- Ένα δείγμα `input.docx` – μπορεί να είναι ένα φρέσκο αρχείο ή ένα μερικώς κατεστραμμένο έγγραφο που θέλετε να σώσετε.
- Ένα IDE ή κειμενογράφο που προτιμάτε (IntelliJ IDEA, VS Code, Eclipse… όπως θέλετε).

Δεν απαιτούνται εξωτερικές βιβλιοθήκες εκτός από το Aspose.Words, κάτι που κρατά τη ρύθμιση ελαφριά και εύκολη στην αναπαραγωγή.

---

![Διάγραμμα εξαγωγής Word σε Markdown](export-word-to-markdown.png "Εξαγωγή Word σε Markdown – οπτική επισκόπηση")

*Image alt text: Διάγραμμα εξαγωγής Word σε Markdown που δείχνει τη ροή μετατροπής.*

## Βήμα 1 – Φόρτωση του εγγράφου Word με λειτουργία ανάκτησης

Όταν ένα `.docx` είναι κατεστραμμένο, το Aspose.Words μπορεί να προσπαθήσει να ξαναχτίσει τη εσωτερική δομή. Η ενεργοποίηση της λειτουργίας ανάκτησης είναι ο ασφαλέστερος τρόπος για να αποφύγετε ένα `FileNotFoundException` ή ένα μερικώς αναλυμένο έγγραφο.

```java
import com.aspose.words.*;

public class CombinedExportTutorial {
    public static void main(String[] args) throws Exception {
        // LoadOptions lets us turn on recovery mode.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryModeEnum.RECOVER);

        // The path can be absolute or relative to your project.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Γιατί είναι σημαντικό:**  
Αν το αρχείο προέλευσης είναι κατεστραμμένο, ο προεπιλεγμένος φορτωτής ρίχνει εξαίρεση και σταματά όλο το pipeline. Η λειτουργία ανάκτησης λέει στο Aspose.Words να “μάντεψε” τα ελλιπή τμήματα, δίνοντάς σας ένα χρήσιμο αντικείμενο `Document` που μπορείτε ακόμη να εξάγετε. Αυτό αποτελεί τη βάση της **αναίρεσης κατεστραμμένων docx**.

---

## Βήμα 2 – Διαμόρφωση επιλογών εξαγωγής Markdown (συμπεριλαμβανομένης της ανάλυσης εικόνας)

Τα αρχεία Markdown συχνά χρειάζονται εικόνες σε συγκεκριμένη ανάλυση ώστε να εμφανίζονται ωραία στο web. Το Aspose.Words σας επιτρέπει να ορίσετε το DPI και ακόμη να ελέγξετε πού θα αποθηκευτούν τα παραγόμενα PNG.

```java
        // Prepare MarkdownSaveOptions
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

        // Export Math equations as LaTeX – perfect for scientific docs.
        markdownOptions.setOfficeMathExportMode(MarkdownSaveOptions.OfficeMathExportModeEnum.LATEX);

        // Set image resolution – this directly influences markdown image resolution.
        markdownOptions.setImageResolution(300); // 300 DPI is a good balance

        // Save each image into a dedicated folder with a predictable name.
        markdownOptions.setResourceSavingCallback(callback -> {
            callback.setDirectory("YOUR_DIRECTORY/md-imgs");
            callback.setFileName("resource_" + callback.getIndex() + ".png");
        });
```

**Βασικά σημεία που πρέπει να θυμάστε:**

- `setImageResolution(300)` λέει στο Aspose.Words να rasterize τα διανυσματικά γραφικά στα 300 DPI. Αν χρειάζεστε πιο καθαρές εικόνες, αυξήστε τον αριθμό· για πιο γρήγορες κατασκευές, μειώστε το.
- Η callback δημιουργεί έναν φάκελο (`md-imgs`) και ονομάζει τα αρχεία `resource_0.png`, `resource_1.png`, … – αυτό κάνει το **save word as markdown** προβλέψιμο για εργαλεία downstream όπως MkDocs ή Jekyll.
- Η εξαγωγή Office Math ως LaTeX διατηρεί τις πολύπλοκες εξισώσεις αναγνώσιμες σε plain‑text markdown, κάτι που υποστηρίζεται από πολλές γεννήτριες στατικών ιστοσελίδων.

---

## Βήμα 3 – Αποθήκευση του εγγράφου ως αρχείο Markdown

Τώρα που οι επιλογές είναι ρυθμισμένες, η πραγματική μετατροπή είναι μια μόνο γραμμή.

```java
        // Perform the conversion
        document.save("YOUR_DIRECTORY/output.md", markdownOptions);
```

Μετά την εκτέλεση αυτής της γραμμής, θα βρείτε το `output.md` δίπλα σε έναν φάκελο γεμάτο PNG. Ανοίξτε το αρχείο markdown σε οποιονδήποτε επεξεργαστή και θα δείτε:

```markdown
# My Document Title

Here’s a paragraph with **bold** text.

![resource_0.png](md-imgs/resource_0.png)

$$
E = mc^2
$$
```

**Τι παίρνετε:** Ένα καθαρό αρχείο markdown που διατηρεί τίτλους, λίστες, πίνακες και εικόνες, συν μπλοκ LaTeX για τυχόν εξισώσεις. Αυτό ικανοποιεί την απαίτηση **convert docx to markdown** ενώ σας δίνει πλήρη έλεγχο στην ποιότητα των εικόνων.

---

## Βήμα 4 – Προετοιμασία επιλογών εξαγωγής PDF/UA (σήμανση σχημάτων)

Αν χρειάζεστε επίσης ένα προσβάσιμο PDF (PDF/UA), το Aspose.Words μπορεί να σημαδέψει τα αιωρούμενα σχήματα ως ενσωματωμένα στοιχεία, βελτιώνοντας την πλοήγηση με αναγνώστες οθόνης.

```java
        // PDF/UA options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(
                PdfSaveOptions.ExportFloatingShapesAsInlineTagEnum.INLINE);
```

**Γιατί να χρησιμοποιήσετε PDF/UA;**  
Το PDF/UA (Universal Accessibility) είναι το πρότυπο ISO για προσβάσιμα PDF. Ορίζοντας `ExportFloatingShapesAsInlineTag` εξασφαλίζετε ότι οι αιωρούμενες εικόνες και τα πλαίσια κειμένου αντιμετωπίζονται ως μέρος της σειράς ανάγνωσης, όχι ως ορφανά αντικείμενα. Αυτό είναι ιδιαίτερα χρήσιμο για βιομηχανίες με αυστηρές απαιτήσεις συμμόρφωσης.

---

## Βήμα 5 – Αποθήκευση του εγγράφου ως αρχείο PDF/UA

```java
        // Write the PDF/UA file
        document.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
    }
}
```

Όταν ανοίξετε το `output.pdf` με έναν ελεγκτή προσβασιμότητας, δεν θα δείτε παραβάσεις σχετικές με αιωρούμενα σχήματα. Το PDF περιέχει επίσης τις ίδιες υψηλής ανάλυσης εικόνες που ορίσατε για το markdown, επειδή η ίδια ρύθμιση `ImageResolution` εφαρμόζεται παγκοσμίως.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι η πλήρης, αυτόνομη κλάση Java που μπορείτε να αντιγράψετε‑επικολλήσετε στο έργο σας:

```java
import com.aspose.words.*;

public class CombinedExportTutorial {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document with recovery mode enabled.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryModeEnum.RECOVER);
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Prepare Markdown export options (including image resolution).
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(MarkdownSaveOptions.OfficeMathExportModeEnum.LATEX);
        markdownOptions.setImageResolution(300);
        markdownOptions.setResourceSavingCallback(callback -> {
            callback.setDirectory("YOUR_DIRECTORY/md-imgs");
            callback.setFileName("resource_" + callback.getIndex() + ".png");
        });

        // 3️⃣ Save as Markdown.
        document.save("YOUR_DIRECTORY/output.md", markdownOptions);

        // 4️⃣ Prepare PDF/UA export options with proper shape tagging.
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(
                PdfSaveOptions.ExportFloatingShapesAsInlineTagEnum.INLINE);

        // 5️⃣ Save as PDF/UA.
        document.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
    }
}
```

Τρέξτε αυτήν την κλάση και θα έχετε:

- `output.md` – έτοιμο για γεννήτριες στατικών ιστοσελίδων.
- `md-imgs/` – φάκελο PNG στα 300 DPI.
- `output.pdf` – ένα προσβάσιμο PDF/UA 1.0 έγγραφο.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν το DOCX περιέχει ενσωματωμένες γραμματοσειρές;**  
Το Aspose.Words ενσωματώνει αυτόματα τις γραμματοσειρές στο PDF όταν χρησιμοποιείτε `PdfSaveOptions`. Για το markdown, οι γραμματοσειρές είναι άσχετες επειδή το αποτέλεσμα είναι απλό κείμενο, αλλά οι εικόνες θα αντικατοπτρίζουν την αρχική απόδοση γραμματοσειράς.

**Μπορώ να μειώσω την ανάλυση εικόνας για πιο γρήγορες κατασκευές;**  
Απολύτως. Αλλάξτε σε `markdownOptions.setImageResolution(150);` για μια ισορροπία μεταξύ μεγέθους και ποιότητας. Θυμηθείτε ότι χαμηλότερο DPI μπορεί να κάνει τις λήψεις οθόνης να φαίνονται θολές σε οθόνες υψηλής πυκνότητας.

**Τι συμβαίνει όταν το αρχείο εισόδου είναι εντελώς μη αναγνώσιμο;**  
Ακόμη και σε λειτουργία “recover”, το Aspose.Words μπορεί να ρίξει εξαίρεση αν η δομή ZIP του DOCX είναι τόσο κατεστραμμένη που δεν μπορεί να επισκευαστεί. Σε αυτήν την περίπτωση, θα χρειαστεί να αποκτήσετε ένα καθαρότερο αντίγραφο ή να χρησιμοποιήσετε ένα εργαλείο τρίτου μέρους για επισκευή πριν τρέξετε αυτόν τον κώδικα.

**Πρέπει να καθαρίσω τον προσωρινό φάκελο εικόνων;**  
Αν εκτελείτε τη μετατροπή επανειλημμένα, ο φάκελος μπορεί να συσσωρεύσει παλιές εικόνες. Η προσθήκη μιας απλής διαδικασίας καθαρισμού πριν από το `document.save` (π.χ., `Files.walk(Paths.get("YOUR_DIRECTORY/md-imgs")).map(Path::toFile).forEach(File::delete);`) διατηρεί τα πράγματα τακτικά.

---

## Pro Tips & Παγίδες

- **Pro tip:** Κρατήστε τη διαδρομή `YOUR_DIRECTORY` ρυθμιζόμενη μέσω αρχείου properties. Κάνει το script επαναχρησιμοποιήσιμο σε διαφορετικά περιβάλλοντα.
- **Watch out for:** Η χρήση του ίδιου φακέλου εξόδου για markdown και PDF μπορεί να προκαλέσει συγκρούσεις ονομάτων αν προσθέσετε περισσότερες μορφές εξαγωγής αργότερα. Ξεχωριστοί φάκελοι κρατούν την οργάνωση.
- **Typical mistake:** Η παράλειψη του `OfficeMathExportMode` – οι εξισώσεις θα μετατραπούν σε εικόνες, αυξάνοντας το μέγεθος του markdown.
- **Performance hint:** Αν χρειάζεστε μόνο markdown (χωρίς PDF), σχολιάστε το μπλοκ PDF. Το Aspose.Words φορτώνει το έγγραφο μόνο μία φορά, οπότε δεν πληρώνετε επιπλέον κόστος για το βήμα PDF.

---

## Συμπέρασμα

Δείξαμε μια αξιόπιστη μέθοδο **εξαγωγής Word σε markdown** χρησιμοποιώντας το Aspose.Words for Java, ενώ ταυτόχρονα διαχειριζόμαστε **ανάλυση εικόνας στο markdown**, **αποθήκευση Word ως markdown**, και **ανάκτηση κατεστραμμένων docx** αρχείων. Η λύση με μία κλάση καλύπτει τόσο ένα φιλικό προς τους προγραμματιστές markdown output όσο και ένα PDF/UA συμβατό με προσβασιμότητα, προσφέροντας ευελιξία για pipelines τεκμηρίωσης, συστήματα διαχείρισης περιεχομένου ή νομικά αρχεία.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να αντικαταστήσετε το `MarkdownSaveOptions` με `HtmlSaveOptions` για δημιουργία HTML, ή εξερευνήστε το `DocxSaveOptions` για διαίρεση μεγάλων εγγράφων σε πολλαπλά αρχεία. Το ίδιο μοτίβο — φόρτωση με ανάκτηση, διαμόρφωση εξαγωγής, αποθήκευση — ισχύει σε όλες τις μορφές του Aspose.Words.

Αν αντιμετωπίσατε κάποιο πρόβλημα ή έχετε μια περίπτωση χρήσης που δεν καλύψαμε, αφήστε ένα σχόλιο παρακάτω. Καλή μετατροπή, και ας αποδίδει πάντα τέλεια το markdown σας!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}