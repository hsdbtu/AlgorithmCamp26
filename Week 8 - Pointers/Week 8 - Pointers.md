# **8. Hafta – Pointer’lar (İşaretçiler)**

## 0. Pointer (İşaretçi) Nedir?

Pointer (işaretçi), **bellekteki bir adresi tutan değişkendir**.
Yani bir pointer, doğrudan bir değeri değil, **o değerin bellekteki konumunu (adresini)** saklar.

📌 C dilinin en güçlü ama en tehlikeli konularından biridir.

Basit örnek:

```c
int x = 10;
int *p = &x;
```

* `x` → Normal değişken
* `&x` → x’in bellek adresi
* `p` → x’in adresini tutan pointer

---

## 1. Pointer Tanımı (Syntax)

Pointer tanımlarken `*` operatörü kullanılır.

```c
veri_tipi *pointer_adi;
```

Örnekler:

```c
int *p;
char *c;
double *d;
```

📌 `*` **pointer olduğunu**, veri tipi ise **adresinde tutulan verinin türünü** belirtir.

---

## 2. Adres Operatörü (&) ve Değer Operatörü (*)

### & (Adres Operatörü)

Bir değişkenin bellekteki adresini verir.

```c
int x = 5;
printf("%p", &x);
```

### * (Dereference / İçeriğe Erişim)

Pointer’ın gösterdiği adresteki değere ulaşır.

```c
int x = 5;
int *p = &x;

printf("%d", *p); // 5
```

📌 Özet:

* `p` → adres
* `*p` → o adresteki değer

---

## 3. Basit Pointer Örneği

```c
#include <stdio.h>

int main() {
    int x = 10;
    int *p = &x;

    printf("x = %d\n", x);
    printf("x adresi = %p\n", &x);
    printf("p = %p\n", p);
    printf("*p = %d\n", *p);
}
```

📌 `p` ile `&x` aynı adresi gösterir.

---

## 4. Pointer ile Değer Değiştirme

Pointer sayesinde **başka bir değişkenin değerini dolaylı yoldan değiştirebiliriz**.

```c
int x = 10;
int *p = &x;

*p = 50;
printf("%d", x); // 50
```

📌 Bu özellik fonksiyonlarda çok kritik rol oynar.

---

## 5. Fonksiyonlarda Pointer Kullanımı (Call by Reference)

### Normal (Call by Value)

```c
void artir(int x) {
    x++;
}
```

→ Asıl değişken değişmez.

### Pointer ile (Call by Reference)

```c
void artir(int *x) {
    (*x)++;
}

int main() {
    int a = 5;
    artir(&a);
    printf("%d", a); // 6
}
```

📌 Pointer ile fonksiyon, **orijinal değişkeni değiştirebilir**.

---

## 6. Pointer ve Diziler

C dilinde **dizi adı aslında bir pointer’dır**.

```c
int dizi[3] = {10, 20, 30};
int *p = dizi;
```

Erişim:

```c
printf("%d\n", *(p + 1)); // 20
```

📌 `dizi[i]` ile `*(dizi + i)` aynıdır.

---

## 7. Pointer Aritmetiği

Pointer’lar üzerinde matematiksel işlemler yapılabilir.

```c
int dizi[3] = {1, 2, 3};
int *p = dizi;

p++;  // Bir sonraki elemana geçer
```

📌 Artış miktarı:

* `int *` → 4 byte
* `char *` → 1 byte
* `double *` → 8 byte

---

## 8. NULL Pointer

Pointer’ın **hiçbir yeri göstermediğini** belirtir.

```c
int *p = NULL;
```

⚠️ NULL pointer dereference edilirse program çöker:

```c
*p = 10; // HATA
```

📌 Pointer kullanılmadan önce NULL kontrolü yapılmalıdır.

---

## 9. Pointer to Pointer (Çift Pointer)

Bir pointer’ın adresini tutan pointer’dır.

```c
int x = 10;
int *p = &x;
int **pp = &p;
```

Erişim:

```c
printf("%d", **pp); // 10
```

📌 Özellikle dinamik bellek ve fonksiyonlarda kullanılır.

---

## 10. Pointer ve Struct

Struct’lar pointer ile çok sık kullanılır.

```c
struct Ogrenci {
    int no;
    float ort;
};

struct Ogrenci ogr;
struct Ogrenci *p = &ogr;

p->no = 10;
p->ort = 3.5;
```

📌 `->` operatörü, struct pointer’larında kullanılır.

---

## 11. Pointer Kullanırken Dikkat Edilmesi Gerekenler

⚠️ Çok kritik noktalar:

* Tanımsız pointer kullanma ❌
* NULL pointer dereference ❌
* Yanlış türde pointer ❌
* Bellek taşmaları ❌

📌 Pointer hataları:

* Segmentation fault
* Program çökmesi
* Debug zor

---

## 12. Avantajlar ve Dezavantajlar

✅ Avantajlar

* Bellek üzerinde tam kontrol
* Performans
* Fonksiyonlarda esneklik

❌ Dezavantajlar

* Hata yapmaya çok açık
* Okunabilirlik azalır
* Debug zor

---

## 13. Örnek – Swap (Yer Değiştirme)

```c
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 3, y = 7;
    swap(&x, &y);
    printf("%d %d", x, y); // 7 3
}
```

---

## 14. Kaynaklar

* GeeksForGeeks – [Pointers in C](https://www.geeksforgeeks.org/c/c-pointers/)
* W3School – [C Pointer](https://www.w3schools.com/c/c_pointers.php)
* YouTube – [C pointers explained👉](https://www.youtube.com/watch?v=DplxIq0mc_Y)

---

## 15. Ödev

* "exercises" klasörüne bakın
