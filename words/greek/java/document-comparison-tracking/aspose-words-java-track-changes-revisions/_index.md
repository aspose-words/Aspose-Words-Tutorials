---
date: '2026-11-02'
description: Μάθετε πώς να παρακολουθείτε αλλαγές σε έγγραφα Word χρησιμοποιώντας
  Aspose.Words for Java, καλύπτοντας document comparison, inline revision handling,
  licensing, και performance tips.
keywords:
- how to track changes
- track formatting changes
- document comparison aspose
- aspose.words license java
lastmod: '2026-11-02'
og_description: Μάθετε πώς να παρακολουθείτε αλλαγές σε έγγραφα Word χρησιμοποιώντας
  Aspose.Words for Java, συμπεριλαμβανομένων document comparison, inline revision
  handling, και licensing details.
og_image_alt: Guide showing how to track changes in Word documents with Aspose.Words
  Java
og_title: Πώς να παρακολουθείτε αλλαγές σε έγγραφα Word με Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-11-02'
  description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  headline: How to track changes in Word docs with Aspose.Words Java
  type: TechArticle
- description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  name: How to track changes in Word docs with Aspose.Words Java
  steps:
  - name: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
    text: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
  - name: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
    text: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
  - name: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
    text: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
  - name: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
    text: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
  - name: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
    text: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
  - name: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
    text: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
  type: HowTo
- questions:
  - answer: An inline node represents a run of text or a character‑level element inside
      a paragraph, such as a `Run` or a `Field`.
    question: What is an inline node in Aspose.Words?
  - answer: Call `document.startTrackRevisions()` on your `Document` instance before
      making any edits.
    question: How do I start tracking revisions with Aspose.Words Java?
  - answer: Yes, use `document.acceptAllRevisions()` or `document.rejectAllRevisions()`
      to apply the changes programmatically.
    question: Can I automate accepting or rejecting revisions in a document?
  - answer: It supports DOCX, PDF, HTML, ODT, RTF, EPUB, and more than 35 formats
      for both import and export.
    question: What types of documents does Aspose.Words support?
  - answer: Process the file section by section, use low‑memory load options, and
      leverage batch revision methods to keep CPU and RAM usage optimal.
    question: How do I handle large documents efficiently with Aspose.Words?
  type: FAQPage
tags:
- track changes
- Aspose.Words Java
- document revisions
- inline revisions
- Java document processing
title: Πώς να παρακολουθείτε αλλαγές σε έγγραφα Word με Aspose.Words Java
url: /el/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να παρακολουθείτε αλλαγές σε έγγραφα Word με Aspose.Words Java

Η συνεργασία σε σημαντικά έγγραφα συχνά σημαίνει ότι πρέπει να **παρακολουθείτε αλλαγές σε έγγραφα Word** ώστε κάθε επεξεργασία να είναι ορατή και ελεγχόμενη. Το Aspose.Words for Java σας παρέχει μια προγραμματιστική μηχανή «Παρακολούθηση αλλαγών» που λειτουργεί χωρίς το Microsoft Word, επιτρέποντάς σας να ξεκινάτε, να ερωτάτε, να αποδέχεστε ή να απορρίπτετε αναθεωρήσεις απευθείας από τον κώδικά σας. Σε αυτόν τον οδηγό θα ρυθμίσετε τη βιβλιοθήκη, θα εξερευνήσετε τη διαχείριση ενσωματωμένων αναθεωρήσεων και θα ανακαλύψετε τεχνικές φιλικές προς την απόδοση για μεγάλα αρχεία.

## Σύντομες απαντήσεις
- **Ποια βιβλιοθήκη επιτρέπει την παρακολούθηση αλλαγών σε έγγραφα Word;** Aspose.Words for Java  
- **Ποιος διαχειριστής εξαρτήσεων συνιστάται;** Maven ή Gradle (και τα δύο υποστηρίζονται)  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται άδεια για παραγωγική χρήση  
- **Μπορώ να επεξεργαστώ μεγάλα έγγραφα αποδοτικά;** Ναι – χρησιμοποιήστε επεξεργασία τμήμα‑ανά‑τμήμα και λειτουργίες παρτίδας  
- **Υπάρχει μέθοδος για να ξεκινήσετε την παρακολούθηση προγραμματιστικά;** `document.startTrackRevisions()` ξεκινά τη συνεδρία παρακολούθησης  

## Τι είναι η παρακολούθηση αλλαγών;
`how to track changes` αναφέρεται στη διαδικασία προγραμματιστικής ενεργοποίησης της ενσωματωμένης λειτουργίας παρακολούθησης αναθεωρήσεων του Word. Όταν είναι ενεργή, κάθε εισαγωγή, διαγραφή, επεξεργασία μορφοποίησης ή μετακίνηση καταγράφεται ως ξεχωριστό αντικείμενο αναθεώρησης. Αυτά τα αντικείμενα μπορούν αργότερα να απαριθμηθούν, να ελεγχθούν και είτε να γίνουν αποδεκτά ώστε η αλλαγή να γίνει μόνιμη, είτε να απορριφθούν, παρέχοντας πλήρη δυνατότητα ελέγχου των επεξεργασιών του εγγράφου.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για την παρακολούθηση αλλαγών;
Το Aspose.Words υποστηρίζει **πάνω από 35 μορφές εισόδου και εξόδου** — συμπεριλαμβανομένων των DOCX, PDF, HTML και ODT — και μπορεί να επεξεργαστεί **έγγραφα 500 σελίδων σε λιγότερο από 3 δευτερόλεπτα** σε τυπικό εξοπλισμό διακομιστή χωρίς την ανάγκη του Microsoft Word. Το API λειτουργεί σε Windows, Linux και macOS, καθιστώντας το ιδανικό για λύσεις στο cloud ή on‑premises που απαιτούν αξιόπιστη διαχείριση αναθεωρήσεων.

## Προαπαιτούμενα

- **Java Development Kit (JDK):** έκδοση 8 ή νεότερη.  
- **IDE:** IntelliJ IDEA, Eclipse ή NetBeans.  
- **Εργαλείο κατασκευής:** Maven ή Gradle για διαχείριση εξαρτήσεων.  
- Βασικές γνώσεις Java για την κατανόηση των αποσπασμάτων κώδικα.

## Ρύθμιση του Aspose.Words

### Ρύθμιση Maven

Προσθέστε την ακόλουθη εξάρτηση στο αρχείο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Ρύθμιση Gradle

Συμπεριλάβετε αυτή τη γραμμή στο αρχείο `build.gradle` σας:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Απόκτηση άδειας

Το Aspose προσφέρει δωρεάν δοκιμή για να δοκιμάσετε τις δυνατότητές του, επιτρέποντάς σας να αξιολογήσετε αν καλύπτει τις ανάγκες σας. Για να ξεκινήσετε:

1. **Δωρεάν δοκιμή:** Κατεβάστε τη βιβλιοθήκη από [Aspose Downloads](https://releases.aspose.com/words/java/) και χρησιμοποιήστε την με περιορισμούς αξιολόγησης.  
2. **Προσωρινή άδεια:** Αποκτήστε προσωρινή άδεια για εκτεταμένη χρήση χωρίς περιορισμούς αξιολόγησης επισκεπτόμενοι το [Temporary License](https://purchase.aspose.com/temporary-license/).  
3. **Αγορά άδειας:** Σκεφτείτε την αγορά εάν χρειάζεστε πλήρη πρόσβαση στις δυνατότητες του Aspose.Words ακολουθώντας τις οδηγίες στη σελίδα αγοράς τους.

#### Βασική αρχικοποίηση

`Document` είναι το κύριο αντικείμενο του Aspose.Words που αντιπροσωπεύει ένα αρχείο Word στη μνήμη. Για αρχικοποίηση, δημιουργήστε μια παρουσία του `Document` και ξεκινήστε να εργάζεστε με αυτήν:

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## Πώς να παρακολουθείτε αλλαγές σε έγγραφα Word χρησιμοποιώντας Aspose.Words Java
`document.startTrackRevisions()` ξεκινά μια συνεδρία παρακολούθησης αναθεωρήσεων στο έγγραφο. Φορτώστε ένα αρχείο Word, καλέστε `startTrackRevisions()` για να ξεκινήσετε τη συνεδρία παρακολούθησης, κάντε τις επιθυμητές επεξεργασίες και, τέλος, αποθηκεύστε το έγγραφο. Το API καταγράφει κάθε επεξεργασία ως αντικείμενο αναθεώρησης που μπορείτε αργότερα να απαριθμήσετε, να αποδεχτείτε ή να απορρίψετε. Αυτό το μοτίβο δύο βημάτων — ξεκινήστε την παρακολούθηση, εκτελέστε τις επεξεργασίες — καλύπτει εισαγωγές, διαγραφές, αλλαγές μορφοποίησης και μετακινήσεις.

## Οδηγός υλοποίησης

Σε αυτήν την ενότητα εξετάζουμε πώς να διαχειριστούμε διαφορετικούς τύπους αναθεωρήσεων χρησιμοποιώντας το Aspose.Words Java.

### Διαχείριση ενσωματωμένων αναθεωρήσεων

#### Επισκόπηση

Κατά την παρακολούθηση αλλαγών, οι ενσωματωμένες αναθεωρήσεις εμφανίζονται μέσα σε μια παράγραφο ως runs. Μπορούν να είναι εισαγωγές, διαγραφές, αλλαγές μορφοποίησης ή λειτουργίες μετακίνησης. Η κατανόηση κάθε τύπου σας επιτρέπει να δημιουργήσετε εργαλεία ανασκόπησης φιλικά προς το UI.

#### Υλοποίηση κώδικα

Το παρακάτω απόσπασμα κώδικα δείχνει πώς να ελέγξετε τον τύπο αναθεώρησης ενός ενσωματωμένου κόμβου:

```java
import com.aspose.words.Document;
import com.aspose.words.Paragraph;
import com.aspose.words.Run;
import com.aspose.words.Revision;
import org.testng.Assert;

public class RevisionHandler {
    public void handleRevisions() throws Exception {
        Document doc = new Document("Revision runs.docx");

        // Check the number of revisions
        Assert.assertEquals(6, doc.getRevisions().getCount());

        // Accessing a specific revision's parent node
        Run run = (Run) doc.getRevisions().get(0).getParentNode();

        Paragraph paragraph = run.getParentParagraph();
        com.aspose.words.RunCollection runs = paragraph.getRuns();

        Assert.assertEquals(runs.getCount(), 6);

        // Identifying different types of revisions
        Assert.assertTrue(runs.get(2).isInsertRevision());  // Insert revision
        Assert.assertTrue(runs.get(2).isFormatRevision());  // Format revision
        Assert.assertTrue(runs.get(4).isMoveFromRevision()); // Move from revision
        Assert.assertTrue(runs.get(1).isMoveToRevision());   // Move to revision
        Assert.assertTrue(runs.get(5).isDeleteRevision());   // Delete revision
    }
}
```

`RevisionType` είναι μια απαρίθμηση που κατηγοριοποιεί το είδος της αλλαγής — Insert, Delete, Format, MoveFrom ή MoveTo. Ελέγχοντας αυτήν την ιδιότητα μπορείτε να αποφασίσετε αν θα εμφανίσετε την αλλαγή στον χρήστη ή θα εφαρμόσετε αυτόματους κανόνες αποδοχής.

#### Επεξήγηση
- **Αναθεώρηση εισαγωγής:** Κείμενο που προστέθηκε ενώ η παρακολούθηση ήταν ενεργή.  
- **Αναθεώρηση μορφοποίησης:** Αλλαγές στη γραμματοσειρά, το χρώμα ή το στυλ που εφαρμόζονται σε υπάρχον κείμενο.  
- **Αναθεωρήσεις μετακίνησης από/προς:** Αντιπροσωπεύουν κείμενο που μετακινήθηκε εντός του εγγράφου· εμφανίζονται πάντα ως ζεύγος.  
- **Αναθεώρηση διαγραφής:** Κείμενο που αφαιρέθηκε αλλά διατηρείται μέχρι να το αποδεχτείτε ή να το απορρίψετε.

### Πρακτικές εφαρμογές

Πραγματικά σενάρια όπου η διαχείριση αναθεωρήσεων διαπρέπει:

1. **Συνεργατική επεξεργασία:** Οι ομάδες μπορούν να ελέγξουν και να εγκρίνουν τις αλλαγές πριν τη δημοσίευση ενός τελικού συμβολαίου.  
2. **Ανασκόπηση νομικών εγγράφων:** Οι δικηγόροι παρακολουθούν τροποποιήσεις σε ρήτρες, διασφαλίζοντας ότι κάθε αλλαγή είναι ελεγχόμενη.  
3. **Τεκμηρίωση λογισμικού:** Οι τεχνικοί συγγραφείς διαχειρίζονται ενημερώσεις σε αναφορές API διατηρώντας το ιστορικό εκδόσεων.

### Σκέψεις απόδοσης

`LoadOptions` ρυθμίζει τον τρόπο φόρτωσης ενός εγγράφου, συμπεριλαμβανομένων των ρυθμίσεων χρήσης μνήμης. Η επεξεργασία μεγάλων εγγράφων με πολλές αναθεωρήσεις μπορεί να είναι απαιτητική σε μνήμη. Ακολουθήστε τις καλύτερες πρακτικές:

- **Επεξεργασία τμήμα‑ανά‑τμήμα:** Φορτώστε και επεξεργαστείτε ένα τμήμα τη φορά για να διατηρήσετε τη χρήση μνήμης χαμηλή.  
- **Λειτουργίες σε παρτίδες:** Χρησιμοποιήστε `Document.acceptAllRevisions()` ή `Document.rejectAllRevisions()` σε ολόκληρα τμήματα αντί για μεμονωμένους κόμβους όταν είναι δυνατόν.  
- **Streaming API:** Για αρχεία μεγαλύτερα από 1 GB, χρησιμοποιήστε τη λειτουργία streaming του `LoadOptions` για να αποφύγετε τη φόρτωση ολόκληρου του αρχείου στη μνήμη.

## Συνηθισμένα προβλήματα και αντιμετώπιση

`document.startTrackRevisions()` ξεκινά την παρακολούθηση αναθεωρήσεων στην δεδομένη παρουσία Document.

- **Απουσία αναθεωρήσεων μετά την επεξεργασία:** Βεβαιωθείτε ότι κάλεσατε `document.startTrackRevisions()` *πριν* κάνετε οποιεσδήποτε αλλαγές· η έναρξη παρακολούθησης μετά τις επεξεργασίες δεν θα καταγράψει τις προηγούμενες τροποποιήσεις.  
- **Απρόσμενες αλλαγές μορφοποίησης:** Ορισμένες αλλαγές στυλ αναφέρονται ως `RevisionType.Format`. Εάν σας ενδιαφέρει μόνο το κείμενο, φιλτράρετε τις αναθεωρήσεις μορφοποίησης στη λογική απαρίθμησής σας.  
- **Μείωση απόδοσης σε μεγάλα έγγραφα:** Ενεργοποιήστε `LoadOptions.memoryUsage = LoadOptions.MemoryUsageMode.LowMemory` για να μειώσετε την κορυφαία κατανάλωση μνήμης.

## Συχνές ερωτήσεις

`Document.acceptAllRevisions()` εφαρμόζει κάθε εκκρεμή αναθεώρηση, καθιστώντας όλες τις αλλαγές μόνιμες. `Document.rejectAllRevisions()` απορρίπτει όλες τις εκκρεμείς αναθεωρήσεις, επαναφέροντας το έγγραφο στην αρχική του κατάσταση.

**Ε: Τι είναι ένας ενσωματωμένος κόμβος στο Aspose.Words;**  
Α: Ένας ενσωματωμένος κόμβος αντιπροσωπεύει μια ακολουθία κειμένου ή ένα στοιχείο επιπέδου χαρακτήρα μέσα σε μια παράγραφο, όπως ένα `Run` ή ένα `Field`.

**Ε: Πώς ξεκινάω την παρακολούθηση αναθεωρήσεων με το Aspose.Words Java;**  
Α: Καλέστε `document.startTrackRevisions()` στην παρουσία `Document` σας πριν κάνετε οποιεσδήποτε επεξεργασίες.

**Ε: Μπορώ να αυτοματοποιήσω την αποδοχή ή απόρριψη αναθεωρήσεων σε ένα έγγραφο;**  
Α: Ναι, χρησιμοποιήστε `document.acceptAllRevisions()` ή `document.rejectAllRevisions()` για να εφαρμόσετε τις αλλαγές προγραμματιστικά.

**Ε: Ποιους τύπους εγγράφων υποστηρίζει το Aspose.Words;**  
Α: Υποστηρίζει DOCX, PDF, HTML, ODT, RTF, EPUB και πάνω από 35 μορφές τόσο για εισαγωγή όσο και για εξαγωγή.

**Ε: Πώς να διαχειριστώ μεγάλα έγγραφα αποδοτικά με το Aspose.Words;**  
Α: Επεξεργαστείτε το αρχείο τμήμα‑ανά‑τμήμα, χρησιμοποιήστε επιλογές φόρτωσης χαμηλής μνήμης και αξιοποιήστε τις μεθόδους παρτίδας αναθεωρήσεων για να διατηρήσετε τη χρήση CPU και RAM σε βέλτιστο επίπεδο.

## Πόροι

- [Τεκμηρίωση Aspose.Words Java](https://reference.aspose.com/words/java/)  
- [Λήψη Aspose.Words for Java](https://releases.aspose.com/words/java/)  
- [Αγορά άδειας](https://purchase.aspose.com/buy)  
- [Δωρεάν δοκιμή](https://releases.aspose.com/words/java/)  
- [Προσωρινή άδεια](https://purchase.aspose.com/temporary-license/)  
- [Φόρουμ υποστήριξης Aspose](https://forum.aspose.com/c/words/10)

Ξεκινήστε το ταξίδι σας με το Aspose.Words Java σήμερα και αξιοποιήστε πλήρως τις δυνατότητες επεξεργασίας εγγράφων στις εφαρμογές σας!

---

**Last Updated:** 2026-11-02  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose

## Σχετικά μαθήματα

- [Υλοποίηση παρακολούθησης αλλαγών στο Aspose.Words for Java](/words/java/document-comparison-tracking/)
- [Μετατροπή Word σε PDF με το Aspose.Words for Java Document Conversion API](/words/java/document-converting/)
- [Aspose Words Loadoptions Ανάκτηση Κατεστραμμένων Εγγράφων Word σε Java](/words/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}