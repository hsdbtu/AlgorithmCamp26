## **Başlangıç**

### **1. SORU**

Kullanıcıdan bir `n` değeri alan ve
`malloc` kullanarak `n` elemanlı bir `int` dizisi oluşturan,
elemanlarını kullanıcıdan alan ve ekrana yazdıran programı yazınız.

📌 Bellek ayırma başarısızlığı kontrol edilmelidir.
📌 Program sonunda bellek serbest bırakılmalıdır.

---


## **Orta**

### **1. SORU**

Kendisine boyut bilgisi verilen,
`calloc` kullanarak dinamik bir dizi oluşturan
ve dizinin tüm elemanlarının başlangıçta **0 olduğunu**
gösteren bir program yazınız.

📌 `malloc` kullanmayınız.

---

### **2. SORU**

Bir dinamik `int` dizisini:

* İlk başta 3 elemanlı oluşturunuz
* `realloc` kullanarak boyutunu 6’ya çıkarınız
* Yeni elemanlara değer atayınız
* Tüm diziyi ekrana yazdırınız

📌 Eski verilerin korunup korunmadığını gözlemleyiniz.

---


## **Zor**

### **1. SORU**

Bir fonksiyon yazınız:

* Parametre olarak `int **p` ve `int n` alsın
* `n` elemanlı dinamik dizi oluştursun
* Diziyi 1’den `n`’e kadar sayılarla doldursun

📌 Fonksiyon içinde `malloc` kullanılmalıdır.

---

### **2. SORU (Advanced)**

Kullanıcıdan girilen string uzunluğuna göre:

* Dinamik olarak string için bellek ayıran
* String’i kullanıcıdan alan
* String’i ekrana yazdıran
* Program sonunda belleği serbest bırakan

bir C programı yazınız.

📌 String literal **kullanılmayacaktır**.

---

