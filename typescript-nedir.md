# TypeScript Nedir?

## TypeSript'e Giriş

TypeScript, JavaScript'in üst kümesidir. _(super set)_ 

> **Super Set:** Programlamada "super set", bir veri tipinin veya bir sınıfın başka bir veri tipinin veya sınıfın tüm özelliklerini içerdiği anlamında kullanılır. Yani, bir veri tipi veya sınıf "super set" olarak tanımlanabilirse, içindeki tüm elemanlar başka bir veri tipinin veya sınıfın elemanlarını da içermelidir. Örneğin, bir dizi veri tipi "super set" olarak tanımlanabilirse, içindeki tüm elemanlar başka bir dizi veri tipinin elemanlarını da içermelidir. [ChatGPT]

TypeScript: tip güvenli TypeScript kodunun yazıldıktan sonra compiler vasıtası ile tarayıcılarımızın içerisinde çalışabilecek JavaScript koduna çevrilmesi ile çalışan bir yapıya sahiptir.

Kısacası: Yazdığınız TypeScript kodu tarayıcı içerisinde çalışmaz. TypeScript tip güvenliği ve diğer geniş özellikleri ile genişletebildiğimiz JavaScript kodları yazmanızda bir arayüz işlevi görür. 

Nihayetinde her zaman elinizde bir JavaScript kodunuz olur ve bunu istediğiniz yere deploy edip kullanabilirsiniz.

TypeScript dosyaları JavaScript'in aksine `.js` yerine `.ts` uzantısını kullanır.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/what-is-typescript-compiler.png)

TypeScript, JavaScript'in syntax'ını kullanır buna ek olarakda Tipleri destekler. 

Eğer JavaScript kodunuzda bir syntax hatanız yoksa, TypeScript'de de hatanız yok demektir. Bu da tüm JavaScript kodlarının aslında TypeScript kodu olduğu anlamına gelir.

Aşağıdaki diyagram JavaScript ve TypeScript arasındaki ilişkiyi göstermektedir.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/what-is-typescript-typescript-and-js.png)

##  Neden TypeScript

TypeScript'in asıl amacı:
- JavaScript'de tip tanımları yapmak
- Mevcut JavaScript'in yanında ECMAScript Next veya ES Next olarak da bilinen gelecekteki JavaScript'in planlanan özelliklerini kullanmaktır.

### 1) TypeScript JavaScript kodu içerisinde oluşabilecek potansiyel tip hatalarının önlenmesine yardımcı olurken üretkenliğinizi de artırır.

TypeScript'in sunduğu tipler oluşabilecek hatalarla boğuşmanızı engellerken üretkenliğinizi de artırır. Tipleri kullanarak, hataları run-time yerine compile-time'da yakalayabilirsiniz.

Aşağıdaki fonksiyon `x` ve `y` değerlerini alıp toplayarak geriye döndürür.

```js
function add(x, y) {
   return x + y;
}
```

Eğer bu değerleri bir HTML etiketinden alıp fonksiyona parametre olarak geçerseniz, parametre olarak girdiğiniz değerlerin tipleri kontrol edilmediği için istemediğiniz bir sonuç alabilirsiniz.

```js
let result = add(input1.value, input2.value);
console.log(result); // iki stringi birleştiren bir sonuç alırsınız
```

Örneğin, kullanıcı `10` ve `20` değerlerini girdiğinde ve fonksiyon çalıştığında `30` yerine `1020` gibi bir sonuç alırsınız.

Bunun sebebi `input1.value` ve `input2.value` değerleri sayı yerine string'dir. Ve `+` operatörünü kullandığınızda eğer sayı yerine string varsa bunları toplamak yerine birleştirecektir.

TypeScript'i kullanarak tip dayatması yaptığınızda:

```js
function add(x: number, y: number) {
   return x + y;
}
```

Yukarıdaki fonksiyonda parametrelere `number` tipini ekledik. Artık `add()` fonksiyonu sadece `number` tipini kabul edecek, diğer bütün tipler reddedilecek.

Aşağıdaki gibi fonksiyonu çağırırsanız:

```js
let result = add(input1.value, input2.value);
```

TypeScript compiler'ı JavaScript'e çevirirken hata verecektir. Böylece runtime'da hata almayı önlemiş olursunuz.

### 2) TypeScript Gelecek JavaScript'i Bugüne Getirir

TypeScript JavaScript'e gelecek olan yeni özellikleri şimdiden destekler. Bu da yeni özelliklerin tarayıcılar (ya da diğer ortamlar) tarafından tamamen desteklenmese bile kullanabileceğiniz anlamına gelir.

Her yıl, TC39 ECMAScript için yeni özellikler çıkarır, JavaScript'in standartlarını. Özellik teklifleri genelde 5 aşamada incelenir:

- Stage 0
- Stage 1 - Teklif
- Stage 2 - Taslak
- Stage 3 - Aday
- Stage 4 - Tamamlanmış

Ve TypeScript genelde 3. aşamadaki özellikleri destekler.

----

| Sonraki Bölüm  👉 |
| ------------- |
| [TypeScript Kurulumu](./typescript-kurulumu.md) |
