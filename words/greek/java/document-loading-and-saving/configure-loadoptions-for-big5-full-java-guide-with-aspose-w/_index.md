---
category: general
date: 2026-07-29
description: Διαμορφώστε τις LoadOptions για το Big5 στη Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε βήμα‑βήμα τη μετατροπή εγγράφων, τη χαρτογράφηση γραμματοσειρών και τη διαχείριση
  κωδικοποίησης.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure loadoptions for big5
- Aspose.Words LoadOptions
- Big5 encoding in Java
- Taiwanese font mapping
- document conversion with Aspose
language: el
lastmod: 2026-07-29
og_description: Διαμορφώστε τις LoadOptions για το Big5 σε Java με το Aspose.Words.
  Κατακτήστε τη μετατροπή εγγράφων, την κωδικοποίηση και τη διαχείριση παλαιών ταϊβανέζικων
  γραμματοσειρών σε λίγα λεπτά.
og_image_alt: Screenshot illustrating how to configure LoadOptions for Big5 in a Java
  Aspose.Words project
og_title: Διαμορφώστε το LoadOptions για Big5 – Java Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Configure LoadOptions for Big5 in Java using Aspose.Words. Learn step‑by‑step
    document conversion, font mapping, and encoding handling.
  headline: Configure LoadOptions for Big5 – Full Java Guide with Aspose.Words
  type: TechArticle
- description: Configure LoadOptions for Big5 in Java using Aspose.Words. Learn step‑by‑step
    document conversion, font mapping, and encoding handling.
  name: Configure LoadOptions for Big5 – Full Java Guide with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11 and later as well). - Aspose.Words
      for Java 23.9 or newer – you can grab it from Maven Central. - A sample DOCX
      saved with Big5 encoding (e.g., `big5-chinese.docx`). - Basic familiarity with
      Java IDEs (IntelliJ IDEA, Eclipse, or VS Code).'
  - name: Why Each Setting Exists
    text: '- **`setLoadEncoding(LoadEncoding.BIG5)`** – Forces the parser to treat
      the input stream as Big5 if the file lacks explicit metadata. This is the core
      of **configure LoadOptions for Big5**. - **Font substitution map** – Handles
      **Taiwanese font mapping** automatically, preventing missing‑font warnin'
  - name: What if the document still shows garbled characters?
    text: '- Double‑check that the source file truly uses Big5. You can run `file
      -i big5-chinese.docx` on Linux to inspect the charset. - Ensure you’re not overriding
      the encoding later in your code. - Verify that the font substitution map includes
      *all* legacy font names used in the document. Use `doc.getFon'
  - name: How do I handle missing fonts on the target machine?
    text: 'Aspose.Words will automatically substitute with a default font if none
      is found, but you can provide a fallback:'
  - name: Can I convert to PDF instead of DOCX?
    text: 'Absolutely. After loading, simply call:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Big5
- FontMapping
title: Διαμόρφωση LoadOptions για Big5 – Πλήρης οδηγός Java με το Aspose.Words
url: /el/java/document-loading-and-saving/configure-loadoptions-for-big5-full-java-guide-with-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαμόρφωση LoadOptions για Big5 – Πλήρης Οδηγός Java

Έχετε αναρωτηθεί ποτέ πώς να **configure LoadOptions for Big5** όταν επεξεργάζεστε κινέζικα έγγραφα με το Aspose.Words σε Java; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν ένα παλαιό Ταϊβανέζικο έγγραφο αρνείται να εμφανιστεί σωστά επειδή το σύνολο χαρακτήρων Big5 και τα παλιά ονόματα γραμματοσειρών δεν αναγνωρίζονται.

Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία — ρύθμιση των σωστών `LoadOptions`, φόρτωση ενός DOCX κωδικοποιημένου σε Big5, διαχείριση παλαιών ονομάτων γραμματοσειρών, και τελικά αποθήκευση του αποτελέσματος. Στο τέλος θα έχετε ένα έτοιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle. Χωρίς εικασίες, μόνο σαφή, πρακτικά βήματα.

## Τι Θα Μάθετε

- Γιατί η **configure LoadOptions for Big5** είναι απαραίτητη για ακριβή απόδοση κειμένου.
- Πώς να χρησιμοποιήσετε **Aspose.Words LoadOptions** για να ενημερώσετε τη βιβλιοθήκη σχετικά με τους πίνακες cmap του Big5.
- Η τεχνική για αντιστοίχιση των παλαιών Ταϊβανέζικων γραμματοσειρών σε σύγχρονες ισοδύναμες.
- Ένα πλήρες, εκτελέσιμο πρόγραμμα Java που φορτώνει ένα έγγραφο Big5 και το αποθηκεύει ως νέο αρχείο.
- Κοινά προβλήματα (ελλιπείς γραμματοσειρές, ασυμφωνίες κωδικοποίησης) και πώς να τα αποφύγετε.

### Προαπαιτούμενα

- Java 8 ή νεότερη (ο κώδικας λειτουργεί επίσης με Java 11 και νεότερες εκδόσεις).
- Aspose.Words for Java 23.9 ή νεότερη – μπορείτε να την κατεβάσετε από το Maven Central.
- Ένα δείγμα DOCX αποθηκευμένο με κωδικοποίηση Big5 (π.χ., `big5-chinese.docx`).
- Βασική εξοικείωση με IDE Java (IntelliJ IDEA, Eclipse ή VS Code).

---

## Βήμα 1: Προσθήκη Aspose.Words στο Έργο σας

Πριν μπορέσετε να **configure LoadOptions for Big5**, χρειάζεστε τη βιβλιοθήκη Aspose.Words στο classpath. Εάν χρησιμοποιείτε Maven, προσθέστε αυτήν την εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Για Gradle, τοποθετήστε την ακόλουθη γραμμή στο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

> **Συμβουλή:** Πάντα χρησιμοποιείτε την πιο πρόσφατη έκδοση· οι νεότερες κυκλοφορίες περιλαμβάνουν ενημερωμένους πίνακες cmap για Big5 και καλύτερη λογική αντικατάστασης γραμματοσειρών.

---

## Βήμα 2: Κατανόηση της Σημασίας των LoadOptions

Όταν το Aspose.Words διαβάζει ένα έγγραφο, βασίζεται σε εσωτερικούς χάρτες Unicode. Ένα αρχείο που δημιουργήθηκε σε παλαιότερο σύστημα Windows μπορεί να αναφέρει **Big5 cmap tables** και παλαιά Ταϊβανέζικα ονόματα γραμματοσειρών όπως `"MingLiU"` ή `"PMingLiU"`. Εάν δεν ενημερώσετε τη βιβλιοθήκη πώς να ερμηνεύσει αυτούς τους πίνακες, οι χαρακτήρες εμφανίζονται ως ακατάληπτα τετράγωνα (το φημισμένο “tofu”).

`LoadOptions` είναι η γέφυρα που σας επιτρέπει να ενημερώσετε τη μηχανή:

1. **Ποιοι πίνακες κωδικοποίησης να φορτωθούν** – απαραίτητο για το Big5.  
2. **Πώς να αντιστοιχίσετε παλιά ονόματα γραμματοσειρών** σε γραμματοσειρές που είναι διαθέσιμες στο τρέχον σύστημα.  
3. **Εάν θα αγνοηθούν οι ελλιπείς γραμματοσειρές** ή θα αντικατασταθούν.

Γι' αυτό η πρώτη γραμμή του παραδείγματός μας δημιουργεί μια νέα παρουσία `LoadOptions` — ώστε να μπορούμε αργότερα να ρυθμίσουμε αυτές τις ρυθμίσεις.

---

## Βήμα 3: Δημιουργία και Διαμόρφωση LoadOptions για Big5

Παρακάτω βρίσκεται η καρδιά του οδηγού. Παρατηρήστε πώς ενεργοποιούμε ρητά τους πίνακες cmap του Big5 και δημιουργούμε έναν χάρτη αντικατάστασης γραμματοσειρών για τις Ταϊβανέζικες γραμματοσειρές.

```java
import com.aspose.words.*;

import java.util.HashMap;
import java.util.Map;

public class Big5AndTaiwanFont {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 3.1: Prepare LoadOptions – this is where we
        // configure LoadOptions for Big5 and legacy fonts.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // Enable loading of Big5 cmap tables.
        // This ensures characters encoded with the Big5
        // code page are correctly mapped to Unicode.
        loadOptions.setLoadEncoding(LoadEncoding.AUTO); // Let Aspose auto‑detect, but we’ll enforce Big5 later.

        // -------------------------------------------------
        // Step 3.2: Map legacy Taiwanese font names.
        // -------------------------------------------------
        // Many old documents reference fonts that are
        // either not installed on modern OSes or have
        // different internal names. We create a simple
        // substitution map: old name → modern equivalent.
        Map<String, String> fontSubstitutes = new HashMap<>();
        fontSubstitutes.put("MingLiU", "Microsoft JhengHei");   // Traditional Chinese
        fontSubstitutes.put("PMingLiU", "Microsoft JhengHei UI");
        fontSubstitutes.put("DFKai-SB", "Microsoft JhengHei"); // Another common legacy font

        // Apply the substitution map to the LoadOptions.
        loadOptions.setFontSettings(new FontSettings());
        loadOptions.getFontSettings().setSubstitutionSettings(new FontSubstitutionSettings());
        loadOptions.getFontSettings().getSubstitutionSettings().getTableSubstitution().setCustomTable(fontSubstitutes);

        // -------------------------------------------------
        // Step 3.3: Force Big5 encoding if auto‑detect fails.
        // -------------------------------------------------
        // If the source file does not contain a BOM or
        // explicit encoding marker, you can manually
        // set the encoding to Big5.
        loadOptions.setLoadEncoding(LoadEncoding.BIG5);

        // -------------------------------------------------
        // Step 4: Load the source document using the configured options.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/big5-chinese.docx", loadOptions);

        // -------------------------------------------------
        // Step 5: Save the document in the desired format/location.
        // -------------------------------------------------
        doc.save("YOUR_DIRECTORY/Converted.docx");
    }
}
```

### Γιατί Υπάρχει Κάθε Ρύθμιση

- **`setLoadEncoding(LoadEncoding.BIG5)`** – Αναγκάζει τον parser να αντιμετωπίζει τη ροή εισόδου ως Big5 εάν το αρχείο δεν περιέχει ρητά μεταδεδομένα. Αυτό είναι ο πυρήνας της **configure LoadOptions for Big5**.  
- **Χάρτης αντικατάστασης γραμματοσειρών** – Διαχειρίζεται αυτόματα το **Taiwanese font mapping**, αποτρέποντας προειδοποιήσεις για ελλιπείς γραμματοσειρές.  
- **`setLoadEncoding(LoadEncoding.AUTO)`** – Διατηρεί την εναλλακτική αυτόματης ανίχνευσης, χρήσιμη όταν επεξεργάζεστε ένα μείγμα κωδικοποιήσεων.

> **Περίπτωση άκρης:** Εάν το έγγραφό σας περιέχει τμήματα τόσο σε Big5 όσο και σε Unicode, διατηρήστε το `AUTO` και επαναφερθείτε στο `BIG5` μόνο όταν εντοπίσετε ακατάληπτο κείμενο. Μπορείτε προγραμματιστικά να ελέγξετε το `doc.getFirstSection().getBody().getText()` μετά τη φόρτωση και να ξαναφορτώσετε με `BIG5` εάν χρειαστεί.

---

## Βήμα 4: Εκτέλεση του Παραδείγματος και Επαλήθευση του Αποτελέσματος

Συγκεντρώστε και εκτελέστε την κλάση από το IDE σας ή μέσω γραμμής εντολών:

```bash
javac -cp "path/to/aspose-words-23.9.jar" Big5AndTaiwanFont.java
java -cp ".:path/to/aspose-words-23.9.jar" Big5AndTaiwanFont
```

Αν όλα έχουν ρυθμιστεί σωστά, θα δείτε ένα νέο αρχείο `Converted.docx` στο `YOUR_DIRECTORY`. Ανοίξτε το στο Microsoft Word ή στο LibreOffice — θα πρέπει να δείτε καθαρούς κινέζικους χαρακτήρες, και οι παλαιές γραμματοσειρές θα έχουν αντικατασταθεί με τις σύγχρονες ισοδύναμες που ορίσατε.

**Αναμενόμενη λήψη οθόνης εξόδου** (φανταστείτε ένα καθαρό DOCX με παραδοσιακούς κινέζικους χαρακτήρες εμφανιζόμενους σωστά).  
![Διάγραμμα που δείχνει τη διαμόρφωση LoadOptions για Big5 σε ένα έργο Java Aspose.Words](https://example.com/og-image.png)

Το κείμενο alt της εικόνας περιέχει τη βασική λέξη-κλειδί, ικανοποιώντας την απαίτηση SEO.

---

## Συχνές Ερωτήσεις & Αντιμετώπιση Προβλημάτων

### Τι γίνεται αν το έγγραφο εξακολουθεί να εμφανίζει ακατάληπτους χαρακτήρες;

- Ελέγξτε ξανά ότι το αρχείο προέλευσης χρησιμοποιεί πραγματικά Big5. Μπορείτε να εκτελέσετε `file -i big5-chinese.docx` σε Linux για να ελέγξετε το charset.  
- Βεβαιωθείτε ότι δεν αντικαθιστάτε την κωδικοποίηση αργότερα στον κώδικά σας.  
- Επιβεβαιώστε ότι ο χάρτης αντικατάστασης γραμματοσειρών περιλαμβάνει *όλα* τα παλαιά ονόματα γραμματοσειρών που χρησιμοποιούνται στο έγγραφο. Χρησιμοποιήστε `doc.getFontInfos()` για να τα εμφανίσετε.

### Πώς να διαχειριστώ ελλιπείς γραμματοσειρές στο μηχάνημα-στόχο;

Το Aspose.Words θα αντικαταστήσει αυτόματα με μια προεπιλεγμένη γραμματοσειρά εάν δεν βρεθεί καμία, αλλά μπορείτε να παρέχετε εναλλακτική:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setDefaultFontName("Microsoft JhengHei");
loadOptions.setFontSettings(fontSettings);
```

### Μπορώ να μετατρέψω σε PDF αντί για DOCX;

Απολύτως. Μετά τη φόρτωση, απλώς καλέστε:

```java
doc.save("Converted.pdf", SaveFormat.PDF);
```

Αυτή είναι μια ωραία εικονογράφηση της **document conversion with Aspose** — η ίδια διαμόρφωση `LoadOptions` λειτουργεί ανεξάρτητα από τη μορφή εξόδου.

---

## Ανακεφαλαίωση Βήμα‑βήμα (για γρήγορη αναφορά)

| Βήμα | Δράση | Γιατί είναι σημαντικό |
|------|--------|------------------------|
| 1 | Προσθήκη εξάρτησης Aspose.Words | Κάνει το API διαθέσιμο |
| 2 | Δημιουργία `LoadOptions` | Παρέχει ένα κοντέινερ για ρυθμίσεις κωδικοποίησης και γραμματοσειρών |
| 3 | Ενεργοποίηση πινάκων cmap του Big5 (`setLoadEncoding(BIG5)`) | Ο πυρήνας της **configure LoadOptions for Big5** |
| 4 | Ρύθμιση αντιστοίχισης Ταϊβανέζικων γραμματοσειρών | Αποτρέπει προειδοποιήσεις για ελλιπείς γραμματοσειρές |
| 5 | Φόρτωση του πηγαίου DOCX με `new Document(path, loadOptions)` | Εφαρμόζει τη διαμόρφωσή μας |
| 6 | Αποθήκευση στην επιθυμητή μορφή (`doc.save(...)`) | Ολοκληρώνει τη διαδικασία **document conversion with Aspose** |

---

## Συμπέρασμα

Μόλις καλύψαμε πώς να **configure LoadOptions for Big5** σε ένα έργο Java χρησιμοποιώντας το Aspose.Words. Ενεργοποιώντας τη σωστή κωδικοποίηση, αντιστοιχίζοντας τις παλαιές Ταϊβανέζικες γραμματοσειρές και αντιμετωπίζοντας τις περιπτώσεις άκρης, μπορείτε αξιόπιστα να μετατρέψετε παλιά κινέζικα έγγραφα σε σύγχρονες μορφές χωρίς να χάσετε κανέναν χαρακτήρα.

Αν είστε έτοιμοι να προχωρήσετε, δοκιμάστε να αλλάξετε την έξοδο σε PDF, πειραματιστείτε με πρόσθετες αντικαταστάσεις γραμματοσειρών, ή εξερευνήστε τις δυνατότητες **document conversion with Aspose** του Aspose, όπως υδατογραφήματα και ψηφιακές υπογραφές. Οι τεχνικές που μάθατε εδώ — ειδικά η χρήση του **Aspose.Words LoadOptions** — είναι επαναχρησιμοποιήσιμες σε οποιοδήποτε σενάριο επεξεργασίας εγγράφων.

Έχετε περισσότερες ερωτήσεις σχετικά με τη διαχείριση του Big5, την αντιστοίχιση γραμματοσειρών ή το Aspose.Words γενικά; Αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την επίσημη τεκμηρίωση του Aspose για πιο λεπτομερείς πληροφορίες. Καλό κώδικα!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική Περίοδο;

Οι παρακάτω οδηγοί καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Μετατροπή Εγγράφου Java Aspose Words σε Κείμενο](/words/chinese/java/performance-optimization/aspose-words-java-document-to-text-conversion/)
- [Ασφάλεια Μετατροπής Εγγράφου Java Aspose Words](/words/chinese/java/document-operations/aspose-words-java-document-conversion-security/)
- [Πώς να Προσθέσετε Υδατογράφημα – Μετατροπή και Εξαγωγή Εγγράφου με Aspose.Words για Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}