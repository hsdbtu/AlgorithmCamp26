## **Başlangıç**

### **1. SORU**

Bir `int` değişkenin adresini alan ve bu adresteki değeri
ekrana yazdıran bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
void yazdir(int *p);
```

**Örnek kullanım:**

```c
int x = 10;
yazdir(&x); // 10
```

---

### **2. SORU**

Bir `int` değişkenin değerini pointer kullanarak **1 artıran**
bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
void artir(int *x);
```

📌 Fonksiyon çağrısından sonra **orijinal değişkenin** değeri değişmelidir.

---


## **Orta**

### **1. SORU**

İki `int` değişkenin değerlerini pointer kullanarak
yer değiştiren (**swap**) bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
void swap(int *a, int *b);
```

**Örnek kullanım:**

```c
int x = 3, y = 7;
swap(&x, &y);
// x = 7, y = 3
```

---

### **2. SORU**

Kendisine bir `int` dizisi ve dizinin boyutu gönderilen,
pointer kullanarak dizinin elemanlarının **ortalamasını** hesaplayan
bir fonksiyon yazınız.

**Fonksiyon prototipi:**

```c
double diziOrtalama(int *dizi, int boyut);
```

📌 Dizi elemanlarına **pointer aritmetiği** ile erişiniz.

---


## **Zor (Advanced)**

### **1. SORU**

Bir fonksiyon yazınız:

* Kendisine bir `int` dizisi alacak
* Dizinin **en büyük elemanının adresini** geri döndürecek

**Fonksiyon prototipi:**

```c
int* maxAdres(int *dizi, int boyut);
```

**Örnek kullanım:**

```c
int dizi[] = {3, 7, 2, 9, 4};
int *p = maxAdres(dizi, 5);

printf("%d\n", *p); // 9
```

📌 Fonksiyon **değer değil, adres** döndürmelidir.


## **Opsiyonel**

C dilinde bir fonksiyon yazınız:

- Fonksiyon içerisinde `const int` türünde bir değişken tanımlayınız
- Bu değişkene bir başlangıç değeri atayınız
- Değişkenin adresini bir pointer’a atayınız
- Pointer kullanarak bu `const` değişkenin değerini değiştirmeye çalışınız
- Değiştirme öncesi ve sonrası değeri ekrana yazdırınız

**Not:** Bu kullanımın tanımsız davranış (undefined behavior) içerdiği bilinmektedir.