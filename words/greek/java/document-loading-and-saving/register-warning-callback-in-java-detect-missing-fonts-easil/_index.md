---
category: general
date: 2026-07-03
description: Καταχωρίστε την κλήση επιστροφής προειδοποίησης σε Java για τον εντοπισμό
  ελλιπών γραμματοσειρών κατά την επεξεργασία εγγράφων Word. Μάθετε τη διαχείριση
  προειδοποιήσεων του Aspose.Words και τον εντοπισμό αντικατάστασης γραμματοσειρών.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: el
og_description: Καταχωρίστε την κλήση επιστροφής προειδοποίησης σε Java για να εντοπίσετε
  ελλιπείς γραμματοσειρές. Αυτός ο οδηγός δείχνει πώς να καταγράψετε προειδοποιήσεις
  αντικατάστασης γραμματοσειρών με το Aspose.Words.
og_title: Καταχώρηση callback προειδοποίησης σε Java – Εντοπισμός ελλιπών γραμματοσειρών
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Καταχώρηση callback προειδοποίησης σε Java – Εύκολη ανίχνευση ελλιπών γραμματοσειρών
url: /el/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταχώρηση callback προειδοποίησης σε Java – Εντοπισμός ελλιπών γραμματοσειρών εύκολα

Έχετε αναρωτηθεί ποτέ πώς να **καταχωρήσετε callback προειδοποίησης** ώστε να μπορείτε να **εντοπίσετε ελλιπείς γραμματοσειρές** κατά τη μετατροπή ή την επεξεργασία εγγράφων Word; Δεν είστε οι μόνοι. Οι ελλιπείς γραμματοσειρές μπορούν σιωπηρά να διαφθείρουν τις διατάξεις, να μετατρέψουν μια κομψή αναφορά σε ένα ακατάστατο χάος, και οι περισσότεροι προγραμματιστές δεν το συνειδητοποιούν μέχρι το τελικό PDF να φαίνεται λανθασμένο.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει ακριβώς πώς να συνδέσετε το σύστημα προειδοποιήσεων του Aspose.Words for Java, να πιάσετε αυτές τις ενοχλητικές ειδοποιήσεις αντικατάστασης γραμματοσειρών, και να τις καταγράψετε ή να αντιδράσετε όπως χρειάζεται. Χωρίς ασαφείς «δείτε τα docs» συντομεύσεις—απλώς καθαρός, αντι‑και‑επικόλλητος κώδικας και η λογική πίσω από κάθε γραμμή.

## Προαπαιτήσεις

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε:

* **Java 17** (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ορισμένο `JAVA_HOME`.  
* **Aspose.Words for Java** JAR (κατεβάστε από την επίσημη ιστοσελίδα ή προσθέστε μέσω Maven).  
* Ένα δείγμα `.docx` που αναφέρει μια γραμματοσειρά **που δεν** είναι εγκατεστημένη στο σύστημά σας—αυτό θα ενεργοποιήσει την προειδοποίηση.  
* Το αγαπημένο σας IDE ή ένας απλός επεξεργαστής κειμένου και εργαλεία κατασκευής γραμμής εντολών.

Αυτό είναι όλο. Χωρίς επιπλέον frameworks, χωρίς εξωτερικές υπηρεσίες. Έτοιμοι; Ας ξεκινήσουμε.

## Step 1: Set up the project and add Aspose.Words

Αν χρησιμοποιείτε Maven, προσθέστε την παρακάτω εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Για Gradle, τοποθετήστε αυτό στο `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Αν προτιμάτε τη χειροκίνητη προσέγγιση, απλώς τοποθετήστε το `aspose-words-24.10.jar` στο classpath σας.  
**Pro tip:** κρατήστε το JAR δίπλα στο φάκελο `src`; απλοποιεί την εντολή `javac` αργότερα.

## Step 2: Load the document that may contain missing fonts

Το πρώτο πράγμα που κάνετε είναι να δημιουργήσετε ένα αντικείμενο `Document` που δείχνει στο αρχείο προέλευσης. Αυτό το βήμα είναι απλό, αλλά είναι επίσης εκεί που η βιβλιοθήκη σαρώσει το αρχείο και *ενδεχομένως* ανακαλύψει ελλιπείς γραμματοσειρές.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Εδώ, το `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες του Aspose.Words. Όταν εκτελείται ο κατασκευαστής, η βιβλιοθήκη αναλύει το XML του εγγράφου, επιλύει τις γραμματοσειρές και, αν κάποια γραμματοσειρά δεν είναι διαθέσιμη, *προγραμματίζει* μια προειδοποίηση που μπορούμε να συλλάβουμε αργότερα.

## Step 3: Register a warning callback to capture font‑substitution alerts

Τώρα για το αστέρι της παράστασης: **καταχώρηση callback προειδοποίησης**. Το Aspose.Words σας επιτρέπει να συνδέσετε μια υλοποίηση του interface `IWarningCallback`. Κάθε φορά που η μηχανή συναντά μια κατάσταση που αξίζει σηματοδότησης—όπως μια ελλιπής γραμματοσειρά—καλεί τη μέθοδο `warning` που έχετε ορίσει.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Why this matters

* **Ορατότητα:** Χωρίς callback, η αντικατάσταση γίνεται σιωπηρά και μπορεί να παραδώσετε ένα έγγραφο με λανθασμένη εμφάνιση.  
* **Αυτοματοποίηση:** Σε δέσμες επεξεργασίας μπορείτε να καταγράψετε κάθε περιστατικό ελλιπής γραμματοσειράς και αργότερα να τροφοδοτήσετε τη λίστα σε ένα script εγκατάστασης γραμματοσειρών.  
* **Συμμόρφωση:** Ορισμένες βιομηχανίες (π.χ. νομική) απαιτούν απόδειξη ότι οι αρχικές γραμματοσειρές χρησιμοποιήθηκαν ή αντικαταστάθηκαν σωστά.

Παρατηρήστε ότι φιλτράρουμε με `WarningType.FONT_SUBSTITUTION`. Το Aspose.Words εκδίδει πολλούς τύπους προειδοποιήσεων—υπέρβαση διάταξης, παρωχημένες λειτουργίες κ.λπ.—αλλά μας ενδιαφέρουν μόνο εκείνες που μας λένε ότι μια γραμματοσειρά λείπει. Αυτό κρατά την κονσόλα καθαρή και εστιάζει στον στόχο **εντοπισμού ελλιπών γραμματοσειρών**.

## Step 4: Save the document and let the callback fire

Όταν τελικά καλέσετε `save`, η μηχανή ολοκληρώνει τυχόν lazy loading και ενεργοποιεί το callback προειδοποίησης για κάθε ελλιπής γραμματοσειρά που ανακάλυψε κατά τη διαδικασία αποθήκευσης.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Expected console output

Υποθέτοντας ότι το `input.docx` αναφέρει τη γραμματοσειρά *“Comic Sans MS”* που δεν είναι εγκατεστημένη, θα δείτε κάτι τέτοιο:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Αν το αρχικό έγγραφο περιέχει μόνο εγκατεστημένες γραμματοσειρές, η γραμμή προειδοποίησης απλώς δεν εμφανίζεται—σημαίνει ότι η **εντοπισμός ελλιπών γραμματοσειρών** ολοκληρώθηκε σιωπηρά.

![Έξοδος κονσόλας που δείχνει την καταχώρηση callback προειδοποίησης σε δράση και εντοπισμό ελλιπών γραμματοσειρών](register-warning-callback-output.png)

*Image alt text: register warning callback output showing detect missing fonts*

## Step 5: Handling edge cases and best‑practice tips

### Multiple missing fonts

Αν ένα έγγραφο αναφέρει πολλές μη διαθέσιμες γραμματοσειρές, το callback θα ενεργοποιηθεί μία φορά ανά γραμματοσειρά. Μπορείτε να συγκεντρώσετε τα μηνύματα σε μια λίστα αν χρειάζεστε μια συνοπτική αναφορά αργότερα.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Controlling substitution behavior

Μερικές φορές *θέλετε* να εξαναγκάσετε μια συγκεκριμένη εφεδρική γραμματοσειρά. Χρησιμοποιήστε το `FontSettings` πριν φορτώσετε το έγγραφο:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Τώρα το callback θα εξακολουθεί να ενεργοποιείται, αλλά ξέρετε ακριβώς ποια γραμματοσειρά θα χρησιμοποιηθεί.

### Performance considerations

Η καταχώρηση ενός callback προειδοποίησης προσθέτει μια μικρή επιβάρυνση—μόνο μερικά νανοδευτερόλεπτα ανά προειδοποίηση. Σε υπηρεσίες υψηλής απόδοσης (π.χ. μετατροπή χιλιάδων εγγράφων ανά ώρα) η επίδραση είναι αμελητέα. Ωστόσο, αν επεξεργάζεστε εκατομμύρια, σκεφτείτε να απενεργοποιήσετε τις προειδοποιήσεις μετά τον έλεγχο ότι το σύνολο γραμματοσειρών είναι πλήρες:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Cross‑platform notes

Το callback λειτουργεί ταυτόσημα σε Windows, macOS και Linux. Η μόνη διαφορά είναι το σύνολο των γραμματοσειρών που είναι διαθέσιμες σε κάθε λειτουργικό σύστημα. Αν εκτελείτε την ίδια εργασία σε πολλαπλούς πράκτορες, μπορεί να δείτε διαφορετικά μηνύματα αντικατάστασης. Για να διατηρήσετε τα αποτελέσματα προβλέψιμα, στείλτε έναν **προσαρμοσμένο φάκελο γραμματοσειρών** και κατευθύνετε το Aspose.Words σε αυτόν μέσω `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Full, runnable example

Παρακάτω βρίσκεται ολόκληρη η κλάση Java που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `src/main/java/FontWarningDemo.java`. Περιλαμβάνει όλες τις εισαγωγές, τη διαχείριση σφαλμάτων και τα σχόλια που χρειάζεστε για να το τρέξετε αμέσως.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Compile and run:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Θα πρέπει να δείτε τις γραμμές προειδοποίησης (αν υπάρχουν) ακολουθούμενες από το μήνυμα επιτυχίας.

## Conclusion

Μόλις μάθατε **πώς να καταχωρήσετε callback προειδοποίησης** σε Java για **εντοπισμό ελλιπών γραμματοσειρών** όταν εργάζεστε με το Aspose.Words. Συνδέοντας το σύστημα προειδοποιήσεων της βιβλιοθήκης, αποκτάτε πλήρη ορατότητα στα γεγονότα αντικατάστασης γραμματοσειρών, μπορείτε να τα καταγράψετε για συμμόρφωση, και ακόμη να αντικαταστήσετε προγραμματιστικά τις γραμματοσειρές αν χρειαστεί.

Από εδώ μπορείτε να εξερευνήσετε:

* **Εντοπισμός ελλιπών γραμματοσειρών** σε μια δέσμη αρχείων χρησιμοποιώντας βρόχο ή παράλληλες ροές.  
* Ενσωμάτωση του callback με ένα πλαίσιο καταγραφής (SLF4J, Log4j) για αναφορές παραγωγικού επιπέδου.  
* Χρήση του `FontSettings` για την επιβολή μιας εταιρικής παλέτας γραμματοσειρών και την αποφυγή ανεπιθύμητων εναλλακτικών.

Δοκιμάστε το—αλλάξτε το έγγραφο εισόδου, δοκιμάστε διαφορετικά σενάρια ελλιπών γραμματοσειρών, και δείτε πώς συμπεριφέρεται το callback. Αν συναντήσετε προβλήματα, αφήστε ένα σχόλιο παρακάτω· καλή προγραμματιστική διασκέδαση!

## What Should You Learn Next?

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειρών σε Java με Aspose.Words – Πλήρης Οδηγός](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback προειδοποίησης σε έγγραφο Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Προσαρμοσμένες Αποθηκεύσεις](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}