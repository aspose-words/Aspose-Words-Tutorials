---
title: Προσθήκη προθέματος ονόματος κλάσης Css
linktitle: Προσθήκη προθέματος ονόματος κλάσης Css
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να προσθέτετε ένα πρόθεμα ονόματος κλάσης CSS κατά την αποθήκευση εγγράφων του Word ως HTML χρησιμοποιώντας το Aspose.Words για .NET. Περιλαμβάνονται οδηγός βήμα προς βήμα, αποσπάσματα κώδικα και συχνές ερωτήσεις.
weight: 10
url: /el/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη προθέματος ονόματος κλάσης Css

## Εισαγωγή

Καλωσόρισμα! Εάν βουτάτε στον κόσμο του Aspose.Words για το .NET, είστε σε μια απόλαυση. Σήμερα, θα εξερευνήσουμε πώς να προσθέσετε ένα πρόθεμα ονόματος κλάσης CSS κατά την αποθήκευση ενός εγγράφου του Word ως HTML χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η δυνατότητα είναι εξαιρετικά βολική όταν θέλετε να αποφύγετε τις συγκρούσεις ονομάτων τάξης στα αρχεία HTML σας.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

-  Aspose.Words για .NET: Εάν δεν το έχετε εγκαταστήσει ακόμα,[κατεβάστε το εδώ](https://releases.aspose.com/words/net/).
- Περιβάλλον ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο C# IDE.
-  Έγγραφο Word: Θα χρησιμοποιήσουμε ένα έγγραφο με το όνομα`Rendering.docx`. Τοποθετήστε το στον κατάλογο του έργου σας.

## Εισαγωγή χώρων ονομάτων

Αρχικά, βεβαιωθείτε ότι έχετε εισαγάγει τους απαραίτητους χώρους ονομάτων στο έργο σας C#. Προσθέστε αυτά στην κορυφή του αρχείου κώδικα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Τώρα, ας βουτήξουμε στον οδηγό βήμα προς βήμα!

## Βήμα 1: Ρύθμιση του έργου σας

Πριν αρχίσουμε να προσθέτουμε ένα πρόθεμα ονόματος κλάσης CSS, ας ρυθμίσουμε το έργο μας.

### Βήμα 1.1: Δημιουργήστε ένα νέο έργο

 Ενεργοποιήστε το Visual Studio και δημιουργήστε ένα νέο έργο εφαρμογής Console. Ονομάστε το κάτι πιασάρικο`AsposeCssPrefixExample`.

### Βήμα 1.2: Προσθήκη Aspose.Words για .NET

Εάν δεν το έχετε κάνει ήδη, προσθέστε το Aspose.Words για .NET στο έργο σας μέσω του NuGet. Απλώς ανοίξτε την κονσόλα NuGet Package Manager και εκτελέστε:

```bash
Install-Package Aspose.Words
```

Μεγάλος! Τώρα, είμαστε έτοιμοι να ξεκινήσουμε την κωδικοποίηση.

## Βήμα 2: Φορτώστε το έγγραφό σας

Το πρώτο πράγμα που πρέπει να κάνουμε είναι να φορτώσουμε το έγγραφο του Word που θέλουμε να μετατρέψουμε σε HTML.

### Βήμα 2.1: Καθορίστε τη διαδρομή εγγράφου

 Ρυθμίστε τη διαδρομή προς τον κατάλογο εγγράφων σας. Για χάρη αυτού του σεμιναρίου, ας υποθέσουμε ότι το έγγραφό σας βρίσκεται σε έναν φάκελο με το όνομα`Documents` στον κατάλογο του έργου σας.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Βήμα 2.2: Φορτώστε το έγγραφο

Τώρα, ας φορτώσουμε το έγγραφο χρησιμοποιώντας το Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Βήμα 3: Διαμόρφωση επιλογών αποθήκευσης HTML

Στη συνέχεια, πρέπει να διαμορφώσουμε τις επιλογές αποθήκευσης HTML για να συμπεριλάβουμε ένα πρόθεμα ονόματος κλάσης CSS.

### Βήμα 3.1: Δημιουργία επιλογών αποθήκευσης HTML

 Στιγμιότυπο το`HtmlSaveOptions` αντικείμενο και ορίστε τον τύπο φύλλου στυλ CSS σε`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Βήμα 3.2: Ορίστε το πρόθεμα ονόματος κλάσης CSS

 Τώρα, ας ορίσουμε το`CssClassNamePrefix` ιδιοκτησία στο επιθυμητό πρόθεμά σας. Για αυτό το παράδειγμα, θα χρησιμοποιήσουμε`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Βήμα 4: Αποθηκεύστε το Έγγραφο ως HTML

Τέλος, ας αποθηκεύσουμε το έγγραφο ως αρχείο HTML με τις διαμορφωμένες επιλογές μας.


Καθορίστε τη διαδρομή του αρχείου HTML εξόδου και αποθηκεύστε το έγγραφο.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Βήμα 5: Επαληθεύστε την έξοδο

 Αφού εκτελέσετε το έργο σας, μεταβείτε στο δικό σας`Documents` ντοσιέ. Θα πρέπει να βρείτε ένα αρχείο HTML με το όνομα`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Ανοίξτε αυτό το αρχείο σε πρόγραμμα επεξεργασίας κειμένου ή πρόγραμμα περιήγησης για να επαληθεύσετε ότι οι κλάσεις CSS έχουν το πρόθεμα`pfx_`.

## Σύναψη

Και ορίστε το! Ακολουθώντας αυτά τα βήματα, προσθέσατε με επιτυχία ένα πρόθεμα ονόματος κλάσης CSS στην έξοδο HTML χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η απλή αλλά ισχυρή δυνατότητα μπορεί να σας βοηθήσει να διατηρήσετε καθαρά και χωρίς συγκρούσεις στυλ στα έγγραφά σας HTML.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω διαφορετικό πρόθεμα για κάθε λειτουργία αποθήκευσης;
 Ναι, μπορείτε να προσαρμόσετε το πρόθεμα κάθε φορά που αποθηκεύετε ένα έγγραφο αλλάζοντας το`CssClassNamePrefix` ιδιοκτησία.

### Αυτή η μέθοδος υποστηρίζει ενσωματωμένο CSS;
 Ο`CssClassNamePrefix`Η ιδιοκτησία λειτουργεί με εξωτερικό CSS. Για το ενσωματωμένο CSS, θα χρειαστείτε διαφορετική προσέγγιση.

### Πώς μπορώ να συμπεριλάβω άλλες επιλογές αποθήκευσης HTML;
 Μπορείτε να διαμορφώσετε διάφορες ιδιότητες του`HtmlSaveOptions` για να προσαρμόσετε την έξοδο HTML σας. Ελέγξτε το[απόδειξη με έγγραφα](https://reference.aspose.com/words/net/) για περισσότερες λεπτομέρειες.

### Είναι δυνατή η αποθήκευση του HTML σε μια ροή;
 Απολύτως! Μπορείτε να αποθηκεύσετε το έγγραφο σε μια ροή περνώντας το αντικείμενο ροής στο`Save` μέθοδος.

### Πώς μπορώ να λάβω υποστήριξη εάν αντιμετωπίσω προβλήματα;
 Μπορείτε να λάβετε υποστήριξη από το[Aspose φόρουμ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
