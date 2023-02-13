# Neden TypeScript

**Özet:** Bu bölümde dinamik veri türleri tarafından oluşabilecek hataları önlemek için neden JavaScript yerine TypeScript kullanmanız gerektiğini öğreneceksiniz.

### Ders Videosu
[![Videolu Ders](https://i.ytimg.com/vi/ihwXELzUIkg/maxresdefault.jpg)](https://www.youtube.com/watch?v=ihwXELzUIkg)

## Neden TypeScript Kullanmalıyız

TypeScript kullanmanın iki temel sebebi vardır:
- TypeScript tip sistemi ekleyerek, dinamik tiplerde oluşabilecek hatalardan kaçınmanızı sağlar.
- TypeScript, gelmesi planlanan JavaScript özelliklerini daha erken kullanmanızı sağlar.

Bu bölüm, ilk sebebe odaklanacağız.

## JavaScript'de Dinamik Tipleri Anlamak

JavaScript, dinamik olarak yazılır. Java ve C# gibi static yazılan dillerin aksine, değişkenlerin tipleri değerlerine göre belirlenir. Örneğin:

```js
"Hello"
```

Değerden bunun `string` olduğunu anlayabilirsiniz. Ayrıca şu ise bir sayıdır:

```js
2023
```

Diğer örneklere bakalım:

```js
let box;
box = "hello";
box = 100;
```

`box` değişkeninin tipi, atanan değerlerin türüne göre değişiyor.

runtime'da `box` değişkenin tipini bulmak için `typeof` kullanabilirsiniz.

```js
let box;
console.log(typeof(box)); // undefined

box = "Hello";
console.log(typeof(box)); // string

box = 100;
console.log(typeof(box)); // number
```

Yukarıdaki örnekte, ilk ifade bir değer atamadan değişken tanımlamak. Bunun tipi `undefined`

Daha sonra, `box` değişkenine `Hello` değeri atayıp tip kontrolü yaptığımızda tipi `string` oldu.

Son olarak, `100` değerini atayıp tekrar tip kontrolü yaptığımızda ise tipi `number` oldu.

Gördüğünüz gibi, yeni bir değer atandıktan sonra değişkenin tipi değerin tipi neyse ona dönüşüyor.

Ve JavaScript'de tipi belirtmenize gerek yok, değerine göre tipi dinamik belirliyor.

Dinamik tipler esneklik kazandırır, ancak aynı zamanda problemleri de beraberinde getirir.

## Dinamik Tip Problemi

Parametre olarak girilen id'ye göre ürün objesi döndüren bir fonksiyonun olduğunu varsayalim.

```js
function getProduct(id){
  return {
    id: id,
    name: `Awesome Gadget ${id}`,
    price: 99.5
  }
}
```

Ve fonksiyona `1` değerini döndürerek bir değişkene aktaralım ve değerleri şöyle gösterelim:

```js
const product = getProduct(1);
console.log(`The product ${product.Name} costs $${product.price}`);
```

Çıktısı şöyle olurdu.

```
The product undefined costs $99.5 
```

Beklediğimiz şey bu değildi. 

Bu koddaki sorun `product` objesinde `Name` adında bir özelliğin bulunmaması. Aynı isimde tamamı küçük harften oluşan bir özelliğimiz var.

Ancak, bunu sadece çalıştırdığınız zaman bilebiliyorsunuz.

Objede var olmayan bir özelliği referans göstermek JavaScript'de yaygınca yapılan bir hatadır. 

Aşağıdaki örnek ise yeni bir fonksiyon tanımlayıp verilen bilgileri konsola çıktı olarak göstermeyi sağlar:

```js
const showProduct = (name, price)  => {
  console.log(`The product ${name} costs ${price}$.`);
};
```

Ve `getProduct()` ile `showProduct()` fonksiyonlarını bir arada şöyle kullanabiliriz:

```js
const product = getProduct(1);
showProduct(product.price, product.name);
```

Çıktı

```
The product 99.5 costs $Awesome Gadget 1 
```

Bu seferde paramatreleri yanlış sırayla belirttik. Bu da JavaScript'de yine yaygın olarak yapılan hatalardan biridir.

İşte bu yüzden TypeScript oyuna dahil oluyor.

## TypeScript Dinamik Tip Problemini Nasıl Çözüyor?

Bir objedeki olmayan özelliğe erişme problemini çözmek için şu adımları takip edebilirsiniz:

1. `interface` kullanarak `Product` objesinin biçimini oluşturun. Not: `interface` konusunu ileride detaylı olarak işleyeceğiz.

```ts
interface Product{
    id: number,
    name: string,
    price: number
};
```

2. `getProduct()` fonksiyonuna kesin olarak dönecek `Product` tipini belirtin.

```ts
function getProduct(id) : Product{
  return {
    id: id,
    name: `Awesome Gadget ${id}`,
    price: 99.5
  }
}
```

Artık olmayan bir özelliğe erişmek istediğinizde, kod editörü sizi anında uyaracak.

```ts
const product = getProduct(1);
console.log(`The product ${product.Name} costs $${product.price}`);
```

Kod editörü `Name` özelliğini vurgulayarak hata olduğunu gösterecektir.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/why-typescript-error.png)

Fareniz ile ilgili hatanın üstüne geldiğinizde ise hata detayını görebilirsiniz.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/why-typescript-hint.png)

Hatalı parametre geçme sorununu düzeltmek için ise, parametrelere kesin bir tip tanımlaması yapabilirsiniz.

```ts
const showProduct = (name: string, price:number)  => {
  console.log(`The product ${name} costs ${price}$.`);
};
```

Artık `showProduct()` fonksiyonuna hatalı bir tip gönderirseniz hata alacaksınız.

```ts
const product = getProduct(1);
showProduct(product.price, product.name);
```

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/why-typescript-error-in-function-arguments.png)

## Özet

- JavaScript dinamik tiptedir. Esneklik sağlarken aynı zamanda bir çok soruna sebep olabilir.
- TypeScript, JavaScript'e tipleri tanımlayarak bu sorunları çözmeni sağlar.
