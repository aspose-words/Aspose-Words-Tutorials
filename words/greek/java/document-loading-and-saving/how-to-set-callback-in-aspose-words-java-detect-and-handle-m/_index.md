---
category: general
date: 2026-06-20
description: πώς να ορίσετε callback στο Aspose.Words Java για να εντοπίζετε ελλείπουσες
  γραμματοσειρές και να προσαρμόζετε τη φόρτωση του εγγράφου. Μάθετε βήμα‑βήμα τη
  διαχείριση των προειδοποιήσεων υποκατάστασης γραμματοσειρών.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: el
og_description: πώς να ορίσετε callback στο Aspose.Words Java για τον εντοπισμό ελλιπών
  γραμματοσειρών, τη διαχείριση αντικαταστάσεων και την προσαρμογή της φόρτωσης εγγράφων.
  Πλήρης οδηγός με κώδικα.
og_title: Πώς να ορίσετε callback – Ανίχνευση ελλειπόντων γραμματοσειρών στο Aspose.Words
  Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: πώς να ορίσετε την επιστροφή κλήσης στο Aspose.Words Java – Εντοπισμός και
  Διαχείριση Ελλειπόντων Γραμματοσειρών
url: /el/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να ορίσετε callback στο Aspose.Words Java – Ανίχνευση και Διαχείριση Ελλειπουσών Γραμματοσειρών

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε callback** στο Aspose.Words Java ώστε να εντοπίζετε ελλειπούσες γραμματοσειρές πριν χαλάσουν το PDF ή το DOCX σας; Δεν είστε ο μόνος. Οι προειδοποιήσεις για ελλειπούσες γραμματοσειρές μπορούν σιωπηρά να διαστέλουν τη διάταξη, και χωρίς ένα κατάλληλο warning callback μπορεί να μην το παρατηρήσετε μέχρι το τελικό έγγραφο να φαίνεται λανθασμένο.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που **ανιχνεύει ελλειπούσες γραμματοσειρές**, **διαχειρίζεται ελλειπούσες γραμματοσειρές** με χάρη, και σας δείχνει πώς να **προσαρμόσετε τη φόρτωση εγγράφου** με ένα warning callback. Στο τέλος θα έχετε μια αυτόνομη κλάση Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε project—χωρίς ανάγκη επιπλέον αναζήτησης τεκμηρίωσης.

## Τι Θα Χρειαστείτε

- Java 8 ή νεότερη (ο κώδικας λειτουργεί επίσης με Java 11+)  
- Aspose.Words for Java library (έκδοση 23.9 ή νεότερη)  
- Ένα αρχείο DOCX που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., μια προσαρμοσμένη εταιρική γραμματοσειρά)  

Αν δεν έχετε προσθέσει το Aspose.Words στο Maven project σας ακόμη, απλώς προσθέστε:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Αυτό είναι όλο—χωρίς επιπλέον plugins, χωρίς native dependencies.

---

## Βήμα 1: Κατανόηση του Μηχανισμού WarningCallback

Το **warning callback** είναι ο τρόπος του Aspose.Words να σας προειδοποιεί όταν συμβαίνει κάτι μη αναμενόμενο κατά τη φόρτωση ή αποθήκευση ενός εγγράφου. Υλοποιώντας το `IWarningCallback` αποκτάτε πλήρη έλεγχο πάνω σε αυτό που καταγράφεται, αγνοείται ή ακόμη και μετατρέπεται σε εξαίρεση.

> **Γιατί είναι σημαντικό:**  
> Όταν λείπει μια γραμματοσειρά, το Aspose αντικαθιστά τη γραμματοσειρά με μια fallback. Το οπτικό αποτέλεσμα μπορεί να είναι δραστικά διαφορετικό, ειδικά για PDFs με έντονη branding. Συλλαμβάνοντας το `WarningType.FONT_SUBSTITUTION`, μπορείτε να καταγράψετε το ακριβές όνομα της γραμματοσειράς, να αποφασίσετε αν θα διακόψετε τη διαδικασία, ή να αντικαταστήσετε προγραμματιστικά τη γραμματοσειρά με τη δική σας.

---

## Βήμα 2: Δημιουργία ενός LoadOptions Instance

`LoadOptions` είναι το σημείο εισόδου για την προσαρμογή της φόρτωσης εγγράφου. Θα συνδέσετε το callback σε αυτό το αντικείμενο πριν φορτώσετε το αρχείο.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Σε αυτό το σημείο το `loadOptions` είναι απλώς ένας απλός container—δεν συμβαίνει τίποτα ακόμη. Η πραγματική μαγεία ξεκινά όταν ενσωματώνουμε το callback.

---

## Βήμα 3: Υλοποίηση και Σύνδεση του Callback

Παρακάτω υπάρχει μια σύντομη ανώνυμη κλάση που υλοποιεί το `IWarningCallback`. Εκτυπώνει μια φιλική γραμμή στην κονσόλα όποτε συμβαίνει αντικατάσταση γραμματοσειράς.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tip:** Αν θέλετε να **διαχειριστείτε ελλειπούσες γραμματοσειρές** παρέχοντας μια αντικατάσταση, μπορείτε επίσης να ορίσετε `FontSettings` στο `LoadOptions` και να αντιστοιχίσετε τις ελλειπούσες γραμματοσειρές σε μια γνωστή fallback.

---

## Βήμα 4: Φόρτωση του Εγγράφου με τις Προσαρμοσμένες Επιλογές σας

Τώρα που το callback είναι συνδεδεμένο, φορτώστε το έγγραφο. Αν το αρχείο αναφέρει μια γραμματοσειρά που δεν έχετε, θα δείτε την προειδοποίηση να εκτυπώνεται.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Όταν εκτελέσετε το πρόγραμμα, η κονσόλα μπορεί να εμφανίσει:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Αυτή η γραμμή αποδεικνύει ότι έχετε εντοπίσει επιτυχώς **ελλειπούσες γραμματοσειρές** και βρίσκεστε σε θέση να **διαχειριστείτε ελλειπούσες γραμματοσειρές** όπως θεωρείτε σκόπιμο.

---

## Βήμα 5: Προαιρετικό – Αντικατάσταση Ελλειπουσών Γραμματοσειρών με Γνωστή Γραμματοσειρά

Αν προτιμάτε να αντικαθιστάτε αυτόματα κάθε ελλειπούσα γραμματοσειρά, π.χ., με `Times New Roman`, μπορείτε να προσθέσετε ένα αντικείμενο `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Τώρα το έγγραφο φορτώνεται, και κάθε αναφορά στο `MyCustomFont` αντικαθίσταται σιωπηρά από το `Times New Roman`. Η κονσόλα θα συνεχίσει να σας ενημερώνει τι αντικαταστάθηκε, κρατώντας σας ενήμερους.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω υπάρχει μια μοναδική κλάση Java που ενσωματώνει όλα τα παραπάνω βήματα. Αντιγράψτε‑και‑επικολλήστε την στο IDE σας, προσαρμόστε το `docPath`, και τρέξτε.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενη έξοδος**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Τώρα έχετε έναν επαναλήψιμο τρόπο να **ανιχνεύσετε ελλειπούσες γραμματοσειρές**, **διαχειριστείτε ελλειπούσες γραμματοσειρές**, και **προσαρμόσετε τη φόρτωση εγγράφου**—όλα μαθαίνοντας **πώς να ορίσετε callback** σωστά.

---

## Συχνές Ερωτήσεις

### Τι γίνεται αν θέλω το πρόγραμμα να σταματήσει τη φόρτωση όταν λείπει μια γραμματοσειρά;

Ρίξτε μια εξαίρεση μέσα στη μέθοδο `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Το block `catch` στο τέλος θα την πιάσει, και μπορείτε να αποφασίσετε πώς θα την καταγράψετε ή θα ειδοποιήσετε τον χρήστη.

### Λειτουργεί αυτό για PDFs που δημιουργούνται από DOCX;

Απολύτως. Το callback ενεργοποιείται κατά τη **φάση φόρτωσης**, η οποία είναι η ίδια για όλες τις μορφές εξόδου (`save` σε PDF, DOCX, HTML κ.λπ.). Εφόσον φορτώνετε το πηγαίο έγγραφο με τα ίδια `LoadOptions`, θα συλλάβετε τις ελλειπούσες γραμματοσειρές πριν επηρεάσουν το τελικό PDF.

### Μπορώ να συλλάβω άλλους τύπους προειδοποιήσεων (π.χ., μετατροπή εικόνας);

Ναι—το `WarningInfo.getWarningType()` μπορεί να συγκριθεί με άλλα enums όπως `WarningType.IMAGE_CONVERSION`. Απλώς προσθέστε περισσότερα `if` κλαδιά στο callback.

### Υπάρχει αντίκτυπος στην απόδοση;

Αμελητέος. Το callback εκτελείται συγχρονισμένα κατά τη φόρτωση, και οι επιπλέον έλεγχοι είναι ελαφροί. Αν φορτώνετε χιλιάδες έγγραφα, ίσως θέλετε να απενεργοποιήσετε τις προειδοποιήσεις σε παραγωγή ορίζοντας `loadOptions.setWarningCallback(null);`.

---

## Οπτική Επισκόπηση

![παράδειγμα πώς να ορίσετε callback στο Aspose.Words Java](https://example.com/images/callback-diagram.png "πώς να ορίσετε callback")

*Το διάγραμμα απεικονίζει τη ροή: `LoadOptions` → `IWarningCallback` → Φόρτωση εγγράφου → Διαχείριση αντικατάστασης γραμματοσειράς.*

---

## Συμπέρασμα

Καλύψαμε **πώς να ορίσετε callback** στο Aspose.Words Java, δείξαμε **πώς να ανιχνεύσετε ελλειπούσες γραμματοσειρές**, παρουσιάσαμε πρακτικούς τρόπους **διαχείρισης ελλειπουσών γραμματοσειρών**, και εξηγήσαμε πώς να **προσαρμόσετε τη φόρτωση εγγράφου** με `LoadOptions`.  

Με αυτή τη γνώση, μπορείτε τώρα να προστατεύσετε τις αλυσίδες επεξεργασίας εγγράφων σας από σιωπηλές αντικαταστάσεις γραμματοσειρών, να διατηρήσετε το branding αμετάβλητο, και να παρέχετε στους χρήστες σαφή ανατροφοδότηση όταν κάτι πάει στραβά.

### Τι Επόμενο;

- Εξερευνήστε τους **πίνακες αντικατάστασης γραμματοσειρών** για μαζική αντιστοίχιση πολλών ελλειπουσών γραμματοσειρών.  
- Συνδυάστε αυτό το callback με **επαλήθευση εγγράφου** για την επιβολή οδηγών στυλ.  
- Δοκιμάστε **προσαρμοσμένα warning callbacks** που γράφουν σε αρχείο καταγραφής ή σε σύστημα παρακολούθησης αντί για `System.out`.  

Νιώστε ελεύθεροι να πειραματιστείτε, και ενημερώστε μας πώς προσαρμόσατε το callback στα δικά σας projects. Καλή προγραμματιστική!

---


## Τι Θα Μάθετε Στη Σύντομη Μελλοντική;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας projects.

- [Πώς να Ορίσετε LoadOptions στο Aspose.Words για Java](/words/english/java/document-loading-and-saving/using-load-options/)  
- [Πώς να Ανιχνεύσετε Γραμματοσειρές στο Aspose.Words – Διαχείριση Προειδοποιήσεων & Ρυθμίσεων](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)  
- [Πώς να Συλλέξετε Γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}