# TypeScript Nedir?

## TypeSript'e Giriş

Typescript, Javascript'in üst kümesidir ve javascript'in üzerine kuruludur. Yani Javascript olmadan Typescript düşünülemez.

Typescript kodunuzu yazdıktan sonra kodunuzu Typescript compiler ile javascript koduna çevirirsiniz.

Nihayetinde her zaman elinizde bir javascript kodunuz olur ve bunu istediğiniz yere deploy edip kullanabilirsiniz.

Typescript dosyaları javascript'in aksine `.js` yerine `.ts` uzantısını kullanır.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/what-is-typescript-compiler.png)

Typescript, Javascript'in syntax'ını kullanır buna ek olarakda Tipleri destekler. 

Eğer javascript kodunuzda bir syntax hatanız yoksa, typescript'de de hatanız yok demektir. Bu da tüm javascript kodlarının aslında typescript kodu olduğu anlamına gelir.

Aşağıdaki diyagram javascript ve typescript arasındaki ilişkiyi göstermektedir.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/what-is-typescript-typescript-and-js.png)

##  Neden TypeScript

TypeScript'in asıl amacı:
- JavaScript'de tip tanımları yapmak
- Mevcut JavaScript'in yanında ECMAScript Next veya ES Next olarak da bilinen gelecekteki JavaScript'in planlanan özelliklerini uygulamak

### 1) TypeScript hataların önlenmesine yardımcı olurken üretkenliğinizi artırır

Tipler hatalarla boğuşmanızı engellerken üretkenliğinizi artırır. Tipleri kullanarak, hataları run-time yerine compile-time'da yakalayabilirsiniz.

Aşağıdaki fonksiyon `x` ve `y` değerlerini alıp toplayarak geriye döndürür.

```js
function add(x, y) {
   return x + y;
}
```

Eğer bu değerleri bir HTML etiketinden alıp fonksiyona parametre olarak geçerseniz, istemediğiniz bir sonuç alabilirsiniz.

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

TypeScript compiler'ı javascript'e çevirirken hata verecektir. Böylece runtime'da hata almayı önlemiş olursunuz.

### 2) TypeScript Gelecek JavaScript'i Bugüne Getirir

TypeScript JavaScript'e gelecek olan yeni özellikleri şimdiden destekler. Bu da yeni özelliklerin tarayıcılar (ya da diğer ortamlar) tarafından tamamen desteklenmese bile kullanabileceğiniz anlamına gelir.

Her yıl, TC39 ECMAScript için yeni özellikler çıkarır, JavaScript'in standartlarını. Özellik teklifleri genelde 5 aşamada incelenir:

- Stage 0
- Stage 1 - Teklif
- Stage 2 - Taslak
- Stage 3 - Aday
- Stage 4 - Tamamlanmış

Ve TypeScript genelde 3. aşamadaki özellikleri destekler.
