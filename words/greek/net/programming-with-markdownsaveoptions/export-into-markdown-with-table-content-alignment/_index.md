---
"description": "Μάθετε πώς να εξάγετε έγγραφα Word στο Markdown με ευθυγραμμισμένους πίνακες χρησιμοποιώντας το Aspose.Words για .NET. Ακολουθήστε τον αναλυτικό οδηγό μας για τέλειους πίνακες Markdown."
"linktitle": "Εξαγωγή σε Markdown με στοίχιση περιεχομένου πίνακα"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Εξαγωγή σε Markdown με στοίχιση περιεχομένου πίνακα"
"url": "/el/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή σε Markdown με στοίχιση περιεχομένου πίνακα

## Εισαγωγή

Γεια σας! Αναρωτηθήκατε ποτέ πώς να εξάγετε το έγγραφό σας στο Word σε μορφή Markdown με τέλεια ευθυγραμμισμένους πίνακες; Είτε είστε προγραμματιστής που εργάζεται σε τεκμηρίωση είτε απλώς κάποιος που αγαπά το Markdown, αυτός ο οδηγός είναι για εσάς. Θα εμβαθύνουμε στις λεπτομέρειες της χρήσης του Aspose.Words για .NET για να το πετύχουμε αυτό. Είστε έτοιμοι να μετατρέψετε τους πίνακες του Word σας σε τακτοποιημένα ευθυγραμμισμένους πίνακες Markdown; Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν εμβαθύνουμε στον κώδικα, υπάρχουν μερικά πράγματα που θα πρέπει να έχετε στη διάθεσή σας:

1. Aspose.Words για βιβλιοθήκη .NET: Βεβαιωθείτε ότι έχετε τη βιβλιοθήκη Aspose.Words για .NET. Μπορείτε να την κατεβάσετε από το [Σελίδα έκδοσης Aspose](https://releases.aspose.com/words/net/).
2. Περιβάλλον Ανάπτυξης: Ρυθμίστε το περιβάλλον ανάπτυξής σας. Το Visual Studio είναι μια δημοφιλής επιλογή για ανάπτυξη .NET.
3. Βασικές γνώσεις C#: Η κατανόηση της C# είναι απαραίτητη, καθώς θα γράφουμε κώδικα σε αυτήν τη γλώσσα.
4. Δείγμα εγγράφου Word: Να έχετε ένα έγγραφο Word που μπορείτε να χρησιμοποιήσετε για δοκιμές.

## Εισαγωγή χώρων ονομάτων

Πριν ξεκινήσουμε τον προγραμματισμό, ας εισαγάγουμε τους απαραίτητους χώρους ονομάτων. Αυτοί θα μας δώσουν πρόσβαση στις κλάσεις και τις μεθόδους Aspose.Words που θα χρησιμοποιήσουμε.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Βήμα 1: Αρχικοποίηση Εγγράφου και DocumentBuilder

Πρώτα απ 'όλα, πρέπει να δημιουργήσουμε ένα νέο έγγραφο του Word και να το αρχικοποιήσουμε. `DocumentBuilder` αντίρρηση για να ξεκινήσουμε τη δημιουργία του εγγράφου μας.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Δημιουργήστε ένα νέο έγγραφο.
Document doc = new Document();

// Αρχικοποίηση του DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Εισαγωγή κελιών και στοίχιση περιεχομένου

Στη συνέχεια, θα εισαγάγουμε ορισμένα κελιά στο έγγραφό μας και θα ορίσουμε την ευθυγράμμισή τους. Αυτό είναι κρίσιμο για να διασφαλίσουμε ότι η εξαγωγή Markdown διατηρεί τη σωστή ευθυγράμμιση.

```csharp
// Εισαγάγετε ένα κελί και ορίστε τη στοίχιση προς τα δεξιά.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Εισαγάγετε ένα άλλο κελί και ορίστε την ευθυγράμμιση στο κέντρο.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Βήμα 3: Ορισμός στοίχισης περιεχομένου πίνακα για εξαγωγή Markdown

Τώρα, ήρθε η ώρα να διαμορφώσετε το `MarkdownSaveOptions` για να ελέγξετε την ευθυγράμμιση του περιεχομένου του πίνακα στο εξαγόμενο αρχείο Markdown. Θα αποθηκεύσουμε το έγγραφο με διαφορετικές ρυθμίσεις ευθυγράμμισης για να δούμε πώς λειτουργεί.

```csharp
// Δημιουργήστε το αντικείμενο MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Αποθήκευση εγγράφου με αριστερή στοίχιση.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Αλλάξτε τη στοίχιση προς τα δεξιά και αποθηκεύστε.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Αλλάξτε την στοίχιση στο κέντρο και αποθηκεύστε.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Βήμα 4: Χρήση αυτόματης στοίχισης περιεχομένου πίνακα

Ο `Auto` Η επιλογή στοίχισης λαμβάνει τη στοίχιση από την πρώτη παράγραφο στην αντίστοιχη στήλη του πίνακα. Αυτό μπορεί να είναι χρήσιμο όταν έχετε μικτές στοίχισης σε έναν μόνο πίνακα.

```csharp
// Ορίστε την ευθυγράμμιση σε Αυτόματη.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Αποθήκευση εγγράφου με αυτόματη ευθυγράμμιση.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Σύναψη

Και να το! Η εξαγωγή εγγράφων Word στο Markdown με ευθυγραμμισμένους πίνακες χρησιμοποιώντας το Aspose.Words για .NET είναι παιχνιδάκι μόλις μάθετε πώς να το κάνετε. Αυτή η ισχυρή βιβλιοθήκη διευκολύνει τον έλεγχο της μορφοποίησης και της ευθυγράμμισης των πινάκων σας, διασφαλίζοντας ότι τα έγγραφά σας στο Markdown θα φαίνονται ακριβώς όπως τα θέλετε. Καλή κωδικοποίηση!

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words για .NET είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν, να μετατρέπουν και να εξάγουν έγγραφα του Word μέσω προγραμματισμού.

### Μπορώ να ορίσω διαφορετικές στοίχισης για διαφορετικές στήλες στον ίδιο πίνακα;
Ναι, χρησιμοποιώντας το `Auto` Με την επιλογή στοίχισης, μπορείτε να έχετε διαφορετικές στοίχισης με βάση την πρώτη παράγραφο σε κάθε στήλη.

### Χρειάζομαι άδεια χρήσης για να χρησιμοποιήσω το Aspose.Words για .NET;
Ναι, το Aspose.Words για .NET απαιτεί άδεια χρήσης για πλήρη λειτουργικότητα. Μπορείτε να αποκτήσετε μια [προσωρινή άδεια](https://purchase.aspose.com/temporary-license/) για αξιολόγηση.

### Είναι δυνατή η εξαγωγή άλλων στοιχείων εγγράφου στο Markdown χρησιμοποιώντας το Aspose.Words;
Ναι, το Aspose.Words υποστηρίζει την εξαγωγή διαφόρων στοιχείων όπως επικεφαλίδες, λίστες και εικόνες σε μορφή Markdown.

### Πού μπορώ να βρω υποστήριξη σε περίπτωση που αντιμετωπίσω κάποιο πρόβλημα;
Μπορείτε να λάβετε υποστήριξη από το [Φόρουμ υποστήριξης Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}