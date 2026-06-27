---
category: general
date: 2026-06-27
description: Αλλάξτε το στυλ γραμματοσειράς σε έγγραφα Word με C#. Μάθετε πώς να ορίζετε
  το βάρος της γραμματοσειράς, το έντονο βάρος και να προσαρμόζετε το πλάτος της γραμματοσειράς
  για ακριβή τυπογραφία.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: el
og_description: Αλλάξτε το στυλ γραμματοσειράς σε έγγραφα Word με C#. Ανακαλύψτε πώς
  να ορίσετε το βάρος της γραμματοσειράς, να ορίσετε το έντονο βάρος και να ρυθμίσετε
  το πλάτος της γραμματοσειράς σε λίγα εύκολα βήματα.
og_title: Αλλαγή Στυλ Γραμματοσειράς σε Έγγραφα Word – Πλήρης Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Αλλαγή Στυλ Γραμματοσειράς σε Έγγραφα Word – Πλήρης Οδηγός C#
url: /el/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αλλαγή Στυλ Γραμματοσειράς σε Έγγραφα Word – Πλήρης Οδηγός C#

Έχετε ποτέ χρειαστεί να **αλλάξετε το στυλ γραμματοσειράς** σε ένα αρχείο Word αλλά δεν ήξερες ποια κλήση API κάνει πραγματικά το τέλειο; Δεν είστε μόνοι—οι περισσότεροι προγραμματιστές συναντούν αυτό το εμπόδιο όταν προσπαθούν για πρώτη φορά να τροποποιήσουν προγραμματιστικά την τυπογραφία.  

Τα καλά νέα είναι ότι με λίγες γραμμές C# μπορείτε να **ορίσετε το βάρος της γραμματοσειράς**, ακόμη και να αυξήσετε το έντονο βάρος, και να ρυθμίσετε με ακρίβεια το πλάτος κάθε γλύφου. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, εκτελέσιμο παράδειγμα που τροποποιεί ένα αρχείο `.docx` από την αρχή μέχρι το τέλος.

## Τι Καλύπτει Αυτός ο Οδηγός

Θα ξεκινήσουμε φορτώνοντας ένα υπάρχον έγγραφο, στη συνέχεια θα δημιουργήσουμε ένα αντικείμενο `FontSettings` που περιέχει ένα `FontVariation`. Από εκεί θα **ορίσουμε το βάρος της γραμματοσειράς**, **ορίσουμε το έντονο βάρος**, και **ρυθμίσουμε το πλάτος της γραμματοσειράς** πριν εφαρμόσουμε τις αλλαγές και αποθηκεύσουμε το αποτέλεσμα. Χωρίς εξωτερικά αρχεία ρυθμίσεων, χωρίς μαγικές συμβολοσειρές—μόνο απλό C# και η βιβλιοθήκη Aspose.Words. Στο τέλος θα μπορείτε να **τροποποιήσετε τη γραμματοσειρά σε Word** έγγραφα με σιγουριά, είτε χτίζετε μια μηχανή αναφορών είτε ένα εργαλείο μαζικής μορφοποίησης.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας μεταγλωττίζεται επίσης σε .NET Core)  
- Πακέτο NuGet Aspose.Words για .NET (`Install-Package Aspose.Words`)  
- Ένα δείγμα `input.docx` τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε (θα το ονομάσουμε `YOUR_DIRECTORY`)  

Αν έχετε καλύψει αυτά τα βασικά, ας βουτήξουμε.

---

## Βήμα 1: Αλλαγή Στυλ Γραμματοσειράς – Φόρτωση του Εγγράφου Word

Το πρώτο πράγμα που πρέπει να κάνετε είναι να φορτώσετε το αρχείο‑στόχο στη μνήμη. Σκεφτείτε το ως το άνοιγμα ενός κεννού καμβά όπου θα ζωγραφίσετε αργότερα τη νέα σας τυπογραφία.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Συμβουλή:** Εάν εκτελείτε αυτόν τον κώδικα σε διακομιστή χωρίς UI, βεβαιωθείτε ότι η άδεια Aspose.Words είναι είτε σε δοκιμαστική λειτουργία είτε έχετε εφαρμόσει ένα κατάλληλο αρχείο άδειας για να αποφύγετε μηνύματα υδατογραφήματος.

---

## Βήμα 2: Ορισμός Βάρους Γραμματοσειράς και Ορισμός Έντονου Βάρους

Τώρα που το έγγραφο βρίσκεται στη μνήμη, δημιουργούμε ένα κοντέινερ `FontSettings`. Αυτό το αντικείμενο είναι η πύλη για κάθε ρύθμιση σε επίπεδο γραμματοσειράς που μπορείτε να κάνετε.

Η κλάση `FontVariation` σας επιτρέπει να ορίσετε τρία βασικά χαρακτηριστικά:

| Ιδιότητα | Τι κάνει | Τυπικό εύρος |
|----------|----------|--------------|
| `Weight` | Ελέγχει πόσο βαρύ εμφανίζεται το γλύφο. Μια τιμή **700** είναι το τυπικό “bold”. | 100‑900 |
| `Width`  | Τεντώνει ή συμπιέζει το γλύφο οριζόντια. **100** σημαίνει κανονικό πλάτος. | 50‑200 |
| `Slant`  | Προσθέτει κλίση παρόμοια με πλάγια. Οι θετικοί αριθμοί κλίνουν προς τα δεξιά. | -90‑90 |

Παρακάτω **ορίζουμε το βάρος της γραμματοσειράς** σε 700 (bold) και επίσης δείχνουμε πώς μπορείτε να το αυξήσετε ακόμη περισσότερο αν η γραμματοσειρά σας υποστηρίζει στυλ “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Γιατί είναι σημαντικό:** Ο ορισμός του **set bold weight** απευθείας μέσω `SetWeight` παρακάμπτει την ανάγκη για ξεχωριστό αντικείμενο στυλ “Bold”, παρέχοντάς σας έλεγχο pixel‑perfect στο πόσο παχιά γίνονται οι γραμμές.

---

## Βήμα 3: Ρύθμιση Πλάτους Γραμματοσειράς

Αν ποτέ χρειαστείτε να κάνετε μια γραμματοσειρά πιο στενή για έναν τίτλο ή πιο ευρύχωρη για μια παράγραφο, θα χαρείτε που φτάσατε σε αυτό το βήμα. Η ιδιότητα `Width` κάνει ακριβώς αυτό.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Συνηθισμένο λάθος:** Δεν σέβεται κάθε γραμματοσειρά τις παραλλαγές πλάτους. Αν δεν δείτε οπτική αλλαγή, ελέγξτε ότι η οικογένεια γραμματοσειράς που χρησιμοποιείτε υποστηρίζει συμπιεσμένα/ανοιγμένα γλύφα.

---

## Βήμα 4: Εφαρμογή Ρυθμίσεων Γραμματοσειράς – Τροποποίηση Γραμματοσειράς σε Word

Με το `FontSettings` μας πλήρως διαμορφωμένο, το τελικό βήμα είναι να πούμε στο έγγραφο να το χρησιμοποιήσει. Εδώ είναι που **τροποποιούμε τη γραμματοσειρά σε Word** σε επίπεδο εγγράφου, επηρεάζοντας κάθε τμήμα κειμένου που κληρονομεί το προεπιλεγμένο στυλ.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Αν θέλετε να στοχεύσετε μόνο μια συγκεκριμένη παράγραφο ή τμήμα, μπορείτε να ανακτήσετε αυτόν τον κόμβο και να ορίσετε το `FontSettings` του ξεχωριστά. Το παραπάνω παράδειγμα δείχνει την προσέγγιση ευρείας κίνησης, η οποία είναι ιδανική για σενάρια μαζικής μορφοποίησης.

---

## Βήμα 5: Αποθήκευση και Επαλήθευση των Αλλαγών

Η αποθήκευση είναι το τελευταίο, αλλά σίγουρα όχι το λιγότερο, μέρος της ροής εργασίας. Μετά την αποθήκευση του αρχείου μπορείτε να το ανοίξετε στο Microsoft Word για να δείτε τη νέα μορφοποίηση σε δράση.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Όλο το κυρίως κείμενο που προηγουμένως χρησιμοποιούσε την προεπιλεγμένη γραμματοσειρά εμφανίζεται τώρα **bold** (βάρος 700).  
- Αν πειραματιστείτε με `SetWidth(80)`, οι χαρακτήρες θα φαίνονται λίγο πιο στενοί· `SetWidth(120)` θα τους κάνει πιο ανοιχτούς.  
- Κανένα άλλο περιεχόμενο (εικόνες, πίνακες κ.λπ.) δεν τροποποιείται—μόνο τα χαρακτηριστικά γραμματοσειράς των τμημάτων κειμένου.

Ανοίξτε το `output.docx` στο Word, επιλέξτε μια παράγραφο και ελέγξτε τον διάλογο **Font**. Θα δείτε το πλαίσιο **Bold** επιλεγμένο και το **Scale** (πλάτος) να αντικατοπτρίζει την τιμή που επιλέξατε.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Μπορώ να αλλάξω την οικογένεια γραμματοσειράς ταυτόχρονα;

Απόλυτα. Αφού ορίσετε το `FontVariation`, μπορείτε επίσης να εκχωρήσετε ένα νέο `FontInfo` στο `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Τι γίνεται αν χρειαστώ να **ορίσω έντονο βάρος** μόνο για επικεφαλίδες;

Ανακτήστε τον κόμβο του στυλ επικεφαλίδας και εφαρμόστε μια ξεχωριστή παρουσία `FontSettings`:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Λειτουργεί αυτό με .NET Core σε Linux;

Ναι—το Aspose.Words είναι δια‑πλατφορμικό. Απλώς βεβαιωθείτε ότι έχετε εγκατεστημένες τις κατάλληλες βιβλιοθήκες χρόνου εκτέλεσης (`libgdiplus` σε ορισμένες διανομές) εάν σκοπεύετε να μετατρέψετε το έγγραφο σε PDF αργότερα.

---

## Συμπέρασμα

Μόλις **αλλάξαμε το στυλ γραμματοσειράς** σε ένα έγγραφο Word από την αρχή μέχρι το τέλος, καλύπτοντας πώς να **ορίσετε το βάρος της γραμματοσειράς**, **ορίσετε το έντονο βάρος**, και **ρυθμίσετε το πλάτος της γραμματοσειράς** χρησιμοποιώντας C#. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει κάθε απαιτούμενη εισαγωγή, δημιουργία αντικειμένου και κλήση μεθόδου, ώστε να μπορείτε να το αντιγράψετε‑και‑επικολλήσετε στο δικό σας έργο και να δείτε την τυπογραφία να μετασχηματίζεται άμεσα.

Τώρα που ξέρετε πώς να **τροποποιήσετε τη γραμματοσειρά σε Word**, μπορείτε να εξερευνήσετε συναφή θέματα όπως **ενσωμάτωση προσαρμοσμένων γραμματοσειρών**, **εφαρμογή χρωματικών διαβαθμίσεων**, ή **δημιουργία δυναμικών πινάκων**. Κάθε ένα από αυτά βασίζεται στην ίδια βάση `FontSettings` που χρησιμοποιήσαμε εδώ, οπότε είστε ήδη ένα βήμα μπροστά.

Έχετε μια περίπτωση που δεν καλύφθηκε; Αφήστε ένα σχόλιο και θα το εξετάσουμε μαζί. Καλή προγραμματιστική δουλειά—και εύχομαι τα έγγραφά σας να φαίνονται πάντα ακριβώς όπως το θέλετε!  

![change font style example](placeholder.png){alt="παράδειγμα αλλαγής στυλ γραμματοσειράς"}

## Τι Θα Πρέπει να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ορισμός Σημαίας Έμφασης Γραμματοσειράς](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Ορισμός Ρυθμίσεων Αντικατάστασης Γραμματοσειράς](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Ορισμός Μορφοποίησης Γραμματοσειράς](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}