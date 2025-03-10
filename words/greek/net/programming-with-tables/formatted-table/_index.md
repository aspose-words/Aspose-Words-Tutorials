---
title: Μορφοποιημένος πίνακας
linktitle: Μορφοποιημένος πίνακας
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να δημιουργείτε και να μορφοποιείτε πίνακες σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET με αυτόν τον αναλυτικό οδηγό βήμα προς βήμα.
weight: 10
url: /el/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μορφοποιημένος πίνακας

## Εισαγωγή

Η δημιουργία και η μορφοποίηση πινάκων σε έγγραφα του Word μέσω προγραμματισμού μπορεί να φαίνεται σαν μια τρομακτική εργασία, αλλά με το Aspose.Words για .NET, γίνεται απλή και διαχειρίσιμη. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στον τρόπο δημιουργίας ενός μορφοποιημένου πίνακα σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Θα καλύψουμε τα πάντα, από τη ρύθμιση του περιβάλλοντος σας έως την αποθήκευση του εγγράφου σας με έναν όμορφα διαμορφωμένο πίνακα.

## Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

1. Aspose.Words for .NET Library: Κάντε λήψη του από[εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Ένα IDE σαν το Visual Studio.
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στον υπολογιστή σας.

## Εισαγωγή χώρων ονομάτων

Πριν γράψετε τον πραγματικό κώδικα, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Βήμα 1: Ρυθμίστε τον Κατάλογο Εγγράφων σας

Αρχικά, πρέπει να ορίσετε τη διαδρομή όπου θα αποθηκευτεί το έγγραφό σας.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Αντικαθιστώ`"YOUR DOCUMENT DIRECTORY"` με την πραγματική διαδρομή όπου θέλετε να αποθηκεύσετε το έγγραφο.

## Βήμα 2: Αρχικοποιήστε το Document και το DocumentBuilder

Τώρα, αρχικοποιήστε ένα νέο έγγραφο και ένα αντικείμενο DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ο`DocumentBuilder` είναι μια βοηθητική κλάση που απλοποιεί τη διαδικασία δημιουργίας εγγράφων.

## Βήμα 3: Ξεκινήστε τον πίνακα

 Στη συνέχεια, ξεκινήστε τη δημιουργία του πίνακα χρησιμοποιώντας το`StartTable` μέθοδος.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Η εισαγωγή ενός κελιού είναι απαραίτητη για την έναρξη του πίνακα.

## Βήμα 4: Εφαρμογή μορφοποίησης σε όλο τον πίνακα

Μπορείτε να εφαρμόσετε μορφοποίηση που επηρεάζει ολόκληρο τον πίνακα. Για παράδειγμα, ορίζοντας την αριστερή εσοχή:

```csharp
table.LeftIndent = 20.0;
```

## Βήμα 5: Μορφοποιήστε τη γραμμή κεφαλίδας

Ορίστε το ύψος, τη στοίχιση και άλλες ιδιότητες για τη σειρά κεφαλίδας.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Σε αυτό το βήμα, κάνουμε τη σειρά της κεφαλίδας να ξεχωρίζει ορίζοντας ένα χρώμα φόντου, μέγεθος γραμματοσειράς και στοίχιση.

## Βήμα 6: Εισαγάγετε πρόσθετα κελιά κεφαλίδας

Εισαγάγετε περισσότερα κελιά για τη σειρά κεφαλίδας:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Βήμα 7: Μορφοποιήστε τις γραμμές σώματος

Αφού ρυθμίσετε την κεφαλίδα, μορφοποιήστε το σώμα του πίνακα:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Βήμα 8: Εισαγάγετε γραμμές σώματος

Εισαγάγετε τις γραμμές του σώματος με περιεχόμενο:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Επαναλάβετε για επιπλέον σειρές:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Βήμα 9: Αποθηκεύστε το έγγραφο

Τέλος, αποθηκεύστε το έγγραφο στον καθορισμένο κατάλογο:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Αυτό θα δημιουργήσει και θα αποθηκεύσει ένα έγγραφο του Word με τον μορφοποιημένο πίνακα.

## Σύναψη

Και ορίστε το! Ακολουθώντας αυτά τα βήματα, μπορείτε να δημιουργήσετε έναν καλά διαμορφωμένο πίνακα σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η ισχυρή βιβλιοθήκη διευκολύνει τον προγραμματισμό των εγγράφων του Word, εξοικονομώντας χρόνο και προσπάθεια.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words for .NET είναι μια ισχυρή βιβλιοθήκη για τη δημιουργία, την επεξεργασία και τη μετατροπή εγγράφων του Word μέσω προγραμματισμού.

### Μπορώ να χρησιμοποιήσω διαφορετικά χρώματα για διαφορετικές σειρές;
Ναι, μπορείτε να εφαρμόσετε διαφορετική μορφοποίηση, συμπεριλαμβανομένων των χρωμάτων, σε διαφορετικές σειρές ή κελιά.

### Είναι δωρεάν το Aspose.Words για .NET;
 Το Aspose.Words για .NET είναι μια πληρωμένη βιβλιοθήκη, αλλά μπορείτε να λάβετε ένα[δωρεάν δοκιμή](https://releases.aspose.com/).

### Πώς μπορώ να λάβω υποστήριξη για το Aspose.Words για .NET;
 Μπορείτε να λάβετε υποστήριξη από το[Υποστηρίξτε φόρουμ κοινότητας](https://forum.aspose.com/c/words/8).

### Μπορώ να δημιουργήσω άλλους τύπους εγγράφων με το Aspose.Words για .NET;
Ναι, το Aspose.Words για .NET υποστηρίζει διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των PDF, HTML και TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
