---
category: general
date: 2026-03-19
description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας το Aspose.Words και μια μεταβλητή
  γραμματοσειρά. Μάθετε πώς να αλλάζετε το βάρος της γραμματοσειράς, να ορίζετε το
  πλάτος της γραμματοσειράς και να καθορίζετε τη μεταβολή της γραμματοσειράς σε C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: el
og_description: Δημιουργήστε έγγραφο Word με μεταβλητή γραμματοσειρά χρησιμοποιώντας
  το Aspose.Words. Αυτό το σεμινάριο δείχνει πώς να φορτώσετε τη γραμματοσειρά, να
  αλλάξετε το βάρος της, να ορίσετε το πλάτος της και να καθορίσετε τη μεταβλητότητα.
og_title: Δημιουργήστε Έγγραφο Word με Μεταβλητή Γραμματοσειρά – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Variable Font
title: Δημιουργία εγγράφου Word με μεταβλητή γραμματοσειρά – Οδηγός
url: /el/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Μεταβλητή Γραμματοσειρά – Οδηγός

Κάποτε χρειάστηκε να **δημιουργήσετε έγγραφο word** που χρησιμοποιεί μια σύγχρονη μεταβλητή γραμματοσειρά, αλλά δεν ήξερατε από πού να ξεκινήσετε; Δεν είστε μόνοι. Σε πολλά έργα—σκεφτείτε δυναμικές αναφορές ή φυλλάδια με συνεπή branding—η δυνατότητα **αλλαγής βάρους γραμματοσειράς** σε πραγματικό χρόνο είναι πραγματικά καθοριστική.  

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από τη φόρτωση μιας μεταβλητής γραμματοσειράς στο Aspose.Words, στον ορισμό του βάρους και του πλάτους, μέχρι την αποθήκευση ενός DOCX που φαίνεται ακριβώς όπως το σχεδιάσατε. Χωρίς ασαφείς αναφορές, μόνο συγκεκριμένος κώδικας που μπορείτε να ενσωματώσετε αμέσως στο έργο C# σας.

## Τι Θα Μάθετε

- Πώς να **φορτώνετε αρχεία μεταβλητής γραμματοσειράς** στο Aspose.Words χρησιμοποιώντας `FontSettings`.
- Η σύνταξη για **ορισμό αξόνων παραλλαγής γραμματοσειράς** όπως `wght` (weight) και `wdth` (width).
- Τρόποι **ορισμού πλάτους γραμματοσειράς** και **αλλαγής βάρους γραμματοσειράς** σε ένα μόνο `Run`.
- Συμβουλές για την αντιμετώπιση κοινών προβλημάτων (ελλιπείς γλύφους, λανθασμένες διαδρομές φακέλων κ.λπ.).
- Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε και να δοκιμάσετε αμέσως.

> **Προαπαιτούμενα**: .NET 6+ (ή .NET Framework 4.6+), Aspose.Words for .NET εγκατεστημένο μέσω NuGet, και ένα αρχείο μεταβλητής γραμματοσειράς όπως *RobotoFlex.ttf* τοποθετημένο σε τοπικό φάκελο *Fonts*.

---

## Βήμα 1 – Φόρτωση της Μεταβλητής Γραμματοσειράς στο Aspose.Words

Πρώτα, πρέπει να πούμε στο Aspose.Words πού να ψάξει για τις προσαρμοσμένες γραμματοσειρές μας. Η κλάση `FontSettings` κάνει το σκληρό κομμάτι.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Γιατί είναι σημαντικό**: Χωρίς την καταχώρηση του φακέλου, το Aspose.Words επιστρέφει στις συστημικές γραμματοσειρές και αγνοεί τυχόν δεδομένα OpenType variation που θα προσπαθήσετε να εφαρμόσετε αργότερα. Δείχνοντας του έναν συγκεκριμένο κατάλογο, εξασφαλίζετε ότι το *RobotoFlex* (ή οποιαδήποτε άλλη μεταβλητή γραμματοσειρά) θα βρεθεί κάθε φορά που εκτελείται ο κώδικας.

> **Pro tip**: Ορίστε τη δεύτερη παράμετρο του `SetFontsFolder` σε `true` αν θέλετε το Aspose να ψάχνει και σε υπο‑φακέλους. Αυτό βοηθά όταν οργανώνετε τις γραμματοσειρές ανά στυλ ή βάρος.

---

## Βήμα 2 – Δημιουργία Νέου Εγγράφου και Προσθήκη Δείγματος Κειμένου

Τώρα που η μηχανή γραμματοσειρών ξέρει πού να ψάξει, δημιουργούμε ένα κενό `Document` και εισάγουμε μια παράγραφο με ένα `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Τι συμβαίνει**: Το `Run` αντιπροσωπεύει ένα συνεχόμενο κομμάτι κειμένου με ομοιόμορφη μορφοποίηση. Δημιουργώντας το πρώτα, κρατάμε τη λογική μορφοποίησης απομονωμένη—τέλεια για μετέπειτα εφαρμογή διαφορετικών αξόνων παραλλαγής σε ξεχωριστά runs αν χρειαστεί.

---

## Βήμα 3 – Ορισμός των Επιθυμητών Αξόνων Παραλλαγής (Weight & Width)

Οι μεταβλητές γραμματοσειρές εκθέτουν *άξονες* που μπορείτε να ρυθμίσετε κατά την εκτέλεση. Οι δύο πιο συνηθισμένοι είναι `wght` (βάρος γραμματοσειράς) και `wdth` (πλάτος γραμματοσειράς). Το Aspose.Words μοντελοποιεί αυτό με τη συλλογή `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Γιατί αυτά τα νούμερα**: Στην προδιαγραφή OpenType, το `wght` κυμαίνεται από το ελάχιστο έως το μέγιστο βάρος της γραμματοσειράς (συχνά 100–900). Μια τιμή **700** αντιστοιχεί σε έντονη (bold) εμφάνιση. Το `wdth` λειτουργεί παρόμοια· **100** σημαίνει το προεπιλεγμένο (κανονικό) πλάτος, ενώ τιμές κάτω από 100 συμπιέζουν τα γλύφα.

> **Edge case**: Κάποιες μεταβλητές γραμματοσειρές δεν υποστηρίζουν έναν συγκεκριμένο άξονα. Αν δώσετε μια μη υποστηριζόμενη ετικέτα, το Aspose θα την αγνοήσει σιωπηλά. Ελέγξτε πάντα την προδιαγραφή της γραμματοσειράς (συνήθως βρίσκεται στα μεταδεδομένα του αρχείου `.ttf` ή `.otf`).

---

## Βήμα 4 – Εφαρμογή της Παραλλαγής στο Run Χρησιμοποιώντας το Όνομα Γραμματοσειράς

Τώρα συνδέουμε τα δεδομένα παραλλαγής με το πραγματικό κείμενο. Η κλάση `FontInfo` κρατά το όνομα οικογένειας γραμματοσειράς και τη συλλογή αξόνων.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Εξήγηση**: Ορίζοντας το `FontInfo`, παρακάμπτουμε την συνήθη ιδιότητα `Font.Name` και παρέχουμε στη μηχανή μια πλήρως καθορισμένη διαμόρφωση γραμματοσειράς. Αυτός είναι ο μοναδικός τρόπος να πείτε στο Aspose.Words να χρησιμοποιήσει μια μεταβλητή γραμματοσειρά με προσαρμοσμένους άξονες.

> **Συνηθισμένο λάθος**: Η παράλειψη του ακριβούς ονόματος οικογένειας μέσα στο αρχείο γραμματοσειράς (`RobotoFlex` σε αυτό το παράδειγμα). Ένα τυπογραφικό λάθος θα κάνει το Aspose να επιστρέψει σε προεπιλεγμένη γραμματοσειρά, και η παραλλαγή σας θα χαθεί.

---

## Βήμα 5 – Αποθήκευση του Εγγράφου και Επαλήθευση του Αποτελέσματος

Τέλος, γράφουμε το έγγραφο στο δίσκο. Το παραγόμενο DOCX θα περιέχει τις οδηγίες μεταβλητής γραμματοσειράς, τις οποίες το Microsoft Word (2016+) μπορεί να αποδώσει σωστά.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Ανοίξτε το παραγόμενο αρχείο στο Word, επιλέξτε το κείμενο και κοιτάξτε τον διάλογο **Font**. Θα πρέπει να δείτε το *Roboto Flex* στη λίστα, και το κείμενο θα εμφανίζεται πιο έντονο από το περιβάλλον κείμενο—ακριβώς όπως ζήτησε η ρύθμιση `wght = 700`.

> **Συμβουλή επαλήθευσης**: Αν το κείμενο φαίνεται αμετάβλητο, ελέγξτε ξανά ότι το αρχείο γραμματοσειράς υποστηρίζει πραγματικά τον άξονα `wght`. Κάποιες “μεταβλητές” γραμματοσειρές εκθέτουν μόνο `ital` (italic) ή `opsz` (optical size).

---

## Προαιρετικό: Προσθήκη Περισσότερων Παραλλαγών – Δυναμική Αλλαγή Πλάτους

Αν θέλετε να *ορίσετε πλάτος γραμματοσειράς* διαφορετικά για άλλη παράγραφο, απλώς επαναλάβετε τα βήματα 3‑4 με μια νέα συλλογή `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Τώρα έχετε δύο runs—ένα έντονο, ένα ελαφρώς πιο πλατύ—που δείχνουν τόσο **αλλαγή βάρους γραμματοσειράς** όσο και **ορισμό πλάτους γραμματοσειράς** στο ίδιο έγγραφο.

---

## Πλήρες Παράδειγμα Εργασίας

Αντιγράψτε το παρακάτω απόσπασμα σε μια νέα εφαρμογή console (`Program.cs`) και τρέξτε το. Βεβαιωθείτε ότι ο φάκελος `Fonts` περιέχει το `RobotoFlex.ttf` (ή οποιαδήποτε μεταβλητή γραμματοσειρά προτιμάτε).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Ένα αρχείο `VariableFont.docx` όπου η φράση “Variable‑weight text” εμφανίζεται έντονη, χάρη στον άξονα `wght = 700`, ενώ διατηρεί το προεπιλεγμένο πλάτος.

---

## Συχνές Ερωτήσεις & Edge Cases

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν η γραμματοσειρά δεν βρεθεί;* | Ελέγξτε τη διαδρομή του φακέλου, βεβαιωθείτε ότι το όνομα αρχείου ταιριάζει, και ότι η διεργασία έχει δικαιώματα ανάγνωσης. Μπορείτε επίσης να καλέσετε `fontSettings.GetFonts()` για να δείτε τις ανιχνευμένες γραμματοσειρές. |
| *Μπορώ να συνδυάσω πολλαπλά runs με διαφορετικές παραλλαγές;* | Απόλυτα. Κάθε `Run` μπορεί να φέρει το δικό του `FontInfo`. Απλώς επαναλάβετε τα βήματα 3‑4 για κάθε run. |
| *Υποστηρίζουν οι παλαιότερες εκδόσεις του Word τις μεταβλητές γραμματοσειρές;* | Το Word 2016 (Build 16.0.8001) εισήγαγε βασική υποστήριξη. Αν στοχεύετε παλαιότερες εκδόσεις, το έγγραφο θα επιστρέψει στην πιο κοντινή στατική εκδοχή της γραμματοσειράς. |
| *Υπάρχει όριο στον αριθμό των αξόνων που μπορώ να ορίσω;* | Μπορείτε να ορίσετε όσους άξονες ορίζει η γραμματοσειρά. Συνηθισμένες ετικέτες είναι `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Η παροχή μη υποστηριζόμενης ετικέτας δεν έχει καμία επίδραση. |
| *Πώς εντοπίζω ελλιπείς γλύφους;* | Χρησιμοποιήστε `FontSettings.GetFontSources()` για να εξετάσετε τις φορτωμένες γραμματοσειρές, και `FontInfo.HasGlyph(char)` για να δοκιμάσετε μεμονωμένους χαρακτήρες. |

---

## Συμπέρασμα

Σε λίγα βήματα δείξαμε **πώς να δημιουργήσετε αρχεία word** που αξιοποιούν τη δύναμη των μεταβλητών γραμματοσειρών, επιτρέποντάς σας **να αλλάζετε το βάρος γραμματοσειράς**, **να ορίζετε πλάτος γραμματοσειράς**, **να φορτώνετε αρχεία μεταβλητής γραμματοσειράς**, και **να ορίζετε άξονες παραλλαγής γραμματοσειράς**—όλα με το Aspose.Words for .NET.  

Η βασική ιδέα είναι απλή: καταχωρήστε το φάκελο γραμματοσειρών, περιγράψτε τους επιθυμητούς άξονες, συνδέστε τους με ένα `Run`, και αποθηκεύστε. Από εδώ μπορείτε να επεκτείνετε την τεχνική σε ολόκληρες ενότητες, πίνακες, ή ακόμη και να δημιουργήσετε προγραμματιστικά αναφορές με brand‑specific στυλ.

**Επόμενα βήματα**: δοκιμάστε να αντικαταστήσετε το `RobotoFlex` με άλλη μεταβλητή γραμματοσειρά, πειραματιστείτε με τον άξονα `ital` (italic), ή δημιουργήστε μια έκδοση PDF του ίδιου εγγράφου χρησιμοποιώντας Aspose.PDF. Το ίδιο μοτίβο ισχύει—φορτώστε, ορίστε, εφαρμόστε, αποθηκεύστε.

Καλό coding, και απολαύστε την ευελιξία που προσφέρουν οι μεταβλητές γραμματοσειρές στα έργα αυτοματοποίησης του Word!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}