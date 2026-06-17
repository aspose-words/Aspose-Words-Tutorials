---
category: general
date: 2026-05-30
description: Καταχωρίστε την κλήση επιστροφής προειδοποίησης σε Java για την παρακολούθηση
  ελλιπών γραμματοσειρών και την προσαρμογή της φόρτωσης εγγράφων με το Aspose.Words.
  Μάθετε τη πλήρη λύση βήμα‑βήμα.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: el
og_description: Καταχωρίστε τη λειτουργία κλήσης προειδοποίησης σε Java για την παρακολούθηση
  ελλιπών γραμματοσειρών και την προσαρμογή της φόρτωσης εγγράφων. Πλήρης οδηγός με
  κώδικα και εξηγήσεις.
og_title: Καταχώριση callback προειδοποίησης σε Java – Παρακολούθηση ελλειπούσων γραμματοσειρών
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Καταχώρηση κλήσης προειδοποίησης σε Java – Παρακολούθηση ελλειπόντων γραμματοσειρών
url: /el/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταχώρηση warning callback σε Java – Παρακολούθηση ελλιπών γραμματοσειρών

Έχετε αναρωτηθεί ποτέ πώς να **παρακολουθήσετε ελλιπείς γραμματοσειρές** κατά τη φόρτωση ενός εγγράφου Word με το Aspose.Words for Java; Ίσως έχετε δει εκείνες τις σιωπηλές αντικαταστάσεις γραμματοσειρών και σκεφτείτε, “Τι συνέβη στη διάταξή μου?” Τα καλά νέα είναι ότι δεν χρειάζεται να μαντεύετε. Με **καταχώρηση ενός warning callback**, μπορείτε να συλλάβετε κάθε γεγονός αντικατάστασης γραμματοσειράς τη στιγμή που διαβάζεται το έγγραφο, και μπορείτε επίσης να **προσαρμόσετε τη φόρτωση του εγγράφου** ώστε να ταιριάζει στη διαδικασία σας.

Σε αυτό το σεμινάριο θα περάσουμε από ένα πραγματικό παράδειγμα που δείχνει ακριβώς πώς να ρυθμίσετε το callback, γιατί είναι σημαντικό, και πώς να διατηρήσετε το υπόλοιπο pipeline επεξεργασίας σας καθαρό. Στο τέλος θα έχετε μια έτοιμη προς εκτέλεση κλάση Java που εκτυπώνει κάθε προειδοποίηση ελλιπούς γραμματοσειράς και αποθηκεύει ένα επεξεργασμένο αντίγραφο του εγγράφου. Δεν απαιτούνται εξωτερικές αναφορές — μόνο καθαρός, εκτελέσιμος κώδικας.

> **Τι θα πάρετε:**  
> • Ένα πλήρες πρόγραμμα Java που χρησιμοποιεί το Aspose.Words  
> • Εξήγηση βήμα‑βήμα κάθε γραμμής  
> • Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως κρυπτογραφημένα αρχεία ή μεγάλες παρτίδες  
> • Ένα γρήγορο sanity‑check που μπορείτε να εκτελέσετε σε οποιοδήποτε αρχείο `.docx`

## Προαπαιτούμενα

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ορίστηκε το `JAVA_HOME`.  
- **Aspose.Words for Java** JAR στο classpath σας. Μπορείτε να κατεβάσετε την τελευταία έκδοση από το αποθετήριο Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Ένα δείγμα εγγράφου Word (`input.docx`) που υποπτεύεστε ότι περιέχει γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας.  
- Ένα IDE ή εργαλείο κατασκευής γραμμής εντολών (Maven/Gradle) με το οποίο αισθάνεστε άνετα.

Αυτό είναι όλο. Χωρίς επιπλέον γραμματοσειρές, χωρίς επιπλέον υπηρεσίες — μόνο καθαρή Java και Aspose.Words.

## Γιατί να καταχωρήσετε ένα warning callback;

Σκεφτείτε το **warning callback** ως μια κάμερα ασφαλείας για τη διαδικασία φόρτωσης του εγγράφου σας. Όταν το Aspose.Words συναντά ένα ελλιπές glyph, δεν ρίχνει εξαίρεση· αντικαθιστά ήσυχα με μια εφεδρική γραμματοσειρά. Αυτή η σιωπηλή αντικατάσταση μπορεί να διαταράξει τη διάταξή σας, ειδικά σε PDF ή τιμολόγια όπου η εμπορική ταυτότητα είναι κρίσιμη. Καταχωρώντας ένα callback, μπορείτε:

1. **Λάβετε πληροφορίες σε πραγματικό χρόνο** – κάθε προειδοποίηση `FONT_SUBSTITUTION` παραδίδεται αμέσως.  
2. **Καταγράψτε ή αντιδράστε** – μπορείτε να καταγράψετε σε αρχείο, να εκκινήσετε μια ειδοποίηση ή ακόμη και να αντικαταστήσετε τη γραμματοσειρά προγραμματιστικά.  
3. **Διατηρήστε καθαρό αποτέλεσμα** – γνωρίζοντας ποιες γραμματοσειρές λείπουν, μπορείτε να διορθώσετε το πηγαίο έγγραφο πριν τη δημοσίευση.

Συνοψίζοντας, το callback μετατρέπει ένα κρυφό πρόβλημα σε εμφανές, κάνοντας το pipeline εγγράφων σας πολύ πιο αξιόπιστο.

## Βήμα 1 – Δημιουργία `LoadOptions` για προσαρμογή του τρόπου φόρτωσης του εγγράφου

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα αντικείμενο `LoadOptions`. Αυτό το αντικείμενο είναι η πύλη για κάθε ρύθμιση κατά τη φόρτωση που μπορεί να χρειαστείτε, από τη διαχείριση κωδικών πρόσβασης μέχρι τη λειτουργία **register warning callback**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Γιατί να μην καλέσετε απλώς `new Document("file.docx")`; Επειδή χωρίς `LoadOptions` χάνετε την ευκαιρία να συνδεθείτε στα γεγονότα φόρτωσης. Το `LoadOptions` είναι το μοναδικό σημείο όπου το Aspose.Words σας επιτρέπει να **προσαρμόσετε τη φόρτωση του εγγράφου**.

## Βήμα 2 – Καταχώρηση ενός warning callback για παρακολούθηση ελλιπών γραμματοσειρών

Τώρα έρχεται το αστέρι της παράστασης: **καταχωρούμε ένα warning callback** που υλοποιεί το `IWarningCallback`. Μέσα στη μέθοδο `warning` φιλτράρουμε για `WarningType.FONT_SUBSTITUTION` και εκτυπώνουμε ένα χρήσιμο μήνυμα.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Μερικά σημεία που πρέπει να σημειώσετε:

- **Γιατί `IWarningCallback`;** Είναι η διεπαφή που χρησιμοποιεί το Aspose.Words για όλους τους τύπους προειδοποιήσεων, παρέχοντάς σας ένα ενιαίο σημείο εισόδου για πολλά πιθανά ζητήματα.  
- **Το φιλτράρισμα είναι κρίσιμο** – χωρίς τον έλεγχο `if` θα δείτε προειδοποιήσεις για ελλιπή εικόνα, παρωχημένες λειτουργίες κ.λπ., που θα γεμίσουν τα αρχεία καταγραφής σας.  
- **Ασφάλεια νήματος** – το callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο, έτσι μπορείτε με ασφάλεια να ενημερώσετε κοινές δομές αν χρειαστεί να συγκεντρώσετε τα αποτελέσματα αργότερα.

Αυτό το απόσπασμα **καταχωρεί το warning callback**, και από εδώ και στο εξής κάθε γεγονός ελλιπούς γραμματοσειράς θα εκτυπώνεται στο `stdout`. Αυτό είναι ο πυρήνας της **παρακολούθησης ελλιπών γραμματοσειρών**.

## Βήμα 3 – Φόρτωση του εγγράφου χρησιμοποιώντας το ρυθμισμένο `LoadOptions`

Με το callback στη θέση του, φορτώνουμε τελικά το αρχείο. Αν το έγγραφο αναφέρει μια γραμματοσειρά που δεν έχετε, το callback ενεργοποιείται πριν το αντικείμενο Document ολοκληρωθεί πλήρως.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο σύστημά σας. Ο κατασκευαστής `Document` διαβάζει το αρχείο, εφαρμόζει τυχόν κωδικό (αν έχετε ορίσει έναν στο `loadOptions`), και ενεργοποιεί το warning callback για κάθε ελλιπή γραμματοσειρά. Θα δείτε έξοδο όπως:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Αυτή η γραμμή αποδεικνύει ότι έχετε παρακολουθήσει επιτυχώς τις ελλιπείς γραμματοσειρές.

## Βήμα 4 – Συνέχεια επεξεργασίας του εγγράφου (προαιρετικό)

Σε αυτό το στάδιο μπορείτε να χειριστείτε το έγγραφο όπως θέλετε — να αντικαταστήσετε κείμενο, να εισάγετε εικόνες ή ακόμη και να ανταλλάξετε προγραμματιστικά τις αντικατεστημένες γραμματοσειρές. Το callback σας έδωσε ήδη μια λίστα με τις προβληματικές γραμματοσειρές, έτσι μπορείτε, για παράδειγμα, να ενσωματώσετε μια εφεδρική γραμματοσειρά:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Μπορείτε να παραλείψετε αυτό το τμήμα αν χρειάζεστε μόνο την **παρακολούθηση ελλιπών γραμματοσειρών**. Το βασικό είναι ότι τώρα έχετε τις πληροφορίες που χρειάζεστε για να λάβετε μια ενημερωμένη απόφαση.

## Βήμα 5 – Αποθήκευση του επεξεργασμένου εγγράφου

Τέλος, αποθηκεύστε το έγγραφο. Μπορείτε να αντικαταστήσετε το αρχικό, να το αποθηκεύσετε σε νέα θέση ή να το εξάγετε σε PDF — όλα χωρίς να χάσετε τα δεδομένα προειδοποίησης που συλλέξατε νωρίτερα.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Η εκτέλεση ολόκληρης της κλάσης θα παράγει έξοδο στην κονσόλα για κάθε ελλιπή γραμματοσειρά και ένα νέο αρχείο με όνομα `processed.docx` στον ίδιο φάκελο.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται η πλήρης κλάση Java που μπορείτε να αντιγράψετε‑επικολλήσετε στο IDE σας. Περιλαμβάνει όλα όσα συζητήσαμε, καθώς και έναν μικρό wrapper με τη μέθοδο `main`.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Αναμενόμενη Έξοδος

Όταν εκτελέσετε το πρόγραμμα σε ένα έγγραφο που χρησιμοποιεί μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας, θα δείτε κάτι όπως:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Αν το έγγραφο δεν περιέχει **ελλιπείς γραμματοσειρές**, η κονσόλα παραμένει ήσυχη μέχρι τη τελική γραμμή «Document saved successfully.» — ακριβώς αυτό που θα περιμένατε από μια σωστή υλοποίηση **register warning callback**.

## Συμβουλές & Συνηθισμένα Πιθανά Σφάλματα

- **Πολλαπλά callbacks;** Το Aspose.Words επιτρέπει μόνο έναν χειριστή προειδοποιήσεων. Αν χρειάζεται να καταγράψετε τόσο σε αρχείο όσο και στην κονσόλα, υλοποιήστε ένα σύνθετο callback που προωθεί την προειδοποίηση σε πολλαπλούς προορισμούς.  
- **Μεγάλες παρτίδες** – όταν επεξεργάζεστε εκατοντάδες αρχεία, σκεφτείτε να επαναχρησιμοποιήσετε ένα μόνο αντικείμενο `LoadOptions`; η δημιουργία του ανά αρχείο προσθέτει περιττό κόστος.  
- **Κρυπτογραφημένα έγγραφα** – ορίστε τον κωδικό στο `LoadOptions` πριν τη φόρτωση, διαφορετικά θα λάβετε `IncorrectPasswordException` πριν το callback ενεργοποιηθεί.  
- **Απόδοση** – το callback εκτελείται συγχρονισμένα. Αν καταγράφετε σε απομακρυσμένη υπηρεσία, κάντε buffer τα μηνύματα και αποστείλετε τα μετά το τέλος της φόρτωσης για να αποφύγετε bottlenecks I/O.  
- **Εφεδρική γραμματοσειρά** – μπορείτε επίσης να παρέχετε μια προσαρμοσμένη συλλογή `FontSource` αν έχετε ιδιόκτητες γραμματοσειρές που θέλετε το Aspose.Words να εξετάσει πριν καταφύγει στις συστημικές γραμματοσειρές.

## Συμπέρασμα

Μόλις μάθατε πώς να **καταχωρήσετε ένα warning callback** σε Java, να **παρακολουθήσετε ελλιπείς γραμματοσειρές** και να **προσαρμόσετε τη φόρτωση του εγγράφου** με το Aspose.Words. Η λύση είναι αυτόνομη, εκτελείται με μια μόνο μέθοδο `main`, και σας παρέχει άμεση ορατότητα σε οποιαδήποτε αντικατάσταση γραμματοσειράς που διαφορετικά θα παρέμενε αθέατη.

Επόμενα βήματα; Δοκιμάστε να επεκτείνετε το callback ώστε να γράφει προειδοποιήσεις σε αρχείο CSV για σκοπούς ελέγχου, ή συνδυάστε το με έναν επεξεργαστή παρτίδας που ενσωματώνει αυτόματα τις ελλιπείς γραμματοσειρές. Μπορείτε επίσης να εξερευνήσετε άλλους τύπους προειδοποιήσεων όπως `IMAGE_SUBSTITUTION` ή `DEPRECATED_FEATURE` — το ίδιο μοτίβο ισχύει.

Καλό κώδικα, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως το θέλετε!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

- [Callback Προειδοποίησης Σε Έγγραφο Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Προσαρμογή Χρωμάτων Θέματος & Γραμματοσειρών στο Aspose.Words Java: Ένας Πλήρης Οδηγός](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Παρακολούθηση Αλλαγών σε Έγγραφα Word Χρησιμοποιώντας Aspose.Words Java: Ένας Πλήρης Οδηγός για Αναθεωρήσεις Εγγράφων](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}