---
date: 2025-12-20
description: Μάθετε πώς να οργανώνετε αρχεία κατά τύπο και να εντοπίζετε μορφές εγγράφων
  σε Java με το Aspose.Words. Υποστηρίζει DOC, DOCX, RTF και άλλα.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Οργάνωση αρχείων κατά τύπο χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Οργάνωση Αρχείων κατά Τύπο χρησιμοποιώντας το Aspose.Words για Java

Όταν χρειάζεται να **οργανώσετε αρχεία κατά τύπο** σε μια εφαρμογή Java, το πρώτο βήμα είναι να προσδιορίσετε αξιόπιστα τη μορφή κάθε εγγράφου. Το Aspose.Words για Java το καθιστά απλό, επιτρέποντάς σας να ανιχνεύσετε DOC, DOCX, RTF, HTML, ODT και πολλές άλλες μορφές – ακόμη και κρυπτογραφημένα ή άγνωστα αρχεία. Σε αυτόν τον οδηγό θα δούμε πώς να δημιουργήσετε φακέλους, να ανιχνεύσετε μορφές αρχείων και να ταξινομήσετε αυτόματα τα αρχεία σας.

## Σύντομες Απαντήσεις
- **Τι σημαίνει “οργάνωση αρχείων κατά τύπο”;** Σημαίνει την αυτόματη μετακίνηση εγγράφων σε φακέλους βάσει της ανιχνευθείσας μορφής τους (π.χ., DOCX, PDF, RTF).  
- **Ποια βιβλιοθήκη βοηθά στην ανίχνευση μορφής αρχείου σε Java;** Το Aspose.Words για Java παρέχει τη μέθοδο `FileFormatUtil.detectFileFormat()`.  
- **Μπορεί το API να αναγνωρίσει άγνωστους τύπους αρχείων;** Ναι – επιστρέφει `LoadFormat.UNKNOWN` για μη υποστηριζόμενα ή μη αναγνωρίσιμα αρχεία.  
- **Υποστηρίζεται η ανίχνευση κρυπτογραφημένων εγγράφων;** Απόλυτα· η σημαία `FileFormatInfo.isEncrypted()` σας λέει αν ένα αρχείο είναι προστατευμένο με κωδικό.  
- **Χρειάζομαι άδεια για παραγωγική χρήση;** Απαιτείται έγκυρη άδεια Aspose.Words για εμπορικές αναπτύξεις.

## Εισαγωγή: Οργάνωση Αρχείων κατά Τύπο με το Aspose.Words για Java

Κατά την επεξεργασία εγγράφων σε Java, είναι κρίσιμο να προσδιορίζετε τη μορφή των αρχείων που διαχειρίζεστε. Το Aspose.Words για Java παρέχει ισχυρές δυνατότητες για **detect file format java**, και θα σας καθοδηγήσουμε στη διαδικασία οργάνωσης των αρχείων σας αποτελεσματικά.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι διαθέτετε τα παρακάτω:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) εγκατεστημένο στο σύστημά σας
- Βασικές γνώσεις προγραμματισμού Java

## Βήμα 1: Ρύθμιση Καταλόγου

Πρώτα, πρέπει να δημιουργήσουμε τους απαραίτητους καταλόγους για να οργανώσουμε τα αρχεία μας αποτελεσματικά. Θα δημιουργήσουμε καταλόγους για διαφορετικούς τύπους εγγράφων.

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

Δημιουργήσαμε καταλόγους για υποστηριζόμενα, άγνωστα, κρυπτογραφημένα και προ‑97 τύπους εγγράφων.

## Βήμα 2: Ανίχνευση Μορφής Εγγράφου

Τώρα, ας ανιχνεύσουμε τη μορφή των εγγράφων στους καταλόγους μας. Θα χρησιμοποιήσουμε το Aspose.Words για Java για να το πετύχουμε.

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

Σε αυτό το απόσπασμα κώδικα διατρέχουμε τα αρχεία, **detect file format java**, και τα οργανώνουμε στους κατάλληλους φακέλους.

## Πλήρης Πηγαίος Κώδικας για τον Προσδιορισμό Μορφής Εγγράφου στο Aspose.Words για Java

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

## Πώς να Ανιχνεύσετε τη Μορφή Αρχείου Java

Η μέθοδος `FileFormatUtil.detectFileFormat()` εξετάζει την κεφαλίδα του αρχείου και επιστρέφει ένα αντικείμενο `FileFormatInfo`. Αυτό το αντικείμενο σας ενημερώνει για το **load format**, αν το αρχείο είναι κρυπτογραφημένο και άλλα χρήσιμα μεταδεδομένα. Χρησιμοποιώντας αυτές τις πληροφορίες, μπορείτε προγραμματιστικά **να αναγνωρίσετε άγνωστους τύπους αρχείων** και να αποφασίσετε πώς θα τα επεξεργαστείτε.

## Αναγνώριση Άγνωστων Τύπων Αρχείων

Όταν το API επιστρέφει `LoadFormat.UNKNOWN`, το αρχείο είναι είτε κατεστραμμένο είτε χρησιμοποιεί μορφή που δεν υποστηρίζει το Aspose.Words. Στο παράδειγμα κώδικα μετακινούμε αυτά τα αρχεία στον φάκελο **Unknown** ώστε να τα ελέγξετε αργότερα.

## Συχνά Προβλήματα και Λύσεις

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Τα αρχεία τοποθετούνται πάντα στον φάκελο *Supported* | Το `FileFormatUtil` δεν μπόρεσε να διαβάσει την κεφαλίδα (π.χ., το αρχείο είναι κενό) | Βεβαιωθείτε ότι περνάτε τη σωστή διαδρομή αρχείου και ότι το αρχείο δεν είναι μηδενικού μεγέθους. |
| Τα κρυπτογραφημένα αρχεία προκαλούν εξαίρεση | Προσπάθεια ανάγνωσης χωρίς διαχείριση κρυπτογράφησης | Χρησιμοποιήστε τον έλεγχο `info.isEncrypted()` πριν προχωρήσετε, όπως φαίνεται στον κώδικα. |
| Τα προ‑97 έγγραφα Word δεν ανιχνεύονται | Οι παλαιότερες μορφές απαιτούν την περίπτωση `DOC_PRE_WORD_60` | Διατηρήστε το τμήμα `case LoadFormat.DOC_PRE_WORD_60` για να τα δρομολογήσετε στον φάκελο *Pre97*. |

## Συχνές Ερωτήσεις

### Πώς εγκαθιστώ το Aspose.Words για Java;

Μπορείτε να κατεβάσετε το Aspose.Words για Java από το [εδώ](https://releases.aspose.com/words/java/) και να ακολουθήσετε τις οδηγίες εγκατάστασης που παρέχονται.

### Ποιες μορφές εγγράφων υποστηρίζονται;

Το Aspose.Words για Java υποστηρίζει διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των DOC, DOCX, RTF, HTML, ODT και άλλων. Ανατρέξτε στην επίσημη τεκμηρίωση για πλήρη λίστα.

### Πώς μπορώ να ανιχνεύσω κρυπτογραφημένα έγγραφα χρησιμοποιώντας το Aspose.Words για Java;

Χρησιμοποιήστε τη μέθοδο `FileFormatUtil.detectFileFormat()`· η επιστρεφόμενη σημαία `FileFormatInfo.isEncrypted()` υποδεικνύει κρυπτογράφηση, όπως φαίνεται σε αυτόν τον οδηγό.

### Υπάρχουν περιορισμοί όταν εργάζομαι με παλαιότερες μορφές εγγράφων;

Οι παλαιότερες μορφές όπως MS Word 6 ή Word 95 μπορεί να λείπουν από σύγχρονα χαρακτηριστικά και να παρουσιάζουν προβλήματα συμβατότητας. Σκεφτείτε τη μετατροπή τους σε νεότερες μορφές όταν είναι δυνατόν.

### Μπορώ να αυτοματοποιήσω την ανίχνευση μορφής εγγράφου στην εφαρμογή μου Java;

Ναι, ενσωματώστε τον παρεχόμενο κώδικα στη διαδικασία επεξεργασίας της εφαρμογής σας. Αυτό επιτρέπει αυτόματη ταξινόμηση και διαχείριση βάσει των ανιχνευμένων μορφών.

---

**Τελευταία Ενημέρωση:** 2025-12-20  
**Δοκιμή Με:** Aspose.Words για Java 24.12 (τελευταία)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}