---
category: general
date: 2026-07-03
description: Ορίστε τη λειτουργία ανάκτησης για την αποκατάσταση κατεστραμμένων αρχείων
  Word σε Java και εμφανίστε τον αριθμό σελίδων μετά τη φόρτωση. Μάθετε βήμα‑βήμα
  με το Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: el
og_description: Ορίστε τη λειτουργία ανάκτησης στο Aspose.Words for Java για να ανακτήσετε
  κατεστραμμένα αρχεία Word και να εμφανίσετε τον αριθμό των σελίδων. Ακολουθήστε
  το πλήρες παράδειγμα τώρα.
og_title: Ορισμός λειτουργίας ανάκτησης στο Aspose.Words για Java – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Ορισμός λειτουργίας ανάκτησης στο Aspose.Words for Java – Πλήρης οδηγός
url: /el/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός Λειτουργίας Ανάκτησης στο Aspose.Words για Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **ορίσετε τη λειτουργία ανάκτησης** κατά τη φόρτωση ενός κατεστραμμένου `.docx` αρχείου με το Aspose.Words; Δεν είστε οι μόνοι που σκεπάζεστε τα κατεστραμμένα έγγραφα Word που αρνούνται να ανοίξουν. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από αυτό—πώς να ρυθμίσετε τη βιβλιοθήκη ώστε να **ανακτά κατεστραμμένα Word** αρχεία και στη συνέχεια **εμφανίζει τον αριθμό σελίδων** του περιεχομένου που φορτώθηκε επιτυχώς.

Θα καλύψουμε τα πάντα, από τη μικρή ρύθμιση `LoadOptions` μέχρι το τελικό `System.out.println` που σας λέει πόσες σελίδες επέζησαν της αποστολής διάσωσης. Χωρίς περιττές πληροφορίες, μόνο μια πρακτική, έτοιμη για αντιγραφή‑επικόλληση λύση που λειτουργεί με την πιο πρόσφατη έκδοση Aspose.Words 23.12.

## Τι Θα Μάθετε

- Γιατί η λειτουργία ανάκτησης είναι σημαντική και ποιες επιλογές προσφέρει το Aspose.Words.  
- Πώς να **ορίσετε τη λειτουργία ανάκτησης** προγραμματιστικά χρησιμοποιώντας Java.  
- Τρόποι για **εμφάνιση του αριθμού σελίδων** μετά τη φόρτωση του εγγράφου, επιβεβαιώνοντας ότι η ανάκτηση πέτυχε.  
- Συνηθισμένα προβλήματα όταν δουλεύετε με κατεστραμμένα Word αρχεία και πώς να τα αποφύγετε.  

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

1. Ένα έγκυρο license του Aspose.Words for Java (ή ένα προσωρινό κλειδί αξιολόγησης).  
2. Java 17 ή νεότερη εγκατεστημένη στον υπολογιστή σας.  
3. Το κατεστραμμένο αρχείο `Corrupted.docx` που θέλετε να δοκιμάσετε.  

Τα έχετε; Τέλεια—ας βουτήξουμε.

> **Pro tip:** Ακόμη και αν χρησιμοποιείτε δοκιμαστική έκδοση, οι λειτουργίες ανάκτησης λειτουργούν ακριβώς όπως σε μια αδειοδοτημένη έκδοση.

---

## ## Πώς να Ορίσετε τη Λειτουργία Ανάκτησης με Aspose.Words για Java

Η καρδιά της λύσης βρίσκεται στην κλάση `LoadOptions`. Από προεπιλογή το Aspose.Words προσπαθεί να φορτώσει ένα έγγραφο, αλλά όταν το αρχείο είναι σοβαρά κατεστραμμένο πρέπει να του πείτε *πώς* να συμπεριφερθεί. Εδώ μπαίνει σε παιχνίδι η **set recovery mode**.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Γιατί `RecoveryMode.PARSE`;

- **PARSE** – Το Aspose.Words αναλύει όσα τμήματα μπορεί να καταλάβει, συνθέτοντας ένα μερικώς λειτουργικό έγγραφο. Ιδανικό όταν χρειάζεστε *οποιοδήποτε* περιεχόμενο από ένα σπασμένο αρχείο.  
- **SKIP** – Η βιβλιοθήκη παραλείπει εντελώς τα κατεστραμμένα τμήματα, κάτι που μπορεί να είναι γρηγορότερο αλλά ενδέχεται να απορρίψει περισσότερα δεδομένα.  

Στις περισσότερες πραγματικές περιπτώσεις, το **PARSE** είναι η ασφαλέστερη επιλογή επειδή μεγιστοποιεί την ποσότητα του ανακτήσιμου κειμένου, εικόνων και μορφοποίησης.

---

## ## Εμφάνιση Αριθμού Σελίδων μετά την Ανάκτηση

Μόλις φορτωθεί το έγγραφο, το επόμενο λογικό βήμα είναι η επαλήθευση της επιτυχίας της λειτουργίας. Το πιο απλό, αλλά και πιο ενημερωτικό, μέτρο είναι ο αριθμός σελίδων. Η μέθοδος `Document.getPageCount()` κάνει ακριβώς αυτό.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Αν το αρχείο ήταν εντελώς μη αναγνώσιμο, το Aspose.Words θα ρίξει εξαίρεση *πριν* φτάσετε σε αυτή τη γραμμή. Όταν δείτε αριθμό σελίδων `0` ή πολύ μικρό αριθμό, συνήθως σημαίνει ότι η λειτουργία ανάκτησης έπρεπε να απορρίψει μεγάλα τμήματα του αρχικού αρχείου.

**Αναμενόμενη έξοδος (παράδειγμα):**

```
Document loaded, page count = 12
```

Αυτό σας λέει ότι η βιβλιοθήκη κατάφερε να ανασυνθέσει δώδεκα σελίδες από την κατεστραμμένη πηγή—αρκετά εντυπωσιακό για ένα σπασμένο `.docx`.

---

## ## Ακραίες Περιπτώσεις & Συνηθισμένα Πιθανά Σφάλματα

### 1️⃣ Κατεστραμμένα Τμήματα Κεφαλίδας/Υποσέλιδου
Μερικές φορές μόνο το κύριο σώμα αναλύεται ενώ οι κεφαλίδες και τα υποσέλιδα χάνονται. Αν βασίζεστε σε αυτά για branding, ίσως χρειαστεί να τα επανα‑εισάγετε μετά την ανάκτηση.

### 2️⃣ Εικόνες που Δεν Φορτώνονται
Οι ενσωματωμένες εικόνες συχνά αφαιρούνται όταν το zip container (η υποκείμενη μορφή `.docx`) είναι κατεστραμμένο. Μπορείτε να το εντοπίσετε διατρέχοντας το `doc.getSections()` και ελέγχοντας το `Section.getBody().getParagraphs()` για αντικείμενα `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Αν ο βρόχος δεν εκτυπώσει τίποτα, η λειτουργία ανάκτησης πιθανότατα παρέλειψε τις εικόνες.

### 3️⃣ Μεγάλα Έγγραφα και Μνήμη
Η ανάκτηση ενός 200‑σελίδων κατεστραμμένου αρχείου μπορεί να απαιτεί πολύ μνήμη. Σκεφτείτε να αυξήσετε το μέγεθος της στοίβας JVM (`-Xmx2g`) όταν προβλέπετε τεράστια έγγραφα.

### 4️⃣ Περιορισμοί Άδειας
Η δοκιμαστική έκδοση περιορίζει ορισμένες λειτουργίες, αλλά η **ανάκτηση** είναι πλήρως λειτουργική. Ωστόσο, ο εκτυπωμένος αριθμός σελίδων μπορεί να περιορίζεται σε λίγες σελίδες στην έκδοση trial. Πάντα δοκιμάζετε με αδειοδοτημένη έκδοση για παραγωγή.

---

## ## Πλήρες Παράδειγμα Από‑Αρχή‑Προς‑Τέλος (Εκτελέσιμο)

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε Maven ή Gradle project. Περιλαμβάνει τη δήλωση εξάρτησης που απαιτείται για το Aspose.Words 23.12.

### Απόσπασμα Maven `pom.xml`

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Αρχείο πηγαίου κώδικα Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Τι κάνει αυτό:**

1. **Ορίζει τη λειτουργία ανάκτησης** – η καρδιά του tutorial μας.  
2. Φορτώνει το κατεστραμμένο αρχείο χρησιμοποιώντας τις ρυθμισμένες `LoadOptions`.  
3. **Εμφανίζει τον αριθμό σελίδων**, δίνοντάς σας άμεση ανάδραση.  
4. Αποθηκεύει μια καθαρή έκδοση (`Recovered.docx`) ώστε να μπορείτε να την ανοίξετε αργότερα στο Word.

Τρέξτε το πρόγραμμα με:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Θα πρέπει να δείτε τον αριθμό σελίδων να εκτυπώνεται στην κονσόλα, επιβεβαιώνοντας ότι η ανάκτηση πέτυχε.

---

## ## Οπτική Επισκόπηση (Εικόνα)

![set recovery mode flow diagram](https://example.com/images/recovery-mode-flow.png "Diagram illustrating how set recovery mode works in Aspose.Words for Java")

*Το κείμενο alt περιλαμβάνει τη βασική λέξη‑κλειδί **set recovery mode** για να ικανοποιήσει το SEO.*

---

## ## Συχνές Ερωτήσεις

**Ε: Τι γίνεται αν το `RecoveryMode.PARSE` εξακολουθεί να ρίχνει εξαίρεση;**  
Α: Συνήθως σημαίνει ότι το αρχείο είναι πέρα από τη δυνατότητα αποκατάστασης—ίσως το zip container είναι εντελώς κατεστραμμένο. Σε τέτοιες περιπτώσεις, ίσως χρειαστεί ένα εξωτερικό εργαλείο επισκευής πριν το περάσετε στο Aspose.Words.

**Ε: Μπορώ να συνδυάσω το `RecoveryMode.PARSE` με προσαρμοσμένα callbacks φόρτωσης εγγράφου;**  
Α: Απόλυτα. Υλοποιήστε το `IWarningCallback` για να συλλάβετε τυχόν προειδοποιήσεις που εκδίδει το Aspose.Words κατά τη διαδικασία ανάλυσης. Αυτό σας δίνει εικόνα για τα τμήματα που παραλείφθηκαν.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Ε: Η αλλαγή της λειτουργίας ανάκτησης επηρεάζει το αρχικό αρχείο;**  
Α: Όχι. Το Aspose.Words εργάζεται πάνω σε ένα αντίγραφο στη μνήμη· το πηγαίο αρχείο παραμένει άθικτο εκτός αν το αποθηκεύσετε ρητά με `doc.save()`.

---

## ## Συμπέρασμα

Καλύψαμε πώς να **ορίσετε τη λειτουργία ανάκτησης** στο Aspose.Words για Java, γιατί το `PARSE` είναι γενικά η καλύτερη επιλογή για την αποκατάσταση ενός σπασμένου εγγράφου, και πώς να **εμφανίσετε τον αριθμό σελίδων** για να επαληθεύσετε το αποτέλεσμα. Ακολουθώντας το πλήρες παράδειγμα, έχετε τώρα μια έτοιμη προς εκτέλεση λύση που μπορεί να **ανακτήσει κατεστραμμένα Word** αρχεία και να σας δώσει άμεση ανάδραση για την επιτυχία της διαδικασίας.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αλλάξετε σε `RecoveryMode.SKIP` για να δείτε τη διαφορά, πειραματιστείτε με μεγάλα αρχεία πολλαπλών τμημάτων, ή ενσωματώστε τη λογική σε μια web υπηρεσία που επισκευάζει αυτόματα έγγραφα που ανεβάζουν οι χρήστες. Το ίδιο μοτίβο λειτουργεί και για PDFs (χρησιμοποιώντας Aspose.PDF) και ακόμη για ανάκτηση απλού κειμένου με άλλες βιβλιοθήκες—απλώς θυμηθείτε το βασικό ιδέα: ρυθμίστε τον φορτωτή, προσπαθήστε την ανάκτηση, μετά επικυρώστε με ένα απλό μέτρο όπως ο αριθμός σελίδων.

Καλή προγραμματιστική δουλειά, και να παραμένουν τα έγγραφά σας ακατάσπαστα!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}