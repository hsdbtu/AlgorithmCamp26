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
