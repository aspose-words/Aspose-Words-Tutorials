---
category: general
date: 2026-07-16
description: cmake build x64 öğreticisi, CMake'i kullanarak Visual Studio 2022 çözümü
  oluşturmayı ve 64‑bit bir ana bilgisayarda bir VS projesi derlemeyi gösterir. Kaynak
  dizini ayarlama adımlarını içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: tr
lastmod: 2026-07-16
og_description: 'cmake build x64 açıklaması: kaynak dizinini nasıl ayarlayacağınızı,
  Visual Studio 2022 çözümünü nasıl oluşturacağınızı ve 64‑bit bir ana bilgisayarda
  VS projesini nasıl derleyeceğinizi öğrenin.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – VS 2022 Çözümlerini Oluşturma ve Derleme İçin Adım Adım
  Rehber
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – VS 2022 Projelerini Oluşturma ve Derleme Tam Rehberi
url: /tr/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – VS 2022 Projeleri Oluşturma ve Derleme Tam Kılavuzu

Hiç **CMake'i nasıl kullanacağınızı** 64‑bit bir Visual Studio çözümü üretirken saçlarınızı çekmek zorunda kalmadan merak ettiniz mi? Yalnız değilsiniz. Bu öğreticide **cmake build x64** iş akışını adım adım inceleyeceğiz; kaynak dizinini ayarlayacak, Visual Studio 2022 için jeneratörü çalıştıracak ve sonunda VS projesini derleyecek—hepsi birkaç temiz Bash komutuyla.

Kılavuzun sonunda, herhangi bir depoya ekleyebileceğiniz tekrarlanabilir bir betiğe sahip olacaksınız ve temel kavramları sağlam bir şekilde kavrayarak ihtiyacınıza göre özelleştirebileceksiniz.

---

## Öğrenecekleriniz

- **Set source directory**'ı doğru şekilde ayarlayın, böylece CMake `CMakeLists.txt` dosyanızın nerede olduğunu bilir.  
- **cmake generate visual studio** – doğru host ve mimari bayraklarıyla Visual Studio 2022 jeneratörünü çalıştırın.  
- Oluşturulan çözüm üzerinde **cmake build x64** işlemini gerçekleştirin, isteğe bağlı olarak Release yapılandırmasını seçin.  
- **build vs project** yaparken 64‑bit bir makinede karşılaşabileceğiniz yaygın tuzakları anlayın.  

Önceden CMake sihirbazlığına gerek yok; sadece bir terminal ve güncel bir Visual Studio kurulumuna ihtiyacınız var.

## Önkoşullar

| Gereksinim | Neden Önemli |
|-------------|----------------|
| CMake ≥ 3.20 | 64‑bit derlemeler için kullanılan `-Thost=` ve `-Ax64` bayraklarını destekler. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | Jeneratör `Visual Studio 17 2022` bu sürüme işaret eder. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | Aşağıdaki betik açıklık için Bash sözdizimini kullanır. |
| Source tree containing a valid `CMakeLists.txt` | CMake, bir çözüm oluşturmak için buna ihtiyaç duyar. |

Eğer bunlardan herhangi biri eksikse, önce yükleyin—CMake'i <https://cmake.org/download/> adresinden ve VS 2022'yi Microsoft kurulum programından.

## Adım 1 – Kaynak ve Derleme Dizinlerini Ayarlama (`set source directory`)

CMake'i çağırmadan önce ona proje dosyalarını **nerede** arayacağını söylemeniz gerekir. Yolları sabit kodlamak betiği kırılgan hâle getirir, bu yüzden proje bazında ayarlayabileceğiniz ortam değişkenlerini kullanacağız.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Neden önemli:**  
> CMake, *source directory* (`SRC_DIR`) dizinini projenin kökü olarak kabul eder. *build directory* (`BUILD_DIR`) ise tüm ara dosyaların, önbelleklerin ve son `.sln` dosyasının bulunduğu yerdir. Bunları ayrı tutmak kaynak ağacınızı kirletmekten kaçınır ve temizliği (`rm -rf "$BUILD_DIR"`) basit hâle getirir.

`YOUR_DIRECTORY` ifadesini herhangi bir mutlak ya da göreli yol ile değiştirebilirsiniz; sadece klasörün bir `CMakeLists.txt` içerdiğinden emin olun.

## Adım 2 – Visual Studio 2022 Çözümü Oluşturma (`cmake generate visual studio`)

Şimdi CMake'den **x64** hedefleyen bir VS 2022 çözümü üretmesini istiyoruz. Önemli bayraklar şunlardır:

- `-G "Visual Studio 17 2022"` – VS 2022 jeneratörünü seçer.  
- `-Thost=x64` – CMake'e *host* (IDE) işleminin 64‑bit olarak çalıştığını söyler.  
- `-Ax64` – oluşturulan projenin x64 mimarisi için derlenmesini zorlar.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Arka planda ne olur?**  
> CMake, `$SRC_DIR` içindeki `CMakeLists.txt` dosyasını okur, tüm `add_executable()` ve `add_library()` çağrılarını çözer, ardından `$BUILD_DIR` içinde bir `.sln` dosyası ve bir dizi `.vcxproj` dosyası oluşturur. Bu proje dosyaları artık Visual Studio'da açılmaya ya da komut satırından derlenmeye hazırdır.

Komutu çalıştırıp `-- Configuring done` ve `-- Generating done` ile biten uzun bir yapılandırma mesajı listesi görürseniz, **cmake generate visual studio** adımını başarıyla tamamlamışsınız demektir.

## Adım 3 – Oluşturulan Çözümü Derleme (`cmake build x64`)

Çözüm hazır olduğunda, bir sonraki mantıklı adım onu derlemektir. CMake, derlemeyi sizin için yönlendirebilir ve arka planda MSBuild'e devredebilir.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Neden `--config Release` kullanılır?**  
> Visual Studio projeleri birden fazla yapılandırmayı (Debug, Release, RelWithDebInfo vb.) destekler. `Release` belirtmek, ikili dosyaların üretim için optimize edilmesini ve ortaya çıkan `.exe` ya da `.dll` dosyasının derleme ağacındaki `Release/` altında bulunmasını sağlar.

Debug derlemesini tercih ederseniz, `Release` yerine `Debug` yazın. Komut aynı şekilde çalışır; bu da **how to use CMake**'in farklı yapılandırmalar için sadece bu bayrağın değiştirilmesiyle mümkün olduğunu gösterir.

## Adım 4 – Derlemeyi Doğrulama (`build vs project` bütünlük kontrolü)

Başarılı bir derleme size bir çalıştırılabilir dosya ya da kütüphane bırakmalıdır. Bunun varlığını doğrulayalım:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Yaygın tuzaklar:**  
> - `CMakeLists.txt` dosyasını değiştirdikten sonra jeneratör adımını çalıştırmayı unutmak bu kontrolün başarısız olmasına neden olur.  
> - 32‑bit ve 64‑bit araç zincirlerini karıştırmak bağlayıcı (linker) hatalarına yol açabilir; her zaman `-Ax64` bayrağını tutarlı kullanın.  
> - “MSB3073” hataları görürseniz, genellikle bir post‑build adımının (örneğin kaynakların kopyalanması) başarısız olduğu anlamına gelir—çıkışı inceleyerek ipuçları bulun.

## Adım 5 – Temizleme ve Yeniden Çalıştırma (`cmake build x64` üzerinde yineleme)

Geliştirme sırasında çoğu zaman sıfırdan yeniden derlemeniz gerekir. En temiz yol, build klasörünü silip yeniden başlamak.

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **İpucu:**  
> `-DCMAKE_BUILD_TYPE=Release` bayrağını jeneratör komutuna eklemek, Visual Studio gibi çok‑konfigürasyonlu jeneratörler için isteğe bağlıdır, ancak Ninja gibi tek‑konfigürasyonlu bir jeneratöre geçerken kullanışlı olabilir.

## Adım 6 – Betiği Genişletme (İleri `cmake generate visual studio` senaryoları)

Projeniz bir alt‑dizinde bulunuyorsa ya da özel tanımlamalar geçirmeniz gerekiyorsa ne olur? CMake, bunu `-D` argümanlarıyla yapmanıza izin verir:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Artık oluşturulan VS çözümünde `MyFeature_ENABLED` makrosu tanımlı olacak ve kurulum hedefi dosyaları `/opt/myapp` altına yerleyecek. Bu, **how to use CMake**'in temel üç‑adımlı akışın ötesindeki esnekliğini gösterir.

## Beklenen Çıktı

Tam betiği baştan sona çalıştırdığınızda, terminal aşağıdakine benzer bir çıktı göstermelidir:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Bir şeyler ters giderse, CMake `CMakeLists.txt` içindeki hatalı satıra ya da eksik SDK bileşenlerine işaret eden hata mesajları verir—hızlı hata ayıklama için idealdir.

## Sonuç

Bir **cmake build x64** gerçekleştirmek için gereken her şeyi ele aldık: kaynak dizinini ayarlama, **cmake generate visual studio** adımını çağırma, ortaya çıkan **build vs project**'i derleme ve çıktıyı doğrulama. Betik kompakt, taşınabilir ve CI hatlarına ya da yerel geliştirme iş akışlarına entegrasyon için hazır.

Sonra şunları keşfedebilirsiniz:

- `ctest` ile birim‑test çalıştırma ekleme.  
- Daha hızlı artımlı derlemeler için Ninja jeneratörüne geçiş (`-G Ninja`).  
- Az önce yazdığımız bayrakları saklamak için CMake ön ayarlarını (`CMakePresets.json`) kullanma.

Denemekten, şeyleri kırmaktan ve ardından yeniden derlemekten çekinmeyin—sonuçta, CMake'i etkili bir şekilde öğrenmenin en hızlı yolu budur. İyi derlemeler!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Tablo Oluştur](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Stil ile Tablo Oluştur](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Kenarlıklı Tablo Oluştur](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}