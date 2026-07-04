---
category: general
date: 2026-06-02
description: Μάθετε πώς να χρησιμοποιείτε γραμματοσειρά με μεταβλητό βάρος σε C# και
  να ορίζετε το βάρος της γραμματοσειράς προγραμματιστικά, ενώ αλλάζετε τον κώδικα
  τεντώματος γραμματοσειράς για δυναμική τυπογραφία.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: el
og_description: Χρησιμοποιήστε γραμματοσειρά μεταβλητού βάρους σε C# για να ορίσετε
  το βάρος της γραμματοσειράς προγραμματιστικά και να αλλάξετε τον κώδικα εκτάσεων
  γραμματοσειράς, επιτρέποντας δυναμική τυπογραφία στα έγγραφά σας.
og_title: Χρησιμοποιήστε γραμματοσειρά με μεταβλητό βάρος σε C# – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Χρήση γραμματοσειράς μεταβλητού βάρους σε C# – Πλήρης οδηγός προγραμματισμού
url: /el/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση γραμματοσειράς μεταβλητού βάρους σε C# – Πλήρης Οδηγός Προγραμματισμού

Έχετε χρειαστεί ποτέ να **χρησιμοποιήσετε γραμματοσειρά μεταβλητού βάρους** σε ένα έργο .NET αλλά δεν ήξερες πώς να κάνεις το βάρος και το stretch να ανταποκρίνονται σε είσοδο χρήστη; Δεν είστε μόνοι. Σε πολλές περιπτώσεις UI ή αναφορών θέλετε το κείμενο να προσαρμόζεται — ίσως μια ελαφριά επικεφαλίδα που γίνεται έντονη κατά το hover, ή μια παράγραφος που επεκτείνει το πλάτος της για έμφαση. Τα καλά νέα είναι ότι με το Aspose.Words μπορείτε **να ορίσετε το βάρος της γραμματοσειράς προγραμματιστικά** και ακόμη **να αλλάξετε τον κώδικα stretch της γραμματοσειράς** σε πραγματικό χρόνο.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πρακτικό παράδειγμα που δείχνει ακριβώς πώς να φορτώσετε μια γραμματοσειρά μεταβλητού βάρους, να εφαρμόσετε προσαρμοσμένο βάρος και να ρυθμίσετε το stretch — όλα με σαφή κώδικα C# που μπορείτε να αντιγράψετε‑επικολλήσετε. Στο τέλος θα έχετε μια εκτελέσιμη εφαρμογή console που παράγει ένα PDF που παρουσιάζει το αποτέλεσμα.

---

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (v23.12 ή νεότερη). Η βιβλιοθήκη παρέχει πλήρη υποστήριξη για γραμματοσειρές μεταβλητού βάρους.
- Ένας φάκελος που περιέχει τουλάχιστον ένα αρχείο γραμματοσειράς μεταβλητού βάρους, π.χ. *RobotoFlex‑Variable.ttf*. Μπορείτε να το κατεβάσετε από το Google Fonts.
- .NET 6 SDK (ή οποιαδήποτε πρόσφατη έκδοση .NET) και ένα IDE της επιλογής σας.
- Βασικές γνώσεις C# — τίποτα περίπλοκο, μόνο λίγες γραμμές κώδικα.

Αυτό είναι όλο. Δεν χρειάζονται επιπλέον πακέτα NuGet εκτός από το Aspose.Words και δεν απαιτούνται περίπλογα αρχεία ρυθμίσεων.

---

![Παράδειγμα χρήσης γραμματοσειράς μεταβλητού βάρους](https://example.com/variable-weight-sample.png "Επίδειξη χρήσης γραμματοσειράς μεταβλητού βάρους")

*Alt text: στιγμιότυπο οθόνης που δείχνει τη χρήση γραμματοσειράς μεταβλητού βάρους σε ένα παραγόμενο έγγραφο PDF.*

---

## Βήμα 1: Ρύθμιση FontSettings και Καθορισμός του Φακέλου Γραμματοσειρών  

Πρώτα απ' όλα — το Aspose.Words πρέπει να ξέρει πού βρίσκονται οι γραμματοσειρές μεταβλητού βάρους. Αυτό γίνεται δημιουργώντας ένα αντικείμενο `FontSettings` και προσθέτοντας ένα `FolderFontSource`. Η σημαία `true` λέει στη μηχανή να ψάχνει και σε υποφακέλους, κάτι χρήσιμο αν κρατάτε πολλές οικογένειες γραμματοσειρών μαζί.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Γιατί είναι σημαντικό:** Χωρίς την καταχώριση του φακέλου, το Aspose.Words επιστρέφει στις συστημικές γραμματοσειρές και αγνοεί τα δεδομένα μεταβλητού βάρους που είναι ενσωματωμένα στο προσαρμοσμένο αρχείο γραμματοσειράς. Αυτό το βήμα αποτελεί τη βάση για όλα τα επόμενα.

---

## Βήμα 2: Σύνδεση FontSettings με το Έγγραφο  

Τώρα δημιουργούμε ένα νέο `Document` (ή φορτώνουμε ένα υπάρχον) και του λέμε να χρησιμοποιήσει το `FontSettings` που μόλις προετοιμάσαμε. Αυτή η σύνδεση είναι αυτή που κάνει τα δεδομένα μεταβλητού βάρους διαθέσιμα σε κάθε `Run` που θα προσθέσουμε αργότερα.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Αν έχετε ήδη ένα πρότυπο — π.χ. ένα αρχείο Word με placeholders — μπορείτε να αντικαταστήσετε το `new Document()` με `new Document("Template.docx")`. Τα ίδια `FontSettings` θα ισχύουν.

---

## Βήμα 3: Προσθήκη Run Κειμένου που Θα Χρησιμοποιεί τη Γραμματοσειρά Μεταβλητού Βάρους  

Ένα **Run** είναι η μικρότερη μονάδα μορφοποίησης κειμένου στο Aspose.Words. Θα δημιουργήσουμε ένα, θα το εισάγουμε σε μια νέα παράγραφο και αργότερα θα αλλάξουμε τις ιδιότητες γραμματοσειράς του.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Σε αυτό το σημείο το κείμενο θα αποδοθεί με τη προεπιλεγμένη γραμματοσειρά (συνήθως Times New Roman). Η μαγεία συμβαίνει όταν αντιστοιχίσουμε την οικογένεια μεταβλητού βάρους.

---

## Βήμα 4: Επιλογή Οικογένειας Γραμματοσειράς Μεταβλητού Βάρους  

Εδώ είναι που **χρησιμοποιούμε πραγματικά τη γραμματοσειρά μεταβλητού βάρους**. Ορίστε το `Font.Name` στο ακριβές όνομα οικογένειας που ορίζεται μέσα στο αρχείο γραμματοσειράς. Για το Roboto Flex, το όνομα είναι `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Αν δεν είστε σίγουροι για το όνομα της οικογένειας, ανοίξτε το αρχείο `.ttf` σε έναν προβολέα γραμματοσειρών ή χρησιμοποιήστε τη μέθοδο `fontSettings.GetFonts()` για να απαριθμήσετε τις διαθέσιμες οικογένειες.

---

## Βήμα 5: Προγραμματιστική Ρύθμιση Βάρους και Stretch της Γραμματοσειράς  

Τώρα το κύριο μέρος του tutorial: **ορίζουμε το βάρος της γραμματοσειράς προγραμματιστικά** και **αλλάζουμε τον κώδικα stretch**. Και οι δύο ιδιότητες δέχονται ακέραιες τιμές που αντιστοιχούν στην προδιαγραφή OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Επιλέξτε οποιαδήποτε τιμή υποστηρίζεται από τη μεταβλητή γραμματοσειρά.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Η προεπιλογή είναι 100 (Normal).

> **Pro tip:** Δεν εκθέτει κάθε μεταβλητή γραμματοσειρά όλο το εύρος. Αν ορίσετε τιμή που δεν υποστηρίζεται, η μηχανή θα περιορίσει στο πλησιέστερο διαθέσιμο βάρος ή stretch.

---

## Βήμα 6: Αποθήκευση του Εγγράφου και Επαλήθευση του Αποτελέσματος  

Τέλος, γράψτε το έγγραφο σε PDF (ή DOCX) και ανοίξτε το για να δείτε το αποτέλεσμα. Το PDF είναι εξαιρετικό για οπτική επαλήθευση επειδή η απόδοση είναι συνεπής σε όλες τις πλατφόρμες.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Όταν ανοίξετε το *VariableWeightDemo.pdf*, θα δείτε τη φράση “Variable‑weight text demo” αποδομένη σε μια ελαφριά, ελαφρώς επεκταμένη έκδοση του Roboto Flex. Αλλάξτε το `FontWeight` σε `700` και το `FontStretch` σε `80` και τρέξτε ξανά — παρακολουθήστε το κείμενο να γίνεται έντονο και πιο συμπυκνωμένο.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις  

### Τι γίνεται αν η γραμματοσειρά δεν εμφανίζεται καθόλου;  

- **Λείπουν FontSettings**: Ελέγξτε ότι η εντολή `doc.FontSettings = fontSettings;` εκτελείται **πριν** προστεθεί οποιοδήποτε κείμενο.
- **Λανθασμένο όνομα οικογένειας**: Χρησιμοποιήστε `fontSettings.GetFonts()` για να δείτε όλες τις εντοπισμένες οικογένειες· αντιγράψτε το ακριβές κείμενο.
- **Μη υποστηριζόμενο βάρος/stretch**: Κάποιες μεταβλητές γραμματοσειρές υποστηρίζουν μόνο ένα υποσύνολο του εύρους 100‑900. Χρησιμοποιήστε `run.Font.FontWeight = 400;` ως ασφαλή εναλλακτική.

### Μπορώ να αλλάξω το βάρος μετά την αποθήκευση του εγγράφου;  

Ναι. Το αντικείμενο `Run` είναι μεταβλητό, οπότε μπορείτε να προσαρμόσετε `FontWeight` ή `FontStretch` οποτεδήποτε πριν το τελικό `Save`. Αν χρειάζεται να εναλλάσσετε βάρη δυναμικά (π.χ. βάσει αλληλεπίδρασης χρήστη), σκεφτείτε να δημιουργήσετε ξεχωριστά runs για κάθε κατάσταση.

### Λειτουργεί αυτό με έξοδο DOCX;  

Απόλυτα. Τα μεταδεδομένα μεταβλητού βάρους αποθηκεύονται στο υποκείμενο OpenXML και οι σύγχρονες εκδόσεις του Word μπορούν να τα ερμηνεύσουν. Ωστόσο, παλαιότερες εκδόσεις του Word μπορεί να αγνοούν τη ρύθμιση stretch.

---

## Πλήρες Παράδειγμα Εργασίας  

Παρακάτω υπάρχει ένα ολοκληρωμένο πρόγραμμα console που μπορείτε να μεταγλωττίσετε και να τρέξετε αμέσως. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using`, διαχείριση σφαλμάτων και σχόλια.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Η κονσόλα εκτυπώνει τη διαδρομή αποθήκευσης και το παραγόμενο PDF εμφανίζει το κείμενο σε ελαφρύ, επεκταμένο στυλ — ακριβώς όπως το ρυθμίσαμε.

---

## Ανακεφαλαίωση  

Καλύψαμε πώς να **χρησιμοποιήσετε γραμματοσειρά μεταβλητού βάρους** σε C# με το Aspose.Words, δείξαμε πώς να **ορίσετε το βάρος της γραμματοσειράς προγραμματιστικά** και παρουσιάσαμε τον ακριβή **κώδικα αλλαγής stretch** που απαιτείται για επέκταση ή σύμπτυξη των γλυφών. Τα βήματα είναι απλά: ρυθμίστε `FontSettings`, συνδέστε τα με ένα `Document`, δημιουργήστε ένα `Run`, επιλέξτε την οικογένεια μεταβλητού βάρους και, τέλος, τροποποιήστε `FontWeight` και `FontStretch`.

---

## Τι Ακολουθεί;  

- **Δυναμική ενσωμάτωση UI**: Ενσωματώστε την ίδια λογική σε εφαρμογή WinForms ή WPF ώστε οι χρήστες να επιλέγουν βάρος/stretch μέσω sliders.
- **Πολλαπλά runs**: Συνδυάστε πολλά runs με διαφορετικά βάρη στην ίδια παράγραφο για πλούσιες τυπογραφικές ιεραρχίες.
- **Πρόσθετοι άξονες**: Κάποιες μεταβλητές γραμματοσειρές εκθέτουν επιπλέον άξονες (π.χ. slant, optical size). Χρησιμοποιήστε `run.Font.FontStyle` ή εξερευνήστε `FontVariationSettings` για ακόμη πιο ακριβή έλεγχο.
- **Συμβουλές απόδοσης**: Κρατήστε το αντικείμενο `FontSettings` στην μνήμη όταν επεξεργάζεστε πολλά έγγραφα για να αποφύγετε επαναλαμβανόμενες σάρωση φακέλων.

Πειραματιστείτε — αντικαταστήστε το *Roboto Flex* με *Inter Variable* ή οποιαδήποτε άλλη OpenType μεταβλητή γραμματοσειρά, και δείτε τα έγγραφά σας να αποκτούν νέο επίπεδο οπτικής ευελιξίας. Καλό coding!


## Τι Θα Μάθετε Στη Σειρά;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}