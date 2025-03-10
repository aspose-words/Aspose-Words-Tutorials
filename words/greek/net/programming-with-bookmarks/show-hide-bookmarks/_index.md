---
title: Εμφάνιση απόκρυψης σελιδοδεικτών στο έγγραφο του Word
linktitle: Εμφάνιση απόκρυψης σελιδοδεικτών στο έγγραφο του Word
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να εμφανίζετε ή να αποκρύπτετε δυναμικά σελιδοδείκτες σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET με τον αναλυτικό οδηγό μας. Ιδανικό για προγραμματιστές.
weight: 10
url: /el/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εμφάνιση απόκρυψης σελιδοδεικτών στο έγγραφο του Word

## Εισαγωγή

Βρεθήκατε ποτέ να χρειάζεται να κρύψετε ή να εμφανίσετε ορισμένα μέρη του εγγράφου του Word δυναμικά; Λοιπόν, είσαι τυχερός! Με το Aspose.Words για .NET, μπορείτε να διαχειριστείτε εύκολα την ορατότητα του περιεχομένου με σελιδοδείκτη στα έγγραφά σας. Αυτό το σεμινάριο θα σας καθοδηγήσει στη διαδικασία εμφάνισης και απόκρυψης σελιδοδεικτών σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Θα αναλύσουμε τον κώδικα βήμα προς βήμα, οπότε είτε είστε έμπειρος προγραμματιστής είτε αρχάριος, θα βρείτε εύκολο να ακολουθήσετε αυτόν τον οδηγό.

## Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

1.  Aspose.Words για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη Aspose.Words για .NET. Εάν όχι, μπορείτε να το κατεβάσετε[εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Ένα IDE σαν το Visual Studio.
3. Βασικές γνώσεις C#: Η εξοικείωση με τον προγραμματισμό C# θα είναι επωφελής.
4. Ένα έγγραφο του Word: Ένα δείγμα εγγράφου του Word με σελιδοδείκτες.

## Εισαγωγή χώρων ονομάτων

Πριν ξεκινήσετε με τον κώδικα, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων. Προσθέστε τα ακόλουθα στην αρχή του αρχείου C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Βήμα 1: Φορτώστε το έγγραφό σας

Πρώτα πρώτα, πρέπει να φορτώσετε το έγγραφο του Word που περιέχει τους σελιδοδείκτες. Δείτε πώς μπορείτε να το κάνετε:

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Εξήγηση

- dataDir: Αυτή είναι η διαδρομή καταλόγου όπου βρίσκεται το έγγραφο του Word.
-  Document doc: Αυτό εκκινεί μια νέα παρουσία του`Document` τάξη με το καθορισμένο αρχείο σας.

## Βήμα 2: Εμφάνιση ή Απόκρυψη περιεχομένου με σελιδοδείκτη

Στη συνέχεια, θα ορίσουμε μια μέθοδο εμφάνισης ή απόκρυψης του σελιδοδείκτη περιεχομένου. Εδώ είναι η πλήρης μέθοδος:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Εξήγηση

- Σελιδοδείκτης bm: Ανακτά τον σελιδοδείκτη από το έγγραφο.
- Πρόγραμμα δημιουργίας DocumentBuilder: Βοηθά στην πλοήγηση και την τροποποίηση του εγγράφου.
- Πεδίο πεδίου: Εισάγει ένα πεδίο IF για να ελέγξει την κατάσταση του σελιδοδείκτη.
- Node currentNode: Διασχίζει τους κόμβους για να βρει την αρχή και το τέλος του πεδίου.

## Βήμα 3: Εκτελέστε τη συνάρτηση Εμφάνιση/Απόκρυψη

 Τώρα, πρέπει να καλέσετε το`ShowHideBookmarkedContent` μέθοδος, διαβίβαση του εγγράφου, όνομα σελιδοδείκτη και σημαία ορατότητας:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Εξήγηση

- doc: Το αντικείμενο του εγγράφου σας.
- "MyBookmark1": Το όνομα του σελιδοδείκτη που θέλετε να εμφανίσετε/κρύψετε.
- false: Η σημαία ορατότητας (αληθής για εμφάνιση, ψευδής για απόκρυψη).

## Βήμα 4: Αποθηκεύστε το έγγραφό σας

Τέλος, αποθηκεύστε το τροποποιημένο έγγραφο:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Εξήγηση

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Η διαδρομή και το όνομα του νέου εγγράφου όπου θα αποθηκευτούν οι αλλαγές.

## συμπέρασμα

Και εκεί το έχετε! Μάθατε με επιτυχία πώς να εμφανίζετε και να αποκρύπτετε σελιδοδείκτες σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η τεχνική μπορεί να είναι απίστευτα χρήσιμη για τη δυναμική δημιουργία εγγράφων με περιεχόμενο υπό όρους.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words για .NET είναι μια ισχυρή βιβλιοθήκη επεξεργασίας εγγράφων που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να μετατρέπουν έγγραφα του Word μέσω προγραμματισμού.

### Πώς μπορώ να αποκτήσω το Aspose.Words για .NET;
 Μπορείτε να κάνετε λήψη του Aspose.Words για .NET από[εδώ](https://releases.aspose.com/words/net/). Διατίθεται επίσης δωρεάν δοκιμή.

### Μπορώ να χρησιμοποιήσω αυτήν τη μέθοδο για άλλους τύπους σελιδοδεικτών;
Ναι, αυτή η μέθοδος μπορεί να προσαρμοστεί για τη διαχείριση της ορατότητας για τυχόν σελιδοδείκτες στο έγγραφο του Word.

### Τι γίνεται αν το έγγραφό μου δεν περιέχει τον καθορισμένο σελιδοδείκτη;
Εάν ο σελιδοδείκτης δεν υπάρχει, η μέθοδος θα εμφανίσει σφάλμα. Βεβαιωθείτε ότι ο σελιδοδείκτης υπάρχει πριν επιχειρήσετε να τον εμφανίσετε/κρύψετε.

### Πώς μπορώ να λάβω υποστήριξη εάν αντιμετωπίσω προβλήματα;
 Μπορείτε να λάβετε υποστήριξη από την κοινότητα Aspose[εδώ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
