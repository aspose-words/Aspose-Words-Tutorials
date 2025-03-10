---
title: Διατήρηση αρίθμησης πηγών
linktitle: Διατήρηση αρίθμησης πηγών
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εισάγετε έγγραφα διατηρώντας παράλληλα τη μορφοποίηση χρησιμοποιώντας το Aspose.Words για .NET. Οδηγός βήμα προς βήμα με παραδείγματα κώδικα.
weight: 10
url: /el/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διατήρηση αρίθμησης πηγών

## Εισαγωγή

 Όταν εργάζεστε με το Aspose.Words για .NET, η εισαγωγή εγγράφων από τη μια πηγή στην άλλη διατηρώντας τη μορφοποίηση μπορεί να γίνει αποτελεσματικά χρησιμοποιώντας το`NodeImporter` τάξη. Αυτό το σεμινάριο θα σας καθοδηγήσει στη διαδικασία βήμα προς βήμα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα ακόλουθα:
- Το Visual Studio είναι εγκατεστημένο στον υπολογιστή σας.
-  Το Aspose.Words για .NET έχει εγκατασταθεί. Αν όχι, κατεβάστε το από[εδώ](https://releases.aspose.com/words/net/).
- Βασικές γνώσεις προγραμματισμού C# και .NET.

## Εισαγωγή χώρων ονομάτων

Πρώτα, συμπεριλάβετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Βήμα 1: Ρύθμιση του έργου σας

Ξεκινήστε δημιουργώντας ένα νέο έργο C# στο Visual Studio και εγκαταστήστε το Aspose.Words μέσω του NuGet Package Manager.

## Βήμα 2: Αρχικοποίηση εγγράφων
Δημιουργήστε περιπτώσεις της πηγής (`srcDoc`) και προορισμός (`dstDoc`) έγγραφα.

```csharp
// Διαδρομή στον κατάλογο εγγράφων σας
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Βήμα 3: Διαμόρφωση επιλογών εισαγωγής
Ρυθμίστε τις επιλογές εισαγωγής για να διατηρήσετε τη μορφοποίηση της πηγής, συμπεριλαμβανομένων των αριθμημένων παραγράφων.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Βήμα 4: Εισαγωγή παραγράφων
Επαναλάβετε τις παραγράφους στο έγγραφο προέλευσης και εισαγάγετέ τις στο έγγραφο προορισμού.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Βήμα 5: Αποθηκεύστε το έγγραφο
Αποθηκεύστε το συγχωνευμένο έγγραφο στην επιθυμητή θέση.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Σύναψη

 Συμπερασματικά, η χρήση του Aspose.Words για .NET για την εισαγωγή εγγράφων με διατήρηση της μορφοποίησης είναι απλή με το`NodeImporter` τάξη. Αυτή η μέθοδος διασφαλίζει ότι τα έγγραφά σας διατηρούν απρόσκοπτα την αρχική τους εμφάνιση και δομή.

## Συχνές ερωτήσεις

### Μπορώ να εισάγω έγγραφα με διαφορετικά στυλ μορφοποίησης;
 Ναι, το`NodeImporter` Η κλάση υποστηρίζει την εισαγωγή εγγράφων με ποικίλα στυλ μορφοποίησης.

### Τι γίνεται αν τα έγγραφά μου περιέχουν σύνθετους πίνακες και εικόνες;
Το Aspose.Words για .NET χειρίζεται πολύπλοκες δομές όπως πίνακες και εικόνες κατά τη διάρκεια εργασιών εισαγωγής.

### Είναι το Aspose.Words συμβατό με όλες τις εκδόσεις του .NET;
Το Aspose.Words υποστηρίζει εκδόσεις .NET Framework και .NET Core για απρόσκοπτη ενσωμάτωση.

### Πώς μπορώ να χειριστώ σφάλματα κατά την εισαγωγή εγγράφων;
Χρησιμοποιήστε μπλοκ try-catch για να χειριστείτε εξαιρέσεις που ενδέχεται να προκύψουν κατά τη διαδικασία εισαγωγής.

### Πού μπορώ να βρω πιο λεπτομερή τεκμηρίωση για το Aspose.Words για .NET;
 Επισκεφθείτε το[απόδειξη με έγγραφα](https://reference.aspose.com/words/net/) για αναλυτικούς οδηγούς και αναφορές API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
