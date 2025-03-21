---
title: Εισαγωγή σχήματος
linktitle: Εισαγωγή σχήματος
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εισάγετε και να χειρίζεστε σχήματα σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET με τον αναλυτικό οδηγό μας.
weight: 10
url: /el/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος

## Εισαγωγή

Όταν πρόκειται για τη δημιουργία οπτικά ελκυστικών και καλά δομημένων εγγράφων του Word, τα σχήματα μπορούν να διαδραματίσουν ζωτικό ρόλο. Είτε προσθέτετε βέλη, πλαίσια ή ακόμα και πολύπλοκα προσαρμοσμένα σχήματα, η δυνατότητα χειρισμού αυτών των στοιχείων μέσω προγραμματισμού προσφέρει απαράμιλλη ευελιξία. Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο εισαγωγής και χειρισμού σχημάτων σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET.

## Προαπαιτούμενα

Πριν βουτήξετε στο σεμινάριο, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

1.  Aspose.Words για .NET: Κάντε λήψη και εγκατάσταση της πιο πρόσφατης έκδοσης από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Ένα κατάλληλο περιβάλλον ανάπτυξης .NET όπως το Visual Studio.
3. Βασικές γνώσεις C#: Εξοικείωση με τη γλώσσα προγραμματισμού C# και βασικές έννοιες.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, θα χρειαστεί να εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Βήμα 1: Ρύθμιση του έργου σας

Για να μπορέσετε να ξεκινήσετε την εισαγωγή σχημάτων, πρέπει να ρυθμίσετε το έργο σας και να προσθέσετε τη βιβλιοθήκη Aspose.Words για .NET.

1. Δημιουργία νέου έργου: Ανοίξτε το Visual Studio και δημιουργήστε ένα νέο έργο εφαρμογής κονσόλας C#.
2. Προσθήκη Aspose.Words για .NET: Εγκαταστήστε τη βιβλιοθήκη Aspose.Words για .NET μέσω του NuGet Package Manager.

```bash
Install-Package Aspose.Words
```

## Βήμα 2: Αρχικοποιήστε το έγγραφο

Αρχικά, θα χρειαστεί να αρχικοποιήσετε ένα νέο έγγραφο και ένα πρόγραμμα δημιουργίας εγγράφων, το οποίο θα σας βοηθήσει στη δημιουργία του εγγράφου.

```csharp
// Διαδρομή στον κατάλογο εγγράφων σας
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Αρχικοποιήστε ένα νέο έγγραφο
Document doc = new Document();

// Αρχικοποιήστε ένα DocumentBuilder για να βοηθήσει στη δημιουργία του εγγράφου
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 3: Εισαγάγετε ένα σχήμα

Τώρα, ας εισαγάγουμε ένα σχήμα στο έγγραφο. Θα ξεκινήσουμε προσθέτοντας ένα απλό πλαίσιο κειμένου.

```csharp
// Εισαγάγετε ένα σχήμα πλαισίου κειμένου στο έγγραφο
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Περιστρέψτε το σχήμα
shape.Rotation = 30.0;
```

Σε αυτό το παράδειγμα, εισάγουμε ένα πλαίσιο κειμένου στη θέση (100, 100) με πλάτος και ύψος 50 μονάδες το καθένα. Περιστρέφουμε επίσης το σχήμα κατά 30 μοίρες.

## Βήμα 4: Προσθέστε ένα άλλο σχήμα

Ας προσθέσουμε ένα άλλο σχήμα στο έγγραφο, αυτή τη φορά χωρίς να καθορίσουμε τη θέση.

```csharp
// Προσθέστε ένα άλλο σχήμα πλαισίου κειμένου
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Περιστρέψτε το σχήμα
secondShape.Rotation = 30.0;
```

Αυτό το απόσπασμα κώδικα εισάγει ένα άλλο πλαίσιο κειμένου με τις ίδιες διαστάσεις και περιστροφή με το πρώτο αλλά χωρίς να προσδιορίζει τη θέση του.

## Βήμα 5: Αποθηκεύστε το έγγραφο

 Μετά την προσθήκη των σχημάτων, το τελευταίο βήμα είναι η αποθήκευση του εγγράφου. Θα χρησιμοποιήσουμε το`OoxmlSaveOptions` για να καθορίσετε τη μορφή αποθήκευσης.

```csharp
// Καθορίστε τις επιλογές αποθήκευσης με συμμόρφωση
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Αποθηκεύστε το έγγραφο
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Σύναψη

Και ορίστε το! Έχετε εισαγάγει και χειριστεί με επιτυχία σχήματα σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτό το σεμινάριο κάλυψε τα βασικά, αλλά το Aspose.Words προσφέρει πολλές πιο προηγμένες δυνατότητες για εργασία με σχήματα, όπως προσαρμοσμένα στυλ, συνδέσεις και σχήματα ομάδας.

 Για πιο αναλυτικές πληροφορίες, επισκεφθείτε το[Aspose.Words για τεκμηρίωση .NET](https://reference.aspose.com/words/net/).

## Συχνές ερωτήσεις

### Πώς εισάγω διαφορετικούς τύπους σχημάτων;
Μπορείτε να αλλάξετε το`ShapeType` στο`InsertShape` μέθοδος εισαγωγής διαφορετικών τύπων σχημάτων όπως κύκλοι, ορθογώνια και βέλη.

### Μπορώ να προσθέσω κείμενο μέσα στα σχήματα;
 Ναι, μπορείτε να χρησιμοποιήσετε το`builder.Write` μέθοδος προσθήκης κειμένου μέσα στα σχήματα μετά την εισαγωγή τους.

### Είναι δυνατόν να διαμορφώσετε τα σχήματα;
 Ναι, μπορείτε να διαμορφώσετε τα σχήματα ορίζοντας ιδιότητες όπως`FillColor`, `StrokeColor` , και`StrokeWeight`.

### Πώς τοποθετώ τα σχήματα σε σχέση με άλλα στοιχεία;
 Χρησιμοποιήστε το`RelativeHorizontalPosition` και`RelativeVerticalPosition` ιδιότητες για την τοποθέτηση σχημάτων σε σχέση με άλλα στοιχεία του εγγράφου.

### Μπορώ να ομαδοποιήσω πολλά σχήματα μαζί;
 Ναι, το Aspose.Words για .NET σάς επιτρέπει να ομαδοποιείτε σχήματα χρησιμοποιώντας το`GroupShape` τάξη.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
