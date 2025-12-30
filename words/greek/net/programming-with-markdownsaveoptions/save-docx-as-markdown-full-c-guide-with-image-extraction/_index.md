---
category: general
date: 2025-12-29
description: Αποθηκεύστε το docx ως markdown χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να μετατρέπετε το Word σε markdown, να εξάγετε εικόνες, να δημιουργείτε φάκελο
  πόρων και να διαμορφώνετε τις επιλογές markdown.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- how to extract images
- create resources folder
- how to configure markdown
language: el
og_description: Αποθηκεύστε το docx ως markdown με το Aspose.Words. Οδηγός βήμα‑προς‑βήμα
  για τη μετατροπή του Word σε markdown, την εξαγωγή εικόνων, τη δημιουργία φακέλου
  πόρων και τη ρύθμιση του markdown.
og_title: Αποθήκευση docx ως markdown – Πλήρης Οδηγός C#
tags:
- Aspose.Words
- C#
- Document Conversion
title: Αποθήκευση docx ως markdown – Πλήρης οδηγός C# με εξαγωγή εικόνων
url: /el/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# αποθήκευση docx ως markdown – Πλήρης Εκπαίδευση C#

Κάποτε χρειάστηκε να **αποθηκεύσετε docx ως markdown** αλλά δεν ήξερες πώς να διατηρήσεις τις ενσωματωμένες εικόνες; Δεν είσαι μόνος. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν η μετατροπή αφαιρεί τις εικόνες, αφήνοντας το αρχείο Markdown κενό. Σε αυτόν τον οδηγό θα περάσουμε βήμα-βήμα από μια πρακτική λύση που όχι μόνο **μετατρέπει word σε markdown** αλλά επίσης δείχνει **πώς να εξάγετε εικόνες**, δημιουργεί αυτόματα **φάκελο πόρων**, και ρυθμίζει σωστά τις **επιλογές markdown** για καθαρό αποτέλεσμα.

Στο τέλος αυτού του άρθρου θα έχετε ένα έτοιμο προς εκτέλεση απόσπασμα C# που παίρνει οποιοδήποτε `.docx`, εξάγει κάθε εικόνα, τις αποθηκεύει σε έναν αφιερωμένο φάκελο και παράγει ένα αρχείο Markdown του οποίου οι σύνδεσμοι εικόνων δείχνουν σε αυτόν το φάκελο. Δεν απαιτείται επιπλέον επεξεργασία.

## Τι Θα Μάθετε

- Φόρτωση εγγράφου Word με Aspose.Words.  
- Ρύθμιση `MarkdownSaveOptions` για καταγραφή εξωτερικών πόρων.  
- Αυτόματη δημιουργία φακέλου **Resources** δίπλα στο αρχείο Markdown.  
- Εγγραφή αρχείων εικόνας χρησιμοποιώντας το `ResourceSavingCallback`.  
- Επαλήθευση ότι το παραγόμενο Markdown αναφέρει σωστά τις εικόνες.

### Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.6+).  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`).  
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία εικόνα.  

Αν έχετε ήδη όλα αυτά, τέλεια—ας ξεκινήσουμε.

## Βήμα 1 – Φόρτωση του Εγγράφου Word

Το πρώτο που κάνουμε είναι να ανοίξουμε το αρχείο προέλευσης. Αυτό το βήμα είναι απλό αλλά ουσιώδες· το αντικείμενο εγγράφου είναι η πηγή τόσο για το κείμενο όσο και για τα μέσα.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the Word document that contains images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί είναι σημαντικό:**  
> Η φόρτωση του αρχείου δημιουργεί μια αναπαράσταση στη μνήμη όπου το Aspose μπορεί να απαριθμήσει κάθε κόμβο—παράγραφοι, πίνακες και, κυρίως, αντικείμενα `Shape` που περιέχουν εικόνες. Χωρίς φόρτωση, δεν υπάρχει τίποτα για εξαγωγή.

## Βήμα 2 – Ρύθμιση Επιλογών Markdown (ο Πυρήνας της Μετατροπής)

Τώρα λέμε στο Aspose πώς θέλουμε να συμπεριφέρεται το αρχείο Markdown. Η κλάση `MarkdownSaveOptions` προσφέρει έναν delegate `ResourceSavingCallback` που καλείται για κάθε εξωτερικό πόρο (εικόνες, διαγράμματα κ.λπ.). Μέσα σε αυτό το callback αποφασίζουμε πού θα γράψουμε το αρχείο και ποιο URI θα ενσωματώσουμε.

```csharp
// Set up Markdown save options with a callback for external resources.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // The callback runs for every image/chart the exporter needs to write.
    ResourceSavingCallback = (sender, args) =>
    {
        // Step 3 – Ensure the Resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build the absolute path for the image file.
        string resourceFilePath = Path.Combine(resourcesFolder, args.ResourceFileName);
        args.Stream = new FileStream(resourceFilePath, FileMode.Create);

        // Use a relative path in the generated Markdown file.
        args.Uri = "Resources/" + args.ResourceFileName;
    }
};
```

### Πώς να Ρυθμίσετε το Markdown για Εξαγωγή Εικόνων

- **`ResourceSavingCallback`** – η αγκίστρωση που μας επιτρέπει να γράψουμε κάθε εικόνα όπου θέλουμε.  
- **`args.ResourceFileName`** – ένα μοναδικό όνομα που δημιουργεί το Aspose (π.χ., `image001.png`).  
- **`args.Uri`** – η συμβολοσειρά που καταλήγει στον σύνδεσμο του Markdown· την ορίζουμε σε σχετική διαδρομή ώστε το Markdown να παραμένει φορητό.

> **Συμβουλή:** Αν χρειάζεστε προσαρμοσμένο σχήμα ονοματοδοσίας (π.χ., διατήρηση του αρχικού ονόματος εικόνας), μπορείτε να ελέγξετε το `args.ResourceFileName` και να το αντικαταστήσετε πριν ορίσετε το `args.Uri`.

## Βήμα 3 – Δημιουργία του Φακέλου Πόρων (και Εξαγωγή Εικόνων)

Το callback που ορίσαμε στο προηγούμενο βήμα δημιουργεί ήδη τον φάκελο «on‑the‑fly», αλλά ας συζητήσουμε γιατί αυτή είναι η προτεινόμενη προσέγγιση.

```csharp
// Inside the callback (repeated for emphasis):
string resourcesFolder = "YOUR_DIRECTORY/Resources/";
Directory.CreateDirectory(resourcesFolder);
```

> **Γιατί να δημιουργήσετε έναν αφιερωμένο φάκελο;**  
> Η αποθήκευση των εικόνων σε ξεχωριστό κατάλογο διατηρεί το Markdown καθαρό και αντανακλά τον τρόπο που πολλοί στατικοί δημιουργοί ιστοτόπων (όπως Jekyll ή Hugo) αναμένουν να οργανώνονται τα περιουσιακά στοιχεία. Επίσης αποτρέπει συγκρούσεις ονομάτων αν εκτελέσετε τη μετατροπή πολλές φορές.

### Ακραίες Περιπτώσεις & Παραλλαγές

| Κατάσταση | Τι Πρέπει να Προσαρμόσετε |
|-----------|---------------------------|
| **Μεγάλο DOCX με εκατοντάδες εικόνες** | Σκεφτείτε τη ροή των εικόνων για αποφυγή πίεσης μνήμης· το callback ήδη γράφει κάθε εικόνα απευθείας στο δίσκο, κάτι που είναι αποδοτικό σε μνήμη. |
| **Μη‑PNG εικόνες (π.χ., JPEG, GIF)** | Το `args.ResourceFileName` περιέχει ήδη τη σωστή επέκταση, οπότε δεν χρειάζεται επιπλέον επεξεργασία. |
| **Προσαρμοσμένη διαδρομή εξόδου** | Αντικαταστήστε το `"YOUR_DIRECTORY/Resources/"` με μια διαδρομή σχετική με τη ρίζα του έργου σας, ή διαβάστε την από αρχείο ρυθμίσεων. |

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Markdown

Με τις επιλογές πλήρως ρυθμισμένες, το τελευταίο βήμα είναι μια μόνο γραμμή που γράφει το αρχείο Markdown και ενεργοποιεί το callback για κάθε εικόνα.

```csharp
// Save the document as Markdown, applying the resource handling logic.
document.Save("YOUR_DIRECTORY/WithResources.md", markdownSaveOptions);
```

### Αναμενόμενο Αποτέλεσμα

- `WithResources.md` – αρχείο Markdown που περιέχει τυπική σύνταξη (`![Alt text](Resources/image001.png)`) για κάθε εικόνα.  
- `Resources/` – φάκελος γεμάτος με τα εξαγόμενα αρχεία εικόνας.

Μπορείτε να ανοίξετε το Markdown σε οποιονδήποτε προβολέα (VS Code, GitHub ή στατικό δημιουργό ιστοτόπων) και θα δείτε τις αρχικές εικόνες να εμφανίζονται ακριβώς εκεί που εμφανίζονταν στο έγγραφο Word.

![Δομή φακέλου που εμφανίζει τον φάκελο Resources με τις εξαγόμενες εικόνες – save docx as markdown](https://example.com/placeholder.png "Δομή φακέλου για εξαγόμενες εικόνες – save docx as markdown")

*Κείμενο alt εικόνας: “Δομή φακέλου που εμφανίζει τον φάκελο Resources με τις εξαγόμενες εικόνες – save docx as markdown” – ικανοποιεί την απαίτηση alt για την κύρια λέξη‑κλειδί.*

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο να ενσωματωθεί σε μια εφαρμογή κονσόλας. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο σύστημά σας.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Prepare Markdown options with a resource callback.
        MarkdownSaveOptions options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                // 3️⃣ Ensure the Resources folder exists.
                string resourcesFolder = "YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                // 4️⃣ Write the image file to disk.
                string filePath = Path.Combine(resourcesFolder, args.ResourceFileName);
                args.Stream = new FileStream(filePath, FileMode.Create);

                // 5️⃣ Set the relative URI used in the Markdown file.
                args.Uri = "Resources/" + args.ResourceFileName;
            }
        };

        // 6️⃣ Save as Markdown – this triggers the callback for each image.
        document.Save("YOUR_DIRECTORY/WithResources.md", options);

        // Inform the user.
        System.Console.WriteLine("Conversion complete! Check the Resources folder and the Markdown file.");
    }
}
```

### Εκτέλεση του Παραδείγματος

1. Εγκαταστήστε το πακέτο NuGet Aspose.Words:  
   ```bash
   dotnet add package Aspose.Words
   ```
2. Συμπιέστε και εκτελέστε:  
   ```bash
   dotnet run
   ```
3. Ανοίξτε το `WithResources.md` σε οποιονδήποτε προβολέα Markdown. Όλες οι εικόνες πρέπει να εμφανιστούν.

## Συχνές Ερωτήσεις & Επαγγελματικές Συμβουλές

### “Μπορώ να μετατρέψω ένα .doc αντί για .docx;”
Βεβαίως—το Aspose.Words υποστηρίζει τόσο `.doc` όσο και `.docx`. Απλώς αλλάξτε την επέκταση αρχείου στον κατασκευαστή `Document`.

### “Τι γίνεται αν δεν θέλω φάκελο Resources;”
Μπορείτε να κατευθύνετε το `args.Uri` σε οποιαδήποτε τοποθεσία, ακόμη και σε URL. Για παράδειγμα, ορίστε `args.Uri = "https://mycdn.com/" + args.ResourceFileName;` και παραλείψτε τη δημιουργία φακέλου.

### “Πώς διαχειρίζομαι γραφικά SVG;”
Το Aspose αντιμετωπίζει το SVG ως ξεχωριστό τύπο πόρου. Μέσα στο callback μπορείτε να ελέγξετε `args.ResourceType` και, αν είναι `ResourceType.Svg`, να το μετονομάσετε ή να το επεξεργαστείτε διαφορετικά.

### “Υπάρχει τρόπος ενσωμάτωσης εικόνων ως Base64;”
Ναι—αντί να γράψετε σε αρχείο, μπορείτε να μετατρέψετε το `args.Stream` σε συμβολοσειρά Base64 και να ορίσετε `args.Uri = "data:image/png;base64," + base64;`. Αυτό κάνει το Markdown αυτόνομο, αλλά αυξάνει το μέγεθος του αρχείου.

### “Τι έκδοση του Aspose.Words χρειάζομαι;”
Η κλάση `MarkdownSaveOptions` εισήχθη στο Aspose.Words 22.9. Αν χρησιμοποιείτε παλαιότερη έκδοση, αναβαθμίστε μέσω NuGet.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **αποθηκεύσετε docx ως markdown** διατηρώντας κάθε εικόνα. Τα βασικά βήματα είναι:

1. Φόρτωση του DOCX με Aspose.Words.  
2. Ρύθμιση `MarkdownSaveOptions` και υλοποίηση `ResourceSavingCallback`.  
3. Μέσα στο callback, **δημιουργία φακέλου πόρων**, εγγραφή κάθε εικόνας και ορισμός σχετικού URI.  
4. Αποθήκευση του εγγράφου, αφήνοντας το Aspose να κάνει το δύσκολο μέρος.

Τώρα μπορείτε να αυτοματοποιήσετε τις διαδικασίες τεκμηρίωσης, να μεταφέρετε παλιά εγχειρίδια Word σε μορφή Markdown φιλική προς στατικούς ιστότοπους, ή απλώς να δώσετε στην ομάδα σας μια ελαφριά, ελεγχόμενη έκδοση χωρίς να χάνετε το οπτικό περιεχόμενο.

### Τι Ακολουθεί;

- Πειραματιστείτε με το **πώς να ρυθμίσετε το markdown** για προσαρμοσμένα στυλ επικεφαλίδων ή μορφοποίηση πινάκων.  
- Συνδυάστε αυτή τη μετατροπή με βήμα CI/CD για αυτόματη δημοσίευση τεκμηρίωσης.  
- Εμβαθύνετε στις άλλες μορφές εξόδου του Aspose (HTML, PDF) και δείτε πώς λειτουργεί το ίδιο μοτίβο callback.

Έχετε περισσότερα σενάρια που σας ενδιαφέρουν; Αφήστε ένα σχόλιο ή ανοίξτε νέο ζήτημα στα φόρουμ του Aspose. Καλή μετατροπή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}