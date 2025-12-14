# **7. Hafta – Esnek Argümanlı Fonksiyonlar (Variadic Functions)**


## 0. Esnek Argümanlı Fonksiyon Nedir?
Esnek argümanlı (variadic) fonksiyonlar, **parametre sayısı önceden belli olmayan** fonksiyonlardır.
C dilinde bu tür fonksiyonlar `stdarg.h` kütüphanesi kullanılarak yazılır.

En bilinen örnek:
```c
printf("Sayi: %d, Metin: %s", 10, "Merhaba");
```

`printf`, kaç tane ve hangi türde parametre geleceğini çalışma anında belirler.

📌 Bu tür fonksiyonlar özellikle:
- Değişken sayıda veri işleme
- Loglama
- Ortalama, toplam gibi işlemler
için kullanılır.


## 1. Genel Tanım (Syntax)
Esnek argümanlı fonksiyonlarda **son parametre sabit**, ondan sonrası esnektir.
```c
geri_donus_turu fonksiyon_adi(sabit_parametreler, ...) {
    // işlemler
}
```

Örnek:
```c
int toplam(int adet, ...);
```

`adet` → Kaç argüman gönderileceğini belirtir

`...` → Esnek argümanlar


## 2. stdarg.h Kütüphanesi
Esnek argümanlı fonksiyonlar için zorunlu olarak `stdarg.h` eklenmelidir.
```c
#include <stdarg.h>
```

Bu kütüphane aşağıdaki yapıları sağlar:

| Makro      | Açıklama                     |
| ---------- | ---------------------------- |
| `va_list`  | Argüman listesini tutar      |
| `va_start` | Argümanlara erişimi başlatır |
| `va_arg`   | Sıradaki argümanı okur       |
| `va_end`   | Argüman işlemini bitirir     |


## 3. Basit Bir Esnek Argümanlı Fonksiyon Örneği
Belirtilen sayı kadar sayının toplamını alan fonksiyon:
````c
#include <stdio.h>
#include <stdarg.h>

int toplam(int adet, ...) {
    va_list args;
    va_start(args, adet);

    int sum = 0;
    for (int i = 0; i < adet; i++) {
        sum += va_arg(args, int);
    }

    va_end(args);
    return sum;
}

int main() {
    printf("%d\n", toplam(3, 10, 20, 30)); // 60
}
````


## 4. va_list ve va_arg Mantığı
Adım adım inceleyelim:
````c
va_list args;
````

➡ Esnek argümanları tutacak yapı
````c
va_start(args, adet);
````

➡ `adet` parametresinden sonra gelen argümanlara erişimi başlatır
````c
va_arg(args, int);
````

➡ Sıradaki argümanı int türünde okur
````c
va_end(args);
````

➡ Bellek ve erişim temizliği yapar

📌 `va_arg` kullanırken türü doğru vermek zorunludur.


## 5. Ortalama Hesaplayan Esnek Argümanlı Fonksiyon
````c
double ortalama(int adet, ...) {
    va_list args;
    va_start(args, adet);

    int toplam = 0;
    for (int i = 0; i < adet; i++) {
        toplam += va_arg(args, int);
    }

    va_end(args);
    return (double)toplam / adet;
}

int main() {
    printf("%.2f\n", ortalama(4, 10, 20, 30, 40)); // 25.00
}
````


## 6. Farklı Türler Kullanılır mı?

❌ Hayır (doğrudan).
C dili, esnek argümanlarda tür bilgisini otomatik taşımaz.

Bu yüzden:
- Ya tüm argümanlar aynı tür olur
- Ya da ek bir bilgi gönderilir

Örnek – Tür Bilgisi ile Kullanım
````c
void yazdir(char tur, ...) {
    va_list args;
    va_start(args, tur);

    if (tur == 'i') {
        int x = va_arg(args, int);
        printf("Int: %d\n", x);
    } else if (tur == 'f') {
        double y = va_arg(args, double);
        printf("Float: %.2f\n", y);
    }

    va_end(args);
}
````


## 7. printf Neden Esnek Argümanlıdır?
```c
printf("Ad: %s Yas: %d Not: %.2f", "Ali", 20, 85.5);
```
`%d`, `%s`, `%f` → Tür bilgisini belirtir
Bu sayede `printf` hangi argümanı nasıl okuyacağını bilir

📌 Bu yüzden **format string** kritik öneme sahiptir.


## 8. Esnek Argümanlı Fonksiyonlarda Dikkat Edilmesi Gerekenler
⚠️ Hatalı kullanım ciddi sorunlara yol açar:

- Tür yanlış verilirse → Tanımsız davranış
- Fazla veya eksik argüman → Çökme (segmentation fault)
- Derleyici hata vermez (runtime hatası olur)

📌 Bu yüzden:

- Çok dikkatli kullanılmalı
- Mümkünse normal fonksiyonlar tercih edilmeli


## 9. Avantajlar ve Dezavantajlar
✅ Avantajlar

- Esnek kullanım
- Tek fonksiyonla farklı senaryolar
- printf gibi güçlü yapılar

❌ Dezavantajlar

- Tür güvenliği yok
- Debug zor
- Okunabilirlik azalır


## 10. Örnek – Maksimum Değeri Bulan Fonksiyon
```c
int maxBul(int adet, ...) {
    va_list args;
    va_start(args, adet);

    int max = va_arg(args, int);
    for (int i = 1; i < adet; i++) {
        int x = va_arg(args, int);
        if (x > max)
            max = x;
    }

    va_end(args);
    return max;
}

int main() {
    printf("%d\n", maxBul(5, 3, 7, 2, 9, 4)); // 9
}
```


## 11. Kaynaklar

- GeeksForGeeks – [C Variadic Functions](https://www.geeksforgeeks.org/c/variadic-functions-in-c/)
- Cppreference – [Variadic Functions](https://en.cppreference.com/w/c/variadic.html)
- YouTube – [What are variadic functions (va_list) in C?](https://www.youtube.com/watch?v=oDC208zvsdg)


## 12. Ödev

- "exercises" klasörüne bakın
