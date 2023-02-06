# Neden TypeScript

**Özet:** Bu bölümde dinamik veri türleri tarafından oluşabilecek hataları önlemek için neden JavaScript yerine TypeScript kullanmanız gerektiğini öğreneceksiniz.

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

## Dinamik Tiplerde Problem

Parametre olarak girilen id'ye göre ürün objesi döndüren bir fonksiyonunuz olduğunu farz edin.

```js
function getProduct(id){
  return {
    id: id,
    name: `Awesome Gadget ${id}`,
    price: 99.5
  }
}
```

