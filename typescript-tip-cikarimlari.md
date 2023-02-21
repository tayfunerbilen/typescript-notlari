# TypeScript Tip Çıkarımları

**Özet:** Bu bölümde TypeScript'de bir tip tanımlaması yapılmadığı durumunda, TypeScript'in tipler hakkında nasıl çıkarım yaptığını öğreneceğiz.

### Ders Videosu
[![Videolu Ders](https://i.ytimg.com/vi/n3DO6pI7ssk/maxresdefault.jpg)](https://www.youtube.com/watch?v=n3DO6pI7ssk)

## Basit Tip Çıkarımları

Bir değişken tanımladığınızda, tip tanımlarını kullanarak değişkenin tipini belirleyebilirsiniz.

```ts
let counter: number;
```

Eğer, `counter` değişkenini `0` değeriyle bir tip tanımı yapmadan oluştursanız TypeScript bunun `number` tipinde olduğunu bilecektir.

```ts
let counter = 0;
```

Aşağıdaki örnekle yukarıdaki örnek birbiriyle aynıdır:

```ts
let counter: number = 0;
```

Aynı şekilde, fonksiyonlarda varsayılan bir parametre değeri tanımımlarken tip belirlenmemişse, TypeScript bunun hangi tipte olduğunu bilecektir.

```ts
function setCounter(max = 100) {
    // ...
}
```

Yukarıdaki örnekte TypeScript `max` parametresinin `number` tipinde olduğunu bilecektir.

Benzer şekilde, TypeScript dönen değerinde tip çıkarımını yapabilir.

```ts
function increment(counter: number) {
    return counter++;
}
```

Yukarıdaki kod aşağıdaki kod ile aynıdır:

```ts
function increment(counter: number) : number {
    return counter++;
}
```

## En Yaygın Tip Algoritması

Aşağıdaki ifadeyi ele alalım.

```ts
let items = [1, 2, 3, null];
```

TypeScript, `items` dizisinin tip çıkarımını yaparken her bir dizi öğesini ele alır. 

En yaygın tip algoritması ile tüm öğeleri analiz ederek uygun olan tipi tespit eder.

Bu örnekte TypeScript `number[]` tipini belirleyecektir. Eğer bu diziye `string` bir ifade ekleseydik:

```ts
let items = [0, 1, null, 'Hi'];
```

TypeScript bu sefer `(number | string)[]` tipini kullanacaktı.

Eğer TypeScript en yaygın tipi bulamazsa, mevcut tipleri birleştirerek bir tip çıkarımı yapar. Örneğin:

```ts
let arr = [new Date(), new RegExp('\d+')];
```

Yukarıdaki örnekte tip çıkarımı `(RegExp | Date)[]` şeklinde olacaktır.

## Bağlamsal Yazma

TypeScript, tiplerini anlamak için değişkenlerin konumlarını kullanır. Bu mekanizma bağlamsal yazma olarak bilinir. Örneğin:

```ts
document.addEventListener('click', function (event) {
    console.log(event.button); // 
});
```

Bu örnekte TypeScript, `event` objesinin bir `MouseEvent` örneği olduğunu `click` olayından dolayı biliyor.

Eğer `click` yerine `scroll` olayına çevirseydik, TypeScript hata verecekti.

```ts
document.addEventListener('scroll', function (event) {
    console.log(event.button); // compiler hatası
});
```

Hata:

```
Property 'button' does not exist on type 'Event'.(2339)
```

TypeScript bu senaryoda `UIEvent` in bir parçası olduğunu ve `event` in `button` adında bir özelliğe erişemeyeceğini biliyor. 

| Tip Çıkarımı | Tip Tanımı |
| -- | -- |
| TypeScript tipi tahmin eder | Siz TypeScript'e tipi belirtirsiniz |

Peki, hangi durumda tip çıkarımı ya da tip tanımını kullanmalısınız?

Pratikte, mümkün olan her senaryoda tip çıkarımını kullanın. Tip tanımını ise şu durumlarda kullanabilirsiniz:

- Bir değişken tanımladığınızda ancak değerini sonradan atadığınız durumlarda
- Tip çıkarımı yapılamayacak olan değişkenlerde
- Bir fonksiyon geriye `any` tipinde değer döndürüyorsa ve siz bunu daha anlaşılır kılmak istiyorsanız

## Özet

- Tip Çıkarımları, bir değişken tanımladığınızda, parametreye vasayılan değer belirlediğinizde, fonsiyonda geriye bir değer dönerken uygulanır.
- TypeScript, en uygun tipi bulmak için en yaygın tip algoritmasını kullanarak çıkarım yapar.
- Ayrıca bağlamsal yazma ile değişkenlerin konumlarını kullanarak çıkarım yapar.
