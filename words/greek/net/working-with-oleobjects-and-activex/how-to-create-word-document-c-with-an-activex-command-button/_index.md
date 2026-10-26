---
category: general
date: 2026-10-26
description: Μάθετε πώς να δημιουργήσετε έγγραφο Word με C# και να προσθέσετε προγραμματιστικά
  ένα κουμπί ActiveX. Αυτός ο οδηγός βήμα‑βήμα καλύπτει την εισαγωγή ενός κουμπιού
  εντολής, την απόκρυψή του κατά το σχεδιασμό και την αποθήκευση του αρχείου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: el
lastmod: 2026-10-26
og_description: Δημιουργήστε έγγραφο Word με C# και προσθέστε προγραμματιστικά ένα
  κουμπί ActiveX. Ακολουθήστε αυτό το πλήρες σεμινάριο για να ενσωματώσετε ένα κουμπί
  εντολής που εμφανίζεται μόνο κατά την εκτέλεση.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Δημιουργία εγγράφου Word με C# και κουμπί εντολής ActiveX – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Πώς να δημιουργήσετε έγγραφο Word με C# και κουμπί εντολής ActiveX
url: /el/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word C# με κουμπί εντολής ActiveX

Αν χρειάζεστε **create Word document C#** που περιέχει ένα διαδραστικό κουμπί, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Μέχρι το τέλος των πρώτων δύο προτάσεων θα γνωρίζετε τη γενική προσέγγιση, και τα επόμενα βήματα θα σας καθοδηγήσουν μέσα από κάθε γραμμή κώδικα που πρέπει να γράψετε.

Θα μάθετε πώς να προσθέσετε ένα κουμπί ActiveX, να το κρύψετε κατά το σχεδιασμό και να το κάνετε ορατό μόνο όταν ο χρήστης ανοίξει το αρχείο. Ο οδηγός καλύπτει επίσης κοινά προβλήματα όπως προειδοποιήσεις ασφαλείας και συμβατότητα εκδόσεων, ώστε να μπορείτε να διανείμετε αξιόπιστα έγγραφα.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
* Αδειοδοτημένο αντίγραφο του **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για πειραματισμό)  
* Βασική εξοικείωση με C# και Visual Studio (οποιοδήποτε IDE που υποστηρίζει .NET είναι αποδεκτό)  

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Βήμα 1: Δημιουργία εγγράφου Word C# και αρχικοποίηση του DocumentBuilder

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document` και ενός `DocumentBuilder`. Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει ρευστές μεθόδους για την προσθήκη περιεχομένου.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Γιατί είναι σημαντικό:** Χωρίς ένα `DocumentBuilder` θα έπρεπε να χειριστείτε το OpenXML DOM χειροκίνητα, κάτι που είναι επιρρεπές σε σφάλματα και πιο δύσκολο στην ανάγνωση. Ο builder αφαιρεί αυτές τις λεπτομέρειες και εγγυάται ένα σωστά δομημένο αρχείο Word.

## Βήμα 2: Πώς να προσθέσετε κουμπί ActiveX – εισαγωγή ελέγχου CommandButton

Τώρα εισάγουμε ένα **CommandButton ActiveX control** σε συγκεκριμένη θέση. Το ορθογώνιο καθορίζει τη θέση του κουμπιού (X, Y) και το μέγεθός του (πλάτος, ύψος) σε μονάδες point.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Γιατί είναι σημαντικό:** Η `InsertForms2OleControl` είναι η μοναδική μέθοδος του Aspose.Words που δημιουργεί ένα πραγματικό αντικείμενο ActiveX OLE. Η τιμή enum `Forms2OleControlType.CommandButton` λέει στο Word να ενσωματώσει ένα κλικ‑μενού κουμπί αντί για ένα γενικό κοντέινερ OLE.

## Βήμα 3: Προγραμματιστική προσθήκη κουμπιού εντολής – απόκρυψη μέχρι το χρόνο εκτέλεσης

Το Word θεωρεί οποιοδήποτε εισαχθέν σχήμα ως ορατό από προεπιλογή. Για να κρατήσετε το κουμπί αόρατο κατά το σχεδιασμό του προτύπου, ορίστε την ιδιότητα `Hidden` στο σχήμα που μόλις δημιούργησε ο builder.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Γιατί είναι σημαντικό:** Ορίζοντας `Hidden = true` αποτρέπει το κουμπί από το να γεμίζει την προβολή σχεδίασης. Όταν το έγγραφο ανοίξει στο Word, το περιβάλλον χρόνου εκτέλεσης αποκαλύπτει αυτόματα τον έλεγχο, διατηρώντας την προοριζόμενη εμπειρία χρήστη.

## Βήμα 4: Αποθήκευση αρχείου – δημιουργία εγγράφου Word με κουμπί εντολής

Τέλος, γράψτε το έγγραφο στον δίσκο. Επιλέξτε μια διαδρομή στην οποία η εφαρμογή σας μπορεί να γράψει και χρησιμοποιήστε την επέκταση `.docx` για να εξασφαλίσετε σύγχρονη συμβατότητα.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ως `.docx` εγγυάται ότι το ενσωματωμένο κουμπί ActiveX συμμορφώνεται με το πρότυπο Office Open XML, το οποίο υποστηρίζεται από το Word 2007 και μεταγενέστερες εκδόσεις. Αν χρειάζεστε υποστήριξη παλαιού `.doc`, αντικαταστήστε την επέκταση και χρησιμοποιήστε το `SaveFormat.Doc`.

## Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση του προγράμματος, ανοίξτε το `C:\Temp\ActiveX.docx` στο Microsoft Word. Θα δείτε ένα κενό έγγραφο· το κουμπί δεν είναι ορατό στη λειτουργία σχεδίασης. Πατήστε **Alt + F9** για εναλλαγή κωδίκων πεδίου, στη συνέχεια κάντε κλικ στην περιοχή του κουμπιού—το Word θα εμφανίσει τον έλεγχο ActiveX και μπορείτε να αλληλεπιδράσετε με αυτόν (π.χ., διπλό κλικ για προβολή των ιδιοτήτων).

## Περιπτώσεις άκρων και συμβουλές βέλτιστων πρακτικών

| Κατάσταση | Τι πρέπει να προσέξετε | Προτεινόμενη διόρθωση |
|-----------|------------------------|-----------------------|
| **Ο χρήστης απενεργοποιεί το ActiveX** | Το Word μπορεί να εμφανίσει προειδοποίηση ασφαλείας ή να αποκλείσει τον έλεγχο. | Καθοδηγήστε τους τελικούς χρήστες να ενεργοποιήσουν τα “ActiveX controls” στο Trust Center, ή παρέχετε μια εναλλακτική υπογεγραμμένη μακροεντολή. |
| **Το έγγραφο ανοίγει στο Word Online** | Το Word Online δεν υποστηρίζει ActiveX· το κουμπί θα παραλειφθεί. | Χρησιμοποιήστε εναλλακτικό υπερσύνδεσμο ή έναν έλεγχο περιεχομένου εάν χρειάζεστε συμβατότητα με το cloud. |
| **Διαφορετικές ρυθμίσεις DPI** | Το μέγεθος του ορθογωνίου μπορεί να εμφανίζεται μεγαλύτερο ή μικρότερο σε οθόνες υψηλού DPI. | Χρησιμοποιήστε `GraphicsUnit.Point` (η προεπιλογή) και δοκιμάστε σε κοινές ρυθμίσεις DPI (96 dpi, 120 dpi). |
| **Πολλά κουμπιά** | Η κλήση `GetChildNodes(NodeType.Shape, true)[0]` επιστρέφει μόνο το πρώτο σχήμα. | Κάντε βρόχο μέσω `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` και ορίστε `Hidden` για κάθε σχήμα που προσθέτετε. |
| **Παλαιό μορφότυπο .doc** | Κάποιες ιδιότητες του ActiveX χάνονται όταν αποθηκεύεται ως `.doc`. | Προτιμήστε `.docx` εκτός εάν έχετε αυστηρή απαίτηση για παλαιό μορφότυπο. |

**Συμβουλή:** Μετά την εισαγωγή του κουμπιού, μπορείτε να εκχωρήσετε μια μακροεντολή στην ιδιότητα `OnAction` μέσω του UI του Word. Αυτό σας επιτρέπει να ορίσετε προσαρμοσμένη συμπεριφορά κλικ χωρίς να γράψετε επιπλέον κώδικα C#.

## Συχνές ερωτήσεις

* **Λειτουργεί αυτό με .NET Core;**  
  Ναι. Το Aspose.Words for .NET είναι πλήρως συμβατό με .NET 5, .NET 6 και μεταγενέστερες εκδόσεις. Απλώς αναφέρετε το ίδιο πακέτο NuGet.

* **Μπορώ να αλλάξω τη λεζάντα του κουμπιού μετά τη δημιουργία του εγγράφου;**  
  Η λεζάντα που ορίζεται στο `InsertForms2OleControl` γίνεται το προεπιλεγμένο κείμενο κατά το σχεδιασμό. Οι χρήστες μπορούν να την επεξεργαστούν στο Word, αλλά μπορείτε επίσης να ενημερώσετε τη λεζάντα προγραμματιστικά προσπερνώντας τις ιδιότητες του αντικειμένου OLE μέσω του API `Shape.OleFormat`.

* **Τι κάνω αν χρειάζομαι διαφορετικό μέγεθος για το κουμπί;**  
  Ρυθμίστε τις τιμές του `RectangleF`. Οι δύο πρώτες παράμετροι είναι οι συντεταγμένες X και Y· οι δύο τελευταίες είναι το πλάτος και το ύψος σε μονάδες point (1 pt = 1/72 ίντσα).

## Συμπέρασμα

Τώρα ξέρετε πώς να **create Word document C#** και **προγραμματιστικά να προσθέσετε κουμπί εντολής** χρησιμοποιώντας το Aspose.Words. Ο οδηγός κάλυψε την αρχικοποίηση του εγγράφου, την εισαγωγή κουμπιού ActiveX, την απόκρυψή του μέχρι το χρόνο εκτέλεσης και την αποθήκευση του τελικού αρχείου. Με αυτά τα δομικά στοιχεία μπορείτε να ενσωματώσετε διαδραστικούς ελέγχους σε οποιοδήποτε πρότυπο Word δημιουργείτε.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως η **how to add ActiveX button** διαχείριση συμβάντων, η **create command button word** μορφοποίηση με VBA, και η **programmatically add command button** σε υπάρχοντα έγγραφα. Η επέκταση αυτού του μοτίβου σε πλαίσια ελέγχου, λίστες επιλογών ή προσαρμοσμένα αντικείμενα OLE ακολουθεί τα ίδια βήματα—απλώς αλλάξτε την τιμή enum `Forms2OleControlType`.

Ξεκινήστε πειραματισμό: αντικαταστήστε τη λεζάντα, προσαρμόστε τη θέση ή συνδέστε πολλαπλούς ελέγχους μαζί. Όσο περισσότερο εξασκείστε, τόσο πιο άνετα θα γίνετε στην παροχή πλούσιων, διαδραστικών εγγράφων Word από C#. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες λειτουργίες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να προσθέσετε προγραμματιστικά ένα κουμπί εντολής σε έγγραφο Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Πώς να προσθέσετε κουμπί ActiveX σε έγγραφο Word με το Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Δημιουργία εγγράφου Word με κουμπί ActiveX – Οδηγός C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}