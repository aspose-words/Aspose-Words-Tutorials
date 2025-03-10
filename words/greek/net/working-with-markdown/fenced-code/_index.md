---
title: Περιφραγμένος Κώδικας
linktitle: Περιφραγμένος Κώδικας
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να προσθέτετε περιφραγμένους κώδικα και συμβολοσειρές πληροφοριών σε έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET. Περιλαμβάνεται οδηγός βήμα προς βήμα. Βελτιώστε τις δεξιότητές σας στη μορφοποίηση εγγράφων.
weight: 10
url: /el/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Περιφραγμένος Κώδικας

## Εισαγωγή

Γεια σου, φίλε κωδικοποιητή! Σήμερα, βουτάμε στον κόσμο του Aspose.Words για το .NET για να κατακτήσουμε την τέχνη της προσθήκης περιφραγμένου κώδικα και περιφραγμένου κώδικα με συμβολοσειρές πληροφοριών στα έγγραφα του Word. Φανταστείτε το έγγραφο του Word ως καμβά και εσείς, ο καλλιτέχνης, πρόκειται να ζωγραφίσετε με την ακρίβεια ενός έμπειρου προγραμματιστή. Με το Aspose.Words, έχετε τη δύναμη να βελτιώσετε μέσω προγραμματισμού τα έγγραφά σας με δομημένα, μορφοποιημένα μπλοκ κώδικα, κάνοντας τα τεχνικά σας έγγραφα να λάμπουν με επαγγελματισμό και σαφήνεια.

## Προαπαιτούμενα

Πριν προχωρήσουμε στο σεμινάριο, ας βεβαιωθούμε ότι έχετε όλα όσα χρειάζεστε:

- Βασικές γνώσεις C#: Η γενική κατανόηση της C# θα σας βοηθήσει να κατανοήσετε γρήγορα τις έννοιες.
-  Aspose.Words για .NET: Πρέπει να έχετε εγκατεστημένο το Aspose.Words για .NET. Αν δεν το έχετε πάρει ακόμα, πιάστε το[εδώ](https://releases.aspose.com/words/net/).
- Περιβάλλον ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο C# IDE με το οποίο αισθάνεστε άνετα.

## Εισαγωγή χώρων ονομάτων

Πρώτα πράγματα πρώτα, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων. Αυτό είναι σαν να συγκεντρώνετε όλα τα εργαλεία σας πριν ξεκινήσετε ένα έργο.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Τώρα, ας αναλύσουμε τη διαδικασία βήμα προς βήμα.

## Βήμα 1: Ρύθμιση του έργου σας

Για να μπορέσουμε να δημιουργήσουμε όμορφα, μορφοποιημένα μπλοκ κώδικα στο έγγραφο του Word, πρέπει να ρυθμίσουμε ένα νέο έργο στο Visual Studio.

1. Δημιουργία νέου έργου: Ανοίξτε το Visual Studio και δημιουργήστε μια νέα εφαρμογή κονσόλας C#.
2. Προσθήκη αναφοράς Aspose.Words: Εγκαταστήστε το Aspose.Words μέσω του NuGet Package Manager. Μπορείτε να το κάνετε αυτό κάνοντας δεξί κλικ στο έργο σας στον Εξερεύνηση λύσεων, επιλέγοντας "Διαχείριση πακέτων NuGet" και αναζητώντας το Aspose.Words.

## Βήμα 2: Αρχικοποιήστε το DocumentBuilder

Τώρα που το έργο σας έχει ρυθμιστεί, ας αρχικοποιήσουμε το DocumentBuilder, το οποίο θα είναι το κύριο εργαλείο μας για την προσθήκη περιεχομένου στο έγγραφο του Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Βήμα 3: Δημιουργήστε ένα στυλ για περιφραγμένο κώδικα

Για να προσθέσουμε περιφραγμένο κώδικα, πρέπει πρώτα να δημιουργήσουμε ένα στυλ. Σκεφτείτε αυτό ως ρύθμιση του θέματος για το μπλοκ κώδικα.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Βήμα 4: Προσθέστε περιφραγμένο κώδικα στο έγγραφο

Με το στυλ μας έτοιμο, μπορούμε τώρα να προσθέσουμε ένα περιφραγμένο μπλοκ κώδικα στο έγγραφο.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Βήμα 5: Δημιουργήστε ένα στυλ για περιφραγμένο κώδικα με συμβολοσειρά πληροφοριών

Μερικές φορές, μπορεί να θέλετε να καθορίσετε τη γλώσσα προγραμματισμού ή να προσθέσετε επιπλέον πληροφορίες στο μπλοκ κώδικα. Ας δημιουργήσουμε ένα στυλ για αυτό.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Βήμα 6: Προσθέστε περιφραγμένο κώδικα με συμβολοσειρά πληροφοριών στο έγγραφο

Τώρα, ας προσθέσουμε ένα περιφραγμένο μπλοκ κώδικα με μια συμβολοσειρά πληροφοριών για να υποδείξουμε ότι είναι κώδικας C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Σύναψη

Συγχαρητήρια! Μόλις προσθέσατε περιφραγμένα μπλοκ κώδικα και περιφραγμένο κώδικα με συμβολοσειρές πληροφοριών στα έγγραφά σας στο Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτή είναι μόνο η κορυφή του παγόβουνου. Με το Aspose.Words, μπορείτε να αυτοματοποιήσετε και να βελτιώσετε την επεξεργασία των εγγράφων σας σε νέα ύψη. Συνεχίστε την εξερεύνηση και χαρούμενη κωδικοποίηση!

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για .NET;
Το Aspose.Words για .NET είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να δημιουργούν, να χειρίζονται και να μετατρέπουν έγγραφα του Word μέσω προγραμματισμού.

### Μπορώ να χρησιμοποιήσω το Aspose.Words με άλλες γλώσσες προγραμματισμού;
Το Aspose.Words υποστηρίζει κυρίως γλώσσες .NET, αλλά υπάρχουν διαθέσιμες εκδόσεις για Java, Python και άλλες γλώσσες.

### Είναι το Aspose.Words δωρεάν στη χρήση;
 Το Aspose.Words είναι ένα εμπορικό προϊόν, αλλά μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμής[εδώ](https://releases.aspose.com/)για να εξερευνήσετε τα χαρακτηριστικά του.

### Πώς μπορώ να λάβω υποστήριξη για το Aspose.Words;
 Μπορείτε να λάβετε υποστήριξη από την κοινότητα Aspose και τους προγραμματιστές[εδώ](https://forum.aspose.com/c/words/8).

### Ποιες άλλες δυνατότητες προσφέρει το Aspose.Words;
Το Aspose.Words προσφέρει ένα ευρύ φάσμα δυνατοτήτων, όπως μετατροπή εγγράφων, δημιουργία εγγράφων βάσει προτύπων, αναφορά και πολλά άλλα.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
