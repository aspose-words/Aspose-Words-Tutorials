---
category: general
date: 2026-05-30
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx στη Java με το Aspose.Words.
  Αυτός ο οδηγός καλύπτει τη λειτουργία πλήρους ανάκτησης, τη φόρτωση σε αυστηρή λειτουργία
  και τη διαχείριση σφαλμάτων.
draft: false
keywords:
- recover corrupted docx
- Aspose.Words recovery mode
- Java document recovery
- LoadOptions
- strict mode loading
- handle corrupted Word document
language: el
og_description: Ανακτήστε κατεστραμμένα αρχεία docx σε Java χρησιμοποιώντας το Aspose.Words.
  Κατακτήστε τη λειτουργία πλήρους ανάκτησης, τη φόρτωση σε αυστηρή λειτουργία και
  την ανθεκτική διαχείριση σφαλμάτων.
og_title: Ανάκτηση κατεστραμμένου docx με Aspose.Words Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to recover corrupted docx files in Java with Aspose.Words.
    This guide covers full recovery mode, strict mode loading, and error handling.
  headline: recover corrupted docx using Aspose.Words Java
  type: TechArticle
- description: Learn how to recover corrupted docx files in Java with Aspose.Words.
    This guide covers full recovery mode, strict mode loading, and error handling.
  name: recover corrupted docx using Aspose.Words Java
  steps:
  - name: '**Full recovery mode** (`RecoveryMode.RECOVER`) to get as much content
      as possible.'
    text: '**Full recovery mode** (`RecoveryMode.RECOVER`) to get as much content
      as possible.'
  - name: '**Strict mode loading** (`RecoveryMode.STRICT`) to detect unrecoverable
      errors.'
    text: '**Strict mode loading** (`RecoveryMode.STRICT`) to detect unrecoverable
      errors.'
  - name: Practical verification of text and images, plus optional `LoadOptions` tweaks.
    text: Practical verification of text and images, plus optional `LoadOptions` tweaks.
  - name: Saving the clean result for downstream processing.
    text: Saving the clean result for downstream processing.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Recovery
title: Ανάκτηση κατεστραμμένου docx με Aspose.Words Java
url: /el/java/document-loading-and-saving/recover-corrupted-docx-using-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου docx με Aspose.Words Java

Έχετε ποτέ χρειαστεί να **ανακτήσετε κατεστραμμένα docx** αρχεία αλλά δεν ήξερτε από πού να ξεκινήσετε; Δεν είστε μόνοι—τα έγγραφα Word μπορούν να καταστραφούν κατά τη μεταφορά, ξαφνικές διακοπές λειτουργίας ή απλώς κακή τύχη. Τα καλά νέα; Το Aspose.Words for Java σας παρέχει μια ενσωματωμένη μηχανή ανάκτησης που μπορεί να εντοπίσει τη ζημιά και να επαναφέρει το μεγαλύτερο μέρος του περιεχομένου.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει πώς να φορτώσετε ένα κατεστραμμένο `.docx` με *πλήρη* ανάκτηση, στη συνέχεια να δοκιμάσετε πιο αυστηρό φόρτωμα για να δείτε τι εξακολουθεί να αποτυγχάνει, και τέλος να διαχειριστείτε τυχόν εξαιρέσεις με χάρη. Στο τέλος θα γνωρίζετε ακριβώς πώς να **ανακτήσετε κατεστραμμένα docx** αρχεία, γιατί κάθε λειτουργία ανάκτησης είναι σημαντική, και πώς να επεκτείνετε το μοτίβο για τις δικές σας αυτοματοποιημένες ροές εργασίας.

> **Τι θα χρειαστείτε**  
> • Java 17 (ή οποιοδήποτε πρόσφατο JDK)  
> • Aspose.Words for Java 23.12 (ή νεότερη) – η τελευταία έκδοση διορθώνει πολλά σφάλματα άκρων περιπτώσεων.  
> • Ένα σκόπιμα κατεστραμμένο `Corrupted.docx` (μπορείτε να το τροποποιήσετε σε zip ένα καλό αρχείο για δοκιμή).  

Αν τα έχετε ήδη, υπέροχα—ας βουτήξουμε.

![παράδειγμα εξόδου ανάκτησης κατεστραμμένου docx](https://example.com/images/recover-corrupted-docx.png "Στιγμιότυπο οθόνης ενός επιτυχώς ανακτημένου docx που εμφανίζεται στο Microsoft Word")

## Ανάκτηση κατεστραμμένου docx – Λειτουργία Πλήρους Ανάκτησης

Το πρώτο πράγμα που θέλετε να δοκιμάσετε είναι η **λειτουργία πλήρους ανάκτησης**. Αυτό λέει στο Aspose.Words να είναι επιεικές: θα παραλείψει τα μη αναγνώσιμα τμήματα, θα ξαναχτίσει το εσωτερικό δέντρο του εγγράφου και θα επιστρέψει ένα αντικείμενο `Document` με το οποίο μπορείτε ακόμη να εργαστείτε.

```java
import com.aspose.words.*;

// Step 1: Prepare LoadOptions for full recovery
LoadOptions recoveryOpts = new LoadOptions();
recoveryOpts.setRecoveryMode(RecoveryMode.RECOVER);   // <-- full recovery

// Load the possibly corrupted file
Document recoveredDoc = new Document("YOUR_DIRECTORY/Corrupted.docx", recoveryOpts);
System.out.println("Full recovery succeeded – document loaded with " 
        + recoveredDoc.getPageCount() + " pages.");
```

**Γιατί είναι σημαντικό:** `RecoveryMode.RECOVER` απενεργοποιεί την αυστηρή επικύρωση, επιτρέποντας στη βιβλιοθήκη να αγνοεί κακοδιατυπωμένα τμήματα XML. Σε πολλές πραγματικές περιπτώσεις το κείμενο, οι εικόνες και οι περισσότερες μορφοποιήσεις παραμένουν, ακόμη και αν χαθούν μερικά εσωτερικά αντικείμενα.

### Συμβουλή επαγγελματία
Αν το έγγραφο είναι τεράστιο, σκεφτείτε να ενεργοποιήσετε ρητά το `setLoadFormat(LoadFormat.DOCX)`—αυτό αποτρέπει τη βιβλιοθήκη από το να μαντεύει τη μορφή και επιταχύνει τη φόρτωση.

## Φόρτωση σε αυστηρή λειτουργία – Εντοπισμός μη ανακτήσιμων προβλημάτων

Αφού έχετε ένα έγγραφο με τη μέγιστη δυνατή προσπάθεια, ίσως θέλετε να γνωρίζετε *ακριβώς* τι δεν μπόρεσε να σωθεί. Εδώ έρχεται η **αυστηρή λειτουργία**: ρίχνει μια εξαίρεση στην πρώτη ένδειξη προβλήματος, δίνοντάς σας ένα σαφές σήμα ότι το αρχείο είναι πέρα από την επισκευή.

```java
// Step 2: Switch to strict mode on the same LoadOptions instance
recoveryOpts.setRecoveryMode(RecoveryMode.STRICT);   // <-- strict validation

try {
    Document strictDoc = new Document("YOUR_DIRECTORY/Corrupted.docx", recoveryOpts);
    System.out.println("Strict mode succeeded – this is unusual for a corrupted file.");
} catch (Exception e) {
    // Step 3: Handle the failure – the document could not be opened strictly.
    System.out.println("Failed to open strictly: " + e.getMessage());
}
```

**Γιατί να τη χρησιμοποιήσετε:** Σε δέσμες επεξεργασίας μπορεί να θέλετε να διαχωρίσετε τα “αρκετά καλά” έγγραφα από εκείνα που χρειάζονται χειροκίνητη παρέμβαση. Η αυστηρή λειτουργία σας δίνει μια δυαδική απόφαση που μπορείτε να καταγράψετε ή να κατευθύνετε σε έναν ανθρώπινο ελεγκτή.

### Συνηθισμένη παγίδα
Μην επαναχρησιμοποιείτε το ίδιο αντικείμενο `Document` μετά από αποτυχημένη αυστηρή φόρτωση· δημιουργήστε πάντα ένα νέο όπως φαίνεται παραπάνω. Διαφορετικά η εσωτερική κατάσταση του parser μπορεί να γίνει ασυνεπής.

## Ανάκτηση εγγράφου Java – Επαλήθευση του ανακτημένου περιεχομένου

Μόλις έχετε ένα `recoveredDoc`, πρέπει να επαληθεύσετε ότι τα βασικά μέρη είναι παρόντα. Παρακάτω υπάρχει ένας γρήγορος έλεγχος που εκτυπώνει το κείμενο της πρώτης παραγράφου και τον αριθμό των εικόνων που βρέθηκαν.

```java
// Step 4: Simple verification of recovered content
if (recoveredDoc.getFirstSection().getBody().getParagraphs().getCount() > 0) {
    String firstParagraph = recoveredDoc.getFirstSection()
            .getBody()
            .getParagraphs()
            .get(0)
            .toTxt();
    System.out.println("First paragraph: " + firstParagraph);
}

// Count images
int imageCount = 0;
for (Shape shape : (Iterable<Shape>) recoveredDoc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.getShapeType() == ShapeType.IMAGE) {
        imageCount++;
    }
}
System.out.println("Recovered " + imageCount + " image(s).");
```

Αν η έξοδος δείχνει μια λογική παράγραφο και μερικές εικόνες, έχετε επιτυχώς **ανακτήσει κατεστραμμένα docx** σε μια χρησιμοποιήσιμη κατάσταση.

## LoadOptions – Ρύθμιση της ανάκτησης για ακραίες περιπτώσεις

Aspose.Words προσφέρει μερικές επιπλέον ρυθμίσεις στο `LoadOptions` που μπορούν να βελτιώσουν τα αποτελέσματα σε ιδιαίτερα δύσκολα αρχεία:

| Επιδιόρθωση | Περιγραφή | Πότε να χρησιμοποιηθεί |
|-------------|-----------|------------------------|
| `setPassword(String)` | Ανοίγει έγγραφα προστατευμένα με κωδικό. | Αν γνωρίζετε τον κωδικό. |
| `setValidateStructure(boolean)` | Ενεργοποιεί επιπλέον δομικούς ελέγχους (προεπιλογή `true`). | Όταν υποψιάζεστε ότι λείπουν μέρη. |
| `setEncoding(Encoding)` | Επιβάλλει συγκεκριμένη κωδικοποίηση κειμένου. | Για παλιά αρχεία αποθηκευμένα με κωδικοποιήσεις μη‑UTF‑8. |

Μπορείτε να αλυσίδετε αυτές τις κλήσεις πριν από τη γραμμή `new Document(...)`. Για παράδειγμα:

```java
recoveryOpts.setPassword("mySecret");
recoveryOpts.setValidateStructure(false);
```

## Αποθήκευση του διορθωμένου εγγράφου

Αφού επιβεβαιώσετε το ανακτημένο περιεχόμενο, πιθανότατα θα θέλετε να το γράψετε ξανά στο δίσκο. Η βιβλιοθήκη αφαιρεί αυτόματα τα κατεστραμμένα τμήματα, έτσι το αποθηκευμένο αρχείο είναι καθαρό.

```java
// Step 5: Persist the recovered document
String outPath = "YOUR_DIRECTORY/Recovered.docx";
recoveredDoc.save(outPath, SaveFormat.DOCX);
System.out.println("Recovered document saved to: " + outPath);
```

Τώρα μπορείτε να ανοίξετε το `Recovered.docx` στο Microsoft Word με σιγουριά—χωρίς περισσότερες προειδοποιήσεις “το αρχείο είναι κατεστραμμένο”.

---

## Συμπέρασμα

Σε αυτόν τον οδηγό δείξαμε πώς να **ανακτήσετε κατεστραμμένα docx** αρχεία χρησιμοποιώντας το Aspose.Words for Java. Καλύψαμε:

1. **Λειτουργία πλήρους ανάκτησης** (`RecoveryMode.RECOVER`) για να λάβετε όσο το δυνατόν περισσότερο περιεχόμενο.  
2. **Φόρτωση σε αυστηρή λειτουργία** (`RecoveryMode.STRICT`) για τον εντοπισμό μη ανακτήσιμων σφαλμάτων.  
3. Πρακτική επαλήθευση κειμένου και εικόνων, συν προαιρετικές ρυθμίσεις `LoadOptions`.  
4. Αποθήκευση του καθαρού αποτελέσματος για επεξεργασία σε επόμενα στάδια.

Με αυτό το μοτίβο μπορείτε να δημιουργήσετε αξιόπιστες ροές εισαγωγής εγγράφων, να αυτοματοποιήσετε μαζικές επισκευές, ή απλώς να σώσετε μια μοναδική σπασμένη αναφορά. Επόμενα βήματα; Δοκιμάστε να αντικαταστήσετε το `SaveFormat.PDF` για να δημιουργήσετε μια έκδοση PDF του ανακτημένου αρχείου, ή εξερευνήστε τις ρυθμίσεις **Aspose.Words recovery mode** για προσαρμοσμένο χειρισμό σφαλμάτων.

Έχετε ερωτήσεις ή ένα δύσκολο αρχείο που ακόμα δεν ανοίγει; Αφήστε ένα σχόλιο παρακάτω—καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

- [Ανάκτηση κατεστραμμένου docx – Πλήρης Οδηγός για Διόρθωση και Επεξεργασία Εγγράφων](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Πώς να φορτώσετε HTML και να αποθηκεύσετε ως DOCX χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Πώς να μετατρέψετε DOCX σε PNG σε Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}