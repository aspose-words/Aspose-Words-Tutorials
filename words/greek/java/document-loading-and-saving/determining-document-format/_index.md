---
date: 2026-02-22
description: Μάθετε πώς να εντοπίζετε τη μορφή εγγράφου Java με το Aspose.Words και
  να μετακινείτε αυτόματα τα αρχεία ανά μορφή. Αναγνωρίστε DOC, DOCX και άλλα.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Ανίχνευση μορφής εγγράφου Java χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ανίχνευση μορφής εγγράφου java χρησιμοποιώντας το Aspose.Words for Java

Όταν χρειάζεται να **detect document format java** σε μια δέσμη αρχείων, η δυνατότητα αυτόματης ταξινόμησής τους στους σωστούς φακέλους μπορεί να εξοικονομήσει ώρες χειροκίνητης εργασίας. Σε αυτό το σεμινάριο θα σας δείξουμε πώς το Aspose.Words for Java καθιστά εύκολη την αναγνώριση μορφών όπως Word, RTF, HTML, ODT και πολλές άλλες, και στη συνέχεια **move files by format** σε οργανωμένους καταλόγους.

## Quick Answers
- **Τι σημαίνει το “detect document format java”;** Είναι η διαδικασία προγραμματιστικής ταυτοποίησης της μορφής επεξεργασίας κειμένου ενός αρχείου (DOC, DOCX, RTF, κ.λπ.) χρησιμοποιώντας κώδικα Java.  
- **Ποια βιβλιοθήκη παρέχει αυτή τη δυνατότητα;** Το Aspose.Words for Java προσφέρει το API `FileFormatUtil.detectFileFormat`.  
- **Μπορεί το εργαλείο επίσης να διαχειριστεί κρυπτογραφημένα αρχεία;** Ναι – η σημαία `FileFormatInfo.isEncrypted()` σας ενημερώνει αν ένα έγγραφο είναι προστατευμένο με κωδικό.  
- **Χρειάζομαι άδεια για χρήση σε παραγωγή;** Απαιτείται εμπορική άδεια Aspose.Words για μη‑αξιολογικές εγκαταστάσεις.  
- **Είναι δυνατόν να μετακινηθούν τα αρχεία αυτόματα μετά την ανίχνευση;** Απόλυτα – συνδυάστε το αποτέλεσμα της ανίχνευσης με το `FileUtils.copyFile` για να ταξινομήσετε τα αρχεία σε προσαρμοσμένους φακέλους.

## Τι είναι το detect document format java;
`detect document format java` αναφέρεται στη χρήση κώδικα Java για την επιθεώρηση της δυαδικής κεφαλίδας ενός αρχείου και τον προσδιορισμό σε ποια μορφή επεξεργασίας κειμένου ανήκει (π.χ., DOC, DOCX, ODT). Το Aspose.Words διαβάζει το αρχείο χωρίς να φορτώνει πλήρως το έγγραφο, καθιστώντας τη λειτουργία γρήγορη και αποδοτική σε μνήμη.

## Γιατί να μετακινείτε αρχεία ανά μορφή;
Η οργάνωση των εγγράφων ανά την αρχική τους μορφή απλοποιεί την επεξεργασία σε επόμενα στάδια:

- **Μαζικές μετατροπές** γίνονται απλές όταν όλα τα αρχεία DOCX βρίσκονται σε έναν φάκελο.  
- **Υποστήριξη παλαιών εκδόσεων**: μπορείτε να απομονώσετε αρχεία Word προ‑97 για ειδική διαχείριση.  
- **Ασφάλεια**: τα κρυπτογραφημένα έγγραφα μπορούν να απομονωθούν αυτόματα.  

## Προαπαιτούμενα

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (κατεβάστε την τελευταία έκδοση)  
- Java Development Kit (JDK) 8 ή νεότερο εγκατεστημένο  
- Βασική εξοικείωση με Java I/O και streams  

## Βήμα 1: Ρύθμιση καταλόγων για κάθε μορφή

Αρχικά δημιουργούμε μια καθαρή δομή φακέλων όπου θα μετακινηθούν τα ανιχνευμένα αρχεία. Αυτό διατηρεί τη ροή εργασίας τακτοποιημένη και διευκολύνει την προσθήκη νέων κατηγοριών μορφών αργότερα.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

> **Συμβουλή:** Χρησιμοποιήστε απόλυτες διαδρομές ή ρυθμίστε τον βασικό κατάλογο μέσω αρχείου ιδιοτήτων για να αποφύγετε την κωδικοποίηση σκληρών διαδρομών στον κώδικα παραγωγής.

## Βήμα 2: Ανίχνευση μορφής εγγράφου και μετακίνηση αρχείων

Ο πυρήνας του **detect document format java** βρίσκεται στον παρακάτω βρόχο. Σαρώνει κάθε αρχείο, προσδιορίζει τον τύπο του και το αντιγράφει στον κατάλληλο φάκελο.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Το μπλοκ `switch` μπορεί να επεκταθεί ώστε να καλύπτει κάθε μορφή που σας ενδιαφέρει. Κάθε περίπτωση εκτυπώνει ένα φιλικό μήνυμα και στη συνέχεια μετακινεί το αρχείο στον αντίστοιχο φάκελο.

## Πλήρης πηγαίος κώδικας για την ανίχνευση μορφής εγγράφου java

Παρακάτω βρίσκεται το πλήρες, έτοιμο προς εκτέλεση παράδειγμα που συνδυάζει τη ρύθμιση των καταλόγων και τη λογική ανίχνευσης. Αντιγράψτε το σε μια κλάση Java, προσαρμόστε τη βασική διαδρομή και τρέξτε το σε έναν φάκελο με μεικτά έγγραφα.

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Συχνά προβλήματα και αντιμετώπιση

| Πρόβλημα | Γιατί συμβαίνει | Πώς να διορθώσετε |
|----------|----------------|-------------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Το αρχείο είναι κατεστραμμένο ή χρησιμοποιεί μορφή που δεν είναι Word. | Επαληθεύστε την επέκταση του αρχείου ή προσθέστε εναλλακτική λύση για να το μετακινήσετε στον φάκελο *Unknown* (ήδη στο παράδειγμα). |
| **Encrypted files throw an exception** | Το API προσπαθεί να διαβάσει το περιεχόμενο πριν ελέγξει την κρυπτογράφηση. | Πάντα καλέστε `info.isEncrypted()` πριν από οποιαδήποτε άλλη ενέργεια στο έγγραφο. |
| **Directory creation fails on Linux** | Ανεπαρκή δικαιώματα ή λείπει ο γονικός φάκελος. | Βεβαιωθείτε ότι η διαδικασία Java έχει δικαιώματα εγγραφής και ότι η βασική διαδρομή υπάρχει. |

## Συχνές Ερωτήσεις

**Q: Πώς εγκαθιστώ το Aspose.Words for Java;**  
A: Μπορείτε να κατεβάσετε το Aspose.Words for Java από το [εδώ](https://releases.aspose.com/words/java/) και να ακολουθήσετε τις παρεχόμενες οδηγίες εγκατάστασης.

**Q: Ποιες μορφές εγγράφων υποστηρίζονται για ανίχνευση;**  
A: Το Aspose.Words μπορεί να ανιχνεύσει DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, καθώς και παλαιότερες μορφές προ‑97, μεταξύ άλλων.

**Q: Μπορεί αυτός ο κώδικας να διαχειριστεί έγγραφα προστατευμένα με κωδικό;**  
A: Ναι. Η σημαία `FileFormatInfo.isEncrypted()` εντοπίζει κρυπτογραφημένα αρχεία, επιτρέποντάς σας να τα μετακινήσετε σε ασφαλή φάκελο χωρίς να τα ανοίξετε.

**Q: Υπάρχει επίπτωση στην απόδοση όταν σαρώνετε μεγάλους φακέλους;**  
A: Η ανίχνευση διαβάζει μόνο την κεφαλίδα του αρχείου, έτσι ακόμη και χιλιάδες αρχεία επεξεργάζονται γρήγορα. Για πολύ μεγάλες δέσμες, σκεφτείτε τη χρήση parallel streams.

**Q: Πώς μπορώ να επεκτείνω το script για να μετατρέψω μη υποστηριζόμενες μορφές;**  
A: Μετά την ανίχνευση, μπορείτε να καλέσετε `Document.save` με την επιθυμητή μορφή εξόδου για οποιονδήποτε υποστηριζόμενο τύπο πηγής.

## Συμπέρασμα

Χρησιμοποιώντας το **detect document format java** με το Aspose.Words, αποκτάτε έναν αξιόπιστο τρόπο για αυτόματη ταξινόμηση, απομόνωση ή μετατροπή αρχείων σχετικών με το Word. Ο κώδικας δείγματος δείχνει πώς να δημιουργήσετε μια καθαρή ιεραρχία φακέλων, να εντοπίσετε τη μορφή κάθε αρχείου και να το μετακινήσετε αναλόγως—εξοικονομώντας χρόνο και μειώνοντας τα χειροκίνητα σφάλματα.

---

**Τελευταία ενημέρωση:** 2026-02-22  
**Δοκιμασμένο με:** Aspose.Words for Java 24.12 (latest)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}