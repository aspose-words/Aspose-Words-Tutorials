---
category: general
date: 2026-03-13
description: Αποθήκευση του Word ως Markdown και μετατροπή του DOCX σε Markdown με
  εξαγωγή εικόνων. Μάθετε πώς να εξάγετε εικόνες από DOCX με το Aspose.Words σε C#.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: el
og_description: Αποθήκευση Word ως Markdown σε C#. Αυτός ο οδηγός δείχνει πώς να μετατρέψετε
  DOCX σε Markdown και να εξάγετε εικόνες, παρέχοντας μια έτοιμη προς εκτέλεση λύση.
og_title: Αποθήκευση Word ως Markdown – Μετατροπή DOCX & Εξαγωγή Εικόνων
tags:
- Aspose.Words
- C#
- Markdown
title: Αποθήκευση Word ως Markdown – Πλήρης Οδηγός για τη Μετατροπή DOCX και την Εξαγωγή
  Εικόνων
url: /el/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word ως Markdown – Πλήρης Οδηγός για Μετατροπή DOCX και Εξαγωγή Εικόνων

Ποτέ χρειάστηκε να **αποθηκεύσετε το Word ως markdown** αλλά δεν ήξερες πώς να διατηρήσεις τις εικόνες άθικτες; Δεν είσαι μόνος. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν τα αρχεία DOCX τους περιέχουν ενσωματωμένα γραφικά και οι απλοί μετατροπείς δημιουργούν μια σειρά σπασμένων συνδέσμων.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από μια πρακτική λύση που **μετατρέπει ένα DOCX σε markdown** **και** εξάγει κάθε εικόνα σε έναν φάκελο που ελέγχεις. Στο τέλος θα έχεις ένα καθαρό αρχείο `.md`, έναν τακτοποιημένο φάκελο `markdown_resources` και μια σαφή κατανόηση γιατί η προσέγγιση με callback είναι ο πιο αξιόπιστος τρόπος διαχείρισης πόρων.

> **Pro tip:** Το ίδιο μοτίβο λειτουργεί για CSS, γραμματοσειρές ή οποιονδήποτε εξωτερικό πόρο μπορεί να εκδώσει το Aspose.Words κατά τη διάρκεια μιας λειτουργίας αποθήκευσης.

![Διάγραμμα ροής μετατροπής Save Word as Markdown](conversion-diagram.png "Διάγραμμα ροής μετατροπής")

## Τι Θα Μάθετε

- Πώς να **αποθηκεύσετε το Word ως markdown** χρησιμοποιώντας το Aspose.Words for .NET.
- Τα ακριβή βήματα για **μετατροπή docx σε markdown** διατηρώντας τις εικόνες.
- Μια επαναχρησιμοποιήσιμη υλοποίηση `IResourceSavingCallback` που **εξάγει εικόνες από docx**.
- Συνηθισμένα προβλήματα (π.χ. διπλά ονόματα αρχείων, ελλιπείς φάκελοι) και πώς να τα αποφύγετε.
- Πώς φαίνεται το παραγόμενο markdown και πού καταλήγουν οι εικόνες.

Θα χρειαστείτε μια πρόσφατη έκδοση του **Aspose.Words for .NET** (ο οδηγός δοκιμάστηκε με την 24.12) και ένα runtime .NET 6+. Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

---

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Aspose.Words for .NET (NuGet `Aspose.Words`) | Παρέχει την κλάση `Document` και το `MarkdownSaveOptions`. |
| .NET 6 ή νεότερο | Εξασφαλίζει ότι χαρακτηριστικά της γλώσσας όπως οι δηλώσεις `using` λειτουργούν χωρίς επιπλέον κώδικα. |
| Ένα αρχείο DOCX που περιέχει εικόνες (π.χ. `Images.docx`) | Η πηγή που θα μετατρέψουμε και από την οποία θα εξάγουμε τις εικόνες. |
| Δικαιώματα εγγραφής στον φάκελο εξόδου | Το callback γράφει αρχεία εικόνας· χωρίς δικαιώματα θα προκύψει εξαίρεση. |

Αν έχετε ήδη όλα αυτά, υπέροχα—ας ξεκινήσουμε.

---

## Βήμα 1: Φόρτωση του Πηγαίου DOCX – Το Αρχικό Σημείο για Save Word as Markdown

Το πρώτο που κάνουμε είναι να ανοίξουμε το έγγραφο Word. Το Aspose.Words διαβάζει το αρχείο στη μνήμη, διατηρώντας όλες τις εσωτερικές δομές (παράγραφοι, πίνακες, εικόνες κ.λπ.).

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **Γιατί είναι σημαντικό:** Η προημερόχρονη φόρτωση του αρχείου μας επιτρέπει να ελέγξουμε τα περιεχόμενά του (π.χ. `sourceDoc.GetChildNodes(NodeType.Shape, true)`) αν χρειαστεί να εντοπίσουμε ελλιπείς εικόνες.

---

## Βήμα 2: Διαμόρφωση των Επιλογών Αποθήκευσης Markdown με Callback Αποθήκευσης Εικόνας

Όταν το Aspose.Words γράφει ένα αρχείο markdown, μπορεί να χρειαστεί να αποθηκεύσει εξωτερικούς πόρους όπως εικόνες. Συνδέοντας ένα `ResourceSavingCallback`, αποκτούμε πλήρη έλεγχο πάνω στο πού θα τοποθετηθούν αυτά τα αρχεία και ποιο όνομα θα λάβουν.

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **Πώς να εξάγετε εικόνες:** Το callback λαμβάνει ένα αντικείμενο `ResourceSavingArgs` που περιέχει το ρεύμα εικόνας, το αρχικό όνομα αρχείου και έναν δείκτη. Μπορούμε να μετονομάσουμε το αρχείο, να το μετακινήσουμε ή ακόμη και να παραλείψουμε την αποθήκευση.

---

## Βήμα 3: Αποθήκευση του Εγγράφου ως Markdown – Ο Πυρήνας του Save Word as Markdown

Τώρα καλούμε το `Document.Save`. Η βιβλιοθήκη θα καλέσει το callback μας για κάθε εικόνα, θα γράψει το αρχείο εικόνας όπου του υποδείξαμε και τέλος θα δημιουργήσει ένα αρχείο markdown με σωστούς συνδέσμους `![]()`.

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

Σε αυτό το σημείο θα πρέπει να δείτε δύο πράγματα στο `YOUR_DIRECTORY`:

1. `DocWithImages.md` – η αναπαράσταση markdown του αρχικού αρχείου Word.
2. Φάκελος `markdown_resources` – μια συλλογή αρχείων `img_0.png`, `img_1.jpg`, … κ.λπ.

---

## Βήμα 4: Υλοποίηση του Callback Αποθήκευσης Εικόνας – Πώς να Εξάγετε Εικόνες από DOCX

Παρακάτω βρίσκεται η πλήρης κλάση callback. Δημιουργεί έναν φάκελο αν χρειάζεται, κατασκευάζει ένα μοναδικό όνομα αρχείου, γράφει το ρεύμα εικόνας και στη συνέχεια ενημερώνει το Aspose.Words να χρησιμοποιήσει το όνομα μας (με την ανάθεση `args.FileName`) και να παραλείψει την προεπιλεγμένη αποθήκευση (`args.Stream = null`).

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### Γιατί Λειτουργεί

- **Καθοριστικά ονόματα αρχείων** – Η χρήση του `args.ImageIndex` εγγυάται μοναδικότητα ακόμα και αν το αρχικό DOCX είχε διπλά ονόματα.
- **Απομόνωση φακέλου** – Όλα τα εξαγόμενα περιουσιακά στοιχεία ζουν κάτω από το `markdown_resources`, διατηρώντας το έργο σας τακτοποιημένο.
- **Απόδοση** – Αντιγράφουμε το ρεύμα άμεσα· χωρίς επιπλέον buffering ή επεξεργασία εικόνας, έτσι η μετατροπή παραμένει γρήγορη.

---

## Βήμα 5: Επαλήθευση της Εξόδου – Πώς Φαίνεται το Markdown

Ανοίξτε το `DocWithImages.md` σε οποιονδήποτε επεξεργαστή. Θα πρέπει να δείτε κάτι σαν:

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

Αν ανοίξετε το αρχείο markdown σε προβολή που σέβεται σχετικές διαδρομές (π.χ. προεπισκόπηση VS Code, GitHub κ.λπ.), οι εικόνες θα εμφανιστούν σωστά.

### Γρήγορος έλεγχος λογικής

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

Θα πρέπει να δείτε μία γραμμή ανά εικόνα· ο αριθμός θα ταιριάζει με τον αριθμό των εικόνων που ήταν ενσωματωμένες αρχικά στο `Images.docx`.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν το DOCX περιέχει γραφικά SVG ή EMF;

Το Aspose.Words μετατρέπει τις περισσότερες μορφές διανυσματικών γραφικών σε PNG αυτόματα. Το callback θα συνεχίσει να λαμβάνει ένα ρεύμα, και η επέκταση αρχείου θα είναι `.png`. Δεν απαιτείται επιπλέον κώδικας.

### Πώς αλλάζω το όνομα του φακέλου εξόδου;

Απλώς τροποποιήστε τη μεταβλητή `resourcesFolder` στην κλάση `ImageSavingCallback`. Θυμηθείτε να διατηρήσετε την ίδια σχετική αναφορά (`args.FileName = Path.GetFileName(imageFileName)`) ώστε οι σύνδεσμοι markdown να παραμείνουν σωστοί.

### Μπορώ να παραλείψω την αποθήκευση ορισμένων εικόνων (π.χ. πολύ μεγάλων);

Ναι. Εξετάστε το `args.Stream.Length` μέσα στο callback. Αν υπερβαίνει ένα όριο, μπορείτε είτε να το μετονομάσετε σε placeholder είτε να ορίσετε `args.Cancel = true` για να το παραλείψετε εντελώς.

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### Λειτουργεί αυτή η προσέγγιση και για άλλους τύπους πόρων όπως CSS;

Απολύτως. Το ίδιο callback ενεργοποιείται για οποιονδήποτε εξωτερικό πόρο. Μπορείτε να ελέγξετε το `args.ContentType` και να διαχειριστείτε CSS, γραμματοσειρές ή βίντεο διαφορετικά.

---

## Πλήρες Παράδειγμα – Έτοιμο για Αντιγραφή‑Επικόλληση

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να τοποθετήσετε σε μια εφαρμογή console. Αλλάξτε το placeholder `YOUR_DIRECTORY` σε απόλυτη ή σχετική διαδρομή στο σύστημά σας.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το παραγόμενο markdown και θα δείτε όλες τις εικόνες να εμφανίζονται ακριβώς εκεί που εμφανίζονταν στο αρχικό αρχείο Word.

---

## Συμπέρασμα

Μόλις καλύψαμε **πώς να αποθηκεύσετε το Word ως markdown** ενώ **εξάγετε εικόνες από docx** χρησιμοποιώντας ένα καθαρό μοτίβο callback. Το κύριο συμπέρασμα είναι ότι το `IResourceSavingCallback` σας δίνει πλήρη έλεγχο πάνω σε κάθε εξωτερικό αρχείο, καθιστώντας τη μετατροπή αξιόπιστη για οποιοδήποτε παραγωγικό pipeline.

Σε ένα μόνο, αντιγράψιμο παράδειγμα:

1. Φορτώσαμε ένα DOCX που περιείχε εικόνες.
2. Διαμορφώσαμε `MarkdownSaveOptions` με προσαρμοσμένο `ImageSavingCallback`.
3. Αποθηκεύσαμε το έγγραφο ως markdown, αφήνοντας το callback να γράψει κάθε εικόνα στο `markdown_resources`.
4. Επαληθεύσαμε την έξοδο και συζητήσαμε πώς να προσαρμόσουμε τη διαδικασία για ακραίες περιπτώσεις.

Από εδώ μπορείτε:

- **Να μετατρέψετε docx σε markdown** μαζικά, επαναλαμβάνοντας τον κώδικα για έναν φάκελο.
- **Να μετονομάσετε τις εικόνες** βάσει των αρχικών λεζαντών για καλύτερο SEO.
- **Να ενσωματώσετε το αποτέλεσμα** σε στατικούς δημιουργούς ιστοσελίδων (π.χ. Hugo, Jekyll) μετακινώντας το φάκελο markdown στο δέντρο περιεχομένου σας.
- **Να επεκτείνετε το callback** ώστε να εξάγει επίσης ενσωματωμένες γραμματοσειρές ή CSS αν χρειαστείτε πλήρη εξαγωγή HTML.

Πειραματιστείτε—ίσως αντικαταστήσετε το σχήμα ονομασίας εικόνων με GUIDs για απόλυτη μοναδικότητα, ή προσθέσετε μια γραμμή καταγραφής για να παρακολουθείτε κάθε αποθηκευμένο πόρο. Ο ουρανός είναι το όριο όταν έχετε τον έλεγχο της διαδικασίας αποθήκευσης.

Καλό coding, και ας εμφανίζονται πάντα οι εικόνες σας σωστά στο markdown!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}