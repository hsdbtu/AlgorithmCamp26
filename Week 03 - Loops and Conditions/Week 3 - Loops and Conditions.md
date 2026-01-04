# **3. Hafta – Döngüler + Koşullar**

## 0. Döngü (Loop) Nedir?

Bir **döngü**, programda bir işlemi **belirli bir koşul sağlandığı sürece tekrarlamak** için kullanılır.

Yani, aynı işlemi defalarca yazmak yerine döngüleri kullanırız.

### C dilinde 3 temel döngü türü vardır:

1. `for` döngüsü
2. `while` döngüsü
3. `do-while` döngüsü

---

## 1. for Döngüsü

Belirli sayıda tekrarlanacak işlemler için kullanılır.

### Genel Yapı:

```c
for (başlangıç; koşul; artış) {
    // Tekrarlanacak işlemler
}

```

### Örnek:

```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        printf("%d. merhaba!\n", i);
    }
    return 0;
}

```

### Açıklama:

- `int i = 1;` → döngü değişkeni başlangıç değeri
- `i <= 5;` → döngü **şartı** (bu sağlandığı sürece döner)
- `i++` → her turda 1 artır

💡 Bu örnek ekrana 5 kez “merhaba” yazar.

---

## 2. while Döngüsü

Koşul **başta kontrol edilir**. Şart doğruysa döngü çalışır.

### Genel Yapı:

```c
while (koşul) {
    // Tekrarlanacak işlemler
}

```

### Örnek:

```c
#include <stdio.h>

int main() {
    int sayi = 1;

    while (sayi <= 5) {
        printf("%d. sayi\n", sayi);
        sayi++;
    }

    return 0;
}

```

💡 Eğer koşul **başta yanlışsa**, döngü **hiç çalışmaz**.

---

## 3. do-while Döngüsü

Koşul **sonda kontrol edilir**, yani döngü **en az bir kez** çalışır.

### Örnek:

```c
#include <stdio.h>

int main() {
    int sayi = 1;

    do {
        printf("%d. tekrar\n", sayi);
        sayi++;
    } while (sayi <= 5);

    return 0;
}

```

💡 Burada `do` bloğu **en az bir kez** çalışır, sonra koşul kontrol edilir.

---

## 4. Döngülerde Koşullar (if – else)

Döngüler içinde **şartlı ifadeler** kullanarak daha dinamik işlemler yapılabilir.

### Örnek 1 – Çift Sayıları Yazdırma:

```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i % 2 == 0)
            printf("%d çift sayidir.\n", i);
        else
            printf("%d tek sayidir.\n", i);
    }
    return 0;
}

```

---

### Örnek 2 – Belirli Şartta Döngüyü Bitirme

`break` komutu döngüyü **hemen durdurur.**

```c
for (int i = 1; i <= 10; i++) {
    if (i == 5)
        break;
    printf("%d\n", i);
}

```

💡 Bu örnekte döngü **5 olduğunda kırılır**, sadece 1–4 yazdırılır.

---

### Örnek 3 – Bazı Değerleri Atlamak

`continue` komutu, o turu **atlayıp** bir sonraki tura geçer.

```c
for (int i = 1; i <= 10; i++) {
    if (i == 5)
        continue;
    printf("%d\n", i);
}

```

💡 Bu örnekte **5 atlanır**, diğer sayılar yazdırılır.

---

## 5. Örnek – Faktöriyel Hesaplama

Kullanıcıdan bir sayı alıp faktöriyelini bulan program:

```c
#include <stdio.h>

int main() {
    int n, i;
    int sonuc = 1;

    printf("Bir sayi girin: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        sonuc = sonuc * i;
    }

    printf("%d! = %d\n", n, sonuc);
    return 0;
}

```

---

## 6. Çözerken Eğlenebileceğiniz Kaynaklar

- GeeksForGeeks – [C Loops](https://www.geeksforgeeks.org/cpp/cpp-loops/)
- W3Schools – [C while Loop](https://www.w3schools.com/c/c_while_loop.php)
- YouTube – [C For Loop Explained](https://www.youtube.com/watch?v=1oed-UmAxFs)

---

## 7. Ödev

- **Exercises klasörüne bakın!!**