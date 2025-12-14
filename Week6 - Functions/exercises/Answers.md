## **Başlangıç**

### **1. SORU**
Bir fonksiyon yazın:
- Parametre olarak bir tam sayı alsın
- Bu sayıya 1 ekleyip sonucu döndürsün
Beklenen:
```c
int artir(int x);
```

**Çözüm:**
```c
int artir(int x) {
    return x + 1;
}
```

### **2. SORU**  
Aşağıdaki özelliklere sahip bir fonksiyon yazın:
- Parametre almayacak
- Değer döndürmeyecek
- İçinde sadece “Merhaba!” yazdıracak
Beklenen:
```c
void selam();
```

**Çözüm:**
```c
#include <stdio.h>

void selam() {
    printf("Merhaba!\n");
}
```


## **Orta**

### **1. SORU**  
Aşağıdaki özelliklere sahip bir fonksiyon yazın:
- 3 adet int parametre alsın
- Ortalamayı float olarak döndürsün
Beklenen:
```c
float ortalama(int a, int b, int c);
```

**Çözüm:**
```c
float ortalama(int a, int b, int c) {
    return (a + b + c) / 3.0f;
}
```

### **2. SORU**  
Aşağıdaki özelliklere sahip bir fonksiyon yazın:
- Parametre olarak bir string alsın
- Kaç tane ' ' (boşluk) karakteri olduğunu döndürsün

**İpucu:**
- Karakter dizisini "str[i] != '\0'" ile döneceksiniz.

Beklenen:
```c
int boslukSayisi(char str[]);
```

**Çözüm:**
```c
int boslukSayisi(char str[]) {
    int sayac = 0;
    int i = 0;

    while (str[i] != '\0') {
        if (str[i] == ' ')
            sayac++;
        i++;
    }

    return sayac;
}
```


## **Zor (Advanced)**

### **1. SORU**  
Bir fonksiyon yazın:
- Parametre: int n
- Eğer n asal ise 1, değilse 0 döndürsün

**Koşullar:**
- 2’den küçük sayılar asal değildir
- 2’den n-1’e kadar tüm sayılarla mod kontrolü yapılabilir
- Performans için i*i <= n da kullanılabilir

Beklenen:
```c
int asalMi(int n);
```

**Çözüm:**
```c
int asalMi(int n) {
    if (n < 2)
        return 0;

    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return 0;
    }

    return 1;
}
```


