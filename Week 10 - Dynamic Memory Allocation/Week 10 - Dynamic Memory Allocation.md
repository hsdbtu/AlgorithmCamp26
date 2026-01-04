# **10. Hafta – Dinamik Bellek Yönetimi**

## 0. Giriş – Neden Dinamik Bellek?

C dilinde normal değişkenler ve diziler:

* **Stack (yığın)** bellekte tutulur
* Boyutları **derleme zamanında** bellidir
* Fonksiyon bitince **otomatik silinir**

Ancak gerçek hayatta:

* Boyutu sonradan belli olan diziler
* Kullanıcıdan gelen veri kadar alan
* Veri yapıları (Linked List, Tree, Graph)

gereklidir.

📌 İşte burada **Heap (yığın belleği)** ve **dinamik bellek** devreye girer.

---


## 1. Stack vs Heap (Kavramsal)

| Stack                     | Heap                       |
| ------------------------- | -------------------------- |
| Otomatik yönetilir        | Manuel yönetilir           |
| Hızlı                     | Görece yavaş               |
| Küçük                     | Büyük                      |
| Fonksiyon bitince silinir | `free` edilene kadar kalır |

📌 Heap kullanımı → **sorumluluk programcıda**

---


## 2. malloc() – Bellek Ayırma

### Temel Tanım

```c
void* malloc(size_t size);
```

* Heap’te **size byte** yer ayırır
* Başlangıç adresini döndürür
* İçeriği **tanımsızdır**
* Başarısızsa `NULL` döner

---

### Basit Örnek

```c
int *p = (int*) malloc(sizeof(int));
```

📌 Bu kod:

* Heap’te 4 byte (int) ayırır
* Adresini `p`’ye verir

---

### Kullanım

```c
*p = 10;
printf("%d", *p);
```

---

### NULL Kontrolü (Çok Önemli)

```c
int *p = (int*) malloc(sizeof(int));

if(p == NULL) {
    printf("Bellek ayrılamadı!");
    return 1;
}
```

📌 `malloc` **her zaman kontrol edilir**

---


## 3. malloc() ile Dinamik Dizi

```c
int n;
scanf("%d", &n);

int *dizi = (int*) malloc(n * sizeof(int));
```

Kullanım:

```c
for(int i = 0; i < n; i++) {
    dizi[i] = i * 10;
}
```

📌 Bu dizi:

* Stack’te değil
* Heap’te
* Boyutu runtime’da belirli

---


## 4. calloc() – Sıfırlanmış Bellek

### Tanım

```c
void* calloc(size_t adet, size_t boyut);
```

* `adet × boyut` kadar bellek ayırır
* **Tüm bitleri 0 yapar**

---

### Örnek

```c
int *dizi = (int*) calloc(5, sizeof(int));
```

Bellek içeriği:

```
0 0 0 0 0
```

📌 `malloc` → çöp değer
📌 `calloc` → sıfır

---


## 5. malloc() vs calloc()

| Özellik   | malloc()   | calloc()   |
| --------- | ---------- | ---------- |
| Hız       | Daha hızlı | Daha yavaş |
| Başlangıç | Tanımsız   | 0          |
| Parametre | Tek        | İki        |

📌 Performans kritikse `malloc`
📌 Temizlik önemliyse `calloc`

---


## 6. realloc() – Belleği Yeniden Boyutlandırma

### Tanım

```c
void* realloc(void* ptr, size_t yeni_boyut);
```

* Mevcut belleği büyütür / küçültür
* Gerekirse yeni yere taşır
* Eski veriyi **korur**

---

### Örnek

```c
int *dizi = (int*) malloc(3 * sizeof(int));

dizi = (int*) realloc(dizi, 5 * sizeof(int));
```

📌 İlk 3 eleman korunur
📌 Yeni alan tanımsızdır

---

### realloc NULL Olursa?

```c
int *temp = realloc(dizi, yeni_boyut);

if(temp == NULL) {
    // eski dizi hâlâ geçerli
} else {
    dizi = temp;
}
```

📌 Direkt `dizi = realloc(...)` **risklidir**

---


## 7. free() – Bellek İade Etme

### Tanım

```c
void free(void* ptr);
```

* Heap’te ayrılan belleği sisteme geri verir
* Pointer **geçersiz olur**

---

### Doğru Kullanım

```c
free(dizi);
dizi = NULL;
```

📌 `NULL` atamak → güvenlik

---


## 8. Çok Yaygın Dinamik Bellek Hataları

### ❌ free() Unutmak (Memory Leak)

```c
int *p = malloc(sizeof(int));
// free yok
```

📌 Program büyüdükçe RAM dolar

---

### ❌ free()’den Sonra Kullanmak

```c
free(p);
*p = 10; // ❌
```

📌 **Use After Free**

---

### ❌ Double Free

```c
free(p);
free(p); // ❌
```

📌 Çökme garantili

---


## 9. Fonksiyon İçinde Dinamik Bellek

```c
int* diziOlustur(int n) {
    int *d = malloc(n * sizeof(int));
    return d;
}
```

Kullanım:

```c
int *p = diziOlustur(5);
free(p);
```

📌 Stack değil → heap döndürülür

---


## 10. Pointer to Pointer + malloc()

Fonksiyon içinde pointer oluşturmak:

```c
void olustur(int **p, int n) {
    *p = malloc(n * sizeof(int));
}
```

Kullanım:

```c
int *dizi;
olustur(&dizi, 5);
```

📌 9. haftadaki **double pointer** bilgisi burada kritik

---


## 11. String için Dinamik Bellek

```c
char *str = (char*) malloc(20 * sizeof(char));
strcpy(str, "Merhaba");
```

📌 String literal yerine **değiştirilebilir bellek**

---


## 12. Dinamik Bellek + Veri Yapıları

Bu konu doğrudan:

* Linked List
* Stack
* Queue
* Tree
* Graph

altyapısıdır.

📌 Veri yapıları = **dinamik bellek olmadan olmaz**

---


## 13. Örnek – Dinamik Dizi Ortalama

```c
int n;
scanf("%d", &n);

int *dizi = malloc(n * sizeof(int));
int toplam = 0;

for(int i = 0; i < n; i++) {
    scanf("%d", &dizi[i]);
    toplam += dizi[i];
}

printf("Ortalama: %.2f", (float)toplam / n);

free(dizi);
```

---


## 14. Avantaj / Risk Dengesi

✅ Avantaj

* Esnek bellek
* Büyük veri
* Gerçek sistemler

❌ Risk

* Memory leak
* Dangling pointer
* Crash

📌 **malloc + free disiplini = sağlam C programcısı**

---


## 15. Kaynaklar

* GeeksForGeeks – [Dynamic Memory Allocation in C](https://www.geeksforgeeks.org/c/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/)
* cppreference – [Dynamic memory management](https://en.cppreference.com/w/c/memory.html)
* YouTube – [Malloc in C is easy! 🏢](https://www.youtube.com/watch?v=n_Se6bt8jM0)

---


## 16. Ödev

* "exercises" klasörüne bakın !!


