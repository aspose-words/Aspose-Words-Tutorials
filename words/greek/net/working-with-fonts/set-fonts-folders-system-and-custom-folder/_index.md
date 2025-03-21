---
title: Ορισμός Fonts Folders System and Custom Folder
linktitle: Ορισμός Fonts Folders System and Custom Folder
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να ορίζετε φακέλους συστήματος και προσαρμοσμένων γραμματοσειρών σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET, διασφαλίζοντας ότι τα έγγραφά σας εμφανίζονται σωστά σε διαφορετικά περιβάλλοντα.
weight: 10
url: /el/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός Fonts Folders System and Custom Folder

## Εισαγωγή

Φανταστείτε ότι δημιουργείτε ένα έγγραφο με μοναδικό στυλ γραμματοσειράς, μόνο για να διαπιστώσετε ότι οι γραμματοσειρές δεν εμφανίζονται σωστά σε άλλο μηχάνημα. Απογοητευτικό, σωστά; Εδώ παίζει ρόλο η διαμόρφωση των φακέλων γραμματοσειρών. Με το Aspose.Words για .NET, μπορείτε να ορίσετε φακέλους συστήματος και προσαρμοσμένων γραμματοσειρών για να διασφαλίσετε ότι τα έγγραφά σας έχουν πάντα την επιθυμητή εμφάνιση. Ας δούμε πώς μπορείτε να το πετύχετε αυτό.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

-  Aspose.Words for .NET Library: Αν δεν το έχετε κάνει ήδη, κατεβάστε το[εδώ](https://releases.aspose.com/words/net/).
- Περιβάλλον ανάπτυξης: Ένα IDE σαν το Visual Studio.
- Βασικές γνώσεις C#: Η εξοικείωση με το C# θα σας βοηθήσει να ακολουθήσετε μαζί με τα παραδείγματα κώδικα.

## Εισαγωγή χώρων ονομάτων

Αρχικά, εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Τώρα, ας αναλύσουμε τη διαδικασία σε απλά βήματα.

## Βήμα 1: Φορτώστε το έγγραφο

 Για να ξεκινήσετε, φορτώστε το έγγραφο του Word σε ένα Aspose.Words`Document` αντικείμενο. Αυτό το έγγραφο θα είναι εκείνο στο οποίο θέλετε να ορίσετε τους φακέλους γραμματοσειρών.

```csharp
// Διαδρομή στον κατάλογο εγγράφων σας
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Βήμα 2: Εκκίνηση των ρυθμίσεων γραμματοσειράς

 Δημιουργήστε μια νέα παρουσία του`FontSettings`. Αυτό το αντικείμενο θα σας επιτρέψει να διαχειριστείτε πηγές γραμματοσειρών.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Βήμα 3: Ανάκτηση πηγών γραμματοσειράς συστήματος

Ανακτήστε τις προεπιλεγμένες πηγές γραμματοσειράς συστήματος. Σε ένα μηχάνημα με Windows, αυτό συνήθως περιλαμβάνει το "Windows\Fonts\" κατάλογος.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Βήμα 4: Προσθέστε έναν φάκελο προσαρμοσμένης γραμματοσειράς

Προσθέστε έναν προσαρμοσμένο φάκελο που περιέχει τις πρόσθετες γραμματοσειρές σας. Αυτό είναι χρήσιμο εάν δεν έχετε εγκαταστήσει συγκεκριμένες γραμματοσειρές στον κατάλογο γραμματοσειρών συστήματος.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Βήμα 5: Ενημερώστε τις πηγές γραμματοσειράς

 Μετατρέψτε τη λίστα των πηγών γραμματοσειρών σε πίνακα και ορίστε την στο`FontSettings` αντικείμενο.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Βήμα 6: Εφαρμογή ρυθμίσεων γραμματοσειράς στο έγγραφο

 Τέλος, εφαρμόστε τα διαμορφωμένα`FontSettings` στο έγγραφό σας και αποθηκεύστε το στην επιθυμητή μορφή, όπως PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Σύναψη

Και ορίστε το! Ακολουθώντας αυτά τα βήματα, μπορείτε να βεβαιωθείτε ότι τα έγγραφά σας Word χρησιμοποιούν τις σωστές γραμματοσειρές, είτε πρόκειται για γραμματοσειρές συστήματος είτε για προσαρμοσμένες γραμματοσειρές που είναι αποθηκευμένες σε έναν συγκεκριμένο κατάλογο. Αυτή η ρύθμιση βοηθά στη διατήρηση της ακεραιότητας της εμφάνισης του εγγράφου σας σε διαφορετικά περιβάλλοντα.

## Συχνές ερωτήσεις

### Τι συμβαίνει εάν λείπει μια γραμματοσειρά τόσο στους φακέλους συστήματος όσο και στους προσαρμοσμένους φακέλους;

Το Aspose.Words θα χρησιμοποιήσει μια προεπιλεγμένη γραμματοσειρά για να αντικαταστήσει τη γραμματοσειρά που λείπει, διασφαλίζοντας ότι το έγγραφο παραμένει αναγνώσιμο.

### Μπορώ να προσθέσω πολλούς φακέλους προσαρμοσμένων γραμματοσειρών;

 Ναι, μπορείτε να προσθέσετε πολλούς φακέλους προσαρμοσμένων γραμματοσειρών επαναλαμβάνοντας τη διαδικασία δημιουργίας`FolderFontSource` αντικείμενα και την προσθήκη τους στη λίστα πηγών γραμματοσειράς.

### Είναι δυνατή η χρήση διαδρομών δικτύου για φακέλους προσαρμοσμένων γραμματοσειρών;

 Ναι, μπορείτε να καθορίσετε μια διαδρομή δικτύου στο`FolderFontSource` κατασκευαστής.

### Ποιες μορφές αρχείων υποστηρίζει το Aspose.Words για την αποθήκευση εγγράφων;

Το Aspose.Words υποστηρίζει διάφορες μορφές, όπως DOCX, PDF, HTML και άλλα.

### Πώς χειρίζομαι τις ειδοποιήσεις αντικατάστασης γραμματοσειράς;

 Μπορείτε να χειριστείτε ειδοποιήσεις αντικατάστασης γραμματοσειράς χρησιμοποιώντας το`FontSettings` της τάξης`FontSubstitutionWarning`συμβάν.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
