---
title: Διάταξη στο κελί
linktitle: Διάταξη στο κελί
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να ορίζετε τη διάταξη στο κελί χρησιμοποιώντας το Aspose.Words για .NET με αυτόν τον περιεκτικό οδηγό. Ιδανικό για προγραμματιστές που θέλουν να προσαρμόσουν τα έγγραφα του Word.
weight: 10
url: /el/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διάταξη στο κελί

## Εισαγωγή

Εάν θελήσατε ποτέ να ρυθμίσετε τη διάταξη των κελιών του πίνακα στα έγγραφα του Word μέσω προγραμματισμού, βρίσκεστε στο σωστό μέρος. Σήμερα, θα δούμε πώς να ορίσετε τη διάταξη στο κελί χρησιμοποιώντας το Aspose.Words για .NET. Θα δούμε ένα πρακτικό παράδειγμα, αναλύοντάς το βήμα-βήμα, ώστε να μπορείτε να το ακολουθήσετε με ευκολία.

## Προαπαιτούμενα

Προτού μεταβούμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

1.  Aspose.Words για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη Aspose.Words για .NET. Αν δεν έχεις, μπορείς[κατεβάστε το εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Θα χρειαστείτε ένα περιβάλλον ανάπτυξης που έχει ρυθμιστεί με .NET. Το Visual Studio είναι μια εξαιρετική επιλογή αν ψάχνετε για συστάσεις.
3. Βασικές γνώσεις C#: Ενώ θα εξηγήσω κάθε βήμα, μια βασική κατανόηση της C# θα σας βοηθήσει να ακολουθήσετε πιο εύκολα.
4.  Κατάλογος εγγράφων: Προετοιμάστε μια διαδρομή καταλόγου όπου θα αποθηκεύσετε τα έγγραφά σας. Θα αναφερθούμε σε αυτό ως`YOUR DOCUMENT DIRECTORY`.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, βεβαιωθείτε ότι εισάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ας αναλύσουμε τη διαδικασία σε διαχειρίσιμα βήματα.

## Βήμα 1: Δημιουργήστε ένα νέο έγγραφο

 Αρχικά, θα δημιουργήσουμε ένα νέο έγγραφο του Word και θα αρχικοποιήσουμε ένα`DocumentBuilder` να μας βοηθήσει να δημιουργήσουμε το περιεχόμενό μας.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Ξεκινήστε έναν πίνακα και ορίστε τη μορφή γραμμής

Θα ξεκινήσουμε την κατασκευή ενός πίνακα και θα καθορίσουμε τον κανόνα ύψους και ύψους για τις σειρές.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Βήμα 3: Εισαγάγετε κελιά και συμπληρώστε περιεχόμενο

Στη συνέχεια, κάνουμε βρόχο για να εισάγουμε κελιά στον πίνακα. Για κάθε 7 κελιά, θα τερματίσουμε τη σειρά για να δημιουργήσουμε μια νέα.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Βήμα 4: Προσθέστε ένα σχήμα υδατογραφήματος

 Τώρα, ας προσθέσουμε ένα υδατογράφημα στο έγγραφό μας. Θα δημιουργήσουμε ένα`Shape` αντικείμενο και ορίστε τις ιδιότητές του.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Εμφανίστε το σχήμα έξω από το κελί του πίνακα εάν θα τοποθετηθεί σε ένα κελί.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Βήμα 5: Προσαρμόστε την εμφάνιση υδατογραφήματος

Θα προσαρμόσουμε περαιτέρω την εμφάνιση του υδατογραφήματος ορίζοντας τις ιδιότητες χρώματος και κειμένου.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Βήμα 6: Εισαγάγετε το υδατογράφημα στο έγγραφο

Θα βρούμε την τελευταία εκτέλεση στο έγγραφο και θα εισαγάγουμε το υδατογράφημα σε αυτήν τη θέση.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Βήμα 7: Βελτιστοποίηση εγγράφου για το Word 2010

Για να διασφαλίσουμε τη συμβατότητα, θα βελτιστοποιήσουμε το έγγραφο για το Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Βήμα 8: Αποθηκεύστε το έγγραφο

Τέλος, θα αποθηκεύσουμε το έγγραφό μας στον καθορισμένο κατάλογο.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Σύναψη

Και ορίστε το! Δημιουργήσατε επιτυχώς ένα έγγραφο του Word με προσαρμοσμένη διάταξη πίνακα και προσθέσατε ένα υδατογράφημα χρησιμοποιώντας το Aspose.Words για .NET. Αυτό το σεμινάριο είχε ως στόχο να παρέχει έναν σαφή, βήμα προς βήμα οδηγό για να σας βοηθήσει να κατανοήσετε κάθε μέρος της διαδικασίας. Με αυτές τις δεξιότητες, μπορείτε πλέον να δημιουργείτε πιο εξελιγμένα και προσαρμοσμένα έγγραφα του Word μέσω προγραμματισμού.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω διαφορετική γραμματοσειρά για το κείμενο του υδατογραφήματος;
 Ναι, μπορείτε να αλλάξετε τη γραμματοσειρά ορίζοντας το`watermark.TextPath.FontFamily` ιδιοκτησία στη γραμματοσειρά που επιθυμείτε.

### Πώς μπορώ να προσαρμόσω τη θέση του υδατογραφήματος;
 Μπορείτε να τροποποιήσετε το`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , και`VerticalAlignment` ιδιότητες για να προσαρμόσετε τη θέση του υδατογραφήματος.

### Είναι δυνατόν να χρησιμοποιηθεί μια εικόνα αντί για κείμενο για το υδατογράφημα;
 Απολύτως! Μπορείτε να δημιουργήσετε ένα`Shape` με τον τύπο`ShapeType.Image` και ορίστε την εικόνα του χρησιμοποιώντας το`ImageData.SetImage` μέθοδος.

### Μπορώ να δημιουργήσω πίνακες με διαφορετικά ύψη σειρών;
Ναι, μπορείτε να ορίσετε διαφορετικά ύψη για κάθε σειρά αλλάζοντας το`RowFormat.Height` ιδιότητα πριν από την εισαγωγή κελιών σε αυτήν τη σειρά.

### Πώς μπορώ να αφαιρέσω ένα υδατογράφημα από το έγγραφο;
 Μπορείτε να αφαιρέσετε το υδατογράφημα εντοπίζοντάς το στη συλλογή σχημάτων του εγγράφου και καλώντας το`Remove` μέθοδος.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
