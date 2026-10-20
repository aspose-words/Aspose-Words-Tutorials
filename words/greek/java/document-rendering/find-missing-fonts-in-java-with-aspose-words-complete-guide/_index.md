---
category: general
date: 2026-06-08
description: Βρείτε γρήγορα τις ελλιπείς γραμματοσειρές χρησιμοποιώντας το Aspose.Words
  για Java. Μάθετε να διαγνώσετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών
  και να διορθώσετε τα προβλήματα ελλιπών γραμματοσειρών σε λίγα μόνο βήματα.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: el
og_description: Βρείτε τις ελλείπουσες γραμματοσειρές στα αρχεία DOCX με το Aspose.Words
  for Java. Αυτό το σεμινάριο δείχνει πώς να ενεργοποιήσετε τη διάγνωση, να διαβάσετε
  τα συμβάντα FontSubstitutionWarning και να εμφανίσετε τα αρχικά ονόματα γραμματοσειρών
  σε σχέση με τα αντικατεστημένα.
og_title: Εύρεση Ελλειπόντων Γραμματοσειρών σε Java – Aspose.Words Βήμα-Βήμα
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Εύρεση ελλειπόντων γραμματοσειρών σε Java με το Aspose.Words – Πλήρης Οδηγός
url: /el/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εύρεση Ελλιπών Γραμματοσειρών σε Java με Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **βρείτε ελλιπείς γραμματοσειρές** σε ένα έγγραφο Word πριν καταστρέψουν τη διάταξη; Δεν είστε οι μόνοι—οι προγραμματιστές συχνά αντιμετωπίζουν σιωπηλές αντικαταστάσεις γραμματοσειρών που χαλούν PDFs ή εκτυπωμένες αναφορές. Τα καλά νέα είναι ότι το Aspose.Words for Java παρέχει ενσωματωμένο API διαγνωστικών που κάνει την ανίχνευση των ελλιπών γραμματοσειρών παιχνιδάκι.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που φορτώνει ένα DOCX, ενεργοποιεί τη συλλογή προειδοποιήσεων και εκτυπώνει κάθε *FontSubstitutionWarning* που χρειάζεστε. Στο τέλος θα μπορείτε να καταγράψετε το αρχικό όνομα γραμματοσειράς, την εναλλακτική που επέλεξε το Aspose και να αποφασίσετε αν θα ενσωματώσετε εσείς την ελλιπή γραμματοσειρά.

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

* **Aspose.Words for Java** (τελευταία έκδοση 23.x) στο classpath σας.  
* Περιβάλλον ανάπτυξης Java 8+ (IDE της επιλογής σας, Maven/Gradle λειτουργούν).  
* Ένα δείγμα DOCX που σκόπιμα αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας—ας το ονομάσουμε `MissingFonts.docx`.

Αυτό είναι όλο. Δεν χρειάζονται επιπλέον βιβλιοθήκες, καμία πολύπλοκη ρύθμιση, μόνο απλή Java και Aspose.

![Διάγραμμα εύρεσης ελλιπών γραμματοσειρών](https://example.com/find-missing-fonts.png "Διάγραμμα εύρεσης ελλιπών γραμματοσειρών")

*Η παραπάνω εικόνα απεικονίζει τη ροή: φόρτωση → διαγνωστικά → προειδοποιήσεις → έξοδος.*

## Βήμα 1: Προετοιμασία LoadOptions και Καθορισμός Μορφής Εγγράφου

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα αντικείμενο **LoadOptions**. Αυτό λέει στο Aspose.Words πώς να ερμηνεύσει το εισερχόμενο αρχείο και, το σημαντικότερο, ενεργοποιεί τη συλλογή *προειδοποιήσεων εγγράφου*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*Γιατί να χρησιμοποιήσετε LoadOptions;*  
Χωρίς αυτό, το Aspose φορτώνει το αρχείο αλλά μπορεί να παραλείψει κάποια διαγνωστικά δεδομένα. Ορίζοντας ρητά τη μορφή, εξασφαλίζετε συνεπή δημιουργία προειδοποιήσεων, ειδικά όταν δουλεύετε με παλαιά ή κατεστραμμένα αρχεία.

## Βήμα 2: Φόρτωση του Εγγράφου με Ενεργοποιημένα Διαγνωστικά

Τώρα διαβάζουμε πραγματικά το αρχείο. Ο κατασκευαστής `Document` ξεκινά αυτόματα τη συλλογή προειδοποιήσεων, οι οποίες αργότερα θα περιλαμβάνουν τυχόν **FontSubstitutionWarning**.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Συμβουλή:** Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση Aspose.Words στο `pom.xml`. Έτσι το JAR θα ληφθεί αυτόματα και δεν θα χρειαστεί να διαχειριστείτε το classpath χειροκίνητα.

## Βήμα 3: Σάρωση των Προειδοποιήσεων Εγγράφου για Συμβάντα Αντικατάστασης Γραμματοσειράς

Το Aspose αποθηκεύει κάθε προειδοποίηση σε μια συλλογή που μπορείτε να διατρέξετε. Φιλτράρουμε για αντικείμενα `FontSubstitutionWarning` επειδή υποδεικνύουν συγκεκριμένα μια ελλιπή γραμματοσειρά που αντικαταστάθηκε.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*Τι συμβαίνει εδώ;*  
`doc.getWarnings()` επιστρέφει μια `List<WarningInfo>`. Ελέγχοντας `instanceof FontSubstitutionWarning` απομονώνουμε μόνο τις εγγραφές σχετικές με γραμματοσειρές, αγνοώντας άλλες προειδοποιήσεις όπως “μη υποστηριζόμενη λειτουργία” ή “μετατροπή εικόνας”.

## Βήμα 4: Εκτύπωση του Αρχικού και του Αντικατασταθέντος Ονόματος Γραμματοσειράς

Τέλος, εκτυπώνουμε τόσο το όνομα της ελλιπής (αρχικής) γραμματοσειράς όσο και τη γραμματοσειρά που επέλεξε το Aspose ως υποκατάστατο. Αυτή η έξοδος είναι ιδανική για καταγραφή ή για ενσωμάτωση σε έλεγχο pipeline.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Αναμενόμενη Έξοδος στην Κονσόλα

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Αν δεν εμφανιστεί τίποτα, σημαίνει ότι **δεν εντοπίστηκαν ελλιπείς γραμματοσειρές**—το έγγραφό σας περιέχει ήδη γραμματοσειρές που υπάρχουν στο μηχάνημα που εκτελεί τον κώδικα.

## Βήμα 5: Διαχείριση Ακραίων Περιπτώσεων και Συνηθισμένων Παγίδων

### Ελλιπής Γραμματοσειρά αλλά Χωρίς Προειδοποίηση

Μερικές φορές μια γραμματοσειρά είναι ενσωματωμένη στο DOCX, αλλά η ενσωμάτωση είναι κατεστραμμένη. Το Aspose θα εξακολουθήσει να εγείρει `FontSubstitutionWarning` επειδή δεν μπορεί να αποδώσει το κείμενο. Για να το διακρίνετε, ελέγξτε `fsWarning.isFontEmbedded()` (διαθέσιμο σε νεότερες εκδόσεις).

### Πολλαπλές Αντικαταστάσεις για την Ίδια Γραμματοσειρά

Μια ελλιπής γραμματοσειρά μπορεί να αντικατασταθεί πολλές φορές σε διαφορετικές εκτελέσεις αν η ιεραρχία εναλλακτικών αλλάζει (π.χ., πρώτα προσπαθεί Arial, μετά Helvetica). Διατηρήστε ένα `Set<String>` των `getOriginalFontName()` για απομάκρυνση διπλοτύπων αν χρειάζεστε μόνο τη λίστα των μοναδικών ελλιπών γραμματοσειρών.

### Σκέψεις για Απόδοση

Η φόρτωση πολύ μεγάλων αρχείων DOCX (εκατοντάδες MB) ενώ συλλέγονται προειδοποιήσεις μπορεί να προσθέσει επιβάρυνση. Αν χρειάζεστε μόνο διαγνωστικά γραμματοσειρών, ορίστε `loadOptions.setValidateStructure(false)` για να παραλείψετε τη βαθιά επικύρωση. Αυτό επιταχύνει τη διαδικασία χωρίς να επηρεάζει τη δημιουργία προειδοποιήσεων.

## Bonus: Αυτοματοποίηση Ενσωμάτωσης Γραμματοσειρών

Μόλις γνωρίζετε ποιες γραμματοσειρές λείπουν, μπορείτε να τις ενσωματώσετε προγραμματιστικά:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Η ενσωμάτωση εξασφαλίζει ότι το τελικό PDF ή το αποθηκευμένο DOCX θα αποδοθεί ακριβώς όπως προορίζεται σε οποιοδήποτε μηχάνημα—χωρίς ξαφνικές εναλλακτικές.

## Ανακεφαλαίωση: Πώς να Βρείτε Ελλιπείς Γραμματοσειρές με Aspose.Words

- **Δημιουργήστε LoadOptions** και ορίστε τη μορφή φόρτωσης.  
- **Φορτώστε το έγγραφο** ενώ το Aspose καταγράφει προειδοποιήσεις.  
- **Διατρέξτε το `doc.getWarnings()`**, φιλτράροντας για `FontSubstitutionWarning`.  
- **Εκτυπώστε** `getOriginalFontName()` και `getSubstitutedFontName()` για να δείτε ποιες γραμματοσειρές λείπουν.  
- **Προαιρετικά:** αφαιρέστε διπλότυπα, ελέγξτε την κατάσταση ενσωμάτωσης ή ενσωματώστε αυτόματα τις ελλιπείς γραμματοσειρές.

Αυτή είναι η πλήρης λύση για **να βρείτε ελλιπείς γραμματοσειρές** σε μια εφαρμογή Java χρησιμοποιώντας Aspose.Words. Έχετε τώρα έναν αξιόπιστο τρόπο να εντοπίζετε προβλήματα γραμματοσειρών νωρίς, να διατηρείτε τα PDFs σας συνεπή και να αποφεύγετε ανεπιθύμητες εκπλήξεις στην παραγωγή.

## Τι Να Εξερευνήσετε Στη Σύντομη Μελλοντική

* **Αυτόματη ενσωμάτωση γραμματοσειρών** (δείτε το bonus snippet).  
* **Δημιουργία PDF** μετά τη διόρθωση των γραμματοσειρών για επαλήθευση του οπτικού αποτελέσματος.  
* **Χρήση FontSettings του Aspose.Words** για ορισμό προσαρμοσμένης αλυσίδας εναλλακτικών.  
* **Εκτέλεση των ίδιων διαγνωστικών σε αρχεία DOC, RTF ή HTML**—απλώς αλλάξτε το `LoadFormat` αναλόγως.

Πειραματιστείτε με διαφορετικούς τύπους εγγράφων και οικογένειες γραμματοσειρών. Αν αντιμετωπίσετε πρόβλημα, αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την επίσημη τεκμηρίωση Java API του Aspose για πιο βαθιά προσαρμογή.

Καλό κώδικα, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα με τις γραμματοσειρές που προορίζονται!

## Τι Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Using Fonts in Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}