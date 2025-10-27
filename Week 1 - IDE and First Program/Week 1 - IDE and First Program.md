## 0. IDE ve Derleyici (Compiler) Nedir?

### IDE (Integrated Development Environment)

Bir **IDE**, yazılım geliştiricilerin kod yazmasını, test etmesini ve çalıştırmasını kolaylaştıran tümleşik geliştirme ortamıdır.

Genellikle şu bileşenleri içerir:

- **Metin Düzenleyici (Editor):** Kodunuzu yazdığınız kısım.
- **Derleyici (Compiler):** Yazdığınız kaynak kodu makine diline çevirir.
- **Hata Ayıklayıcı (Debugger):** Hataları bulup düzeltmenize yardımcı olur.
- **Proje Yönetimi Araçları:** Dosya, kütüphane ve ayarların düzenlenmesini sağlar.

Popüler IDE’ler:

- **Code::Blocks** → Basit ve özellikle C/C++ için başlangıç dostu. Eğitimimizde bu IDE yi kullanacağız.
- **Visual Studio Code (VS Code)** → Eklentilerle güçlü hale gelen modern bir editör. Özellikle python dili için idealdir.

### Derleyici (Compiler)

- İnsanların yazdığı **kaynak kodu (source code)** alır.
- Bilgisayarın anlayacağı **makine koduna (machine code)** dönüştürür.
- C dilinde yaygın kullanılan derleyiciler: **GCC**, **Clang**, **MSVC**.

## 1. C Programlama Diline Giriş

C dili, **1972 yılında Dennis Ritchie** tarafından geliştirilmiş, sistem programlamadan gömülü cihazlara kadar birçok alanda kullanılan güçlü ve düşük seviyeye yakın bir programlama dilidir.

C’nin öne çıkan özellikleri:

- **Hızlı** ve donanıma yakın çalışır.
- **Taşınabilir**: Farklı işletim sistemlerinde derlenip çalıştırılabilir.
- **Basit ama güçlü**: Az sayıda anahtar kelimeyle çok şey yapılabilir.

Bugün kullandığımız dillerin çoğu (**C++, Java, C#, Go, Rust**) aslında C’den etkilenmiştir.

## 2. İlk Programımız – “Hello World”

Birçok programlama dilinde öğrenmeye başlanırken yazılan ilk program, ekrana **“Hello World”** çıktısını veren koddur.

### Örnek Kod:

```c
#include <stdio.h>   // Giriş/çıkış fonksiyonlarını içeren kütüphane

int main() {
    printf("Hello World!\n");  // Ekrana yazdır
    return 0;                  // Programı başarıyla sonlandır
}
```

### Açıklama:

- `#include <stdio.h>` → Standart giriş/çıkış fonksiyonlarını (ör. `printf`) kullanmamızı sağlayan kütüphanedir.
- `int main()` → Program başlatıldığında otomatik çalışan fonksiyon.
- `printf()` → Ekrana yazı yazdıran fonksiyon.
- `return 0;` → Programın başarıyla sonlandığını gösterir.

## 3. Kullanıcıdan Girdi Alma – İsim Yazdırma

Biraz daha ileri gidip kullanıcıdan **adını alıp ekrana yazdırmayı deniyelim.**

### Örnek Kod:

```c
#include <stdio.h>

int main() {
    char isim[30];   // Kullanıcının adını saklayacak karakter dizisi

    printf("Adinizi giriniz: ");
    scanf("%s", isim);  // Kullanıcıdan string (kelime) al

    printf("Merhaba %s!\n", isim);  // Kullanıcının adını ekrana yazdır

    return 0;
}

```

### Açıklama:

- `char isim[30];` → Maksimum 30 karakterlik bir dizi (string) tanımlar.
- `scanf("%s", isim);` → Kullanıcıdan adını alır.
- `printf("Merhaba %s!\n", isim);` → `%s` → string (metin) format belirtecidir.

## Çözerken Eğlenebileceğinizi Düşündüğümüz İçerikler

- [GeeksForGeeks – C Programming Language](https://www.geeksforgeeks.org/c/c-programming-language/)
- [YouTube: C Programming Tutorial for Beginners](https://www.youtube.com/watch?v=KJgsSFOSQv0)
- [W3Schools-C](https://www.w3schools.com/c/)

## 4. Ödev
- **Exercises klasörüne bakın!!**