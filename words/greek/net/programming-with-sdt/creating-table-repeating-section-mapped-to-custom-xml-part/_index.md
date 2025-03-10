---
title: Δημιουργία πίνακα Επαναλαμβανόμενη ενότητα αντιστοιχισμένη σε προσαρμοσμένο τμήμα Xml
linktitle: Δημιουργία πίνακα Επαναλαμβανόμενη ενότητα αντιστοιχισμένη σε προσαρμοσμένο τμήμα Xml
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να δημιουργείτε έναν πίνακα με μια επαναλαμβανόμενη ενότητα αντιστοιχισμένη σε ένα CustomXmlPart σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET.
weight: 10
url: /el/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία πίνακα Επαναλαμβανόμενη ενότητα αντιστοιχισμένη σε προσαρμοσμένο τμήμα Xml

## Εισαγωγή

Σε αυτό το σεμινάριο, θα ακολουθήσουμε τη διαδικασία δημιουργίας ενός πίνακα με μια επαναλαμβανόμενη ενότητα που αντιστοιχίζεται σε ένα προσαρμοσμένο τμήμα XML χρησιμοποιώντας το Aspose.Words για .NET. Αυτό είναι ιδιαίτερα χρήσιμο για τη δυναμική δημιουργία εγγράφων που βασίζονται σε δομημένα δεδομένα.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1.  Εγκαταστάθηκε η βιβλιοθήκη Aspose.Words για .NET. Μπορείτε να το κατεβάσετε από το[Aspose website](https://releases.aspose.com/words/net/).
2. Βασική κατανόηση της C# και της XML.

## Εισαγωγή χώρων ονομάτων

Φροντίστε να συμπεριλάβετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Βήμα 1: Αρχικοποιήστε το Document and DocumentBuilder

 Αρχικά, δημιουργήστε ένα νέο έγγραφο και αρχικοποιήστε το a`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Βήμα 2: Προσθέστε προσαρμοσμένο τμήμα XML

Προσθέστε ένα προσαρμοσμένο τμήμα XML στο έγγραφο. Αυτό το XML περιέχει τα δεδομένα που θέλουμε να αντιστοιχίσουμε στον πίνακά μας:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Βήμα 3: Δημιουργήστε τη δομή του πίνακα

 Στη συνέχεια, χρησιμοποιήστε το`DocumentBuilder` για να δημιουργήσετε την κεφαλίδα του πίνακα:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Βήμα 4: Δημιουργία Επαναλαμβανόμενης Ενότητας

 Δημιουργία α`StructuredDocumentTag` (SDT) για το επαναλαμβανόμενο τμήμα και αντιστοιχίστε το στα δεδομένα XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Βήμα 5: Δημιουργία επαναλαμβανόμενου στοιχείου ενότητας

Δημιουργήστε ένα SDT για το επαναλαμβανόμενο στοιχείο ενότητας και προσθέστε το στην επαναλαμβανόμενη ενότητα:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Βήμα 6: Αντιστοίχιση δεδομένων XML σε κελιά πίνακα

Δημιουργήστε SDT για τον τίτλο και τον συγγραφέα, αντιστοιχίστε τα στα δεδομένα XML και προσαρτήστε τα στη σειρά:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Βήμα 7: Αποθηκεύστε το έγγραφο

Τέλος, αποθηκεύστε το έγγραφο στον καθορισμένο κατάλογο:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Σύναψη

Ακολουθώντας αυτά τα βήματα, δημιουργήσατε με επιτυχία έναν πίνακα με μια επαναλαμβανόμενη ενότητα αντιστοιχισμένη σε ένα προσαρμοσμένο τμήμα XML χρησιμοποιώντας το Aspose.Words για .NET. Αυτό επιτρέπει τη δυναμική παραγωγή περιεχομένου που βασίζεται σε δομημένα δεδομένα, καθιστώντας τη δημιουργία εγγράφων πιο ευέλικτη και ισχυρή.

## Συχνές ερωτήσεις

### Τι είναι ένα StructuredDocumentTag (SDT);
Ένα SDT, γνωστό και ως στοιχείο ελέγχου περιεχομένου, είναι μια οριοθετημένη περιοχή σε ένα έγγραφο που χρησιμοποιείται για να περιέχει δομημένα δεδομένα.

### Μπορώ να χρησιμοποιήσω άλλους τύπους δεδομένων στο προσαρμοσμένο τμήμα XML;
Ναι, μπορείτε να δομήσετε το προσαρμοσμένο τμήμα XML σας με οποιουσδήποτε τύπους δεδομένων και να τους αντιστοιχίσετε ανάλογα.

### Πώς μπορώ να προσθέσω περισσότερες σειρές στην ενότητα που επαναλαμβάνεται;
Το επαναλαμβανόμενο τμήμα αναπαράγει αυτόματα τη δομή της γραμμής για κάθε στοιχείο στην αντιστοιχισμένη διαδρομή XML.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
