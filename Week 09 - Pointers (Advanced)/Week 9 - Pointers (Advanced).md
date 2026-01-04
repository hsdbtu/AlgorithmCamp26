# **9. Hafta – Pointer Derinleşme**


## 0. Giriş – Neden Pointer Derinleşme?

Pointer’lar sadece **adres tutmakla kalmaz**,
aynı zamanda:

* Diziler üzerinde gezinmemizi
* String’leri verimli işlememizi
* Çok katmanlı veri yapıları kurmamızı
* Dinamik bellek yönetimini

sağlar.

📌 Bu hafta pointer’ların **daha ileri ve gerçek hayatta kullanılan** yönlerine odaklanıyoruz.

---


## 1. Pointer Aritmetiği (Detaylı)

Pointer’lar üzerinde **+ , - , ++ , --** işlemleri yapılabilir.

```c
int dizi[5] = {10, 20, 30, 40, 50};
int *p = dizi;
```

Erişim:

```c
printf("%d\n", *p);       // 10
printf("%d\n", *(p + 1)); // 20
printf("%d\n", *(p + 4)); // 50
```

📌 `p + i` → **i. elemana gider**, byte byte değil.

---

### Pointer ++ ve --

```c
p++;  // Bir sonraki elemana geçer
printf("%d", *p); // 20
```

📌 Pointer artışı:

| Pointer Türü | Artış Miktarı |
| ------------ | ------------- |
| `char *`     | 1 byte        |
| `int *`      | 4 byte        |
| `double *`   | 8 byte        |

---


## 2. Pointer ile Dizi Gezme (Traversal)

```c
int dizi[4] = {1, 2, 3, 4};
int *p = dizi;

for(int i = 0; i < 4; i++) {
    printf("%d ", *(p + i));
}
```

📌 Bu yapı özellikle **fonksiyonlara dizi gönderirken** kullanılır.

---


## 3. Pointer ve Fonksiyon Parametreleri (Dizi Gönderme)

```c
void yazdir(int *p, int boyut) {
    for(int i = 0; i < boyut; i++) {
        printf("%d ", *(p + i));
    }
}

int main() {
    int dizi[3] = {10, 20, 30};
    yazdir(dizi, 3);
}
```

📌 Dizi adı → pointer olarak gönderilir.

---


## 4. Pointer to Pointer (Çift Pointer – Derinlemesine)

Bir pointer’ın **adresini tutan** pointer’dır.

```c
int x = 10;
int *p = &x;
int **pp = &p;
```

Erişim zinciri:

| İfade  | Anlam        |
| ------ | ------------ |
| `p`    | x’in adresi  |
| `*p`   | x            |
| `pp`   | p’nin adresi |
| `*pp`  | p            |
| `**pp` | x            |

```c
printf("%d", **pp); // 10
```

---

### Neden Pointer to Pointer Kullanılır?

* Fonksiyon içinde pointer değiştirmek
* Dinamik diziler
* 2D diziler
* String dizileri

---


## 5. Fonksiyonda Pointer’ı Değiştirmek

❌ Yanlış kullanım:

```c
void ata(int *p) {
    p = NULL;
}
```

✔️ Doğru kullanım:

```c
void ata(int **p) {
    *p = NULL;
}
```

```c
int *p;
ata(&p);
```

📌 Pointer’ı değiştirmek için **adresinin adresi** gerekir.

---


## 6. String Nedir? (Pointer Bakış Açısı)

C’de string:

> **Sonu `'\0'` ile biten char dizisidir.**

```c
char str[] = "Merhaba";
char *p = str;
```

Bellekte:

```
M e r h a b a \0
```

---


## 7. String ve Pointer ile Gezinme

```c
char str[] = "C Dili";
char *p = str;

while(*p != '\0') {
    printf("%c", *p);
    p++;
}
```

📌 String işlemlerinin temeli **pointer artışı**dır.

---


## 8. String Fonksiyonlarının Pointer Mantığı

### strlen (mantık)

```c
int uzunluk(char *p) {
    int sayac = 0;
    while(*p != '\0') {
        sayac++;
        p++;
    }
    return sayac;
}
```

📌 Dizi index’i yok → sadece pointer.

---

### strcpy (mantık)

```c
void kopyala(char *hedef, char *kaynak) {
    while(*kaynak != '\0') {
        *hedef = *kaynak;
        hedef++;
        kaynak++;
    }
    *hedef = '\0';
}
```

---


## 9. String Dizileri (char **)

```c
char *isimler[] = {
    "Ali",
    "Ayşe",
    "Mehmet"
};
```

Erişim:

```c
printf("%s", isimler[1]);     // Ayşe
printf("%c", isimler[1][0]);  // A
```

Pointer gösterimi:

```c
char **p = isimler;
```

📌 `p[i]` → string
📌 `p[i][j]` → karakter

---


## 10. Pointer + String Karşılaştırması

```c
char a[] = "Test";
char b[] = "Test";

if(a == b) // ❌ Yanlış
```

✔️ Doğru:

```c
strcmp(a, b) == 0
```

📌 `==` adres karşılaştırır, içerik değil.

---


## 11. Sık Yapılan Pointer Hataları (Derin)

⚠️ Çok yaygın hatalar:

```c
int *p;
*p = 10; // TANIMSIZ DAVRANIŞ
```

```c
char *p = "Hello";
p[0] = 'h'; // ❌ (string literal)
```

```c
int *p = NULL;
printf("%d", *p); // ❌
```

---


## 12. Pointer’ların Gerçek Hayat Kullanımı

* Dinamik bellek (`malloc`, `free`)
* Veri yapıları (Linked List, Tree)
* String işlemleri
* Sistem programlama
* Oyun motorları (C / C++)

📌 Senin **veri yapıları** ve **C temelin** için bu konu kritik.

---


## 13. Örnek – String Ters Çevirme (Pointer ile)

```c
void ters(char *p) {
    char *bas = p;
    char *son = p;

    while(*son != '\0') son++;
    son--;

    while(bas < son) {
        char temp = *bas;
        *bas = *son;
        *son = temp;
        bas++;
        son--;
    }
}
```

---


## 14. Avantaj / Risk Dengesi

✅ Güç

* Performans
* Esneklik
* Sistem seviyesinde kontrol

❌ Risk

* Segmentation fault
* Bellek sızıntısı
* Debug zor

📌 **Doğru kullanılırsa pointer = süper güç**

---


## 15. Kaynaklar

* GeeksForGeeks – [C - Pointer to Pointer (Double Pointer)](https://www.geeksforgeeks.org/c/c-pointer-to-pointer-double-pointer/)
* W3School – [C Pointer To Pointer](https://www.w3schools.com/c/c_pointer_to_pointer.php)
* YouTube – [Pointers to Pointers in C/C++](https://www.youtube.com/watch?v=d3kd5KbGB48)

---

## 16. Ödev

- "exercises" klasörüne bakın !!

---
