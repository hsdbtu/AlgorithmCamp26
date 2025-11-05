## 3. Ödev

### **Başlangıç**

1. **Girilen iki sayı arasındaki tek sayıların toplamı**
```c
#include <stdio.h>

int main() {
    int sayi1, sayi2;
    int toplam = 0;

    printf("Iki sayi giriniz: ");
    scanf("%d %d", &sayi1, &sayi2);

    if (sayi1 > sayi2) {
        int temp = sayi1;
        sayi1 = sayi2;
        sayi2 = temp;
    }

    for (int i = sayi1 + 1; i < sayi2; i++) {
        if (i % 2 != 0) {
            toplam += i;
        }
    }

    printf("Aradaki tek sayilarin toplami: %d", toplam);

    return 0;
}
```

2. **Girilen sayının faktöriyelini hesaplama**
```c
#include <stdio.h>

int main() {
    int sayi;
    int faktoriyel = 1;

    printf("Bir sayi giriniz: ");
    scanf("%d", &sayi);

    for (int i = 1; i <= sayi; i++) {
        faktoriyel = faktoriyel * i;
    }

    printf("%d sayisinin faktoriyeli: %d", sayi, faktoriyel);

    return 0;
}
```


---

### **Orta**

1. **Girilen sayının asal olup olmadığını bulan algoritma**
```c
#include <stdio.h>

int main() {
    int sayi;
    int asal = 1;

    printf("Bir sayi giriniz: ");
    scanf("%d", &sayi);

    if (sayi <= 1) {
        asal = 0;
    } else {
        for (int i = 2; i < sayi; i++) {
            if (sayi % i == 0) {
                asal = 0;
                break;
            }
        }
    }

    if (asal == 1)
        printf("%d sayisi asaldir.", sayi);
    else
        printf("%d sayisi asal degildir.", sayi);

    return 0;
}
```
     
2. **Mükemmel sayı bulma algoritması**
```c
#include <stdio.h>

int main() {
    int sayi;
    int toplam = 0;

    printf("Bir sayi giriniz: ");
    scanf("%d", &sayi);

    for (int i = 1; i < sayi; i++) {
        if (sayi % i == 0) {
            toplam += i;
        }
    }

    if (toplam == sayi)
        printf("%d bir mukemmel sayidir.", sayi);
    else
        printf("%d bir mukemmel sayi degildir.", sayi);

    return 0;
}
```


---

### **Zor (Advanced)**

1. **Palindrom sayı kontrolü**
```c
#include <stdio.h>

int main() {
    int sayi, gecici, ters = 0, kalan;

    printf("Bir sayi giriniz: ");
    scanf("%d", &sayi);

    gecici = sayi;

    while (gecici != 0) {
        kalan = gecici % 10;
        ters = ters * 10 + kalan;
        gecici = gecici / 10;
    }

    if (sayi == ters)
        printf("%d bir palindrom sayidir.", sayi);
    else
        printf("%d bir palindrom sayi degildir.", sayi);

    return 0;
}
```
