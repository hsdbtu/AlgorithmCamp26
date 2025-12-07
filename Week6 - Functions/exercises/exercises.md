## **Başlangıç**

### **1. SORU**
Bir fonksiyon yazın:
- Parametre olarak bir tam sayı alsın
- Bu sayıya 1 ekleyip sonucu döndürsün
Beklenen:
```c
int artir(int x);
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


## **Orta**

### **1. SORU**  
Aşağıdaki özelliklere sahip bir fonksiyon yazın:
- 3 adet int parametre alsın
- Ortalamayı float olarak döndürsün
Beklenen:
```c
float ortalama(int a, int b, int c);
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