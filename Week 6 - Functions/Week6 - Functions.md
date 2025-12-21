# **6. Hafta – Fonksiyonlar (Functions)**
## 0. Fonksiyon Nedir?
Fonksiyon, belirli bir görevi yerine getiren ve gerektiğinde çağrılabilen kod bloklarıdır.
C dilinde fonksiyonlar kod tekrarını azaltır, programı daha düzenli ve okunabilir hale getirir.

Genel tanımı:
```c
geri_donus_turu fonksiyon_adi(parametreler) {
    // yapılacak işlemler
    return deger;  // (varsa)
}
```

Örnek:
```c
int topla(int a, int b) {
    return a + b;
}
```

Açıklama:

- int → Geri dönüş türü
- topla → Fonksiyonun adı
- (int a, int b) → Parametreler
- return a + b; → Sonuç döndürme


## 1. Fonksiyon Çağırma
Tanımlanan bir fonksiyon, ismi ve parametreleri kullanılarak çalıştırılır. Çağırma sırasında parametreler fonksiyona gönderilir:
```c
int sonuc = topla(5, 3);
printf("%d", sonuc);  // 8
```


## 2. Parametreli ve Parametresiz Fonksiyonlar
Fonksiyonlar, çalışmak için değer alabilir (parametreli) veya hiçbir değer almadan da işlem yapabilir (parametresiz).

a) Parametre alan fonksiyon
```c
void yazdir(int x) {
    printf("Sayi: %d\n", x);
}
```

Çağırma:
```c
yazdir(10);
```

b) Parametresiz fonksiyon
```c
void selam() {
    printf("Merhaba!\n");
}
```

Çağırma:
```c
selam();
```


## 3. Geri Değer Döndüren ve Döndürmeyen Fonksiyonlar
Bazı fonksiyonlar return ile değer döndürür bu değerin türü fonksiyonu yazarken tanımlanır (int Topla(), void main() vb.), bazıları ise sadece işlem yapar (void).

a) Değer döndüren (return kullanan)
```c
float kare(float x) {
    return x * x;
}
```

b) Değer döndürmeyen (void)
```c
void menu() {
    printf("1- Baslat\n2- Cikis\n");
}
```


## 4. Fonksiyon Bildirimi (Prototype)
Fonksiyon tanımı main fonksiyonundan sonra yazılacaksa, derleyicinin fonksiyonu önceden tanıması için bildirimi gereklidir. Buna Prototip de denebilir.
```c
int topla(int, int);  // Bildirim

int main() {
    printf("%d", topla(3, 4));
}

int topla(int a, int b) {  // Tanım
    return a + b;
}
```
💡 Bildirim yapılmazsa C derleyicisi fonksiyonun ne olduğunu bilmez.


## 5. Örnek – Bir Sayının Faktöriyelini Hesaplayan Fonksiyon
```c
int faktoriyel(int n) {
    int f = 1;
    for (int i = 1; i <= n; i++) {
        f *= i;
    }
    return f;
}

int main() {
    printf("%d", faktoriyel(5));  // 120
}
```


## 6. Örnek – Bir Sayının Tek mi Çift mi Olduğunu Döndüren Fonksiyon
```c
int tekMiCiftMi(int n) {
    if (n % 2 == 0)
        return 0;  // Çift
    else
        return 1;  // Tek
}

int main() {
    if (tekMiCiftMi(7))
        printf("Tek");
    else
        printf("Cift");
}
```


## 7. Fonksiyonlarda Değer ve Referans Kavramı
C dilinde parametreler değere göre aktarılır, yani gönderilen değişkenin bir kopyası üzerinde işlem yapılır. Orijinal değer değişmez.
```c
void arttir(int x) {
    x++;
    printf("Fonksiyon içi: %d\n", x);
}

int main() {
    int a = 5;
    arttir(a);
    printf("Fonksiyon disi: %d\n", a);
}
```

Çıktı:
```c
Fonksiyon içi: 6
Fonksiyon disi: 5
```
📌 Çünkü x, a'nın kopyasıdır.

Pointer kullanarak referans yöntemi taklit edilebilir:
```c
void arttirPtr(int *x) {
    (*x)++;
}

int main() {
    int a = 5;
    arttirPtr(&a);
    printf("%d", a);  // 6
}
```


## 8. C Dilinde Sık Kullanılan Standart Fonksiyonlar

Bu bölümde C’nin kendi kütüphanelerinde (stdlib, stdio, math, string, ctype) bulunan hazır fonksiyonlar tanıtılmaktadır.
Bu fonksiyonlar bizim tarafımızdan yazılmaz, C’nin kendisinde zaten hazırdır.

### 📌 8.1. stdio.h – Girdi / Çıktı Fonksiyonları
| Fonksiyon   | Açıklama                  |
| ----------- | ------------------------- |
| `printf()`  | Ekrana yazı yazdırır      |
| `scanf()`   | Kullanıcıdan değer alır   |
| `putchar()` | Tek bir karakter yazdırır |
| `gets()` ❌  | Güvensiz (kullanma)       |
| `fgets()`   | Güvenli string okuma      |

**Örnek:**
```c
printf("Merhaba %d", 10);

```

### 📌 8.2. string.h – String (Karakter Dizisi) Fonksiyonları
| Fonksiyon      | Açıklama                            |
| -------------- | ----------------------------------- |
| `strlen(str)`  | String uzunluğunu bulur             |
| `strcpy(a, b)` | b'yi a'ya kopyalar                  |
| `strcat(a, b)` | b stringini a'nın sonuna ekler      |
| `strcmp(a, b)` | Stringleri karşılaştırır (0 → eşit) |

**Örnek:**
```c
int uzunluk = strlen("Merhaba");

```

### 📌 8.3. ctype.h – Karakter Türü Fonksiyonları
| Fonksiyon    | Açıklama          |
| ------------ | ----------------- |
| `toupper(c)` | Harfi büyük yapar |
| `tolower(c)` | Harfi küçük yapar |
| `isdigit(c)` | Rakam mı?         |
| `isalpha(c)` | Harf mi?          |
| `isspace(c)` | Boşluk mu?        |

**Örnek:**
```c
char c = toupper('a');  // 'A'

```

### 📌 8.4. math.h – Matematik Fonksiyonları
| Fonksiyon           | Açıklama                    |
| ------------------- | --------------------------- |
| `sqrt(x)`           | Karekök alır                |
| `pow(a, b)`         | a üzeri b                   |
| `abs(x)`            | Mutlak değer (int)          |
| `fabs(x)`           | Mutlak değer (float/double) |
| `sin(x)` / `cos(x)` | Trigonometrik fonksiyonlar  |
| `ceil(x)`           | Yukarı yuvarla              |
| `floor(x)`          | Aşağı yuvarla               |

**Örnek:**
```c
double r = sqrt(16);  // 4

```

### 📌 8.5. stdlib.h – Genel Amaçlı Fonksiyonlar
| Fonksiyon   | Açıklama                        |
| ----------- | ------------------------------- |
| `atoi(str)` | String → int                    |
| `atof(str)` | String → double                 |
| `rand()`    | Rastgele sayı üretir            |
| `srand()`   | Rastgeleliği başlatır           |
| `malloc()`  | Bellekten yer ayırır            |
| `free()`    | Ayrılan belleği serbest bırakır |
| `exit()`    | Programı sonlandırır            |

**Örnek:**
```c
int x = atoi("123");  // 123

```

### 📌 8.6. time.h – Zaman Fonksiyonları
| Fonksiyon        | Açıklama                       |
| ---------------- | ------------------------------ |
| `time(NULL)`     | Şu anki UNIX zamanını döndürür |
| `clock()`        | İşlemci zamanını döndürür      |
| `difftime(a, b)` | Zaman farkı                    |

**Örnek:**
```c
unsigned t = time(NULL);

```


## 9. Çözerken İşinize Yarayacak Kaynaklar
- GeeksForGeeks – [C Functions](https://www.geeksforgeeks.org/c/c-functions/)
- W3Schools – [C Functions](https://www.w3schools.com/c/c_functions.php)
- YouTube – [C Function](https://www.youtube.com/watch?v=ou_G7_zodR4)


## 10. Ödev
- "exercises" klasörüne bakın.