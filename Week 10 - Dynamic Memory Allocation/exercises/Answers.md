## **Başlangıç**

### **1. SORU**

Kullanıcıdan bir `n` değeri alan ve
`malloc` kullanarak `n` elemanlı bir `int` dizisi oluşturan,
elemanlarını kullanıcıdan alan ve ekrana yazdıran programı yazınız.

📌 Bellek ayırma başarısızlığı kontrol edilmelidir.  
📌 Program sonunda bellek serbest bırakılmalıdır.

Çözüm:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;
    printf("Eleman sayisini giriniz: ");
    scanf("%d", &n);

    int *dizi = (int*) malloc(n * sizeof(int));

    if(dizi == NULL) {
        printf("Bellek ayrilamadi!\n");
        return 1;
    }

    for(int i = 0; i < n; i++) {
        printf("%d. eleman: ", i + 1);
        scanf("%d", &dizi[i]);
    }

    printf("Dizi elemanlari:\n");
    for(int i = 0; i < n; i++) {
        printf("%d ", dizi[i]);
    }

    free(dizi);
    dizi = NULL;

    return 0;
}

```
---


## **Orta**

### **1. SORU**

Kendisine boyut bilgisi verilen,
`calloc` kullanarak dinamik bir dizi oluşturan
ve dizinin tüm elemanlarının başlangıçta **0 olduğunu**
gösteren bir program yazınız.

📌 `malloc` kullanmayınız.

Çözüm:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;
    printf("Dizi boyutunu giriniz: ");
    scanf("%d", &n);

    int *dizi = (int*) calloc(n, sizeof(int));

    if(dizi == NULL) {
        printf("Bellek ayrilamadi!\n");
        return 1;
    }

    for(int i = 0; i < n; i++) {
        printf("%d ", dizi[i]);
    }

    free(dizi);
    dizi = NULL;

    return 0;
}

```
---

### **2. SORU**

Bir dinamik `int` dizisini:

* İlk başta 3 elemanlı oluşturunuz
* `realloc` kullanarak boyutunu 6’ya çıkarınız
* Yeni elemanlara değer atayınız
* Tüm diziyi ekrana yazdırınız

📌 Eski verilerin korunup korunmadığını gözlemleyiniz.

Çözüm:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *dizi = (int*) malloc(3 * sizeof(int));

    if(dizi == NULL) {
        printf("Bellek ayrilamadi!\n");
        return 1;
    }

    for(int i = 0; i < 3; i++) {
        dizi[i] = i + 1;
    }

    int *temp = (int*) realloc(dizi, 6 * sizeof(int));

    if(temp == NULL) {
        printf("Yeniden boyutlandirma basarisiz!\n");
        free(dizi);
        return 1;
    }

    dizi = temp;

    for(int i = 3; i < 6; i++) {
        dizi[i] = (i + 1) * 10;
    }

    for(int i = 0; i < 6; i++) {
        printf("%d ", dizi[i]);
    }

    free(dizi);
    dizi = NULL;

    return 0;
}

```
---


## **Zor**

### **1. SORU**

Bir fonksiyon yazınız:

* Parametre olarak `int **p` ve `int n` alsın
* `n` elemanlı dinamik dizi oluştursun
* Diziyi 1’den `n`’e kadar sayılarla doldursun

📌 Fonksiyon içinde `malloc` kullanılmalıdır.

Çözüm:
```c
#include <stdio.h>
#include <stdlib.h>

void diziOlustur(int **p, int n) {
    *p = (int*) malloc(n * sizeof(int));

    if(*p == NULL) {
        return;
    }

    for(int i = 0; i < n; i++) {
        (*p)[i] = i + 1;
    }
}

int main() {
    int *dizi;
    int n = 5;

    diziOlustur(&dizi, n);

    if(dizi == NULL) {
        printf("Bellek ayrilamadi!\n");
        return 1;
    }

    for(int i = 0; i < n; i++) {
        printf("%d ", dizi[i]);
    }

    free(dizi);
    dizi = NULL;

    return 0;
}

```
---

### **2. SORU (Advanced)**

Kullanıcıdan girilen string uzunluğuna göre:

* Dinamik olarak string için bellek ayıran
* String’i kullanıcıdan alan
* String’i ekrana yazdıran
* Program sonunda belleği serbest bırakan

bir C programı yazınız.

📌 String literal **kullanılmayacaktır**.

Çözüm:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int uzunluk;
    printf("String uzunlugunu giriniz: ");
    scanf("%d", &uzunluk);

    char *str = (char*) malloc((uzunluk + 1) * sizeof(char));

    if(str == NULL) {
        printf("Bellek ayrilamadi!\n");
        return 1;
    }

    printf("String giriniz: ");
    scanf("%s", str);

    printf("Girilen string: %s\n", str);

    free(str);
    str = NULL;

    return 0;
}

```
---

