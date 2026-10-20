---
category: general
date: 2026-05-26
description: Εξαγωγή docx σε txt χρησιμοποιώντας Java και Aspose.Words. Μάθετε πώς
  να μετατρέπετε docx σε κείμενο, να διατηρείτε το Unicode και να εξάγετε το Word
  ως txt σε λίγα βήματα.
draft: false
keywords:
- export docx to txt
- convert docx to text
- convert word to text
- plain text unicode
- export word as txt
language: el
og_description: Εξαγωγή docx σε txt σε Java. Αυτό το σεμινάριο δείχνει πώς να μετατρέψετε
  το docx σε κείμενο, να διατηρήσετε το απλό κείμενο Unicode και να εξάγετε το Word
  ως txt αποδοτικά.
og_title: Εξαγωγή docx σε txt με Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Export docx to txt using Java and Aspose.Words. Learn how to convert
    docx to text, preserve Unicode, and export word as txt in a few steps.
  headline: Export docx to txt with Java – Complete Programming Guide
  type: TechArticle
- description: Export docx to txt using Java and Aspose.Words. Learn how to convert
    docx to text, preserve Unicode, and export word as txt in a few steps.
  name: Export docx to txt with Java – Complete Programming Guide
  steps:
  - name: '**Checksum comparison** – compute a SHA‑256 hash of the `.txt` file before
      and after a round‑trip conversion (txt → docx → txt) to ensure stability.'
    text: '**Checksum comparison** – compute a SHA‑256 hash of the `.txt` file before
      and after a round‑trip conversion (txt → docx → txt) to ensure stability.'
  - name: "**Search for Unicode markers** – use `grep` or IDE find‑in‑file to locate
      characters like “\U0001F60A”."
    text: "**Search for Unicode markers** – use `grep` or IDE find‑in‑file to locate
      characters like “\U0001F60A”."
  - name: '**Open in multiple editors** – some old Windows Notepad versions still
      misinterpret UTF‑8 without BOM; opening the file in VS Code confirms proper
      encoding.'
    text: '**Open in multiple editors** – some old Windows Notepad versions still
      misinterpret UTF‑8 without BOM; opening the file in VS Code confirms proper
      encoding.'
  type: HowTo
tags:
- Java
- Aspose.Words
- File Conversion
title: Εξαγωγή docx σε txt με Java – Πλήρης Οδηγός Προγραμματισμού
url: /el/java/document-conversion-and-export/export-docx-to-txt-with-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή docx σε txt με Java – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **εξάγετε docx σε txt** αλλά ανησυχείτε για την απώλεια ειδικών χαρακτήρων; Δεν είστε μόνοι. Όταν μετατρέπετε έγγραφα Word σε αρχεία plain‑text, τα σύμβολα Unicode, οι πίνακες και ακόμη και η απλή μορφοποίηση μπορούν να εξαφανιστούν σαν μαγεία.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα μια αξιόπιστη μέθοδο για **εξαγωγή docx σε txt** χρησιμοποιώντας το Aspose.Words for Java, διατηρώντας κάθε χαρακτήρα Unicode και κρατώντας τις διατάξεις των πινάκων αναγνώσιμες. Στο τέλος θα γνωρίζετε επίσης πώς να **μετατρέψετε docx σε κείμενο**, **μετατρέψετε word σε κείμενο**, και ακόμη **εξάγετε word ως txt** χωρίς προβλήματα.

## Τι Καλύπτει Αυτός ο Οδηγός

* Ρύθμιση του Aspose.Words σε ένα έργο Java  
* Φόρτωση αρχείου DOCX και προετοιμασία του για έξοδο plain‑text  
* Διαμόρφωση υποστήριξης **plain text unicode** μέσω του `TxtSaveOptions`  
* Προαιρετικές τεχνικές για να διατηρηθούν οι πίνακες ευανάγνωστοι στο παραγόμενο αρχείο `.txt`  
* Αποθήκευση του αρχείου και επαλήθευση του αποτελέσματος  

Χωρίς εξωτερικά σκριπτάκια, χωρίς μυστηριώδη εργαλεία γραμμής εντολών—μόνο καθαρός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.  

> **Γιατί να νοιάζεστε;** Τα αρχεία plain‑text είναι ελαφριά, φιλικά στο version‑control και ιδανικά για ευρετηρίαση ή επεξεργασία σε downstream pipelines. Αν έχετε προσπαθήσει ποτέ να `cat` ένα αρχείο Word και έχετε λάβει ακατανόητο κείμενο, αυτός ο οδηγός λύνει το πρόβλημα.

## Export docx to txt – Επισκόπηση

Πριν βουτήξουμε στον κώδικα, ας ξεκαθαρίσουμε την ορολογία. **Εξαγωγή docx σε txt** σημαίνει τη λήψη ενός πακέτου Microsoft Word `.docx` και την εγγραφή του κειμενικού του περιεχομένου σε ένα απλό αρχείο `.txt`. Σε αντίθεση με μια μετατροπή PDF, η εξαγωγή κειμένου αφαιρεί το στυλ αλλά μπορεί να διατηρήσει αλλαγές γραμμής, δείκτες παραγράφων και—αν το ρυθμίσετε σωστά—χαρακτήρες Unicode όπως emojis, τονισμένα γράμματα ή ασιατικά σενάρια.

Το Aspose.Words το κάνει αυτό αβίαστο επειδή αφαιρεί την πολυπλοκότητα του φορμάτ Word και προσφέρει μια κλάση `TxtSaveOptions` όπου μπορείτε να καθορίσετε την κωδικοποίηση, τη διαχείριση πινάκων και άλλα.

### Προαπαιτούμενα

* Java 11 ή νεότερη (το API λειτουργεί με Java 8+, αλλά θα υποθέσουμε ένα πρόσφατο JDK)  
* Aspose.Words for Java JAR (διαθέσιμο από το Maven Central)  
* Ένα δείγμα αρχείου `unicode.docx` που περιέχει διάφορους χαρακτήρες Unicode—π.χ. “こんにちは”, “😊”, και έναν απλό πίνακα  

Αν τα έχετε αυτά, ας ξεκινήσουμε.

## Βήμα 1: Φόρτωση του Αρχείου DOCX (Μετατροπή docx σε κείμενο)

Το πρώτο πράγμα που πρέπει να κάνετε είναι να διαβάσετε το πηγαίο έγγραφο στη μνήμη. Εδώ ξεκινά επίσημα η διαδικασία **μετατροπής docx σε κείμενο**.

```java
import com.aspose.words.*;

public class ExportDocxToTxt {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX. Replace the path with your actual file location.
        Document doc = new Document("YOUR_DIRECTORY/unicode.docx");
```

*Γιατί είναι σημαντικό:* `Document` είναι η αναπαράσταση του Aspose.Words για ένα αρχείο Word. Φορτώνοντάς το, αποκτάτε πρόσβαση σε όλες τις παραγράφους, τους πίνακες και ακόμη και στα κρυφά στοιχεία. Αν το αρχείο δεν βρεθεί, το Aspose ρίχνει ένα σαφές `FileNotFoundException`, ώστε να ξέρετε αμέσως τι πήγε στραβά.

## Βήμα 2: Διαμόρφωση TxtSaveOptions για Unicode (Plain text unicode)

Τα αρχεία plain‑text είναι απλώς ροές byte, επομένως πρέπει να πείτε στη Java ποιο σύνολο χαρακτήρων να χρησιμοποιήσει. Το UTF‑8 είναι το de‑facto πρότυπο για **plain text unicode** επειδή μπορεί να κωδικοποιήσει κάθε κωδικό σημείο Unicode.

```java
        // Create TXT save options and enforce UTF‑8 encoding.
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        // This guarantees that every Unicode character survives the conversion.
        saveOptions.setEncoding(java.nio.charset.StandardCharsets.UTF_8);
```

> **Συμβουλή:** Αν παραλείψετε την κλήση `setEncoding`, το Aspose χρησιμοποιεί το προεπιλεγμένο charset της πλατφόρμας, το οποίο σε πολλά Windows μηχανήματα είναι Windows‑1252. Αυτή η προεπιλογή θα αφαιρέσει σιωπηλά χαρακτήρες όπως “ß” ή “—”.

## Βήμα 3: Διατήρηση Διάταξης Πίνακα (Προαιρετικό, αλλά χρήσιμο για αναγνωσιμότητα)

Όταν **εξάγετε word ως txt**, οι πίνακες συνήθως ισοπεδώνουν σε μια μόνο γραμμή κειμένου, κάνοντάς τους μη αναγνώσιμους. Το Aspose.Words προσφέρει μια απλή σημαία για να διατηρήσετε τη οπτική δομή.

```java
        // Keep simple tables readable in the plain‑text output.
        saveOptions.setPreserveTableLayout(true);
```

*Πότε να το χρησιμοποιήσετε:* Αν το πηγαίο DOCX περιέχει τιμολόγια, προγράμματα ή οποιαδήποτε δεδομένα σε μορφή πλέγματος, η ενεργοποίηση του `PreserveTableLayout` θα εισάγει tabs και αλλαγές γραμμής ώστε το παραγόμενο αρχείο να μοιάζει ακόμη με πίνακα. Αν δεν το χρειάζεστε, μπορείτε να παραλείψετε τη γραμμή και να έχετε πιο συμπαγές αποτέλεσμα.

## Βήμα 4: Αποθήκευση του Εγγράφου ως Plain‑Text (Export word as txt)

Η εκτέλεση του προγράμματος παράγει το `plain.txt` στον ίδιο φάκελο. Ανοίξτε το με οποιονδήποτε επεξεργαστή κειμένου (Notepad++, VS Code, ακόμη και `cat` σε τερματικό) και θα δείτε:

```java
        // Save the document as a UTF‑8 encoded .txt file.
        doc.save("YOUR_DIRECTORY/plain.txt", saveOptions);
    }
}
```

Running the program produces `plain.txt` in the same folder. Open it with any text editor (Notepad++, VS Code, even `cat` in a terminal) and you’ll see:

```
Hello, world! こんにちは 😊
-------------------------------
| Item | Qty | Price |
|------|-----|-------|
| Apple|  2  | $1.00 |
| Banana| 5  | $0.50 |
```

Παρατηρήστε πώς η ιαπωνική χαιρετισμός και το χαμόγελο επιβίωσαν, και ο πίνακας διατήρησε τις στήλες του χάρη στο `PreserveTableLayout`. Αυτή είναι η ουσία μιας καθαρής **εξαγωγής docx σε txt**.

## Βήμα 5: Επαλήθευση του Αποτελέσματος (Έλεγχος λογικής μετατροπής word σε κείμενο)

Ένας γρήγορος έλεγχος λογικής αποτρέπει σιωπηλή απώλεια δεδομένων. Εδώ είναι μερικοί τρόποι για να επιβεβαιώσετε ότι πραγματικά **μετατρέπετε word σε κείμενο** σωστά:

1. **Σύγκριση checksum** – υπολογίστε ένα SHA‑256 hash του αρχείου `.txt` πριν και μετά από μια μετατροπή γύρω (txt → docx → txt) για να εξασφαλίσετε σταθερότητα.  
2. **Αναζήτηση για δείκτες Unicode** – χρησιμοποιήστε `grep` ή τη λειτουργία find‑in‑file του IDE για να εντοπίσετε χαρακτήρες όπως “😊”.  
3. **Άνοιγμα σε πολλαπλούς επεξεργαστές** – κάποιες παλιές εκδόσεις του Windows Notepad εξακολουθούν να ερμηνεύουν λανθασμένα UTF‑8 χωρίς BOM· το άνοιγμα του αρχείου στο VS Code επιβεβαιώνει τη σωστή κωδικοποίηση.

Αν κάποιος από αυτούς τους ελέγχους αποτύχει, ελέγξτε ξανά ότι υπάρχει η εντολή `saveOptions.setEncoding(StandardCharsets.UTF_8)` και ότι το πηγαίο DOCX περιέχει πραγματικά κείμενο Unicode.

## Συνηθισμένα Πιθανά Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Λείπουν χαρακτήρες** | Το προεπιλεγμένο charset του συστήματος (π.χ. Windows‑1252) αφαιρεί μη‑ASCII σύμβολα. | Ορίστε ρητά UTF‑8 μέσω του `saveOptions.setEncoding`. |
| **Οι πίνακες γίνονται μια γραμμή** | Το `PreserveTableLayout` παραμένει στο προεπιλεγμένο `false`. | Καλέστε `saveOptions.setPreserveTableLayout(true)`. |
| **Αρχείο δεν βρέθηκε** | Λάθος διαδρομή ή έλλειψη δικαιωμάτων ανάγνωσης. | Χρησιμοποιήστε απόλυτες διαδρομές ή `Paths.get(...)` με κατάλληλη διαχείριση εξαιρέσεων. |
| **Μείωση απόδοσης σε μεγάλα έγγραφα** | Φόρτωση ολόκληρου του εγγράφου στη μνήμη. | Διαβάστε το έγγραφο σε τμήματα χρησιμοποιώντας `DocumentBuilder` αν χρειάζεστε μόνο συγκεκριμένα τμήματα. |

## Bonus: Εξαγωγή Πολλαπλών Αρχείων DOCX σε Μαζική Επεξεργασία

Αν χρειάζεστε να **μετατρέψετε docx σε κείμενο** για ολόκληρο φάκελο, τυλίξτε τη λογική σε έναν βρόχο:

```java
import java.nio.file.*;

public class BatchExport {
    public static void main(String[] args) throws Exception {
        Path sourceDir = Paths.get("YOUR_DIRECTORY");
        TxtSaveOptions opts = new TxtSaveOptions();
        opts.setEncoding(StandardCharsets.UTF_8);
        opts.setPreserveTableLayout(true);

        try (DirectoryStream<Path> stream = Files.newDirectoryStream(sourceDir, "*.docx")) {
            for (Path docxPath : stream) {
                Document doc = new Document(docxPath.toString());
                String txtPath = docxPath.toString().replaceAll("\\.docx$", ".txt");
                doc.save(txtPath, opts);
                System.out.println("Exported: " + txtPath);
            }
        }
    }
}
```

Αυτό το απόσπασμα **εξάγει docx σε txt** για κάθε αρχείο στον κατάλογο, εξοικονομώντας σας ώρες χειροκίνητης εργασίας.

## Συμπέρασμα

Μόλις μάθατε πώς να **εξάγετε docx σε txt** με Java, διασφαλίζοντας ότι κάθε χαρακτήρας Unicode παραμένει αμετάβλητος, οι πίνακες παραμένουν αναγνώσιμοι, και όλη η διαδικασία είναι επαναλήψιμη. Διαμορφώνοντας το `TxtSaveOptions` για UTF‑8 και προαιρετικά διατηρώντας τις διατάξεις των πινάκων, μπορείτε αξιόπιστα να **μετατρέψετε docx σε κείμενο**, **μετατρέψετε word σε κείμενο**, και **εξάγετε word ως txt** για οποιοδήποτε downstream workflow.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να εξάγετε σε άλλες μορφές plain‑text όπως markdown (`.md`) ή CSV, ή εξερευνήστε τις δυνατότητες μετατροπής PDF του Aspose.Words. Οι ίδιες αρχές—ρητή κωδικοποίηση, διατήρηση διάταξης και πλήρης επαλήθευση—εφαρμόζονται παντού.

Καλό κώδικα, και εύχομαι τα αρχεία κειμένου σας να παραμένουν πάντα πλούσια σε Unicode!

---  

![Διάγραμμα που δείχνει τη διαδικασία εξαγωγής docx σε txt](/images/export-docx-to-txt-pipeline.png){alt="διάγραμμα διαδικασίας εξαγωγής docx σε txt"}

## Σχετικά Μαθήματα

- [Μετατροπή Docx σε Txt](/words/english/net/basic-conversions/docx-to-txt/)
- [aspose word to pdf – Μετατροπή DOCX σε PDF με Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [Μετατροπή docx σε markdown – Εξαγωγή Μαθηματικών Εξισώσεων σε LaTeX με Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}