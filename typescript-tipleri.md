# TypeScript Tipleri

**Özet:** Bu bölümde TypeScript tiplerini ve kullanım amaçlarını öğreneceksiniz.

### Ders Videosu
[![Videolu Ders](https://i.ytimg.com/vi/3FwPXbi6chQ/maxresdefault.jpg)](https://www.youtube.com/watch?v=3FwPXbi6chQ)

## TypeScript'de Tip Nedir?

TypeScript'de tip, bir değerin sahip olduğu farklı özellik ve metodlara başvurmanın doğru bir yoludur.

Değer, bir değişkene atanabilen herhangi bir şey olabilir. Örn: number, string, array, object, function.

Örneğe bakalım:

```ts
'Hello'
```

Değere baktığınızda, bunun bir string olduğunu söyleyebilirsiniz. Ve bu değer `string` in sahip olduğu özellik ve metodlara sahiptir.

Örneğin, `Hello` değeri karakter uzunluğunu döndüren `length` özelliğine sahiptir. 

```ts
console.log('Hello'.length); // 5
```

Aynı zamanda `match()`, `indexOf()` ve `toLocaleUpperCase()` gibi bir çok metoda da sahiptir.

```ts
console.log('Hello'.toLocaleUpperCase()); // HELLO 
```

Eğer `Hello` değerine bakarak aldığı özellik ve metodlara göre tahmin etmeye çalışırsanız bu doğru bir yöntem olmayacaktır.

Bir değerin neyi temsil ettiğini anlamanın en kısa yolu ona bir tip tanımlamaktır. Bu örnekte `Hello` string'dir. O halde hangi özellik ve metodları kullanacağını da biliyorsun.

Özetle, TypeScript'de:

- Tip, bir değerin sahip olabileceği özellik ve metodları tanımlayan bir tanımdır
- Her değerin bir tipi vardır.

## TypeScript'de Tipler

TypeScript, JavaScript'de olan tipleri miras alır. TypeScript tipleri şu şekilde kategorize edilir:

- Primitive tipler (İlkel)
- Object tipler (Nesne, Obje)

### Primitive Tipler

| Ad | Açıklama |
| -- | -- |
| string | Yazılar |
| number | Sayısal değerler |
| boolean | `true` ya da `false` değerleri |
| null | `null` değeri |
| undefined | `undefined` değeri - varsayılan olarak tanımlanan değişene değer atanmaz ise değeri `undefined` olur |
| symbol | Benzersiz bir sabit değer |

### Object Tipleri

Object tipleri fonksiyonlar, diziler, sınıflar vb. olabilir. Daha sonra, özel object tipleri oluşturmayı öğreneceğiz.

## TypeScript'de Tiplerin Amacı

İki ana amaç vardır:

- Tipler, kodlarınızı analiz edip hatalarını bulmak için TypeScript Compiler tarafından kullanılır
- Tipler, atanan değerlerin değişkenlerle olan ilişkisini daha kolay anlamanızı sağlar.

## TypeScript Tip Örnekleri

Aşağıdaki örnek `h1` etiketini seçmek için `querySelector()` metodunu kullanıyor.

```js
const heading = document.querySelector('h1');
```

TypeScript compiler'ı `heading` değişkeninin bir `HTMLHeadingElement` tipinde olduğunu biliyor.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/TypeScript-types-example-1.png)

Ve `HTMLHeadingElement` tipine ait kullanabileceği özellik ve metodları listeliyor.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/TypeScript-types-properties-and-methods.png)

Eğer olmayan bir özellik ya da metoda erişmeye çalışırsanız, TypeScript compiler'ı hatayı gösterceektir.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/09/TypeScript-types-error.png)

## Özet

- Typescript'de her değerin bir tipi vardır.
- Tip, bir değerin sahip olabileceği özellik ve metodları tanımlayan bir tanımdır
- TypeScript Compiler, tipleri kodlarınızı analiz etmek ve hataları bulmak için kullanır.
