---
"description": "Μάθετε πώς να προσθέτετε και να προσαρμόζετε κεφαλίδες και υποσέλιδα σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτός ο οδηγός βήμα προς βήμα διασφαλίζει επαγγελματική μορφοποίηση εγγράφων."
"linktitle": "Δημιουργία Κεφαλίδας Υποσέλιδου"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Δημιουργία Κεφαλίδας Υποσέλιδου"
"url": "/el/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Κεφαλίδας Υποσέλιδου

## Εισαγωγή

Η προσθήκη κεφαλίδων και υποσέλιδων στα έγγραφά σας μπορεί να βελτιώσει τον επαγγελματισμό και την αναγνωσιμότητά τους. Με το Aspose.Words για .NET, μπορείτε εύκολα να δημιουργήσετε και να προσαρμόσετε κεφαλίδες και υποσέλιδα για τα έγγραφά σας στο Word. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία βήμα προς βήμα, διασφαλίζοντας ότι μπορείτε να εφαρμόσετε αυτές τις λειτουργίες απρόσκοπτα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:

- Aspose.Words για .NET: Λήψη και εγκατάσταση από το [σύνδεσμος λήψης](https://releases.aspose.com/words/net/).
- Περιβάλλον Ανάπτυξης: Όπως το Visual Studio, για να γράψετε και να εκτελέσετε τον κώδικά σας.
- Βασικές γνώσεις C#: Κατανόηση της C# και του .NET framework.
- Δείγμα εγγράφου: Ένα δείγμα εγγράφου για την εφαρμογή των κεφαλίδων και των υποσέλιδων ή για τη δημιουργία ενός νέου, όπως φαίνεται στο σεμινάριο.

## Εισαγωγή χώρων ονομάτων

Αρχικά, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων για να αποκτήσετε πρόσβαση στις κλάσεις και τις μεθόδους Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Βήμα 1: Ορισμός του καταλόγου εγγράφων

Ορίστε τον κατάλογο όπου θα αποθηκευτεί το έγγραφό σας. Αυτό βοηθά στην αποτελεσματική διαχείριση της διαδρομής.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Βήμα 2: Δημιουργία νέου εγγράφου

Δημιουργήστε ένα νέο έγγραφο και ένα `DocumentBuilder` για να διευκολύνουν την προσθήκη περιεχομένου.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 3: Ρύθμιση παραμέτρων σελίδας

Ορίστε τις ρυθμίσεις σελίδας, συμπεριλαμβανομένου του εάν η πρώτη σελίδα θα έχει διαφορετική κεφαλίδα/υποσέλιδο.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Βήμα 4: Προσθήκη κεφαλίδας στην πρώτη σελίδα

Μεταβείτε στην ενότητα κεφαλίδας για την πρώτη σελίδα και διαμορφώστε το κείμενο της κεφαλίδας.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Βήμα 5: Προσθήκη κύριας κεφαλίδας

Μεταβείτε στην κύρια ενότητα κεφαλίδας και εισαγάγετε μια εικόνα και ένα κείμενο.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Εισαγωγή εικόνας στην κεφαλίδα
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Βήμα 6: Προσθήκη κύριου υποσέλιδου

Μεταβείτε στην ενότητα του κύριου υποσέλιδου και δημιουργήστε έναν πίνακα για να μορφοποιήσετε το περιεχόμενο του υποσέλιδου.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Προσθήκη αρίθμησης σελίδων
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Βήμα 7: Προσθήκη περιεχομένου και αλλαγών σελίδας

Μετακινηθείτε στο τέλος του εγγράφου, προσθέστε μια αλλαγή σελίδας και δημιουργήστε μια νέα ενότητα με διαφορετικές ρυθμίσεις σελίδας.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Βήμα 8: Αντιγραφή κεφαλίδων και υποσέλιδων από την προηγούμενη ενότητα

Εάν θέλετε να επαναχρησιμοποιήσετε κεφαλίδες και υποσέλιδα από μια προηγούμενη ενότητα, αντιγράψτε τα και εφαρμόστε τις απαραίτητες τροποποιήσεις.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Σύναψη

Ακολουθώντας αυτά τα βήματα, μπορείτε να προσθέσετε και να προσαρμόσετε αποτελεσματικά κεφαλίδες και υποσέλιδα στα έγγραφά σας στο Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτό βελτιώνει την εμφάνιση και τον επαγγελματισμό του εγγράφου σας, καθιστώντας το πιο ευανάγνωστο και ελκυστικό.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;

Το Aspose.Words για .NET είναι μια βιβλιοθήκη που επιτρέπει στους προγραμματιστές να δημιουργούν, να επεξεργάζονται και να μετατρέπουν έγγραφα Word μέσω προγραμματισμού μέσα σε εφαρμογές .NET.

### Μπορώ να προσθέσω εικόνες στην κεφαλίδα ή στο υποσέλιδο;

Ναι, μπορείτε εύκολα να προσθέσετε εικόνες στην κεφαλίδα ή το υποσέλιδο χρησιμοποιώντας το `DocumentBuilder.InsertImage` μέθοδος.

### Πώς μπορώ να ορίσω διαφορετικές κεφαλίδες και υποσέλιδα για την πρώτη σελίδα;

Μπορείτε να ορίσετε διαφορετικές κεφαλίδες και υποσέλιδα για την πρώτη σελίδα χρησιμοποιώντας το `DifferentFirstPageHeaderFooter` ιδιοκτησία του `PageSetup` τάξη.

### Πού μπορώ να βρω περισσότερη τεκμηρίωση για το Aspose.Words;

Μπορείτε να βρείτε πλήρη τεκμηρίωση στο [Σελίδα τεκμηρίωσης του Aspose.Words API](https://reference.aspose.com/words/net/).

### Υπάρχει διαθέσιμη υποστήριξη για το Aspose.Words;

Ναι, η Aspose προσφέρει υποστήριξη μέσω των [φόρουμ υποστήριξης](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}