---
category: general
date: 2026-02-10
description: Πώς να διαχειριστείτε τις γραμματοσειρές σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε τις προειδοποιήσεις υποκατάστασης γραμματοσειρών, τις κλήσεις επιστροφής
  LoadOptions και τη διαχείριση ελλιπών γραμματοσειρών σε λίγα βήματα.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: el
og_description: Πώς να διαχειριστείτε τις γραμματοσειρές σε Java με το Aspose.Words.
  Αυτός ο οδηγός σας δείχνει βήμα‑βήμα τη διαχείριση αντικατάστασης γραμματοσειρών,
  τις κλήσεις επιστροφής προειδοποιήσεων και τη διαχείριση ελλιπών γραμματοσειρών.
og_title: Πώς να διαχειριστείτε τις γραμματοσειρές στη Java – Πλήρης οδηγός Aspose.Words
tags:
- Java
- Aspose.Words
- Document Processing
title: Πώς να διαχειριστείτε τις γραμματοσειρές σε Java με το Aspose.Words – Πλήρης
  Οδηγός
url: /el/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

αρχεία· κάθε μορφή μπορεί να προκαλέσει διαφορετικούς τύπους προειδοποιήσεων."

Next "## Conclusion" translate.

Paragraphs.

Finally "Ready for the next challenge? ..." translate.

Then shortcodes closing.

Make sure to keep all shortcodes unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Διαχειριστείτε τις Γραμματοσειρές σε Java – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να διαχειριστείτε τις γραμματοσειρές** όταν ένα έγγραφο Word αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή σας; Είναι ένα σενάριο που παρενοχλεί πολλούς προγραμματιστές, ειδικά όταν αυτοματοποιείτε τη δημιουργία ή τη μετατροπή εγγράφων με Aspose.Words. Τα καλά νέα; Μπορείτε να εντοπίσετε κάθε συμβάν αντικατάστασης γραμματοσειράς και να αντιδράσετε σε αυτό—χωρίς εικασίες.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που δείχνει **πώς να διαχειριστείτε τις γραμματοσειρές** χρησιμοποιώντας Aspose.Words for Java. Θα συνδέσουμε ένα warning callback, θα φιλτράρουμε μόνο τις προειδοποιήσεις αντικατάστασης γραμματοσειράς και θα εκτυπώσουμε ένα φιλικό μήνυμα για κάθε λείπουσα γραμματοσειρά. Στο τέλος θα καταλάβετε γιατί είναι σημαντικό, πώς να το υλοποιήσετε καθαρά και τι να περιμένετε όταν τρέξει ο κώδικας.

> **Τι θα πάρετε:** μια πλήρη, έτοιμη προς εκτέλεση κλάση Java, εξήγηση κάθε γραμμής, συμβουλές για παραγωγική χρήση και έναν γρήγορο τρόπο επαλήθευσης του αποτελέσματος.

---

## Προαπαιτούμενα

Πριν προχωρήσουμε, βεβαιωθείτε ότι έχετε:

- **Java 8** (ή νεότερη) εγκατεστημένη στο μηχάνημά σας.  
- **Aspose.Words for Java** JAR (η πιο πρόσφατη έκδοση μέχρι 2026‑02, π.χ., `aspose-words-23.11.jar`).  
- Ένα δείγμα εγγράφου (`MissingFont.docx`) που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη.  
- Ένα περιβάλλον ανάπτυξης (IntelliJ IDEA, Eclipse ή ακόμη και έναν απλό επεξεργαστή κειμένου + γραμμή εντολών).

Δεν απαιτούνται πρόσθετα frameworks—απλώς καθαρή Java και το Aspose.Words JAR.

![Διάγραμμα που δείχνει πώς να διαχειριστείτε τις γραμματοσειρές σε Java με Aspose.Words](https://example.com/handle-fonts-diagram.png "διάγραμμα πώς να διαχειριστείτε τις γραμματοσειρές")

*Κείμενο alt εικόνας: διάγραμμα πώς να διαχειριστείτε τις γραμματοσειρές*

---

## Βήμα 1 – Ρύθμιση Callback Προειδοποίησης (ο πυρήνας του **πώς να διαχειριστείτε τις γραμματοσειρές**)

Όταν το Aspose.Words φορτώνει ένα έγγραφο, δημιουργεί μια σειρά από αντικείμενα `WarningInfo` για οτιδήποτε δεν είναι τέλειο. Συνδέοντας ένα `IWarningCallback`, μπορείτε να παρεμβείτε σε αυτές τις προειδοποιήσεις σε πραγματικό χρόνο.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Γιατί είναι σημαντικό:**  
Αν παραλείψετε το callback, το Aspose.Words αντικαθιστά σιωπηλά τις λείπουσες γραμματοσειρές με μια προεπιλεγμένη, και δεν ξέρετε ποτέ ποιες γραμματοσειρές λείπουν. Με τη διαχείριση της προειδοποίησης αποκτάτε διαφάνεια και μπορείτε να αποφασίσετε αν θα ενσωματώσετε μια εναλλακτική γραμματοσειρά, θα καταγράψετε το ζήτημα ή ακόμη και θα ακυρώσετε τη λειτουργία.

---

## Βήμα 2 – Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Ρυθμισμένες `LoadOptions`

Τώρα που το callback είναι έτοιμο, απλώς φορτώνουμε το έγγραφο. Η παρουσίαση `LoadOptions` που δημιουργήσαμε παραπάνω περνιέται απευθείας στον κατασκευαστή `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**Τι να περιμένετε:**  
Όταν το `MissingFont.docx` αναφέρει, για παράδειγμα, *Comic Sans MS* αλλά ο διακομιστής έχει μόνο *Arial*, το callback εκτυπώνει κάτι σαν:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Αν το έγγραφο φορτωθεί χωρίς λείπουσες γραμματοσειρές, δεν εκτυπώνεται τίποτα—ακριβώς αυτό που θέλετε όταν **πώς να διαχειριστείτε τις γραμματοσειρές** με χάρη.

---

## Βήμα 3 – (Προαιρετικό) Επαλήθευση του Πίνακα Γραμματοσειρών του Εγγράφου

Μερικές φορές χρειάζεται να ελέγξετε ποιες γραμματοσειρές χρησιμοποιεί πραγματικά το έγγραφο μετά τη φόρτωση. Το Aspose.Words το κάνει εύκολα.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Πότε να το χρησιμοποιήσετε:**  
Αν δημιουργείτε έναν επεξεργαστή παρτίδας που πρέπει να αναφέρει λείπουσες γραμματοσειρές πριν τη δημοσίευση ενός PDF, η εκτύπωση του πίνακα γραμματοσειρών σας δίνει έναν τελικό έλεγχο λογικής.

---

## Πλήρες, Εκτελέσιμο Παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι η πλήρης κλάση που μπορείτε να αντιγράψετε‑επικολλήσετε στο `FontSubstitutionDemo.java` και να τρέξετε:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Εκτέλεση του κώδικα:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Θα πρέπει να δείτε τα μηνύματα αντικατάστασης ακολουθούμενα από τον τελικό κατάλογο γραμματοσειρών.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι κάνω αν θέλω να αντικαταστήσω τη γραμματοσειρά μόνος μου;

Το callback προειδοποίησης μόνο σας λέει *τι* αντικαταστάθηκε. Αν θέλετε να επιβάλετε μια συγκεκριμένη εναλλακτική, μπορείτε να χρησιμοποιήσετε `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Τώρα κάθε εμφάνιση του “MissingFont” θα αντικατασταθεί με “Arial” πριν φορτωθεί το έγγραφο.

### Λειτουργεί αυτό όταν αποθηκεύεται σε PDF;

Απολύτως. Το ίδιο callback ενεργοποιείται κατά το `document.save("out.pdf")` αν ο PDF renderer χρειάζεται επίσης αντικατάσταση γραμματοσειρών. Απλώς διατηρήστε τις ίδιες `LoadOptions` ή συνδέστε ένα νέο callback στα `PdfSaveOptions`.

### Πώς συμπεριφέρεται σε πολυνηματικό περιβάλλον;

Το `LoadOptions` **δεν** είναι thread‑safe, οπότε δημιουργήστε μια νέα παρουσία ανά νήμα. Το ίδιο το callback μπορεί να είναι χωρίς κατάσταση (όπως φαίνεται) ή μπορείτε να ενσωματώσετε έναν logger που είναι aware των νημάτων.

### Τι γίνεται αν η λείπουσα γραμματοσειρά είναι μια προσαρμοσμένη εταιρική γραμματοσειρά;

Συνήθως ενσωματώνετε αυτή τη γραμματοσειρά στον φάκελο γραμματοσειρών του διακομιστή και δείχνετε στο Aspose.Words μέσω `FontSettings.setFontsFolder("path/to/fonts", true)`. Το callback τότε θα σταματήσει να πυροδοτείται για αυτή τη γραμματοσειρά επειδή δεν λείπει πλέον.

---

## Pro Tips για Παραγωγική Διαχείριση Γραμματοσειρών

- **Καταγράψτε, μην χρησιμοποιείτε μόνο `System.out.println`** – χρησιμοποιήστε ένα κατάλληλο πλαίσιο καταγραφής (SLF4J, Log4j) ώστε να μπορείτε να συλλαμβάνετε προειδοποιήσεις στο σύστημα παρακολούθησής σας.  
- **Κάντε cache τις αναζητήσεις γραμματοσειρών** – αν επεξεργάζεστε χιλιάδες έγγραφα, αποφύγετε το επαναλαμβανόμενο σάρωση του φακέλου γραμματοσειρών του λειτουργικού συστήματος. Φορτώστε τις γραμματοσειρές μία φορά σε ένα αντικείμενο `FontSettings` και επαναχρησιμοποιήστε το.  
- **Αποτύχετε γρήγορα όταν λείπουν κρίσιμες γραμματοσειρές** – μπορείτε να ρίξετε εξαίρεση μέσα στο callback αν μια συγκεκριμένη γραμματοσειρά είναι υποχρεωτική για τη συμμόρφωση με την επωνυμία.  
- **Δοκιμάστε με ποικιλία εγγράφων** – συμπεριλάβετε PDF, DOCX και DOC αρχεία· κάθε μορφή μπορεί να προκαλέσει διαφορετικούς τύπους προειδοποιήσεων.  

---

## Συμπέρασμα

Καλύψαμε **πώς να διαχειριστείτε τις γραμματοσειρές** σε Java χρησιμοποιώντας Aspose.Words από την αρχή μέχρι το τέλος:

1. Συνδέστε ένα `IWarningCallback` για να εντοπίζετε προειδοποιήσεις αντικατάστασης γραμματοσειράς.  
2. Φορτώστε το έγγραφο με `LoadOptions` ώστε το callback να εκτελείται αυτόματα.  
3. (Προαιρετικά) Εξετάστε τον τελικό κατάλογο γραμματοσειρών για να επιβεβαιώσετε το αποτέλεσμα.  

Ακολουθώντας αυτά τα βήματα αποκτάτε πλήρη ορατότητα στις λείπουσες γραμματοσειρές, μπορείτε να επιβάλετε εταιρικές πολιτικές γραμματοσειρών και να αποφύγετε σιωπηλές εναλλακτικές που θα μπορούσαν να χαλάσουν την εμφάνιση των παραγόμενων PDF ή Word αρχείων.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αλλάξετε το callback ώστε να καταγράφει *όλες* τις προειδοποιήσεις, πειραματιστείτε με `FontSettings` για προσαρμοσμένους κανόνες αντικατάστασης ή ενσωματώστε αυτή τη λογική σε μια μικροϋπηρεσία Spring‑Boot που επεξεργάζεται έγγραφα σε πραγματικό χρόνο.

Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας να εμφανίζονται πάντα με τη σωστή γραμματοσειρά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}