# **5. Hafta – Karakter Dizileri (Strings)**
## 0. Karakter Dizisi (String) Nedir?

Karakter dizisi, sonunda mutlaka \0 (null terminator) bulunan karakterlerden oluşan bir dizidir.
C dilinde özel bir string türü yoktur; tüm stringler aslında char dizileridir.

```c
char kelime[6] = "hello";
```

**Açıklama:**
- char → Eleman türü
- kelime → Dizinin adı
- [6] → Boyut (5 harf + 1 \0)
- "hello" → Karakter dizisi

💡 Not: Dizinin boyutu string uzunluğu + 1 olacak şekilde ayarlanmalıdır.


## 1. Karakter Dizisi Elemanlarına Erişim

String içindeki karakterlere indeksle ulaşılır.

```c
char kelime[] = "Merhaba";

printf("%c\n", kelime[0]);  // M
printf("%c\n", kelime[3]);  // h
```

Eleman değiştirme:
```c
kelime[0] = 'm';
```

## 2. Kullanıcıdan String Alma
### a) scanf ile string alma

```c
char isim[20];
scanf("%s", isim);
```
⚠️ scanf, boşluk görünce durur.

### b) fgets ile güvenli okuma (önerilen)
```c
char isim[20];
fgets(isim, 20, stdin);
```
✔️ Boşlukları da alır
✔️ Taşma riskini azaltır


## 3. String Yazdırma

Tamamını yazdırmak için:

```c
char selam[] = "Merhaba";
printf("%s\n", selam);
```

Tek tek yazdırmak:

```c
for (int i = 0; selam[i] != '\0'; i++) {
    printf("%c", selam[i]);
}
```


## 4. Örnek – String Uzunluğu Bulma

```c
char kelime[] = "program";
int i = 0;

while (kelime[i] != '\0') {
    i++;
}

printf("Uzunluk: %d\n", i);
```


## 5. Örnek – Kaç Adet ‘a’ Harfi Var?
```c
char metin[] = "alabama";
int sayac = 0;

for (int i = 0; metin[i] != '\0'; i++) {
    if (metin[i] == 'a') {
        sayac++;
    }
}

printf("'a' harfi sayisi: %d\n", sayac);
```


## 6. Faydalı String Fonksiyonları (string.h)

| Fonksiyon        | Açıklama                             |
|------------------|--------------------------------------|
| `strlen(str)`    | String uzunluğunu döndürür           |
| `strcpy(a, b)`   | b stringini a dizisine kopyalar      |
| `strcat(a, b)`   | b stringini a'nın sonuna ekler       |
| `strcmp(a, b)`   | İki stringi karşılaştırır (0 → eşit) |

Örnek:

```c
#include <string.h>

char a[20] = "Merhaba";
char b[] = " Dünya";

strcat(a, b);
printf("%s", a);  // Merhaba Dünya
```


## 7. Çözerken Eğlenebileceğiniz Kaynaklar
- GeeksForGeeks – [C Strings](https://www.geeksforgeeks.org/c/string-functions-in-c/?utm_source=chatgpt.com)
- W3Schools – [C Strings](https://www.w3schools.com/c/c_strings_functions.php?utm_source=chatgpt.com)
- YouTube – [C Strings Functions](https://www.youtube.com/watch?v=5p4YpQmZdwU)

## 8. Ödev

- exercises klasörüne bakın.