## **Başlangıç**

### **1. SORU**
Kendisine gönderilen adet kadar int sayının toplamını hesaplayan
esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
int toplam(int adet, ...);
```

**Örnek kullanım:**
```c
toplam(3, 5, 10, 15); // 30
```
**Çözüm:**
```c
#include <stdarg.h>

int toplam(int adet, ...)
{
    va_list args;
    va_start(args, adet);

    int sum = 0;
    for (int i = 0; i < adet; i++)
        sum += va_arg(args, int);

    va_end(args);
    return sum;
}
```

### **2. SORU**  
Kendisine gönderilen sayıların ortalamasını döndüren esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
double ortalama(int adet, ...);
```
📌 Bölme işlemi sırasında double tür dönüşümüne dikkat ediniz.

**Çözüm:**
```c
#include <stdarg.h>

double ortalama(int adet, ...)
{
    va_list args;
    va_start(args, adet);

    int toplam = 0;
    for (int i = 0; i < adet; i++)
        toplam += va_arg(args, int);

    va_end(args);
    return (double)toplam / adet;
}
```


## **Orta**

### **1. SORU**  
Kendisine gönderilen sayılar arasındaki en büyük (max) ve
en küçük (min) değeri bulan iki ayrı esnek argümanlı fonksiyon yazınız.

**Fonksiyon prototipleri:**
```c
int maxBul(int adet, ...);
int minBul(int adet, ...);
```c

**Örnek:**
```c
maxBul(5, 3, 7, 2, 9, 4); // 9
minBul(5, 3, 7, 2, 9, 4); // 2
```
**Çözüm:**
```c
#include <stdarg.h>

int maxBul(int adet, ...)
{
    va_list args;
    va_start(args, adet);

    int max = va_arg(args, int);
    for (int i = 1; i < adet; i++)
    {
        int x = va_arg(args, int);
        if (x > max) max = x;
    }

    va_end(args);
    return max;
}

int minBul(int adet, ...)
{
    va_list args;
    va_start(args, adet);

    int min = va_arg(args, int);
    for (int i = 1; i < adet; i++)
    {
        int x = va_arg(args, int);
        if (x < min) min = x;
    }

    va_end(args);
    return min;
}
```

### **2. SORU**  
İlk parametre olarak bir karakter türü alan (`'i'` → int, `'f'` → double)
ve bu türe göre **tek bir değeri** ekrana yazdıran esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
void yazdir(char tur, ...);
```

**Örnek kullanım:**
```c
yazdir('i', 10);     // Int: 10
yazdir('f', 3.14);   // Float: 3.14
```

📌 `va_arg` kullanırken doğru türü seçtiğinizden emin olunuz.
**Çözüm:**
```c
#include <stdio.h>
#include <stdarg.h>

void yazdir(char tur, ...)
{
    va_list args;
    va_start(args, tur);

    if (tur == 'i')
        printf("Int: %d\n", va_arg(args, int));
    else if (tur == 'f')
        printf("Float: %.2f\n", va_arg(args, double));

    va_end(args);
}
```


## **Zor (Advanced)**

### **1. SORU**  
Basit bir **log fonksiyonu** yazınız.
Fonksiyon, ilk parametre olarak bir **format string**, devamında esnek argümanlar almalıdır.

**Fonksiyon prototipi:**
```c
void logla(const char *format, ...);
```

**Örnek kullanım:**
```c
logla("Sayi: %d, Metin: %s", 10, "Deneme");
```

📌 İpucu:
- `printf` benzeri çalışması beklenmektedir
- `stdarg.h` zorunludur
**Çözüm:**
```c
#include <stdio.h>
#include <stdarg.h>

void logla(const char *format, ...)
{
    va_list args;
    va_start(args, format);

    vprintf(format, args);
    printf("\n");

    va_end(args);
}
```

