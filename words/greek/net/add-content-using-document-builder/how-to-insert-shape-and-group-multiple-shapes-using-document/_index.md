---
category: general
date: 2026-11-15
description: Μάθετε πώς να εισάγετε σχήμα σε ένα έγγραφο Word και να ομαδοποιήσετε
  πολλαπλά σχήματα με το Aspose.Words DocumentBuilder. Περιλαμβάνει παραδείγματα εισαγωγής
  σχήματος ορθογωνίου και εισαγωγής πολλαπλών σχημάτων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: el
lastmod: 2026-11-15
og_description: Πώς να εισάγετε σχήμα σε αρχείο Word χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός καλύπτει την ομαδοποίηση πολλαπλών σχημάτων, την εισαγωγή σχήματος
  ορθογωνίου και την προσθήκη πολλαπλών σχημάτων αποδοτικά.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Πώς να εισαγάγετε σχήμα και να ομαδοποιήσετε πολλαπλά σχήματα με το DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Πώς να εισάγετε σχήμα και να ομαδοποιήσετε πολλαπλά σχήματα χρησιμοποιώντας
  το DocumentBuilder σε C#
url: /el/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισάγετε σχήμα και να ομαδοποιήσετε πολλαπλά σχήματα χρησιμοποιώντας το DocumentBuilder σε C#

Αν χρειάζεστε να μάθετε **πώς να εισάγετε σχήμα** σε ένα έγγραφο Word με το Aspose.Words, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε επίσης πώς να **ομαδοποιήσετε πολλαπλά σχήματα** ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο, και πώς να **εισάγετε σχήμα ορθογωνίου** μαζί με άλλα γραφικά.

Η αυτοματοποίηση εγγράφων συχνά απαιτεί την προσθήκη πολλαπλών γραφικών—διαγραμμάτων, λογοτύπων, σημειώσεων—διατηρώντας τα οργανωμένα. Στο τέλος αυτού του tutorial θα μπορείτε να **εισάγετε πολλαπλά σχήματα**, να τα τοποθετήσετε μέσα σε μια ομάδα και να αποθηκεύσετε μια καθαρή, επαναχρησιμοποιήσιμη διάταξη.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)  
* Άδεια Aspose.Words για .NET ή δωρεάν κλειδί αξιολόγησης  
* Βασική εξοικείωση με τη γλώσσα C# και την κλάση Aspose.Words `DocumentBuilder`  

Δεν χρειάζεστε **καμία** άλλη βιβλιοθήκη τρίτου μέρους· όλα όσα απαιτούνται περιλαμβάνονται στο Aspose.Words.

## Βήμα 1: Εγκατάσταση Aspose.Words μέσω NuGet

Ανοίξτε το έργο σας στο Visual Studio και εκτελέστε την παρακάτω εντολή στην Κονσόλα Διαχειριστή Πακέτων:

```powershell
Install-Package Aspose.Words
```

Το πακέτο περιλαμβάνει τις κλάσεις `DocumentBuilder`, `Shape` και `GroupShape` που χρησιμοποιούνται σε όλο αυτό το tutorial.

## Βήμα 2: Δημιουργία ενός αντικειμένου DocumentBuilder – η βάση για **πώς να εισάγετε σχήμα**

Η πρώτη ενεργή γραμμή κώδικα είναι η δημιουργία ενός `DocumentBuilder`. Αυτό το αντικείμενο σας δίνει άμεση πρόσβαση στο δέντρο του εγγράφου, επιτρέποντάς σας να τοποθετείτε σχήματα ακριβώς όπου τα θέλετε.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Γιατί είναι σημαντικό*: Το `DocumentBuilder` διατηρεί έναν κέρσορα (το “σημείο εισαγωγής”). Κάθε επόμενη κλήση `Insert...` χρησιμοποιεί αυτόν τον κέρσορα, γι' αυτό αργότερα τον μεταφέρουμε σε ένα `GroupShape` για να κρατήσουμε όλα τα σχήματα μαζί.

## Βήμα 3: **Εισαγωγή σχήματος ορθογωνίου** – το πρώτο γραφικό που θα προσθέσετε

Ένα ορθογώνιο είναι ένα κοινό placeholder για πίνακες, εικόνες ή σημειώσεις. Χρησιμοποιήστε `InsertShape` με `ShapeType.Rectangle` και καθορίστε το πλάτος και το ύψος σε σημεία (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Το ορθογώνιο εμφανίζεται στη τρέχουσα θέση του κέρσορα. Μπορείτε να προσαρμόσετε το γέμισμα, το στυλ γραμμής ή το κείμενο αργότερα, εάν χρειαστεί.

## Βήμα 4: Εισαγωγή άλλου σχήματος – μια έλλειψη για οπτική ποικιλία

Η προσθήκη περισσοτέρων από ένα σχήματος δείχνει **εισαγωγή πολλαπλών σχημάτων**. Η έλλειψη θα τοποθετηθεί μετά το ορθογώνιο στη ροή του εγγράφου.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Σε αυτό το σημείο το έγγραφο περιέχει δύο ανεξάρτητα σχήματα. Αν μετακινήσετε τον κέρσορα ή προσθέσετε κείμενο, τα σχήματα παραμένουν εκεί που εισήχθησαν.

## Βήμα 5: **Ομαδοποίηση πολλαπλών σχημάτων** ώστε να λειτουργούν ως μία ενότητα

Η ομαδοποίηση είναι απαραίτητη όταν χρειάζεται να μετακινήσετε, περιστρέψετε ή μορφοποιήσετε πολλά γραφικά μαζί. Ο παρακάτω κώδικας δημιουργεί ένα `GroupShape`, μετακινεί τον κέρσορα του builder μέσα σε αυτό, και στη συνέχεια εισάγει ξανά τα ίδια σχήματα—αυτή τη φορά γίνονται παιδιά της ομάδας.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Γιατί να χρησιμοποιήσετε μια ομάδα;

* **Μετασχηματισμός από ένα σημείο** – περιστρέψτε ή αλλάξτε το μέγεθος ολόκληρης της ομάδας με μία κλήση.  
* **Λογική οργάνωση** – το δέντρο του εγγράφου Word αντικατοπτρίζει την ομαδοποίηση, καθιστώντας τις μετέπειτα επεξεργασίες πιο εύκολες.  
* **Συνεπής διάταξη** – η μετακίνηση της ομάδας διατηρεί τις σχετικές θέσεις των παιδιών της αμετάβλητες.  

### Προσθήκη περισσότερων σχημάτων – επέκταση του **insert multiple shapes** μέσα στην ομάδα

Μπορείτε να συνεχίσετε να καλείτε το `InsertShape` ενώ ο κέρσορας παραμένει μέσα στο `GroupShape`. Για παράδειγμα, για να προσθέσετε ένα τρίγωνο:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Κάθε κλήση σέβεται το πλαίσιο της ομάδας, έτσι το τρίγωνο γίνεται αυτόματα μέρος του ίδιου ομαδοποιημένου συνόλου.

## Βήμα 6: Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Αφού τοποθετηθούν όλα τα σχήματα, αποθηκεύστε το έγγραφο σε αρχείο `.docx`. Το άνοιγμα του αρχείου στο Microsoft Word (ή σε οποιονδήποτε συμβατό προβολέα) θα πρέπει να εμφανίζει δύο ξεχωριστά σχήματα, ακολουθούμενα από ένα ομαδοποιημένο σύνολο που περιέχει το ίδιο ορθογώνιο, την έλλειψη και το τρίγωνο.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Αναμενόμενο αποτέλεσμα

* **Τα πρώτα δύο σχήματα** – ένα ορθογώνιο και μια έλλειψη τοποθετημένα ανεξάρτητα στη σελίδα.  
* **Ομαδοποιημένο μπλοκ** – ένα ορθογώνιο, μια έλλειψη και ένα τρίγωνο που μετακινούνται μαζί όταν κάνετε κλικ σε οποιοδήποτε από αυτά στο Word.  

Μπορείτε να δοκιμάσετε την ομαδοποίηση επιλέγοντας οποιοδήποτε σχήμα μέσα στην ομάδα· το Word θα επισημάνει ολόκληρη τη συλλογή, επιβεβαιώνοντας ότι η λειτουργία **group multiple shapes** πέτυχε.

## Συνηθισμένα προβλήματα και επαγγελματικές συμβουλές

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|-----------------|----------|
| Σχήματα εμφανίζονται εκτός της προοριζόμενης σελίδας | Ο κέρσορας του builder δεν μετακινήθηκε στο `GroupShape` πριν από την εισαγωγή. | Καλείτε πάντα `builder.MoveTo(group)` **πριν** οποιεσδήποτε κλήσεις `InsertShape` που ανήκουν στην ομάδα. |
| Η ομάδα εξαφανίζεται μετά την αποθήκευση | Η ομάδα εισήχθη χωρίς να προστεθεί στη συλλογή κόμβων του εγγράφου. | Χρησιμοποιήστε `builder.InsertNode(group)` αμέσως μετά τη δημιουργία του `GroupShape`. |
| Απρόσμενο μέγεθος λόγω DPI του εγγράφου | Το Aspose.Words χρησιμοποιεί σημεία· αν σκέφτεστε σε pixel μπορεί να προκύψουν ασυμφωνίες διαστάσεων. | Μετατρέψτε τα pixel σε σημεία (`points = pixels * 72 / 96`) ή εργαστείτε απευθείας σε σημεία. |
| Τα σχήματα επικαλύπτονται ακούσια | Δεν ορίστηκε ρητή θέση· το Word τα τοποθετεί διαδοχικά. | Ορίστε `Shape.Left` και `Shape.Top` μετά την εισαγωγή για ακριβή τοποθέτηση. |

**Συμβουλή επαγγελματία:** Μετά την ομαδοποίηση, μπορείτε να ανακτήσετε τη συλλογή `Shapes` της ομάδας (`group.Shapes`) για να την επαναλάβετε, να μετονομάσετε ή να εφαρμόσετε μαζική μορφοποίηση.

## Βήμα 7: Επέκταση του παραδείγματος – τι ακολουθεί;

Τώρα που γνωρίζετε **πώς να εισάγετε σχήμα**, **εισάγετε σχήμα ορθογωνίου**, και **ομαδοποιήσετε πολλαπλά σχήματα**, μπορείτε να εξερευνήσετε:

* **Κινούμενα ομαδοποιημένα σχήματα** – ορίστε ιδιότητες περιστροφής ή αναστροφής στην ομάδα.  
* **Εφαρμογή στυλ** – χρησιμοποιήστε `Shape.FillColor`, `Shape.LineFormat` ή `Shape.TextBox` για να προσθέσετε ετικέτες.  
* **Εξαγωγή σε PDF** – η ίδια ομαδοποιημένη διάταξη αποδίδει σωστά όταν καλέσετε `doc.Save("output.pdf")`.  

Όλες αυτές οι επεκτάσεις χρησιμοποιούν την ίδια ροή εργασίας `DocumentBuilder`, διατηρώντας τον κώδικά σας καθαρό και εύκολα συντηρήσιμο.

## Συμπέρασμα

Αυτό το tutorial έδειξε **πώς να εισάγετε σχήμα** σε ένα έγγραφο Word με το Aspose.Words, πώς να **εισάγετε σχήμα ορθογωνίου**, και πώς να **ομαδοποιήσετε πολλαπλά σχήματα** ώστε να λειτουργούν ως ένα ενιαίο αντικείμενο. Ακολουθώντας τον κώδικα βήμα‑βήμα, μπορείτε αξιόπιστα **να εισάγετε πολλαπλά σχήματα**, να τα οργανώσετε σε ομάδες και να δημιουργήσετε επαγγελματικής ποιότητας έγγραφα προγραμματιστικά.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους σχημάτων, χρώματα και μετασχηματισμούς ομάδας. Όταν είστε έτοιμοι, ενσωματώστε το πρότυπο σε μεγαλύτερες λύσεις αναφοράς ή δημιουργίας προτύπων για να αυτοματοποιήσετε σύνθετες διατάξεις εγγράφων. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική Περίοδο;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Σχημάτων σε Έγγραφα Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Πώς να δημιουργήσετε και να εισάγετε σχήματα έλλειψης και ορθογωνίου μέσα σε ένα group shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Πώς να ομαδοποιήσετε σχήματα σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}