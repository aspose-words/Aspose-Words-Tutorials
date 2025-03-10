---
title: Προσδιορισμός μορφής εγγράφου στο Aspose.Words για Java
linktitle: Καθορισμός Μορφής Εγγράφου
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να εντοπίζετε μορφές εγγράφων σε Java με το Aspose.Words. Προσδιορίστε τα DOC, DOCX και άλλα. Οργανώστε τα αρχεία αποτελεσματικά.
weight: 25
url: /el/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσδιορισμός μορφής εγγράφου στο Aspose.Words για Java


## Εισαγωγή στον προσδιορισμό της μορφής εγγράφου στο Aspose.Words για Java

Όταν εργάζεστε με την επεξεργασία εγγράφων σε Java, είναι σημαντικό να καθορίσετε τη μορφή των αρχείων με τα οποία αντιμετωπίζετε. Το Aspose.Words για Java παρέχει ισχυρές δυνατότητες για τον εντοπισμό μορφών εγγράφων και θα σας καθοδηγήσουμε στη διαδικασία.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- [Aspose.Words για Java](https://releases.aspose.com/words/java/)
- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας
- Βασικές γνώσεις προγραμματισμού Java

## Βήμα 1: Ρύθμιση καταλόγου

Αρχικά, πρέπει να ρυθμίσουμε τους απαραίτητους καταλόγους για την αποτελεσματική οργάνωση των αρχείων μας. Θα δημιουργήσουμε καταλόγους για διαφορετικούς τύπους εγγράφων.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Δημιουργήστε τους καταλόγους εάν δεν υπάρχουν ήδη.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Δημιουργήσαμε καταλόγους για υποστηριζόμενους, άγνωστους, κρυπτογραφημένους και τύπους εγγράφων πριν από το 97.

## Βήμα 2: Ανίχνευση μορφής εγγράφου

Τώρα, ας εντοπίσουμε τη μορφή των εγγράφων στους καταλόγους μας. Θα χρησιμοποιήσουμε το Aspose.Words για Java για να το πετύχουμε αυτό.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Εμφάνιση του τύπου εγγράφου
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Προσθέστε θήκες για άλλες μορφές εγγράφων όπως απαιτείται
    }

    // Χειριστείτε κρυπτογραφημένα έγγραφα
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Χειριστείτε άλλους τύπους εγγράφων
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

Σε αυτό το απόσπασμα κώδικα, επαναλαμβάνουμε τα αρχεία, εντοπίζουμε τις μορφές τους και τα οργανώνουμε στους αντίστοιχους καταλόγους.

## Πλήρης πηγαίος κώδικας για τον προσδιορισμό της μορφής εγγράφου στο Aspose.Words για Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Δημιουργήστε τους καταλόγους εάν δεν υπάρχουν ήδη.
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
            // Εμφάνιση του τύπου εγγράφου
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

## Σύναψη

Ο καθορισμός μορφών εγγράφων στο Aspose.Words για Java είναι απαραίτητος για την αποτελεσματική επεξεργασία εγγράφων. Με τα βήματα που περιγράφονται σε αυτόν τον οδηγό, μπορείτε να αναγνωρίσετε τύπους εγγράφων και να τους χειριστείτε ανάλογα στις εφαρμογές σας Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να εγκαταστήσω το Aspose.Words για Java;

 Μπορείτε να κάνετε λήψη του Aspose.Words για Java από το[εδώ](https://releases.aspose.com/words/java/)και ακολουθήστε τις οδηγίες εγκατάστασης που παρέχονται.

### Ποιες είναι οι υποστηριζόμενες μορφές εγγράφων;

Το Aspose.Words για Java υποστηρίζει διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των DOC, DOCX, RTF, HTML και άλλων. Μπορείτε να ανατρέξετε στην τεκμηρίωση για μια πλήρη λίστα.

### Πώς μπορώ να εντοπίσω κρυπτογραφημένα έγγραφα χρησιμοποιώντας το Aspose.Words για Java;

 Μπορείτε να χρησιμοποιήσετε το`FileFormatUtil.detectFileFormat()` μέθοδος για τον εντοπισμό κρυπτογραφημένων εγγράφων, όπως φαίνεται σε αυτόν τον οδηγό.

### Υπάρχουν περιορισμοί κατά την εργασία με παλαιότερες μορφές εγγράφων;

Οι παλαιότερες μορφές εγγράφων, όπως το MS Word 6 ή το Word 95, ενδέχεται να έχουν περιορισμούς όσον αφορά τις δυνατότητες και τη συμβατότητα με σύγχρονες εφαρμογές. Εξετάστε το ενδεχόμενο αναβάθμισης ή μετατροπής αυτών των εγγράφων όταν είναι απαραίτητο.

### Μπορώ να αυτοματοποιήσω τον εντοπισμό μορφής εγγράφου στην εφαρμογή Java;

Ναι, μπορείτε να αυτοματοποιήσετε τον εντοπισμό μορφής εγγράφου ενσωματώνοντας τον παρεχόμενο κώδικα στην εφαρμογή Java. Αυτό σας επιτρέπει να επεξεργάζεστε έγγραφα με βάση τις μορφές που έχουν εντοπιστεί.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
