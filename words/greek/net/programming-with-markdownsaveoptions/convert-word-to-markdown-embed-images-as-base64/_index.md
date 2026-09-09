---
category: general
date: 2026-01-03
description: Μετατρέψτε το Word σε Markdown και ενσωματώστε τις εικόνες ως base64
  σε ένα βήμα. Μάθετε πώς να αποθηκεύετε το Word ως markdown, να δημιουργείτε markdown
  από το Word και να χρησιμοποιείτε base64 data‑uri εικόνας.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: el
og_description: Μετατρέψτε το Word σε Markdown και ενσωματώστε εικόνες ως base64 data
  URIs. Αυτός ο βήμα‑βήμα οδηγός δείχνει πώς να αποθηκεύσετε το Word ως markdown και
  να δημιουργήσετε markdown από το Word.
og_title: Μετατροπή Word σε Markdown – Οδηγός Ενσωμάτωσης Εικόνας Base64
tags:
- Aspose.Words
- C#
- Markdown
title: Μετατροπή Word σε Markdown – Ενσωμάτωση εικόνων ως Base64
url: /el/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Word σε Markdown – Ενσωμάτωση Εικόνων ως Base64

Έχετε ποτέ χρειαστεί να **convert Word to markdown** αλλά να αντιμετωπίζετε προβλήματα με τις εικόνες; Δεν είστε μόνοι. Το Word αποθηκεύει τις εικόνες ως ξεχωριστά αρχεία, ενώ το markdown προτιμά εκείνα τα μικρά `data:image/...;base64,` strings που κρατούν τα πάντα τακτικά σε ένα μόνο αρχείο.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που **αποθηκεύει το Word ως markdown**, **ενσωματώνει εικόνες ως base64**, και ακόμη δείχνει πώς να **generate markdown from Word** χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος, θα έχετε ένα ενιαίο αρχείο `.md` που αποδίδει ακριβώς όπως το αρχικό έγγραφο—χωρίς εξωτερικούς φακέλους εικόνων.

## Τι Θα Χρειαστείτε

- **.NET 6.0 ή νεότερο** (οτιδήποτε μπορεί να αναφερθεί σε πακέτο NuGet)
- **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί καλά για δοκιμές)
- Ένα απλό αρχείο `.docx` με μερικές εικόνες (θα το ονομάσουμε `input.docx`)
- Το αγαπημένο σας IDE (Visual Studio, Rider, VS Code—επιλέξτε ό,τι προτιμάτε)

Αν τα έχετε ήδη, τέλεια—ας ξεκινήσουμε. Αν όχι, η εγκατάσταση του πακέτου NuGet γίνεται με μια γραμμή:

```bash
dotnet add package Aspose.Words
```

## Βήμα 1: Φόρτωση του Εγγράφου Word — το σημείο εκκίνησης για **convert word to markdown**

Πρώτα πρέπει να φέρουμε το `.docx` στη μνήμη. Εδώ αρχίζει η μαγεία της μετατροπής.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί αυτό έχει σημασία:**  
> Η φόρτωση του εγγράφου δίνει στο Aspose πλήρη πρόσβαση στο κείμενο, τα στυλ και κάθε ενσωματωμένο πόρο. Χωρίς αυτό το βήμα, δεν υπάρχει τίποτα προς μετατροπή.

## Βήμα 2: Ρύθμιση του MarkdownSaveOptions με Callback Αποθήκευσης Πόρων

Το Aspose σας επιτρέπει να παρεμβείτε σε κάθε πόρο (όπως εικόνες) που κανονικά θα γραφόταν στο δίσκο. Παρέχοντας ένα προσαρμοσμένο `IResourceSavingCallback`, μπορούμε να αντικαταστήσουμε την προεπιλεγμένη αποθήκευση σε αρχείο με μια **base64 image data uri**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### Ο Προσαρμοσμένος Χειριστής – Μετατροπή εικόνων σε Base64

Παρακάτω είναι η πλήρης υλοποίηση. Παρατηρήστε πώς ελέγχουμε `args.ResourceType == ResourceType.Image` και μετά:

1. Γράφουμε την εικόνα σε ένα `MemoryStream`.
2. Μετατρέπουμε το byte array σε συμβολοσειρά Base64.
3. Δημιουργούμε ένα URI `data:image/jpeg;base64,` και το αναθέτουμε στο `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Pro tip:** Αν το πηγαίο Word χρησιμοποιεί PNG, αντικαταστήστε το `ImageSaveOptions.DefaultJpeg` με `ImageSaveOptions.DefaultPng` και αλλάξτε τον τύπο MIME ανάλογα (`image/png`).

## Βήμα 3: Αποθήκευση του Εγγράφου ως Markdown – το τελικό **save word as markdown** βήμα

Τώρα που το callback είναι έτοιμο, η πραγματική αποθήκευση είναι μια γραμμή κώδικα.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

Όταν ανοίξετε το `output.md` σε οποιονδήποτε markdown viewer (προεπισκόπηση VS Code, GitHub, κλπ.), θα δείτε το κείμενο ακριβώς όπως στο αρχικό αρχείο Word, και οι εικόνες θα εμφανιστούν ενσωματωμένες χωρίς ξεχωριστά αρχεία εικόνας.

## Αναμενόμενο Αποτέλεσμα

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

Η γραμμή `![Embedded Image]` είναι μια **base64 image data uri**—η ολόκληρη εικόνα είναι κωδικοποιημένη εκεί. Χωρίς επιπλέον φακέλους, χωρίς σπασμένους συνδέσμους.

## Περιπτώσεις Ορίων & Πώς να τις Διαχειριστείτε

| Κατάσταση | Τι να κάνετε |
|-----------|--------------|
| **Μεγάλες Εικόνες** – Το Base64 αυξάνει το μέγεθος κατά ~33% | Σκεφτείτε να αλλάξετε το μέγεθος πριν τη μετατροπή: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Μη‑JPEG Εικόνες** (PNG, GIF) | Εντοπίστε την αρχική μορφή μέσω `args.ResourceData.ImageType` και ορίστε τον σωστό τύπο MIME (`image/png`, `image/gif`). |
| **Πολύ Μεγάλα Έγγραφα** (εκατοντάδες εικόνες) | Παρακολουθήστε τη χρήση μνήμης· μπορείτε να μεταφέρετε προσωρινά κάθε εικόνα στο δίσκο αν η διαδικασία εξαντλήσει τη RAM. |
| **Απαιτούνται Ξεχωριστά Αρχεία Εικόνας** (π.χ., για static site) | Επιστρέψτε `false` από το callback για τις εικόνες που θέλετε να διατηρήσετε ως αρχεία, και αφήστε το Aspose να τις γράψει σε φάκελο. |

## Συχνές Ερωτήσεις (Απαντημένες Εμπρός)

- **Does this work with .doc files?** Ναι—το Aspose.Words μπορεί να φορτώσει παλαιά αρχεία `.doc` με τον ίδιο τρόπο που φορτώνετε `.docx`. Απλώς δείξτε το `new Document("myfile.doc")` σε αυτό.
- **What about tables and footnotes?** Υποστηρίζονται πλήρως από τον Markdown exporter. Οι πίνακες γίνονται markdown tables· οι υποσημειώσεις γίνονται ενσωματωμένες αναφορές.
- **Can I change the markdown flavor?** Το `MarkdownSaveOptions` έχει ιδιότητα `MarkdownVersion` (CommonMark, GitHub, κλπ.). Ορίστε την πριν την αποθήκευση αν χρειάζεστε συγκεκριμένη σύνταξη.

## Πλήρες, Έτοιμο‑για‑Εκτέλεση Παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια console app. Περιλαμβάνει όλες τις δηλώσεις using, την κλάση του handler και τη διαχείριση σφαλμάτων.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το παραγόμενο `output.md`, και θα δείτε ένα τέλειο αντίγραφο markdown του αρχείου Word—**convert word to markdown** δεν ήταν ποτέ πιο απλό.

## Περίληψη

Ξεκινήσαμε με το πρόβλημα του **convert word to markdown** ενώ διατηρούσαμε τις εικόνες ενσωματωμένες. Φορτώνοντας το έγγραφο, ρυθμίζοντας ένα callback `MarkdownSaveOptions` και αποθηκεύοντας το αρχείο, πετύχαμε μια καθαρή λύση **save word as markdown** που παράγει **base64 image data uri** strings. Τώρα ξέρετε επίσης πώς να **embed images as base64**, να διαχειριστείτε περιπτώσεις ορίων και να προσαρμόσετε τη διαδικασία για διαφορετικούς τύπους εικόνων.

## Τι Ακολουθεί;

- **Generate HTML instead of markdown** – αντικαταστήστε το `MarkdownSaveOptions` με `HtmlSaveOptions` και χρησιμοποιήστε ξανά το ίδιο callback.
- **Batch convert multiple files** – τυλίξτε τη λογική σε έναν βρόχο `foreach` πάνω σε φάκελο.
- **Integrate into a CI pipeline** – αυτοματοποιήστε τη δημιουργία τεκμηρίωσης για static sites.

Νιώστε ελεύθεροι να πειραματιστείτε, να ρυθμίσετε την ποιότητα των εικόνων, ή ακόμη και να προσθέσετε τη δική σας προσαρμοσμένη διαχείριση πόρων (π.χ., ανεβάζοντας εικόνες σε CDN και εισάγοντας το URL). Ο ουρανός είναι το όριο όταν συνδυάζετε το Aspose.Words με λίγη εφευρετικότητα σε C#.

Καλή προγραμματιστική, και ας αποδίδει πάντα τέλεια το markdown σας! 

![Διάγραμμα που δείχνει τη ροή μετατροπής word σε markdown – ενσωμάτωση εικόνων ως base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}