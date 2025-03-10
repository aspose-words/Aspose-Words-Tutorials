---
title: Εισαγωγή εγγράφου στη συγχώνευση αλληλογραφίας
linktitle: Εισαγωγή εγγράφου στη συγχώνευση αλληλογραφίας
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εισάγετε έγγραφα σε πεδία συγχώνευσης αλληλογραφίας χρησιμοποιώντας το Aspose.Words για .NET σε αυτόν τον αναλυτικό, βήμα προς βήμα εκμάθηση.
weight: 10
url: /el/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή εγγράφου στη συγχώνευση αλληλογραφίας

## Εισαγωγή

Καλώς ήρθατε στον κόσμο της αυτοματοποίησης εγγράφων με το Aspose.Words για .NET! Έχετε αναρωτηθεί ποτέ πώς να εισάγετε δυναμικά έγγραφα σε συγκεκριμένα πεδία ενός κύριου εγγράφου κατά τη διάρκεια μιας λειτουργίας συγχώνευσης αλληλογραφίας; Λοιπόν, είσαι στο σωστό μέρος. Αυτό το σεμινάριο θα σας καθοδηγήσει βήμα προς βήμα στη διαδικασία εισαγωγής εγγράφων στα πεδία συγχώνευσης αλληλογραφίας χρησιμοποιώντας το Aspose.Words για .NET. Είναι σαν να συναρμολογείτε ένα παζλ, όπου κάθε κομμάτι μπαίνει τέλεια στη θέση του. Λοιπόν, ας βουτήξουμε!

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

1.  Aspose.Words για .NET: Μπορείτε[κατεβάστε την τελευταία έκδοση εδώ](https://releases.aspose.com/words/net/) . Εάν χρειάζεται να αγοράσετε άδεια, μπορείτε να το κάνετε[εδώ](https://purchase.aspose.com/buy) . Εναλλακτικά, μπορείτε να πάρετε ένα[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/) ή δοκιμάστε το με ένα[δωρεάν δοκιμή](https://releases.aspose.com/).
2. Περιβάλλον ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο C# IDE.
3. Βασικές γνώσεις C#: Η εξοικείωση με τον προγραμματισμό C# θα κάνει αυτό το σεμινάριο παιχνιδάκι.

## Εισαγωγή χώρων ονομάτων

Πρώτα πράγματα πρώτα, θα χρειαστεί να εισαγάγετε τους απαραίτητους χώρους ονομάτων. Αυτά είναι σαν τα δομικά στοιχεία του έργου σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Ας αναλύσουμε τη διαδικασία σε διαχειρίσιμα βήματα. Κάθε βήμα θα βασίζεται στο προηγούμενο, οδηγώντας σας σε μια ολοκληρωμένη λύση.

## Βήμα 1: Ρύθμιση του καταλόγου σας

Για να μπορέσετε να ξεκινήσετε την εισαγωγή εγγράφων, πρέπει να ορίσετε τη διαδρομή προς τον κατάλογο των εγγράφων σας. Εδώ αποθηκεύονται τα έγγραφά σας.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Βήμα 2: Φόρτωση του κύριου εγγράφου

Στη συνέχεια, θα φορτώσετε το κύριο έγγραφο. Αυτό το έγγραφο περιέχει τα πεδία συγχώνευσης όπου θα εισαχθούν άλλα έγγραφα.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Βήμα 3: Ρύθμιση της επιστροφής κλήσης συγχώνευσης πεδίων

Για να χειριστείτε τη διαδικασία συγχώνευσης, θα χρειαστεί να ορίσετε μια λειτουργία επανάκλησης. Αυτή η λειτουργία θα είναι υπεύθυνη για την εισαγωγή εγγράφων στα καθορισμένα πεδία συγχώνευσης.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Βήμα 4: Εκτέλεση της συγχώνευσης αλληλογραφίας

Τώρα ήρθε η ώρα να εκτελέσετε τη συγχώνευση αλληλογραφίας. Εδώ συμβαίνει η μαγεία. Θα καθορίσετε το πεδίο συγχώνευσης και το έγγραφο που πρέπει να εισαχθεί σε αυτό το πεδίο.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Βήμα 5: Αποθήκευση του εγγράφου

Αφού ολοκληρωθεί η συγχώνευση αλληλογραφίας, θα αποθηκεύσετε το τροποποιημένο έγγραφο. Αυτό το νέο έγγραφο θα έχει το περιεχόμενο που έχει εισαχθεί ακριβώς εκεί που θέλετε.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Βήμα 6: Δημιουργία του Χειριστή επανάκλησης

Ο χειριστής επανάκλησης είναι μια κλάση που κάνει ειδική επεξεργασία για το πεδίο συγχώνευσης. Φορτώνει το έγγραφο που καθορίζεται στην τιμή πεδίου και το εισάγει στο τρέχον πεδίο συγχώνευσης.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Βήμα 7: Εισαγωγή του Εγγράφου

Αυτή η μέθοδος εισάγει το καθορισμένο έγγραφο στην τρέχουσα παράγραφο ή κελί πίνακα.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Σύναψη

Και ορίστε το! Έχετε εισαγάγει επιτυχώς έγγραφα σε συγκεκριμένα πεδία κατά τη διάρκεια μιας λειτουργίας συγχώνευσης αλληλογραφίας χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η ισχυρή λειτουργία μπορεί να σας εξοικονομήσει πολύ χρόνο και προσπάθεια, ειδικά όταν ασχολείστε με μεγάλους όγκους εγγράφων. Σκεφτείτε το σαν να έχετε έναν προσωπικό βοηθό που φροντίζει για όλα τα βαρέα για εσάς. Λοιπόν, προχωρήστε και δοκιμάστε το. Καλή κωδικοποίηση!

## Συχνές ερωτήσεις

### Μπορώ να εισάγω πολλά έγγραφα σε διαφορετικά πεδία συγχώνευσης;
Ναι, μπορείς. Απλώς καθορίστε τα κατάλληλα πεδία συγχώνευσης και τις αντίστοιχες διαδρομές εγγράφου στο`MailMerge.Execute` μέθοδος.

### Είναι δυνατό να μορφοποιήσετε το εισαγόμενο έγγραφο διαφορετικά από το κύριο έγγραφο;
 Απολύτως! Μπορείτε να χρησιμοποιήσετε το`ImportFormatMode` παράμετρος στο`NodeImporter` για τον έλεγχο της μορφοποίησης.

### Τι γίνεται αν το όνομα του πεδίου συγχώνευσης είναι δυναμικό;
Μπορείτε να χειριστείτε ονόματα πεδίων δυναμικής συγχώνευσης μεταβιβάζοντάς τα ως παραμέτρους στον χειριστή επανάκλησης.

### Μπορώ να χρησιμοποιήσω αυτήν τη μέθοδο με διαφορετικές μορφές αρχείων;
Ναι, το Aspose.Words υποστηρίζει διάφορες μορφές αρχείων, όπως DOCX, PDF και άλλα.

### Πώς μπορώ να χειριστώ τα σφάλματα κατά τη διαδικασία εισαγωγής εγγράφου;
Εφαρμόστε τη διαχείριση σφαλμάτων στο πρόγραμμα χειρισμού επανάκλησης για να διαχειριστείτε τυχόν εξαιρέσεις που ενδέχεται να προκύψουν.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
