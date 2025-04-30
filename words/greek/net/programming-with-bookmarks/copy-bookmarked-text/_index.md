---
"description": "Αντιγράψτε εύκολα κείμενο με σελιδοδείκτες μεταξύ εγγράφων Word χρησιμοποιώντας το Aspose.Words για .NET. Μάθετε πώς με αυτόν τον οδηγό βήμα προς βήμα."
"linktitle": "Αντιγραφή κειμένου με σελιδοδείκτη σε έγγραφο του Word"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Αντιγραφή κειμένου με σελιδοδείκτη σε έγγραφο του Word"
"url": "/el/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αντιγραφή κειμένου με σελιδοδείκτη σε έγγραφο του Word

## Εισαγωγή

Έχετε ποτέ χρειαστεί να αντιγράψετε συγκεκριμένες ενότητες από ένα έγγραφο του Word σε ένα άλλο; Λοιπόν, είστε τυχεροί! Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στον τρόπο αντιγραφής κειμένου με σελιδοδείκτες από ένα έγγραφο του Word σε ένα άλλο χρησιμοποιώντας το Aspose.Words για .NET. Είτε δημιουργείτε μια δυναμική αναφορά είτε αυτοματοποιείτε τη δημιουργία εγγράφων, αυτός ο οδηγός θα απλοποιήσει τη διαδικασία για εσάς.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

- Aspose.Words για τη βιβλιοθήκη .NET: Μπορείτε να το κατεβάσετε από [εδώ](https://releases.aspose.com/words/net/).
- Περιβάλλον Ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο περιβάλλον ανάπτυξης .NET.
- Βασικές γνώσεις C#: Εξοικείωση με τον προγραμματισμό C# και το .NET framework.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, βεβαιωθείτε ότι έχετε εισαγάγει τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Βήμα 1: Φόρτωση του εγγράφου προέλευσης

Πρώτα απ 'όλα, πρέπει να φορτώσετε το έγγραφο προέλευσης που περιέχει το κείμενο με σελιδοδείκτη που θέλετε να αντιγράψετε.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Εδώ, `dataDir` είναι η διαδρομή προς τον κατάλογο εγγράφων σας και `Bookmarks.docx` είναι το έγγραφο πηγής.

## Βήμα 2: Προσδιορίστε τον σελιδοδείκτη

Στη συνέχεια, προσδιορίστε τον σελιδοδείκτη που θέλετε να αντιγράψετε από το έγγραφο προέλευσης.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Αντικαθιστώ `"MyBookmark1"` με το πραγματικό όνομα του σελιδοδείκτη σας.

## Βήμα 3: Δημιουργήστε το έγγραφο προορισμού

Τώρα, δημιουργήστε ένα νέο έγγραφο όπου θα αντιγραφεί το κείμενο που έχετε προσθέσει στους σελιδοδείκτες.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Βήμα 4: Εισαγωγή περιεχομένου σελιδοδεικτών

Για να διασφαλίσετε ότι τα στυλ και η μορφοποίηση διατηρούνται, χρησιμοποιήστε `NodeImporter` για να εισαγάγετε το περιεχόμενο που έχει προστεθεί στους σελιδοδείκτες από το έγγραφο προέλευσης στο έγγραφο προορισμού.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Βήμα 5: Ορίστε τη μέθοδο AppendBookmarkedText

Εδώ είναι που συμβαίνει η μαγεία. Ορίστε μια μέθοδο για τον χειρισμό της αντιγραφής του κειμένου που έχει προστεθεί στους σελιδοδείκτες:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Βήμα 6: Αποθήκευση του εγγράφου προορισμού

Τέλος, αποθηκεύστε το έγγραφο προορισμού για να επαληθεύσετε το αντιγραμμένο περιεχόμενο.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Σύναψη

Και αυτό είναι όλο! Αντιγράψατε με επιτυχία κείμενο με σελιδοδείκτες από ένα έγγραφο του Word σε ένα άλλο χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η μέθοδος είναι ισχυρή για την αυτοματοποίηση εργασιών χειρισμού εγγράφων, καθιστώντας τη ροή εργασίας σας πιο αποτελεσματική και βελτιστοποιημένη.

## Συχνές ερωτήσεις

### Μπορώ να αντιγράψω πολλούς σελιδοδείκτες ταυτόχρονα;
Ναι, μπορείτε να κάνετε επανάληψη σε πολλαπλούς σελιδοδείκτες και να χρησιμοποιήσετε την ίδια μέθοδο για να αντιγράψετε τον καθένα.

### Τι συμβαίνει εάν δεν βρεθεί ο σελιδοδείκτης;
Ο `Range.Bookmarks` η περιουσία θα επιστρέψει `null`, επομένως φροντίστε να χειριστείτε αυτήν την περίπτωση για να αποφύγετε εξαιρέσεις.

### Μπορώ να διατηρήσω τη μορφοποίηση του αρχικού σελιδοδείκτη;
Απολύτως! Χρησιμοποιώντας `ImportFormatMode.KeepSourceFormatting` διασφαλίζει ότι διατηρείται η αρχική μορφοποίηση.

### Υπάρχει όριο στο μέγεθος του κειμένου που έχει προστεθεί στους σελιδοδείκτες;
Δεν υπάρχει συγκεκριμένο όριο, αλλά η απόδοση ενδέχεται να διαφέρει σε εξαιρετικά μεγάλα έγγραφα.

### Μπορώ να αντιγράψω κείμενο μεταξύ διαφορετικών μορφών εγγράφων του Word;
Ναι, το Aspose.Words υποστηρίζει διάφορες μορφές Word και η μέθοδος λειτουργεί σε όλες αυτές τις μορφές.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}