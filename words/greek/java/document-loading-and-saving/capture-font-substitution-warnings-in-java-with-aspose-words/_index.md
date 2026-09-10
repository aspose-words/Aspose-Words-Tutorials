---
category: general
date: 2026-01-11
description: Μάθετε πώς να καταγράφετε προειδοποιήσεις αντικατάστασης γραμματοσειράς
  χρησιμοποιώντας το Aspose.Words για Java. Αυτό το βήμα‑βήμα εκπαιδευτικό υλικό καλύπτει
  επίσης τις LoadOptions και τις κλήσεις επιστροφής προειδοποιήσεων.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: el
og_description: Καταγράψτε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών με το
  Aspose.Words για Java. Ακολουθήστε αυτόν τον οδηγό για να ρυθμίσετε τις LoadOptions
  και μια κλήση επιστροφής προειδοποίησης για αξιόπιστη φόρτωση εγγράφων.
og_title: Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς σε Java – Πλήρης
  Οδηγός
tags:
- Aspose.Words
- Java
- Document Processing
title: Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς σε Java με το Aspose.Words
  – Πλήρης Οδηγός
url: /el/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς – Πλήρες Java Tutorial

Έχετε χρειαστεί ποτέ να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** όταν ανοίγετε ένα έγγραφο Word με ελλιπείς γραμματοσειρές; Είναι ένα συχνό πρόβλημα, ειδικά όταν δημιουργείτε PDF ή εκτυπώνετε σε διακομιστή που δεν έχει εγκατεστημένες όλες τις γραμματοσειρές. Τα καλά νέα; Το Aspose.Words for Java το κάνει εύκολο — αρκεί να διαμορφώσετε ένα αντικείμενο `LoadOptions` και να συνδέσετε μια callback προειδοποίησης. Σε αυτόν τον οδηγό θα δείτε ακριβώς πώς γίνεται, γιατί είναι σημαντικό και τι να περιμένετε όταν ενεργοποιηθεί η προειδοποίηση.

Θα αγγίξουμε επίσης σχετικά θέματα όπως **Aspose.Words font substitution**, χρήση **Java warning callback**, και βέλτιστες πρακτικές για **LoadOptions usage**. Στο τέλος, θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα που καταγράφει κάθε συμβάν ελλιπούς γραμματοσειράς, ώστε η επόμενη επεξεργασία σας να μην σας εκπλήσσει.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ρυθμισμένο.
- Aspose.Words for Java 23.10 (ή νεότερη) στο classpath σας.
- Ένα έγγραφο Word που αναφέρει μια γραμματοσειρά που δεν έχετε τοπικά (π.χ., `DocWithMissingFont.docx`).
- Βασική εξοικείωση με τα μπλοκ try/catch της Java — τίποτα περίπλοκο.

Αν κάποιο από αυτά δεν σας είναι γνωστό, κάντε ένα διάλειμμα και εγκαταστήστε τη βιβλιοθήκη από το Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Τώρα που το υπόβαθρο είναι έτοιμο, ας περάσουμε στον κώδικα.

## Βήμα 1: Ρύθμιση Callback Προειδοποίησης για **Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς**

Το πρώτο που χρειάζεστε είναι μια callback που το Aspose.Words θα καλέσει όποτε εντοπίσει μια ελλιπή γραμματοσειρά. Εδώ **καταγράφετε προειδοποιήσεις αντικατάστασης γραμματοσειράς**. Η callback υλοποιεί τη διεπαφή `IWarningCallback` και ελέγχει το `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Γιατί είναι σημαντικό:** Χωρίς μια callback, το Aspose.Words αντικαθιστά σιωπηλά τη λείπουσα γραμματοσειρά με μια προεπιλεγμένη, και δεν γνωρίζετε ότι η οπτική έξοδος έχει αλλάξει. Καταγράφοντας την προειδοποίηση, μπορείτε να την καταγράψετε, να στείλετε ειδοποίηση ή ακόμη και να ακυρώσετε τη φόρτωση αν η λείπουσα γραμματοσειρά είναι κρίσιμη.

## Βήμα 2: Διαμόρφωση **LoadOptions** και Καταχώρηση της Callback

Τώρα δημιουργούμε ένα αντικείμενο `LoadOptions` και συνδέουμε το `FontWarningCallback`. Αυτό το βήμα είναι ουσιώδες για **LoadOptions usage** και εξασφαλίζει ότι κάθε φόρτωση εγγράφου περνάει από το ίδιο φίλτρο προειδοποιήσεων.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Συμβουλή:** Μπορείτε να επαναχρησιμοποιήσετε το ίδιο αντικείμενο `LoadOptions` για πολλά έγγραφα, εξοικονομώντας μερικές γραμμές κώδικα και εξασφαλίζοντας συνεπή **document loading warnings** σε όλη την εφαρμογή σας.

## Βήμα 3: Φόρτωση του Εγγράφου και Παρατήρηση της Εξόδου

Με τη callback συνδεδεμένη, απλώς φορτώστε το αρχείο Word. Αν το έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, η callback θα ενεργοποιηθεί και θα εκτυπώσει λεπτομέρειες στην κονσόλα.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Αναμενόμενη Έξοδος Κονσόλας

Υποθέτοντας ότι το `DocWithMissingFont.docx` αναφέρει τη λείπουσα γραμματοσειρά *«Comic Sans MS»*, θα δείτε κάτι όπως:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Αν το έγγραφο **δεν περιέχει ελλιπείς γραμματοσειρές**, η κονσόλα θα εμφανίσει μόνο τη τελευταία γραμμή, επιβεβαιώνοντας ότι η callback δεν παρήγαγε ψευδείς θετικές.

## Βήμα 4: Διαχείριση Ακραίων Περιπτώσεων και Συνηθισμένων Παγίδων

### Πολλαπλές Λείπουσες Γραμματοσειρές

Αν ένα έγγραφο χρησιμοποιεί πολλές μη διαθέσιμες γραμματοσειρές, η callback εκτελείται μία φορά ανά γραμματοσειρά. Θα λάβετε μια σειρά μηνυμάτων, το καθένα με το δικό του `source` και `description`. Δεν απαιτείται επιπλέον κώδικας — απλώς βεβαιωθείτε ότι το σύστημα καταγραφής σας μπορεί να διαχειριστεί γρήγορες διαδοχικές κλήσεις.

### Καταστολή Προειδοποιήσεων

Σε σπάνιες περιπτώσεις μπορεί να θέλετε να αγνοήσετε ορισμένες αντικαταστάσεις (π.χ., γνωρίζετε ότι μια συγκεκριμένη εναλλακτική είναι αποδεκτή). Επεκτείνετε τη λογική της callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Ασφάλεια Στο Νήμα

Το `LoadOptions` του Aspose.Words δεν είναι thread‑safe από προεπιλογή. Αν φορτώνετε έγγραφα παράλληλα, δημιουργήστε ξεχωριστό αντικείμενο `LoadOptions` ανά νήμα ή συγχρονίστε τη callback για να αποφύγετε συνθήκες αγώνα.

## Βήμα 5: Επαλήθευση της Αντικατασταθείσας Γραμματοσειράς στο Τελικό Έγγραφο

Μετά τη φόρτωση, ίσως θέλετε να επιβεβαιώσετε ότι η αντικατάσταση πραγματικά πραγματοποιήθηκε. Το API σας επιτρέπει να επαναλάβετε όλα τα runs και να ελέγξετε το τελικό όνομα γραμματοσειράς:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Αυτό το απόσπασμα εκτυπώνει κάθε τμήμα κειμένου με τη τελική του γραμματοσειρά. Είναι ένας χρήσιμος έλεγχος λογικής όταν χτίζετε αυτοματοποιημένες αλυσίδες μετατροπής PDF.

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας τα παραπάνω, ορίστε το ολοκληρωμένο, έτοιμο‑για‑εκτέλεση πρόγραμμα:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Αποθηκεύστε το ως `FontSubstitutionInfo.java`, μεταγλωττίστε με `javac` και τρέξτε με `java FontSubstitutionInfo`. Θα πρέπει να δείτε τα μηνύματα προειδοποίησης (αν υπάρχουν) ακολουθούμενα από τη λίστα των runs και τις τελικές τους γραμματοσειρές.

## Οπτική Βοήθεια

![Screenshot of console output showing font substitution warnings](/images/font-substitution-warning.png "capture font substitution warnings example")

*Alt text:* **capture font substitution warnings** – έξοδος κονσόλας μετά τη φόρτωση εγγράφου με λείπουσες γραμματοσειρές.

## Συμπέρασμα

Τώρα ξέρετε πώς να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** χρησιμοποιώντας το Aspose.Words for Java. Διαμορφώνοντας ένα αντικείμενο `LoadOptions` και παρέχοντας μια προσαρμοσμένη `IWarningCallback`, αποκτάτε πλήρη ορατότητα σε οποιαδήποτε συμβάντα ελλιπών γραμματοσειρών που διαφορετικά θα μπορούσαν να επηρεάσουν σιωπηλά την εμφάνιση του εγγράφου σας. Αυτή η τεχνική ενσωματώνεται απευθείας στη **Aspose.Words font substitution** διαχείριση, εξασφαλίζει αξιόπιστες **document loading warnings** και σας δίνει την ευελιξία να καταγράψετε, να ειδοποιήσετε ή να ακυρώσετε ανάλογα με τους επιχειρηματικούς σας κανόνες.

### Τι Ακολουθεί;

- Εξερευνήστε πρότυπα **Java warning callback** για άλλους τύπους προειδοποιήσεων (π.χ., `DEPRECATED_FEATURE`).
- Συνδυάστε αυτήν την προσέγγιση με **PDF conversion** για να εγγυηθείτε ότι οι αντικαταστάσεις γραμματοσειρών δεν θα διαταράξουν τη διάταξη.
- Βυθιστείτε περισσότερο στη **LoadOptions usage** — πειραματιστείτε με `Password`, `Encoding` και `ResourceLoadingCallback` για πιο προχωρημένα σενάρια.

Μη διστάσετε να τροποποιήσετε τη callback, να κατευθύνετε τις προειδοποιήσεις σε ένα πλαίσιο καταγραφής ή ακόμη και να ρίξετε μια προσαρμοσμένη εξαίρεση αν λείπει κρίσιμη γραμματοσειρά. Ο ουρανός είναι το όριο, και τώρα έχετε μια σταθερή βάση για να χτίσετε πάνω της.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα όπως το περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}