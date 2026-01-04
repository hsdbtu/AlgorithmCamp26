### **Başlangıç**

**1. SORU** 
Kullanıcıdan bir sayı girmesini isteyen ve **1'den o sayıya kadar olan tüm çift sayıların toplamını** bulan bir C programı yazınız.  
(Örneğin, kullanıcı **10** girerse çıktı **2 + 4 + 6 + 8 + 10 = 30** olmalıdır).  
Bu programı **for döngüsü** kullanarak yazınız.
```c
#include <stdio.h>

int main() {
    int n, sum = 0;

    printf("Bir sayı girin: ");
    scanf("%d", &n);

    for (int i = 2; i <= n; i += 2) {
        sum += i;
    }

    printf("Cift sayilarin toplami: %d\n", sum);

    return 0;
}
```

**2. SORU**  
Kullanıcı **-1** değerini girene kadar, girdiği tüm **pozitif sayıları toplayan** bir C programı yazınız.  
Kullanıcı **-1** girdiğinde döngü sonlanmalı ve o ana kadar girilen sayıların toplamı ekrana yazdırılmalıdır.  
Bu işlemi **while döngüsü** kullanarak yapınız.
```c
#include <stdio.h>

int main() {
    int number, sum = 0;

    printf("Pozitif sayilar girin (-1 ile bitir): ");

    scanf("%d", &number);
    while (number != -1) {
        if (number > 0)
            sum += number;

        scanf("%d", &number);
    }

    printf("Girilen pozitif sayilarin toplami: %d\n", sum);

    return 0;
}

```

---


### **Orta**

**1. SORU** 
Kullanıcıya bir **menü** gösteren (örneğin:  
1 - Toplama  
2 - Çıkarma  
3 - Çıkış)  
ve kullanıcı **geçerli bir seçenek (1, 2 veya 3)** girene kadar menüyü tekrar tekrar gösteren bir program parçasını **do-while döngüsü** kullanarak yazınız.  
(*Menü seçiminden sonra programın toplama veya çıkarma yapmasına gerek yok.*)
```c
#include <stdio.h>

int main() {
    int secim;

    do {
        printf("\n--- MENU ---\n");
        printf("1 - Toplama\n");
        printf("2 - Cikarma\n");
        printf("3 - Cikis\n");
        printf("Secim yapiniz: ");
        scanf("%d", &secim);
    } while (secim < 1 || secim > 3);

    printf("Gecerli secim yaptiniz: %d\n", secim);

    return 0;
}

```

**2. SORU**  
Standart **Floyd Üçgeni**’ni (1’den başlayarak sıralı artan sayılarla oluşan üçgen) ekrana yazdıran, ancak **her satırın sonuna o satırdaki sayıların toplamını da ekleyen** bir C programı yazınız.
```c
#include <stdio.h>

int main() {
    int satir, sayi = 1;

    printf("Kac satirlik Floyd Ucgeni olsun? ");
    scanf("%d", &satir);

    for (int i = 1; i <= satir; i++) {
        int satirToplam = 0;

        for (int j = 1; j <= i; j++) {
            printf("%d ", sayi);
            satirToplam += sayi;
            sayi++;
        }

        printf(" | Toplam = %d", satirToplam);
        printf("\n");
    }

    return 0;
}

```

---


### **Zor (Advanced)**

**1. SORU**  
Kullanıcıdan **pozitif bir tam sayı** alan ve bu sayıyı **ters çevirerek ekrana yazdıran** bir C programı yazınız.
```c
#include <stdio.h>

int main() {
    int num, reverse = 0;

    printf("Pozitif bir tam sayi girin: ");
    scanf("%d", &num);

    while (num > 0) {
        reverse = reverse * 10 + (num % 10);
        num /= 10;
    }

    printf("Ters cevrilmis hali: %d\n", reverse);

    return 0;
}

```

---
