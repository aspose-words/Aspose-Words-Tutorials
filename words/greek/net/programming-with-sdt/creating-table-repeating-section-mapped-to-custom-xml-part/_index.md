---
"description": "Μάθετε πώς να δημιουργείτε έναν πίνακα με μια επαναλαμβανόμενη ενότητα που αντιστοιχίζεται σε ένα CustomXmlPart σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET."
"linktitle": "Δημιουργία επαναλαμβανόμενης ενότητας πίνακα που αντιστοιχίζεται σε προσαρμοσμένο τμήμα Xml"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Δημιουργία επαναλαμβανόμενης ενότητας πίνακα που αντιστοιχίζεται σε προσαρμοσμένο τμήμα Xml"
"url": "/el/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία επαναλαμβανόμενης ενότητας πίνακα που αντιστοιχίζεται σε προσαρμοσμένο τμήμα Xml

## Εισαγωγή

Σε αυτό το σεμινάριο, θα περιηγηθούμε στη διαδικασία δημιουργίας ενός πίνακα με μια επαναλαμβανόμενη ενότητα που αντιστοιχίζεται σε ένα προσαρμοσμένο τμήμα XML χρησιμοποιώντας το Aspose.Words για .NET. Αυτό είναι ιδιαίτερα χρήσιμο για τη δυναμική δημιουργία εγγράφων που βασίζονται σε δομημένα δεδομένα.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1. Εγκατεστημένο το Aspose.Words για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε από το [Ιστότοπος Aspose](https://releases.aspose.com/words/net/).
2. Βασική κατανόηση της C# και της XML.

## Εισαγωγή χώρων ονομάτων

Βεβαιωθείτε ότι έχετε συμπεριλάβει τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Βήμα 1: Αρχικοποίηση Εγγράφου και DocumentBuilder

Αρχικά, δημιουργήστε ένα νέο έγγραφο και αρχικοποιήστε ένα `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Προσθήκη προσαρμοσμένου τμήματος XML

Προσθέστε ένα προσαρμοσμένο τμήμα XML στο έγγραφο. Αυτό το XML περιέχει τα δεδομένα που θέλουμε να αντιστοιχίσουμε στον πίνακά μας:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Βήμα 3: Δημιουργήστε τη δομή πίνακα

Στη συνέχεια, χρησιμοποιήστε το `DocumentBuilder` για να δημιουργήσετε την κεφαλίδα του πίνακα:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Βήμα 4: Δημιουργία επαναλαμβανόμενης ενότητας

Δημιουργήστε ένα `StructuredDocumentTag` (SDT) για την επαναλαμβανόμενη ενότητα και αντιστοιχίστε την στα δεδομένα XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Βήμα 5: Δημιουργία επαναλαμβανόμενου στοιχείου ενότητας

Δημιουργήστε ένα SDT για το στοιχείο επαναλαμβανόμενης ενότητας και προσθέστε το στην επαναλαμβανόμενη ενότητα:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Βήμα 6: Αντιστοίχιση δεδομένων XML σε κελιά πίνακα

Δημιουργήστε SDT για τον τίτλο και τον συγγραφέα, αντιστοιχίστε τα στα δεδομένα XML και προσαρτήστε τα στη γραμμή:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Βήμα 7: Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στον καθορισμένο κατάλογο:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Σύναψη

Ακολουθώντας αυτά τα βήματα, δημιουργήσατε με επιτυχία έναν πίνακα με μια επαναλαμβανόμενη ενότητα που αντιστοιχίζεται σε ένα προσαρμοσμένο τμήμα XML χρησιμοποιώντας το Aspose.Words για .NET. Αυτό επιτρέπει τη δυναμική δημιουργία περιεχομένου με βάση δομημένα δεδομένα, καθιστώντας τη δημιουργία εγγράφων πιο ευέλικτη και ισχυρή.

## Συχνές ερωτήσεις

### Τι είναι μια ετικέτα δομημένου εγγράφου (SDT);
Ένα SDT, γνωστό και ως στοιχείο ελέγχου περιεχομένου, είναι μια οριοθετημένη περιοχή σε ένα έγγραφο που χρησιμοποιείται για να περιέχει δομημένα δεδομένα.

### Μπορώ να χρησιμοποιήσω άλλους τύπους δεδομένων στο προσαρμοσμένο τμήμα XML;
Ναι, μπορείτε να δομήσετε το προσαρμοσμένο τμήμα XML σας με οποιονδήποτε τύπο δεδομένων και να τους αντιστοιχίσετε ανάλογα.

### Πώς μπορώ να προσθέσω περισσότερες γραμμές στην επαναλαμβανόμενη ενότητα;
Η επαναλαμβανόμενη ενότητα αναπαράγει αυτόματα τη δομή γραμμών για κάθε στοιχείο στην αντιστοιχισμένη διαδρομή XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}