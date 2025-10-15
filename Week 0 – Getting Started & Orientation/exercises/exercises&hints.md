## 3. Ödev

### **Başlangıç**

1. **Girilen iki sayı arasındaki tek sayıların toplamı**
    - Kullanıcıdan iki sayı al.
    - Aralarındaki tüm tek sayıları bul.
    - Bu sayıların toplamını ekrana yazdır.
    - İpucu
        
        Tek sayıları bulmak için mod alma (`%`) işlemini kullanabilirsiniz. Döngüyle tüm sayıları kontrol edin ve tek olanları toplama ekleyin.
        
2. **Girilen sayının faktöriyelini hesaplama**
    - Kullanıcıdan bir sayı al.
    - 1’den o sayıya kadar çarp.
    - Sonucu yazdır.
    - İpucu
        
        Döngü kullanarak çarpma işlemini tekrarlayın ve sonucu bir değişkende saklayın. Kümülatif bir çarpım yapmak daha işlevsel olacaktır. 
        
        Yani 4 girilmişse “2*3*4*5” yapmaktansa “2*3” sonucunu bir değişkende tutup sonrasında bu değişkeni 4 ile çarpıp değişkene tekrar atamak ve sonucu 5 ile çarpmak döngü kullanımı mantığını anlamanıza yardımcı olacaktır.
        

---

### **Orta**

1. **Girilen sayının asal olup olmadığını bulan algoritma**
    - İpucu
        
        Bir sayının asal olup olmadığını kontrol etmek için 2’den √N’e kadar olan sayılarla bölünüp bölünmediğini kontrol edebilirsiniz. Bölünebiliyorsa asal değildir.
        
2. **Mükemmel sayı bulma algoritması**
    - Bir sayının bölenlerinin toplamı sayının kendisine eşitse mükemmel sayıdır.
    - İpucu
        
        Döngü ve mod alma (`%`) burada çok işe yarar.
        

---

### **Zor (Advanced)**

1. **Palindrom sayı kontrolü**
    - Palindrom sayı soldan ve sağdan okunuşları aynı olan sayılara denir. 1001, 4224 gibi.
    - Girilen sayının palindrom olup olmadığını kontrol edin. Polindrom ise ekrana “N sayısı polindromdur”, değilse “N sayısı polindrom değildir” yazdırın.
    - İpucu 1
        
        Sayıyı basamaklarına ayırmak için mod 10 ve bölme işlemleri kullanabilirsiniz. Basamakları ters sırayla toplayarak yeni sayı oluşturun ve orijinal sayıyla karşılaştırın.
        
    - İpucu 2
        
        Son basamaktan kurtulmak için 10’a bölüp `int` tipine sahip değişkene atayabilirsiniz.