# **12. Hafta – Dosyalama (File I/O)**


## 0. Giriş – Neden Dosya?

Şimdiye kadar programlarda:

* Verileri **klavyeden** aldık
* Sonuçları **ekrana** yazdırdık

📌 Ancak program kapandığında:  
❌ Tüm veriler **kaybolur**

Gerçek hayatta ise:

* Öğrenci listeleri
* Kullanıcı kayıtları
* Oyun kayıtları (save files)
* Log dosyaları

👉 **kalıcı olarak saklanmalıdır**  
📌 İşte bu yüzden **dosyalama (File I/O)** kullanılır.

---


## 1. Dosya Nedir?

**Dosya**, verilerin kalıcı olarak saklandığı depolama alanıdır.

C dilinde dosyalar:

* Metin dosyaları (`.txt`)
* İkili dosyalar (`.dat`, `.bin`)

şeklinde tutulur.

📌 Bu haftada **temel File I/O mantığı** öğreneceğiz.

---


## 2. FILE Pointer Kavramı

C’de dosyalar **FILE pointer** ile kontrol edilir.

```c
FILE *fp;
```

📌 `FILE`, C’nin standart dosya yapısıdır  
📌 Tüm dosya işlemleri bu pointer üzerinden yapılır

---


## 3. Dosya Açma – `fopen()`

```c
fp = fopen("dosya.txt", "r");
```

Genel yapı:

```c
FILE *fopen(const char *dosyaAdi, const char *mod);
```

---

### Dosya Açma Modları

| Mod    | Açıklama            |
| ------ | ------------------- |
| `"r"`  | Okuma               |
| `"w"`  | Yazma (varsa siler) |
| `"a"`  | Sona ekleme         |
| `"r+"` | Okuma + yazma       |
| `"w+"` | Yazma + okuma       |
| `"a+"` | Okuma + sona ekleme |

📌 Yanlış mod → veri kaybı riski

---


## 4. Dosya Açma Kontrolü (ÇOK ÖNEMLİ)

```c
fp = fopen("veri.txt", "r");

if(fp == NULL) {
    printf("Dosya acilamadi!");
    return 1;
}
```

📌 Dosya yoksa veya yetki yoksa `NULL` döner

---


## 5. Dosyaya Yazma – `fprintf()`

```c
fprintf(fp, "Merhaba Dunya\n");
```

📌 `printf` → ekrana  
📌 `fprintf` → dosyaya

---

### Örnek – Dosyaya Sayı Yazma

```c
FILE *fp = fopen("sayilar.txt", "w");

fprintf(fp, "%d %f", 10, 3.14);

fclose(fp);
```

---


## 6. Dosyadan Okuma – `fscanf()`

```c
int x;
fscanf(fp, "%d", &x);
```

📌 `scanf` → klavye  
📌 `fscanf` → dosya

---

### Örnek – Dosyadan Veri Okuma

```c
int a;
float b;

FILE *fp = fopen("veri.txt", "r");

fscanf(fp, "%d %f", &a, &b);

fclose(fp);
```

---


## 7. Dosya Kapatma – `fclose()`

```c
fclose(fp);
```

📌 Açılan **her dosya mutlaka kapatılmalıdır**

Aksi halde:

❌ Veri kaybı  
❌ Bellek sızıntısı

---


## 8. Karakter Bazlı Okuma/Yazma

### `fputc()` – Tek karakter yazma

```c
fputc('A', fp);
```

---

### `fgetc()` – Tek karakter okuma

```c
char c = fgetc(fp);
```

📌 EOF kontrolü gerekir

---


## 9. Satır Bazlı Okuma/Yazma

### `fputs()` – Satır yazma

```c
fputs("Merhaba\n", fp);
```

---

### `fgets()` – Satır okuma

```c
char satir[100];
fgets(satir, 100, fp);
```

📌 Güvenlidir, taşma riskini azaltır

---


## 10. Dosya Sonu Kontrolü – `EOF`

```c
while((c = fgetc(fp)) != EOF) {
    printf("%c", c);
}
```

📌 Dosya bitince `EOF` döner

---


## 11. Dosya Konumu – `fseek`, `ftell`, `rewind`

### `rewind()`

```c
rewind(fp);
```

📌 Dosya başına döner

---

### `fseek()`

```c
fseek(fp, 0, SEEK_SET);
```

📌 Dosya imlecini hareket ettirir

---


## 12. Struct + Dosya (Temel Mantık)

📌 Dosyalama **struct** ile birlikte çok güçlüdür.

---

### Örnek Struct

```c
struct Ogrenci {
    int no;
    float ort;
};
```

---

### Struct Dosyaya Yazma

```c
FILE *fp = fopen("ogr.dat", "wb");

struct Ogrenci o = {1, 3.20};

fwrite(&o, sizeof(struct Ogrenci), 1, fp);

fclose(fp);
```

---

### Struct Dosyadan Okuma

```c
FILE *fp = fopen("ogr.dat", "rb");

struct Ogrenci o;

fread(&o, sizeof(struct Ogrenci), 1, fp);

fclose(fp);
```

📌 Binary dosyalar **hızlı ve güvenlidir**

---


## 13. Metin Dosyası vs Binary Dosya

| Metin      | Binary     |
| ---------- | ---------- |
| Okunabilir | Okunamaz   |
| Daha büyük | Daha küçük |
| Yavaş      | Hızlı      |

📌 Veri yapıları → **binary**

---


## 14. Çok Yapılan Dosya Hataları

### ❌ Dosya kontrolü yapmamak

```c
fp = fopen("x.txt", "r");
// NULL kontrolü yok ❌
```

---

### ❌ Yanlış mod kullanmak

```c
fopen("veri.txt", "w"); // Eski veri silinir ❌
```

---

### ❌ Dosyayı kapatmamak

```c
// fclose(fp); yok ❌
```

---


## 15. Örnek – Dosyadan Ortalama Hesaplama

```c
FILE *fp = fopen("notlar.txt", "r");

int n;
float x, toplam = 0;

fscanf(fp, "%d", &n);

for(int i = 0; i < n; i++) {
    fscanf(fp, "%f", &x);
    toplam += x;
}

printf("Ortalama: %.2f", toplam / n);

fclose(fp);
```

---


## 16. Dosyalama Nerelerde Kullanılır?

* Kullanıcı kayıtları
* Oyun save sistemi
* Log dosyaları
* Veri tabanı altyapısı
* Konfigürasyon dosyaları

📌 Gerçek programların **vazgeçilmezidir**

---


## 17. Avantaj / Risk Dengesi

✅ Avantaj

* Kalıcı veri
* Büyük veri saklama
* Gerçek dünya uygulaması

❌ Risk

* Dosya bozulması
* Yanlış mod
* Veri uyumsuzluğu

---


## 18. Struct + File I/O → Veri Yapıları

Bu konu:

* Linked List dosyaya yazma
* Binary Tree kayıtları
* Öğrenci otomasyonu

için **zorunlu altyapıdır**

📌 **Struct + File I/O bilen öğrenci → mini proje yapabilir**

---


## 19. Kaynaklar

* GeeksForGeeks – [File Handling in C](https://www.geeksforgeeks.org/c/basics-file-handling-c/)
* cppreference – [File input/output](https://en.cppreference.com/w/c/io.html)
* YouTube – [C writing files✍️](https://www.youtube.com/watch?v=UqB4EgUxapM)

---


## 20. Ödev

* "exercises" klasörüne bakın !!

---

