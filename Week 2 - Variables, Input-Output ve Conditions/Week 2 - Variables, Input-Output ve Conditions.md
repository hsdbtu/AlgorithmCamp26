# **2. Hafta – Değişkenler, Input/Output ve Koşullar**

## 0. Değişken (Variable) Nedir?

Bir **değişken**, programın çalışması sırasında bilgi saklamak için kullandığımız bir “etiketli kutu” gibidir.

Her değişkenin bir **adı**, **veri tipi** ve **değeri** vardır.

### Örnek:

```c
int yas = 20;
float boy = 1.75;
char harf = 'A';

```

### Açıklama:

- **int** → Tam sayı (örnek: 5, -10, 42)
- **float** → Ondalıklı sayı (örnek: 3.14, 2.7)
- **char** → Tek bir karakter (örnek: 'A', 'b')
- **double** → Daha hassas ondalıklı sayı türü
- **char dizi[]** → Metin (örnek: "Merhaba")

💡 **Not:** C dilinde her değişkenin türü **önceden tanımlanmak zorundadır.**

---

## 1. Girdi (Input) ve Çıktı (Output) İşlemleri

Programlarda kullanıcıyla etkileşime girmek için **girdi (input)** alır ve **çıktı (output)** veririz.

### Ekrana Yazı Yazdırma

```c
#include <stdio.h>

int main() {
    printf("Merhaba Dunya!\n");
    return 0;
}

```

### Kullanıcıdan Veri Alma

```c
#include <stdio.h>

int main() {
    int yas;
    printf("Yasinizi girin: ");
    scanf("%d", &yas);   // %d → int türü için format belirteci
    printf("Yasiniz: %d\n", yas);
    return 0;
}

```

### Format Belirteçleri:

| Tür | Açıklama | Örnek |
| --- | --- | --- |
| `%d` | Tam sayı | int |
| `%f` | Ondalıklı sayı | float |
| `%c` | Karakter | char |
| `%s` | Metin (string) | char[] |

---

## 2. Koşullar (if – else)

Programlarımızın **duruma göre farklı işlemler** yapmasını isteriz.

Bunun için `if`, `else if` ve `else` yapıları kullanılır.

### Örnek:

```c
#include <stdio.h>

int main() {
    int sayi;

    printf("Bir sayi girin: ");
    scanf("%d", &sayi);

    if (sayi > 0) {
        printf("Sayi pozitiftir.\n");
    } else if (sayi < 0) {
        printf("Sayi negatiftir.\n");
    } else {
        printf("Sayi sifirdir.\n");
    }

    return 0;
}

```

### Açıklama:

- `if` → Şart sağlanıyorsa bu blok çalışır.
- `else if` → İlk şart sağlanmazsa ikinciyi dener.
- `else` → Hiçbiri sağlanmazsa burası çalışır.

---

## 3. Örnek – Not Hesaplama

Kullanıcının notunu alıp geçti mi kaldı mı söyleyen bir program yazalım.

```c
#include <stdio.h>

int main() {
    int not;

    printf("Notunuzu girin: ");
    scanf("%d", &not);

    if (not >= 50) {
        printf("Tebrikler, gectiniz!\n");
    } else {
        printf("Maalesef, kaldiniz.\n");
    }

    return 0;
}

```

### Gelişmiş Versiyon (Harf Notu)

```c
if (not >= 90) printf("Harf Notu: A\n");
else if (not >= 80) printf("Harf Notu: B\n");
else if (not >= 70) printf("Harf Notu: C\n");
else if (not >= 60) printf("Harf Notu: D\n");
else printf("Harf Notu: F\n");

```

---

## 4. Çözerken Eğlenebileceğiniz Kaynaklar

- GeeksForGeeks – C if-else
- [W3Schools – C Conditions](https://www.w3schools.com/c/c_conditions.php)
- [YouTube: C Programming – if else Explained](https://www.youtube.com/watch?v=f4KOjWS_KZs)

---

## 5. Ödev
- **Exercises klasörüne bakın!!**