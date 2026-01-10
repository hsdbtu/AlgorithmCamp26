# **11. Hafta – Structs (Yapılar)**


## 0. Giriş – Neden Struct?

C dilinde temel veri tipleri:

* `int`
* `float`
* `char`
* `double`

tek bir **değeri** temsil eder.

Ancak gerçek hayatta:

* Bir öğrencinin → numarası, adı, notu
* Bir ürünün → adı, fiyatı, stoğu
* Bir oyundaki karakterin → canı, gücü, seviyesi

**birden fazla farklı türde veri** ile ifade edilir.

📌 İşte bu noktada **struct (yapı)** kullanılır.

---


## 1. Struct Nedir?

**Struct**, farklı türde değişkenleri tek bir isim altında toplayan **kullanıcı tanımlı veri tipidir**.

📌 Kısaca:

> **Birden fazla değişken → tek mantıksal bütün**

---


## 2. Struct Tanımlama

### Genel Yapı

```c
struct YapıAdi {
    tip1 degisken1;
    tip2 degisken2;
    ...
};
```

---

### Örnek – Öğrenci Yapısı

```c
struct Ogrenci {
    int no;
    float ort;
    char harf;
};
```

📌 Bu bir **tip tanımıdır**, henüz değişken yoktur.

---


## 3. Struct Değişkeni Tanımlama

```c
struct Ogrenci o1;
```

Alanlara erişim:

```c
o1.no = 123;
o1.ort = 3.25;
o1.harf = 'B';
```

📌 Struct üyelerine **nokta (`.`) operatörü** ile erişilir.

---


## 4. Struct + Initialization (Başlatma)

```c
struct Ogrenci o2 = {456, 2.75, 'C'};
```

Sıra **tanım sırasına göre** olmalıdır.

---


## 5. Struct İçinde Array

```c
struct Ogrenci {
    int no;
    char ad[20];
    float ort;
};
```

Kullanım:

```c
struct Ogrenci o;
strcpy(o.ad, "Ahmet");
```

📌 `char*` değil → **char array**

---


## 6. Struct Türüne typedef

Sürekli `struct` yazmamak için:

```c
typedef struct {
    int no;
    float ort;
} Ogrenci;
```

Kullanım:

```c
Ogrenci o1;
```

📌 Bu kullanım **çok yaygındır** (özellikle veri yapılarında)

---


## 7. Struct ve Fonksiyonlar

### Struct Parametre Olarak Gönderme

```c
void yazdir(struct Ogrenci o) {
    printf("%d %.2f", o.no, o.ort);
}
```

📌 **Kopya gönderilir**

---

### Struct Pointer ile Gönderme (Önerilen)

```c
void yazdir(struct Ogrenci *o) {
    printf("%d %.2f", o->no, o->ort);
}
```

📌 `->` operatörü = pointer + struct erişimi

---


## 8. Struct Pointer (`->`) Operatörü

```c
struct Ogrenci o;
struct Ogrenci *p = &o;

p->no = 100;
```

📌 `(*p).no` yerine `p->no`

---


## 9. Struct Dizileri

```c
struct Ogrenci sinif[3];
```

Kullanım:

```c
sinif[0].no = 1;
sinif[1].ort = 3.10;
```

📌 Öğrenci listeleri bu şekilde tutulur

---


## 10. Dinamik Struct (malloc + struct)

```c
struct Ogrenci *o;
o = (struct Ogrenci*) malloc(sizeof(struct Ogrenci));
```

Kullanım:

```c
o->no = 5;
o->ort = 2.90;
```

📌 Veri yapılarının **temel taşı**

---


## 11. Struct Dizisi + Dinamik Bellek

```c
int n;
scanf("%d", &n);

struct Ogrenci *dizi =
    (struct Ogrenci*) malloc(n * sizeof(struct Ogrenci));
```

📌 Runtime’da kaç öğrenci olduğu belli

---


## 12. İç İçe Struct (Nested Struct)

```c
struct Tarih {
    int gun, ay, yil;
};

struct Ogrenci {
    int no;
    struct Tarih dogum;
};
```

Erişim:

```c
o.dogum.yil = 2002;
```

---


## 13. Struct Kopyalama

```c
struct Ogrenci a, b;
a.no = 10;
b = a;
```

📌 Tüm alanlar **otomatik kopyalanır**

---


## 14. Struct ile Veri Yapılarına Geçiş

Bu konu doğrudan:

* Linked List düğümleri
* Stack node yapıları
* Tree node’ları
* Graph vertex’leri

için altyapıdır.

📌 **Struct + Pointer + malloc = Veri Yapıları**

---


## 15. Çok Yapılan Struct Hataları

### ❌ Pointer yerine nokta kullanmak

```c
p.no = 5; // ❌
p->no = 5; // ✅
```

---

### ❌ Struct içinde string literal

```c
char *ad = "Ali"; // ❌ (değiştirilemez)
```

📌 `char ad[20]` tercih edilir

---

### ❌ malloc sonrası NULL kontrolü yapmamak

```c
if(o == NULL) {
    printf("Bellek hatası");
}
```

---


## 16. Örnek – Öğrenci Ortalama Hesabı

```c
int n;
scanf("%d", &n);

struct Ogrenci *ogr =
    malloc(n * sizeof(struct Ogrenci));

float toplam = 0;

for(int i = 0; i < n; i++) {
    scanf("%f", &ogr[i].ort);
    toplam += ogr[i].ort;
}

printf("Ortalama: %.2f", toplam / n);

free(ogr);
```

---


## 17. Avantaj / Risk Dengesi

✅ Avantaj

* Anlamlı veri gruplama
* Temiz kod
* Veri yapıları için zorunlu

❌ Risk

* Pointer karmaşası
* Yanlış erişim
* Bellek hataları

📌 **Struct mantığını oturtan öğrenci → veri yapılarında zorlanmaz**

---


## 18. Kaynaklar

* GeeksForGeeks – [C Structures](https://www.geeksforgeeks.org/c/structures-c/)
* cppreference – [Struct declaration](https://en.cppreference.com/w/c/language/struct.html)
* YouTube – [C structs 🏠](https://www.youtube.com/watch?v=oKXP1HZ8xIs)

---


## 19. Ödev

* "exercises" klasörüne bakın !!

---


