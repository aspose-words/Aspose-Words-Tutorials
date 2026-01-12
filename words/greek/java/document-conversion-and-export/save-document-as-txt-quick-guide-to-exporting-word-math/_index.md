---
category: general
date: 2026-01-11
description: Αποθηκεύστε το έγγραφο ως txt με λίγες μόνο γραμμές κώδικα. Μάθετε πώς
  να μετατρέψετε docx σε txt και να εξάγετε μαθηματικές εξισώσεις χωρίς κόπο.
draft: false
keywords:
- save document as txt
- convert docx to txt
- how to convert docx
- how to export math
- how to save txt
language: el
og_description: Αποθηκεύστε το έγγραφο ως txt σε λίγα βήματα. Αυτό το σεμινάριο δείχνει
  πώς να μετατρέψετε το docx σε txt και να εξάγετε μαθηματικό περιεχόμενο με σαφή
  παραδείγματα κώδικα.
og_title: Αποθήκευση εγγράφου ως TXT – Σύντομος οδηγός εξαγωγής μαθηματικών του Word
tags:
- Aspose.Words
- Java
- Document Conversion
title: Αποθήκευση εγγράφου ως TXT – Σύντομος οδηγός εξαγωγής μαθηματικών του Word
url: /el/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως TXT – Σύντομος Οδηγός για Εξαγωγή Μαθηματικών στο Word

Κάποτε χρειάστηκε να **αποθηκεύσετε το έγγραφο ως txt** αλλά δεν ήξερες πώς να διατηρήσεις ανέπαφα τις μαθηματικές εξισώσεις; Δεν είσαι μόνος. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν προσπαθούν να μετατρέψουν ένα πλούσιο αρχείο Word σε απλό κείμενο, ειδικά όταν αυτά τα αρχεία περιέχουν Office Math.  

Σε αυτό το tutorial θα μάθεις ακριβώς **πώς να μετατρέψεις docx σε txt** διατηρώντας (ή σκόπιμα απλουστεύοντας) το μαθηματικό περιεχόμενο. Θα περάσουμε από τον κώδικα, θα εξηγήσουμε γιατί κάθε ρύθμιση είναι σημαντική και θα δείξουμε ακόμη και πώς να χειριστείς ειδικές περιπτώσεις όπως κρυφές εξισώσεις ή προσαρμοσμένες γραμματοσειρές. Στο τέλος θα μπορείς να ενσωματώσεις μια μέθοδο στο πρόγραμμά σου και να εξάγεις οποιοδήποτε `.docx` σε ένα καθαρό αρχείο `.txt`.

## Τι Θα Μάθεις

* Τη διαφορά μεταξύ εξαγωγής απλού κειμένου και εξαγωγής με γνώση μαθηματικών.  
* Πώς να ρυθμίσεις το `TxtSaveOptions` για να ελέγξεις το `OfficeMathExportMode`.  
* Ένα πλήρες, εκτελέσιμο παράδειγμα Java που αποθηκεύει ένα έγγραφο Word ως txt.  
* Συμβουλές για την αντιμετώπιση κοινών προβλημάτων (ελλιπείς σύμβολα, προβλήματα κωδικοποίησης κ.λπ.).  

**Προαπαιτούμενα** – Χρειάζεσαι τη βιβλιοθήκη Aspose.Words for Java (ή το αντίστοιχο πακέτο .NET) και ένα βασικό περιβάλλον ανάπτυξης Java. Δεν απαιτούνται άλλα εξωτερικά εργαλεία.

---

## Αποθήκευση Εγγράφου ως TXT – Βήμα‑βήμα

Παρακάτω βρίσκεται η καρδιά της λύσης. Κάθε βήμα είναι χωρισμένο σε δική του ενότητα ώστε να μπορείς να επιλέξεις ό,τι χρειάζεσαι.

### Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου

Πρώτα ανοίγουμε το αρχείο `.docx` που θέλουμε να μετατρέψουμε. Η κλάση `Document` διαχειρίζεται τόσο `.docx` όσο και παλαιότερα `.doc` φορμά, οπότε δεν χρειάζεται να ανησυχείς για συμβατότητα.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;

// Load the Word file from disk
LoadOptions loadOpts = new LoadOptions();
loadOpts.setLoadFormat(com.aspose.words.LoadFormat.DOCX); // optional, helps with auto‑detection
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOpts);
```

*Γιατί είναι σημαντικό:* Η φόρτωση με ρητές επιλογές μπορεί να αποτρέψει σιωπηλές αποτυχίες όταν το αρχείο περιέχει πολύπλοκο περιεχόμενο όπως ενσωματωμένα αντικείμενα OLE. Επίσης, διασφαλίζει ότι η βιβλιοθήκη γνωρίζει ότι δουλεύεις με σύγχρονο DOCX.

### Βήμα 2: Ρύθμιση Επιλογών Αποθήκευσης TXT για Εξαγωγή Μαθηματικών

Η ουσία του «πώς να εξάγεις μαθηματικά» βρίσκεται στο enum `OfficeMathExportMode`. Έχεις τρεις επιλογές:

| Mode | Αποτέλεσμα |
|------|------------|
| **TXT** | Τα μαθηματικά μετατρέπονται σε γραμμικό μορφότυπο απλού κειμένου (π.χ., `a+b=c`). |
| **IMAGE** | Κάθε εξίσωση γίνεται εικόνα PNG ενσωματωμένη στο κείμενο (σπάνια χρήσιμη για καθαρό txt). |
| **MATHML** | Εξάγει markup MathML – μη αναγνώσιμο σε κανονικό πρόγραμμα προβολής txt. |

Για μια πραγματική εμπειρία **αποθήκευσης εγγράφου ως txt** συνήθως επιλέγουμε `TXT`.

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Create save options and set the math export mode
TxtSaveOptions txtOpts = new TxtSaveOptions();
txtOpts.setOfficeMathExportMode(OfficeMathExportMode.TXT);
```

*Γιατί είναι σημαντικό:* Αν παραλείψεις αυτό το βήμα, η βιβλιοθήκη προεπιλέγει το `OfficeMathExportMode.IMAGE`, αφήνοντάς σου ακατανόητους δείκτες όπως `[Image: Equation]`. Ορίζοντας το σε `TXT` απλουστεύει τις εξισώσεις σε μια γραμμική, αναζητήσιμη συμβολοσειρά.

### Βήμα 3: Αποθήκευση του Εγγράφου ως Αρχείο TXT

Τώρα γράφουμε το αποτέλεσμα. Η μέθοδος `save` δέχεται τη διαδρομή προορισμού και τις επιλογές που μόλις ρυθμίσαμε.

```java
import com.aspose.words.SaveFormat;

// Save as plain text
doc.save("YOUR_DIRECTORY/MathSample.txt", txtOpts);
System.out.println("Document successfully saved as txt!");
```

Αυτό είναι—τρεις σύντομα βήματα, και έχεις μια αναπαράσταση απλού κειμένου του αρχείου Word, με γραμμικές μαθηματικές εκφράσεις.

### Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας τα παραπάνω, εδώ είναι μια έτοιμη‑για‑εκτέλεση κλάση. Μην διστάσεις να την αντιγράψεις‑και‑επικολλήσεις στο IDE σου.

```java
import com.aspose.words.*;

public class DocxToTxtExporter {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            LoadOptions loadOpts = new LoadOptions();
            loadOpts.setLoadFormat(LoadFormat.DOCX);
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOpts);

            // 2️⃣ Configure TXT options – this is how to export math as plain text
            TxtSaveOptions txtOpts = new TxtSaveOptions();
            txtOpts.setOfficeMathExportMode(OfficeMathExportMode.TXT);

            // 3️⃣ Save the file
            doc.save("YOUR_DIRECTORY/MathSample.txt", txtOpts);
            System.out.println("✅ Save document as txt completed successfully.");
        } catch (Exception e) {
            System.err.println("❌ An error occurred while converting the file:");
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** – Μετά την εκτέλεση, άνοιξε το `MathSample.txt` σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δεις κάτι σαν:

```
This is a sample paragraph.
Equation: a + b = c
Another line of text.
```

Παρατήρησε πώς η εξίσωση εμφανίζεται ως γραμμική έκφραση (`a + b = c`). Αυτό είναι το αποτέλεσμα του **πώς να εξάγεις μαθηματικά** χρησιμοποιώντας τη λειτουργία `TXT`.

---

## Πώς να Μετατρέψεις DOCX σε TXT – Συνηθισμένες Παραλλαγές

Αν και ο κώδικας παραπάνω καλύπτει το πιο τυπικό σενάριο, τα πραγματικά έργα συχνά απαιτούν λίγη επιπλέον διαχείριση. Ακολουθούν μερικές περιπτώσεις «τι θα γίνει αν…» που μπορεί να συναντήσεις.

### Μετατροπή Πολλαπλών Αρχείων σε Batch

Αν έχεις έναν φάκελο γεμάτο έγγραφα Word, τυλίγεις τη λογική μετατροπής σε βρόχο:

```java
File folder = new File("YOUR_DIRECTORY");
for (File file : folder.listFiles((dir, name) -> name.endsWith(".docx"))) {
    Document d = new Document(file.getPath());
    TxtSaveOptions opts = new TxtSaveOptions();
    opts.setOfficeMathExportMode(OfficeMathExportMode.TXT);
    String outPath = file.getPath().replace(".docx", ".txt");
    d.save(outPath, opts);
}
```

**Συμβουλή:** Χρησιμοποίησε το `java.nio.file.Files` για καλύτερο χειρισμό σφαλμάτων και απόδοση όταν δουλεύεις με χιλιάδες αρχεία.

### Διαχείριση Προβλημάτων Κωδικοποίησης

Τα αρχεία απλού κειμένου προεπιλεγμένα είναι UTF‑8 στην Aspose.Words, αλλά παλαιότερα συστήματα μπορεί να περιμένουν ANSI ή ISO‑8859‑1. Μπορείς να εξαναγκάσεις κωδικοποίηση ως εξής:

```java
txtOpts.setEncoding(java.nio.charset.StandardCharsets.ISO_8859_1);
```

### Διατήρηση Αλλαγών Γραμμής

Μερικές φορές η αυτόματη λογική αλλαγής γραμμής συμπτύσσει μεγάλες παραγράφους. Για να διατηρήσεις τις αρχικές αλλαγές γραμμής του Word, ενεργοποίησε:

```java
txtOpts.setPreserveTableLayout(true); // keeps tables as plain‑text grids
txtOpts.setExportHeadersFootersMode(TxtSaveOptions.ExportHeadersFootersMode.CUSTOM);
```

Αυτές οι επιπλέον σημαίες είναι προαιρετικές, αλλά μπορούν να κάνουν μεγάλη διαφορά όταν **πώς να μετατρέψεις docx** για επεξεργαστικά pipelines.

---

## Συχνές Ερωτήσεις

**Ε: Η μετατροπή θα αφαιρέσει τις εικόνες;**  
Α: Ναι. Επειδή αποθηκεύουμε σε απλό κείμενο, οι εικόνες παραλείπονται εκ προθέσεως. Αν τις χρειάζεσαι, σκέψου εξαγωγή σε HTML.

**Ε: Τι γίνεται αν το έγγραφό μου περιέχει πολύπλοκο MathML;**  
Α: Η λειτουργία `TXT` θα το απλουστεύσει σε μια γραμμική συμβολοσειρά, κάτι που μπορεί να χάσει δομικές λεπτομέρειες. Για πλήρη πιστότητα, χρησιμοποίησε `OfficeMathExportMode.MATHML` και μετά επεξεργάσου το MathML με μετασχηματιστή XSLT.

**Ε: Μπορώ να το τρέξω σε Android;**  
Α: Η Aspose.Words for Android υποστηρίζει το ίδιο API, οπότε ο ίδιος κώδικας λειτουργεί—απλώς βεβαιώσου ότι η βιβλιοθήκη περιλαμβάνεται στο APK.

**Ε: Πώς εντοπίζω σιωπηλή αποτυχία όπου το αρχείο εξόδου είναι κενό;**  
Α: Έλεγξε την κονσόλα για εξαιρέσεις, βεβαιώσου ότι το πηγαίο `.docx` περιέχει ορατό περιεχόμενο, και ότι η διαδρομή εξόδου είναι εγγράψιμη. Επίσης, βεβαιώσου ότι δεν αντικαθιστάς κατά λάθος το αρχείο με έναν μηδενικού μεγέθους placeholder αλλού στον κώδικά σου.

---

## Εικονογραφική Παράσταση

Παρακάτω υπάρχει ένα σχήμα του pipeline μετατροπής. Το alt text περιλαμβάνει τη βασική λέξη‑κλειδί για SEO.

![Save document as txt conversion flow diagram – shows loading DOCX, setting TXT options, and writing to TXT file](/images/save-doc-as-txt-flow.png)

---

## Συμπέρασμα

Τώρα ξέρεις **πώς να αποθηκεύσεις έγγραφο ως txt** χρησιμοποιώντας την Aspose.Words, και είδες διάφορους τρόπους **να μετατρέψεις docx σε txt** ελέγχοντας τη συμπεριφορά εξαγωγής μαθηματικών. Το βασικό μοτίβο—φόρτωση, ρύθμιση `TxtSaveOptions`, αποθήκευση—καλύπτει το 95 % των πραγματικών σεναρίων.  

Αν θέλεις να εμβαθύνεις, δοκίμασε να αλλάξεις το `OfficeMathExportMode.TXT` σε `MATHML` και επεξεργάσου το αποτέλεσμα με έναν parser MathML. Ή πειραματίσου με τη σημαία `PreserveTableLayout` για να κρατήσεις τα δεδομένα πινάκων αναγνώσιμα. Όπως και να έχει, η βάση που μόλις δημιούργησες θα σε εξυπηρετήσει σε οποιεσδήποτε μελλοντικές εργασίες επεξεργασίας εγγράφων.

---

### Επόμενα Βήματα & Σχετικά Θέματα

* **Πώς να εξάγεις μαθηματικά** σε άλλες μορφές (HTML, PDF) – απλώς άλλαξε το `SaveFormat`.  
* **Πώς να μετατρέψεις docx** από τη γραμμή εντολών χρησιμοποιώντας το Aspose.Words for Java CLI.  
* **Πώς να αποθηκεύσεις txt** με προσαρμοσμένες συμβάσεις λήξης γραμμής για Windows vs. Unix.  

Μη διστάσεις να αφήσεις σχόλιο αν αντιμετωπίσεις πρόβλημα, ή να μοιραστείς τις δικές σου συμβουλές για τη διαχείριση δύσκολων εξισώσεων. Καλός κώδικας!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}