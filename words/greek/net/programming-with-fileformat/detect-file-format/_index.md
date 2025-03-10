---
title: Ανίχνευση μορφής αρχείου εγγράφου
linktitle: Ανίχνευση μορφής αρχείου εγγράφου
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εντοπίζετε μορφές αρχείων εγγράφων χρησιμοποιώντας το Aspose.Words για .NET με αυτόν τον περιεκτικό, βήμα προς βήμα οδηγό.
weight: 10
url: /el/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανίχνευση μορφής αρχείου εγγράφου

## Εισαγωγή

Στον σημερινό ψηφιακό κόσμο, η αποτελεσματική διαχείριση διαφορετικών μορφών εγγράφων είναι ζωτικής σημασίας. Είτε χειρίζεστε Word, PDF, HTML ή άλλες μορφές, το να μπορείτε να εντοπίσετε και να επεξεργαστείτε σωστά αυτά τα αρχεία μπορεί να σας εξοικονομήσει πολύ χρόνο και προσπάθεια. Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να ανιχνεύουμε μορφές αρχείων εγγράφων χρησιμοποιώντας το Aspose.Words για .NET. Αυτός ο οδηγός θα σας καθοδηγήσει σε όλα όσα πρέπει να γνωρίζετε, από προαπαιτούμενα έως έναν λεπτομερή οδηγό βήμα προς βήμα.

## Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

-  Aspose.Words για .NET: Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/net/) . Βεβαιωθείτε ότι έχετε έγκυρη άδεια. Εάν όχι, μπορείτε να πάρετε ένα[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Οποιαδήποτε πρόσφατη έκδοση θα λειτουργεί καλά.
- .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη σωστή έκδοση.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, θα χρειαστεί να εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Ας αναλύσουμε το παράδειγμα σε πολλαπλά βήματα για να το ακολουθήσουμε πιο εύκολα.

## Βήμα 1: Ρύθμιση καταλόγων

Αρχικά, πρέπει να δημιουργήσουμε καταλόγους όπου τα αρχεία θα ταξινομούνται με βάση τη μορφή τους.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Δημιουργήστε τους καταλόγους εάν δεν υπάρχουν ήδη.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Βήμα 2: Λήψη της λίστας αρχείων

Στη συνέχεια, θα λάβουμε μια λίστα αρχείων από τον κατάλογο, εξαιρουμένων τυχόν κατεστραμμένων εγγράφων.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Βήμα 3: Εντοπισμός μορφών αρχείων

Τώρα, επαναλαμβάνουμε κάθε αρχείο και εντοπίζουμε τη μορφή του χρησιμοποιώντας το Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Εμφάνιση του τύπου εγγράφου
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Σύναψη

Ο εντοπισμός μορφών αρχείων εγγράφων χρησιμοποιώντας το Aspose.Words για .NET είναι μια απλή διαδικασία. Ρυθμίζοντας τους καταλόγους σας, λαμβάνοντας τη λίστα των αρχείων σας και χρησιμοποιώντας το Aspose.Words για τον εντοπισμό μορφών αρχείων, μπορείτε να οργανώσετε και να διαχειριστείτε αποτελεσματικά τα έγγραφά σας. Αυτή η προσέγγιση όχι μόνο εξοικονομεί χρόνο, αλλά διασφαλίζει επίσης ότι χειρίζεστε σωστά διάφορες μορφές εγγράφων.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words for .NET είναι μια ισχυρή βιβλιοθήκη για την εργασία με έγγραφα του Word μέσω προγραμματισμού. Επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να μετατρέπουν έγγραφα σε διάφορες μορφές.

### Μπορεί το Aspose.Words να εντοπίσει κρυπτογραφημένα έγγραφα;
Ναι, το Aspose.Words μπορεί να εντοπίσει εάν ένα έγγραφο είναι κρυπτογραφημένο και μπορείτε να χειριστείτε ανάλογα έγγραφα.

### Ποιες μορφές μπορεί να ανιχνεύσει το Aspose.Words;
Το Aspose.Words μπορεί να ανιχνεύσει ένα ευρύ φάσμα μορφών, όπως DOC, DOCX, RTF, HTML, MHTML, ODT και πολλά άλλα.

### Πώς μπορώ να πάρω μια προσωρινή άδεια για το Aspose.Words;
 Μπορείτε να πάρετε μια προσωρινή άδεια από το[Aspose Αγορά](https://purchase.aspose.com/temporary-license/) σελίδα.

### Πού μπορώ να βρω την τεκμηρίωση για το Aspose.Words;
 Μπορείτε να βρείτε την τεκμηρίωση για το Aspose.Words[εδώ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
