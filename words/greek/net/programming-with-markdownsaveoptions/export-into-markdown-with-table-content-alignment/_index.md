---
title: Εξαγωγή σε Markdown με ευθυγράμμιση περιεχομένου πίνακα
linktitle: Εξαγωγή σε Markdown με ευθυγράμμιση περιεχομένου πίνακα
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εξάγετε έγγραφα του Word στο Markdown με στοιχισμένους πίνακες χρησιμοποιώντας το Aspose.Words για .NET. Ακολουθήστε τον βήμα προς βήμα οδηγό μας για τέλειους πίνακες Markdown.
weight: 10
url: /el/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή σε Markdown με ευθυγράμμιση περιεχομένου πίνακα

## Εισαγωγή

Γεια σου! Αναρωτηθήκατε ποτέ πώς να εξάγετε το έγγραφο Word σας σε μορφή Markdown με τέλεια ευθυγραμμισμένους πίνακες; Είτε είστε προγραμματιστής που εργάζεται σε τεκμηρίωση είτε απλώς κάποιος που αγαπά το Markdown, αυτός ο οδηγός είναι για εσάς. Θα προσπαθήσουμε να χρησιμοποιήσουμε το Aspose.Words για το .NET για να το πετύχουμε αυτό. Είστε έτοιμοι να μετατρέψετε τους πίνακες του Word σε πίνακες Markdown που έχουν ευθυγραμμιστεί σωστά; Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, υπάρχουν μερικά πράγματα που θα πρέπει να έχετε στη θέση του:

1.  Aspose.Words για .NET Library: Βεβαιωθείτε ότι έχετε τη βιβλιοθήκη Aspose.Words για .NET. Μπορείτε να το κατεβάσετε από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Ρυθμίστε το αναπτυξιακό σας περιβάλλον. Το Visual Studio είναι μια δημοφιλής επιλογή για ανάπτυξη .NET.
3. Βασικές γνώσεις C#: Η κατανόηση της C# είναι απαραίτητη καθώς θα γράφουμε κώδικα σε αυτή τη γλώσσα.
4. Δείγμα εγγράφου Word: Έχετε ένα έγγραφο του Word που μπορείτε να χρησιμοποιήσετε για δοκιμή.

## Εισαγωγή χώρων ονομάτων

Πριν ξεκινήσουμε την κωδικοποίηση, ας εισάγουμε τους απαραίτητους χώρους ονομάτων. Αυτά θα μας δώσουν πρόσβαση στις τάξεις και τις μεθόδους Aspose.Words που θα χρησιμοποιήσουμε.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Βήμα 1: Αρχικοποιήστε το Document and DocumentBuilder

Πρώτα πράγματα πρώτα, πρέπει να δημιουργήσουμε ένα νέο έγγραφο του Word και να αρχικοποιήσουμε ένα`DocumentBuilder` αντιταχθούμε να ξεκινήσουμε τη δημιουργία του εγγράφου μας.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Δημιουργήστε ένα νέο έγγραφο.
Document doc = new Document();

// Εκκινήστε το DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Εισαγωγή κελιών και ευθυγράμμιση περιεχομένου

Στη συνέχεια, θα εισαγάγουμε μερικά κελιά στο έγγραφό μας και θα ορίσουμε την ευθυγράμμισή τους. Αυτό είναι ζωτικής σημασίας για τη διασφάλιση ότι η εξαγωγή Markdown διατηρεί τη σωστή ευθυγράμμιση.

```csharp
// Εισαγάγετε ένα κελί και ορίστε τη στοίχιση προς τα δεξιά.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Εισαγάγετε ένα άλλο κελί και ορίστε τη στοίχιση στο κέντρο.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Βήμα 3: Ορίστε τη στοίχιση περιεχομένου πίνακα για εξαγωγή Markdown

 Τώρα, ήρθε η ώρα να διαμορφώσετε το`MarkdownSaveOptions` για να ελέγξετε τη στοίχιση του περιεχομένου του πίνακα στο εξαγόμενο αρχείο Markdown. Θα αποθηκεύσουμε το έγγραφο με διαφορετικές ρυθμίσεις ευθυγράμμισης για να δούμε πώς λειτουργεί.

```csharp
// Δημιουργήστε αντικείμενο MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Αποθήκευση εγγράφου με αριστερή στοίχιση.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Αλλάξτε τη στοίχιση προς τα δεξιά και αποθηκεύστε.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Αλλάξτε τη στοίχιση στο κέντρο και αποθηκεύστε.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Βήμα 4: Χρησιμοποιήστε την αυτόματη στοίχιση περιεχομένου πίνακα

 Ο`Auto`Η επιλογή στοίχισης παίρνει τη στοίχιση από την πρώτη παράγραφο στην αντίστοιχη στήλη πίνακα. Αυτό μπορεί να είναι βολικό όταν έχετε μικτές ευθυγραμμίσεις σε ένα μόνο τραπέζι.

```csharp
// Ορίστε τη στοίχιση σε Αυτόματη.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Αποθήκευση εγγράφου με αυτόματη ευθυγράμμιση.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Σύναψη

Και ορίστε το! Η εξαγωγή εγγράφων του Word στο Markdown με ευθυγραμμισμένους πίνακες χρησιμοποιώντας το Aspose.Words για .NET είναι παιχνιδάκι μόλις μάθετε πώς να το κάνετε. Αυτή η ισχυρή βιβλιοθήκη διευκολύνει τον έλεγχο της μορφοποίησης και της ευθυγράμμισης των πινάκων σας, διασφαλίζοντας ότι τα έγγραφά σας Markdown φαίνονται ακριβώς όπως τα θέλετε. Καλή κωδικοποίηση!

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words για .NET είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν, να μετατρέπουν και να εξάγουν έγγραφα του Word μέσω προγραμματισμού.

### Μπορώ να ορίσω διαφορετικές στοίχιση για διαφορετικές στήλες στον ίδιο πίνακα;
 Ναι, χρησιμοποιώντας το`Auto` επιλογή στοίχισης, μπορείτε να έχετε διαφορετικές στοίχιση με βάση την πρώτη παράγραφο σε κάθε στήλη.

### Χρειάζομαι άδεια χρήσης για να χρησιμοποιήσω το Aspose.Words για .NET;
 Ναι, το Aspose.Words για .NET απαιτεί άδεια χρήσης για πλήρη λειτουργικότητα. Μπορείτε να πάρετε ένα[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/) για αξιολόγηση.

### Είναι δυνατή η εξαγωγή άλλων στοιχείων εγγράφου στο Markdown χρησιμοποιώντας το Aspose.Words;
Ναι, το Aspose.Words υποστηρίζει την εξαγωγή διαφόρων στοιχείων όπως επικεφαλίδες, λίστες και εικόνες σε μορφή Markdown.

### Πού μπορώ να λάβω υποστήριξη εάν αντιμετωπίσω προβλήματα;
 Μπορείτε να λάβετε υποστήριξη από το[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
