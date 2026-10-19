---
category: general
date: 2026-05-26
description: Δημιουργία εγγράφου Word σε C# με Aspose.Words, εισαγωγή σχήματος ορθογωνίου,
  ορισμός χρώματος γεμίσματος και προσθήκη εφέ σκιάς – οδηγός βήμα‑προς‑βήμα.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: el
og_description: Δημιουργήστε έγγραφο Word σε C# χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να εισάγετε ένα σχήμα ορθογωνίου, να ορίσετε το χρώμα γεμίσματος και να προσθέσετε
  εφέ σκιάς.
og_title: Δημιουργία εγγράφου Word – Εισαγωγή σχήματος ορθογωνίου & σκιά σε C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργία εγγράφου Word – Εισαγωγή σχήματος ορθογωνίου & σκιάς σε C#
url: /el/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word – Εισαγωγή Σχήματος Ορθογωνίου & Σκιά σε C#

Αναρωτηθήκατε ποτέ πώς να **δημιουργήσετε έγγραφο Word** προγραμματιστικά χωρίς να ανοίξετε πρώτα το Microsoft Word; Δεν είστε οι μόνοι. Σε πολλές περιπτώσεις αυτοματοποίησης — σκεφτείτε τιμολόγια, συμβόλαια ή μαζική δημιουργία αναφορών — χρειάζεστε έναν αξιόπιστο τρόπο να δημιουργήσετε ένα αρχείο .docx, να τοποθετήσετε ένα σχήμα μέσα, να του δώσετε χρώμα και ίσως και σκιά για ένα πιο επαγγελματικό αποτέλεσμα.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από το ένα στο άλλο: χρησιμοποιώντας το Aspose.Words for .NET για **δημιουργία εγγράφου Word**, **εισαγωγή σχήματος ορθογωνίου**, εφαρμογή γεμίσματος και **προσθήκη σκιάς**. Στο τέλος θα έχετε ένα έτοιμο αρχείο που μπορείτε να αποθηκεύσετε και να ενσωματώσετε σε οποιαδήποτε επόμενη ροή εργασίας.  

Θα δούμε επίσης **πώς να εισάγετε σχήμα** με ευέλικτο τρόπο και γιατί **πώς να ορίσετε γέμισμα** είναι σημαντικό για τη σταθερότητα της εμφάνισης. Χωρίς περιττές εξηγήσεις, μόνο ο κώδικας που μπορείτε να αντιγράψετε‑και‑επικολλήσετε.

## Προαπαιτούμενα

Πριν προχωρήσουμε, βεβαιωθείτε ότι έχετε:

- .NET 6+ (ή .NET Framework 4.7+) εγκατεστημένο.
- Ένα έγκυρο license του Aspose.Words for .NET (ή ένα προσωρινό κλειδί αξιολόγησης).
- Visual Studio, Rider ή οποιοδήποτε IDE για C# προτιμάτε.
- Βασική εξοικείωση με τη σύνταξη της C# — δεν απαιτείται τίποτα περίπλοκο.

Τα έχετε όλα; Τέλεια, ας ξεκινήσουμε.

## Βήμα 1 – Δημιουργία Εγγράφου Word

Το πρώτο που χρειάζεστε είναι ένα κενό αντικείμενο εγγράφου. Αυτό είναι ο καμβάς όπου θα ζήσει ό,τι ακολουθεί.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` αντιπροσωπεύει το αρχείο .docx στη μνήμη, ενώ το `DocumentBuilder` μας παρέχει ένα βολικό API για εισαγωγή κειμένου, πινάκων και σχημάτων. **Η δημιουργία του εγγράφου Word** με αυτόν τον τρόπο είναι άμεση — χωρίς UI, χωρίς COM interop, μόνο καθαρή .NET.

## Βήμα 2 – Εισαγωγή Σχήματος Ορθογωνίου

Τώρα που έχουμε το έγγραφο, ας **εισάγουμε σχήμα ορθογωνίου**. Η μέθοδος `InsertShape` δέχεται μια τιμή του enum `ShapeType`, πλάτος και ύψος (σε points). Θα χρησιμοποιήσουμε ένα ορθογώνιο διαστάσεων 150 × 80 points, που αντιστοιχεί περίπου σε 2 × 1 ίντσες.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Στο παρασκήνιο, το Aspose δημιουργεί ένα αντικείμενο `Shape`, το προσθέτει στην τρέχουσα παράγραφο και επιστρέφει μια αναφορά που μπορείτε να μορφοποιήσετε. Αυτό είναι το βασικό **πώς να εισάγετε σχήμα** — μια μόνο γραμμή κώδικα, αλλά εξαιρετικά ισχυρή.

## Βήμα 3 – Πώς να Ορίσετε Γέμισμα

Ένα σχήμα χωρίς γέμισμα είναι αόρατο σε λευκή σελίδα. Ας του δώσουμε ένα ευχάριστο ανοιχτό‑μπλε φόντο.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Μπορείτε επίσης να χρησιμοποιήσετε διαβαθμίσεις, υφές ή ακόμη και γέμισμα με εικόνα, αλλά ένα στερεό χρώμα κρατά το παράδειγμα απλό. Αυτό δείχνει **πώς να ορίσετε γέμισμα** σε οποιοδήποτε σχήμα δημιουργείτε, εξασφαλίζοντας το οπτικό cue που αναμένουν οι αναγνώστες σας.

## Βήμα 4 – Πώς να Προσθέσετε Σκιά

Οι σκιές προσθέτουν βάθος και κάνουν το σχήμα να «εξέχει». Το Aspose.Words εκθέτει ένα αντικείμενο `ShadowFormat` όπου μπορείτε να ενεργοποιήσετε την ορατότητα, να επιλέξετε χρώμα και να ρυθμίσετε την θολότητα, την απόσταση και τη γωνία.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Γιατί αυτές οι συγκεκριμένες τιμές; Μια γωνία 45° δίνει μια φυσική πηγή φωτός από πάνω‑δεξιά, μια μέτρια θολότητα κρατά τη σκιά διακριτική, και μια μικρή απόσταση αποτρέπει το σχήμα να φαίνεται αποσπασμένο. Δοκιμάστε ελεύθερα — αλλάζοντας τη γωνία σε 135° η σκιά θα πέσει προς τα κάτω‑αριστερά, για παράδειγμα.

## Βήμα 5 – Αποθήκευση του Εγγράφου

Όλη η δουλειά ολοκληρώθηκε· τώρα γράφουμε το αρχείο στο δίσκο. Επιλέξτε οποιοδήποτε μονοπάτι θέλετε· απλώς βεβαιωθείτε ότι ο φάκελος υπάρχει.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Όταν ανοίξετε το `ShadowShape.docx` στο Microsoft Word, θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο με μια ήπια γκρι σκιά — ακριβώς όπως το προγραμματίσαμε.

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες, έτοιμο‑για‑αντιγραφή πρόγραμμα:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Ένα αρχείο με όνομα **ShadowShape.docx** εμφανίζεται στον προορισμό.
- Το άνοιγμα του στο Word δείχνει ένα ανοιχτό‑μπλε ορθογώνιο κεντραρισμένο στην πρώτη σελίδα.
- Το ορθογώνιο ρίχνει μια γκρι σκιά με γωνία 45°, δημιουργώντας ένα διακριτικό 3‑Δ εφέ.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν χρειαστώ διαφορετικό σχήμα;**  
Αντικαταστήστε το `ShapeType.Rectangle` με οποιαδήποτε άλλη τιμή του enum (`Ellipse`, `Star`, `Arrow`, κ.λπ.). Το υπόλοιπο του κώδικα παραμένει ίδιο.

**Μπορώ να προσθέσω κείμενο μέσα στο σχήμα;**  
Ναι — μετά τη δημιουργία του σχήματος, καλέστε `shape.AppendChild(new Paragraph(doc))` και στη συνέχεια εισάγετε ένα `Run` με το κείμενό σας. Θυμηθείτε να ορίσετε τις ιδιότητες `shape.TextBox` αν θέλετε περιτύλιξη.

**Τι γίνεται με DPI ή μονάδες μέτρησης;**  
Το Aspose εργάζεται σε points (1 pt = 1/72 ίντσες). Αν προτιμάτε εκατοστά, πολλαπλασιάστε με 28.35 (αφού 1 cm ≈ 28.35 pt).

**Χρειάζεται άδεια για να λειτουργήσει αυτό;**  
Η έκδοση αξιολόγησης προσθέτει υδατογράφημα στην πρώτη σελίδα. Μια έγκυρη άδεια το αφαιρεί και ξεκλειδώνει ολόκληρο το API.

## Συμβουλές & Προειδοποιήσεις

- **Pro tip:** Καλέστε `builder.MoveToDocumentEnd()` πριν εισάγετε ένα σχήμα αν θέλετε να βρίσκεται στο πολύ τέλος του εγγράφου.
- **Προσοχή:** Η αποθήκευση σε φάκελο μόνο για ανάγνωση θα προκαλέσει `UnauthorizedAccessException`. Βεβαιωθείτε ότι η εφαρμογή σας έχει δικαιώματα εγγραφής.
- **Σημείωση απόδοσης:** Για μαζική δημιουργία (εκατοντάδες έγγραφα), επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` ως πρότυπο και κλωνοποιήστε το με `doc.Clone(true)` για να αποφύγετε επαναλαμβανόμενο κόστος αρχικοποίησης.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε έγγραφο Word**, **εισάγετε σχήμα ορθογωνίου**, **ορίσετε γέμισμα** και **προσθέσετε σκιά** χρησιμοποιώντας το Aspose.Words for .NET. Το παραπάνω απόσπασμα είναι μια αυτόνομη λύση που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο C#, είτε πρόκειται για κονσόλα, web API ή υπηρεσία παρασκηνίου.

Από εδώ μπορείτε να εξερευνήσετε:

- Προσθήκη πολλαπλών σχημάτων με διαφορετικά χρώματα.
- Χρήση διαβαθμίσεων ή γεμίσματος με εικόνα (`shape.FillColor = ...` → `shape.FillPattern`).
- Συνδυασμός σχημάτων με πίνακες για σύνθετες διατάξεις αναφορών.

Δοκιμάστε το, τροποποιήστε τις παραμέτρους και παρακολουθήστε τα αυτοματοποιημένα αρχεία Word σας να γίνονται πιο επαγγελματικά με λίγες μόνο γραμμές κώδικα. Καλή προγραμματιστική!

## Σχετικά Tutorials

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}