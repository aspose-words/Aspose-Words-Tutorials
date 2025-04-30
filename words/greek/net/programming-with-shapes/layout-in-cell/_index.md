---
"description": "Μάθετε πώς να ορίσετε τη διάταξη σε κελί χρησιμοποιώντας το Aspose.Words για .NET με αυτόν τον ολοκληρωμένο οδηγό. Ιδανικό για προγραμματιστές που θέλουν να προσαρμόσουν έγγραφα Word."
"linktitle": "Διάταξη σε κελί"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Διάταξη σε κελί"
"url": "/el/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Διάταξη σε κελί

## Εισαγωγή

Αν ποτέ θέλατε να βελτιώσετε τη διάταξη των κελιών του πίνακα σε έγγραφα του Word μέσω προγραμματισμού, βρίσκεστε στο σωστό μέρος. Σήμερα, θα εμβαθύνουμε στον τρόπο ορισμού της διάταξης σε κελί χρησιμοποιώντας το Aspose.Words για .NET. Θα δούμε ένα πρακτικό παράδειγμα, αναλύοντάς το βήμα προς βήμα, ώστε να μπορείτε να το παρακολουθείτε με ευκολία.

## Προαπαιτούμενα

Πριν προχωρήσουμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

1. Aspose.Words για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη Aspose.Words για .NET. Εάν δεν την έχετε, μπορείτε να [κατεβάστε το εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον Ανάπτυξης: Θα χρειαστείτε ένα περιβάλλον ανάπτυξης με .NET. Το Visual Studio είναι μια εξαιρετική επιλογή αν ψάχνετε για συστάσεις.
3. Βασικές γνώσεις C#: Ενώ θα εξηγήσω κάθε βήμα, μια βασική κατανόηση της C# θα σας βοηθήσει να παρακολουθήσετε πιο εύκολα.
4. Κατάλογος εγγράφων: Προετοιμάστε μια διαδρομή καταλόγου όπου θα αποθηκεύσετε τα έγγραφά σας. Θα αναφερόμαστε σε αυτήν ως `YOUR DOCUMENT DIRECTORY`.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, βεβαιωθείτε ότι εισάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ας χωρίσουμε τη διαδικασία σε διαχειρίσιμα βήματα.

## Βήμα 1: Δημιουργία νέου εγγράφου

Αρχικά, θα δημιουργήσουμε ένα νέο έγγραφο του Word και θα αρχικοποιήσουμε ένα `DocumentBuilder` αντικείμενο για να μας βοηθήσει να κατασκευάσουμε το περιεχόμενό μας.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Έναρξη πίνακα και ορισμός μορφής γραμμής

Θα ξεκινήσουμε την κατασκευή ενός πίνακα και θα καθορίσουμε το ύψος και τον κανόνα ύψους για τις γραμμές.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Βήμα 3: Εισαγωγή κελιών και συμπλήρωση με περιεχόμενο

Στη συνέχεια, κάνουμε επανάληψη για να εισάγουμε κελιά στον πίνακα. Για κάθε 7 κελιά, θα τερματίζουμε τη γραμμή για να δημιουργήσουμε μια νέα.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Βήμα 4: Προσθήκη σχήματος υδατογραφήματος

Τώρα, ας προσθέσουμε ένα υδατογράφημα στο έγγραφό μας. Θα δημιουργήσουμε ένα `Shape` αντικείμενο και ορίστε τις ιδιότητές του.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Εμφάνιση του σχήματος εκτός του κελιού του πίνακα, εάν πρόκειται να τοποθετηθεί σε ένα κελί.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Βήμα 5: Προσαρμόστε την εμφάνιση του υδατογραφήματος

Θα προσαρμόσουμε περαιτέρω την εμφάνιση του υδατογραφήματος ορίζοντας το χρώμα και τις ιδιότητες κειμένου.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Βήμα 6: Εισαγωγή υδατογραφήματος στο έγγραφο

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

## Βήμα 8: Αποθήκευση του εγγράφου

Τέλος, θα αποθηκεύσουμε το έγγραφό μας στον καθορισμένο κατάλογο.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Σύναψη

Και να το! Δημιουργήσατε με επιτυχία ένα έγγραφο Word με προσαρμοσμένη διάταξη πίνακα και προσθέσατε ένα υδατογράφημα χρησιμοποιώντας το Aspose.Words για .NET. Στόχος αυτού του σεμιναρίου ήταν να σας παρέχει έναν σαφή, βήμα προς βήμα οδηγό που θα σας βοηθήσει να κατανοήσετε κάθε μέρος της διαδικασίας. Με αυτές τις δεξιότητες, μπορείτε πλέον να δημιουργείτε πιο εξελιγμένα και προσαρμοσμένα έγγραφα Word μέσω προγραμματισμού.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω διαφορετική γραμματοσειρά για το κείμενο του υδατογραφήματος;
Ναι, μπορείτε να αλλάξετε τη γραμματοσειρά ορίζοντας το `watermark.TextPath.FontFamily` ιδιότητα στην επιθυμητή γραμματοσειρά.

### Πώς μπορώ να προσαρμόσω τη θέση του υδατογραφήματος;
Μπορείτε να τροποποιήσετε το `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, και `VerticalAlignment` ιδιότητες για να προσαρμόσετε τη θέση του υδατογραφήματος.

### Είναι δυνατόν να χρησιμοποιήσω εικόνα αντί για κείμενο για το υδατογράφημα;
Απολύτως! Μπορείτε να δημιουργήσετε ένα `Shape` με τον τύπο `ShapeType.Image` και ορίστε την εικόνα του χρησιμοποιώντας το `ImageData.SetImage` μέθοδος.

### Μπορώ να δημιουργήσω πίνακες με διαφορετικά ύψη γραμμών;
Ναι, μπορείτε να ορίσετε διαφορετικά ύψη για κάθε σειρά αλλάζοντας το `RowFormat.Height` ιδιότητα πριν από την εισαγωγή κελιών σε αυτήν τη γραμμή.

### Πώς μπορώ να αφαιρέσω ένα υδατογράφημα από ένα έγγραφο;
Μπορείτε να αφαιρέσετε το υδατογράφημα εντοπίζοντάς το στη συλλογή σχημάτων του εγγράφου και καλώντας το `Remove` μέθοδος.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}