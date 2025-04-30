---
"description": "Μάθετε πώς να δημιουργείτε και να μορφοποιείτε πίνακες σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET με αυτόν τον λεπτομερή οδηγό βήμα προς βήμα."
"linktitle": "Μορφοποιημένος πίνακας"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Μορφοποιημένος πίνακας"
"url": "/el/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Μορφοποιημένος πίνακας

## Εισαγωγή

Η δημιουργία και η μορφοποίηση πινάκων σε έγγραφα του Word μέσω προγραμματισμού μπορεί να φαίνεται σαν μια δύσκολη εργασία, αλλά με το Aspose.Words για .NET, γίνεται απλή και διαχειρίσιμη. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στον τρόπο δημιουργίας ενός μορφοποιημένου πίνακα σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Θα καλύψουμε τα πάντα, από τη ρύθμιση του περιβάλλοντός σας έως την αποθήκευση του εγγράφου σας με έναν όμορφα μορφοποιημένο πίνακα.

## Προαπαιτούμενα

Πριν εμβαθύνουμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

1. Aspose.Words για τη βιβλιοθήκη .NET: Κατεβάστε το από [εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον Ανάπτυξης: Ένα IDE όπως το Visual Studio.
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στον υπολογιστή σας.

## Εισαγωγή χώρων ονομάτων

Πριν γράψετε τον πραγματικό κώδικα, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Βήμα 1: Ρύθμιση του καταλόγου εγγράφων σας

Αρχικά, πρέπει να ορίσετε τη διαδρομή στην οποία θα αποθηκευτεί το έγγραφό σας.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Αντικαθιστώ `"YOUR DOCUMENT DIRECTORY"` με την πραγματική διαδρομή όπου θέλετε να αποθηκεύσετε το έγγραφο.

## Βήμα 2: Αρχικοποίηση του Εγγράφου και του DocumentBuilder

Τώρα, αρχικοποιήστε ένα νέο έγγραφο και ένα αντικείμενο DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο `DocumentBuilder` είναι μια βοηθητική κλάση που απλοποιεί τη διαδικασία δημιουργίας εγγράφων.

## Βήμα 3: Ξεκινήστε τον πίνακα

Στη συνέχεια, ξεκινήστε τη δημιουργία του πίνακα χρησιμοποιώντας το `StartTable` μέθοδος.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Η εισαγωγή ενός κελιού είναι απαραίτητη για την έναρξη του πίνακα.

## Βήμα 4: Εφαρμογή μορφοποίησης σε ολόκληρο τον πίνακα

Μπορείτε να εφαρμόσετε μορφοποίηση που επηρεάζει ολόκληρο τον πίνακα. Για παράδειγμα, ορίζοντας την αριστερή εσοχή:

```csharp
table.LeftIndent = 20.0;
```

## Βήμα 5: Μορφοποίηση της γραμμής κεφαλίδας

Ορίστε το ύψος, την στοίχιση και άλλες ιδιότητες για τη γραμμή κεφαλίδας.

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

Σε αυτό το βήμα, κάνουμε τη γραμμή κεφαλίδας να ξεχωρίζει ορίζοντας χρώμα φόντου, μέγεθος γραμματοσειράς και στοίχιση.

## Βήμα 6: Εισαγωγή επιπλέον κελιών κεφαλίδας

Εισαγωγή περισσότερων κελιών για τη γραμμή κεφαλίδας:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Βήμα 7: Μορφοποίηση των γραμμών σώματος

Αφού ρυθμίσετε την κεφαλίδα, μορφοποιήστε το κύριο μέρος του πίνακα:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Βήμα 8: Εισαγωγή γραμμών σώματος

Εισαγάγετε τις γραμμές του κύριου μέρους με περιεχόμενο:

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

## Βήμα 9: Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στον καθορισμένο κατάλογο:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Αυτό θα δημιουργήσει και θα αποθηκεύσει ένα έγγραφο Word με τον μορφοποιημένο πίνακα.

## Σύναψη

Και να το! Ακολουθώντας αυτά τα βήματα, μπορείτε να δημιουργήσετε έναν καλά μορφοποιημένο πίνακα σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η ισχυρή βιβλιοθήκη διευκολύνει τον προγραμματιστικό χειρισμό εγγράφων του Word, εξοικονομώντας σας χρόνο και προσπάθεια.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words για .NET είναι μια ισχυρή βιβλιοθήκη για τη δημιουργία, επεξεργασία και μετατροπή εγγράφων Word μέσω προγραμματισμού.

### Μπορώ να χρησιμοποιήσω διαφορετικά χρώματα για διαφορετικές σειρές;
Ναι, μπορείτε να εφαρμόσετε διαφορετική μορφοποίηση, συμπεριλαμβανομένων χρωμάτων, σε διαφορετικές γραμμές ή κελιά.

### Είναι το Aspose.Words για .NET δωρεάν;
Το Aspose.Words για .NET είναι μια βιβλιοθήκη επί πληρωμή, αλλά μπορείτε να αποκτήσετε ένα [δωρεάν δοκιμή](https://releases.aspose.com/).

### Πώς μπορώ να λάβω υποστήριξη για το Aspose.Words για .NET;
Μπορείτε να λάβετε υποστήριξη από το [Φόρουμ κοινότητας Aspose](https://forum.aspose.com/c/words/8).

### Μπορώ να δημιουργήσω άλλους τύπους εγγράφων με το Aspose.Words για .NET;
Ναι, το Aspose.Words για .NET υποστηρίζει διάφορες μορφές εγγράφων, όπως PDF, HTML και TXT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}