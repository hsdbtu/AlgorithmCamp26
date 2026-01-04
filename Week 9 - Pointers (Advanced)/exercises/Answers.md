## **Başlangıç**

### **1. SORU**

Kendisine bir `int` dizisi ve boyutu verilen,
pointer aritmetiği kullanarak dizinin tüm elemanlarını
ekrana yazdıran bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
void diziYazdir(int *p, int boyut);
```

**Örnek kullanım:**

```c
int dizi[] = {1, 2, 3, 4};
diziYazdir(dizi, 4);
// Çıktı: 1 2 3 4
```

📌 Dizi elemanlarına **index (`[]`) kullanmadan**, sadece pointer aritmetiği ile erişiniz.

---
**Çözüm:**
```c
void diziYazdir(int *p, int boyut) {
    for(int i = 0; i < boyut; i++) {
        printf("%d ", *(p + i));
    }
}

```


### **2. SORU**

Bir string’in (`char` dizisi) uzunluğunu,
pointer kullanarak hesaplayan bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
int stringUzunluk(char *p);
```

**Örnek kullanım:**

```c
char str[] = "C Dili";
printf("%d", stringUzunluk(str)); // 6
```

📌 `strlen` kullanmayınız.

---
**Çözüm:**
```c
int stringUzunluk(char *p) {
    int sayac = 0;
    while(*p != '\0') {
        sayac++;
        p++;
    }
    return sayac;
}

```


## **Orta**

### **1. SORU**

Kendisine bir `int` dizisi ve boyutu gönderilen,
pointer kullanarak dizinin **en küçük elemanını** bulan
bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
int minDeger(int *dizi, int boyut);
```

**Örnek kullanım:**

```c
int dizi[] = {5, 2, 8, 1, 4};
printf("%d", minDeger(dizi, 5)); // 1
```

📌 Dizi elemanlarına `*(dizi + i)` şeklinde erişiniz.

---
**Çözüm:**
```c
int minDeger(int *dizi, int boyut) {
    int min = *dizi;

    for(int i = 1; i < boyut; i++) {
        if(*(dizi + i) < min) {
            min = *(dizi + i);
        }
    }
    return min;
}

```


### **2. SORU**

Bir string’i pointer kullanarak **tersine çeviren**
bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
void stringTersCevir(char *p);
```

**Örnek kullanım:**

```c
char str[] = "Pointer";
stringTersCevir(str);
printf("%s", str); // retnioP
```

📌 Ek dizi kullanmayınız, işlemi **yerinde (in-place)** yapınız.

---
**Çözüm:**
```c
void stringTersCevir(char *p) {
    char *bas = p;
    char *son = p;

    while(*son != '\0') {
        son++;
    }
    son--;

    while(bas < son) {
        char temp = *bas;
        *bas = *son;
        *son = temp;

        bas++;
        son--;
    }
}

```


## **Zor (Advanced)**

### **1. SORU**

Bir fonksiyon yazınız:

* Kendisine bir `int` dizisi ve boyutu verilecek
* Dizinin **en büyük elemanının adresini** pointer olarak döndürecek

**Fonksiyon prototipi:**

```c
int* maxAdres(int *dizi, int boyut);
```

**Örnek kullanım:**

```c
int dizi[] = {4, 9, 1, 7, 3};
int *p = maxAdres(dizi, 5);

printf("%d", *p); // 9
```

📌 Fonksiyon **değer değil, adres** döndürmelidir.
📌 Pointer aritmetiği kullanımı zorunludur.

---
**Çözüm:**
```c
int* maxAdres(int *dizi, int boyut) {
    int *max = dizi;

    for(int i = 1; i < boyut; i++) {
        if(*(dizi + i) > *max) {
            max = dizi + i;
        }
    }
    return max;
}

```