### **Başlangıç**

1. Kullanıcıdan bir sayı alıp çift mi tek mi olduğunu yazdırın.
```c
#include <stdio.h>

int main() {
    int sayi;

    printf("Bir sayi girin: ");
    scanf("%d", &sayi);

    if (sayi % 2 == 0)
        printf("Sayi cift.\n");
    else
        printf("Sayi tek.\n");

    return 0;
}

```

2. Kullanıcıdan iki sayı alıp büyük olanı ekrana yazdırın.
```c
#include <stdio.h>

int main() {
    int a, b;

    printf("Iki sayi girin: ");
    scanf("%d %d", &a, &b);

    if (a > b)
        printf("Buyuk sayi: %d\n", a);
    else if (b > a)
        printf("Buyuk sayi: %d\n", b);
    else
        printf("Iki sayi esit.\n");

    return 0;
}

```


### **Orta**

1. Kullanıcıdan üç sayı alıp en büyüğünü bulun.
```c
#include <stdio.h>

int main() {
    int a, b, c;

    printf("Uc sayi girin: ");
    scanf("%d %d %d", &a, &b, &c);

    if (a >= b && a >= c)
        printf("En buyuk sayi: %d\n", a);
    else if (b >= a && b >= c)
        printf("En buyuk sayi: %d\n", b);
    else
        printf("En buyuk sayi: %d\n", c);

    return 0;
}

```

2. Girilen bir sayının **pozitif, negatif veya sıfır** olduğunu belirten program yazın.
```c
#include <stdio.h>

int main() {
    int sayi;

    printf("Bir sayi girin: ");
    scanf("%d", &sayi);

    if (sayi > 0)
        printf("Sayi pozitif.\n");
    else if (sayi < 0)
        printf("Sayi negatif.\n");
    else
        printf("Sayi sifir.\n");

    return 0;
}

```


### **Zor (Advanced)**

1. Kullanıcının notunu alıp aşağıdaki kurala göre \*\*harf notu\*\* yazdırın:  

&nbsp;  - 90 ve üzeri → \*\*A\*\*  

&nbsp;  - 80–89 → \*\*B\*\*  

&nbsp;  - 70–79 → \*\*C\*\*  

&nbsp;  - 60–69 → \*\*D\*\*  

&nbsp;  - 60’tan küçük → \*\*F\*\*
```c
#include <stdio.h>

int main() {
    int not;

    printf("Notunuzu girin: ");
    scanf("%d", &not);

    if (not >= 90)
        printf("Harf Notu: A\n");
    else if (not >= 80)
        printf("Harf Notu: B\n");
    else if (not >= 70)
        printf("Harf Notu: C\n");
    else if (not >= 60)
        printf("Harf Notu: D\n");
    else
        printf("Harf Notu: F\n");

    return 0;
}

```
