# TypeScript Tip Tanımı (Type Annotation)

Değişken, fonksiyon, nesne gibi tanımlayıcıların tiplerini açıkça belirtmek için tip tanımları yapılır. Şu ana kadar zaten nasıl yapıldığını gördünüz ama bu bölümde detaylı olarak bundan bahsedeceğiz.

### Ders Videosu
[![Videolu Ders](https://i.ytimg.com/vi/h_e8K5XDMd4/maxresdefault.jpg)](https://www.youtube.com/watch?v=h_e8K5XDMd4)

TypeScript'de tip tanımı yapmak için tanımlayıcıdan sonra `: type` syntax'ı kullanılır. Burada `type` değeri herhangi bir geçerli tip olabilir.

Bir kez tip tanımlandığında, sadece o tip değerlerle işlem yapılabilir. Eğer farklı tipte bir değer tanımı yapmaya çalışırsanız TypeScript Compiler hata verecektir.

## Değişkenlerde Tip Tanımı

Aşağıda değişken ve sabitlere nasıl tip tanımı yapılacağının örnekleri verilmiştir:

```ts
let variableName: type;
let variableName: type = value;
const constantName: type = value;
```

Tip tanımı değişken ya da sabit isminden hemen sonra `:` işareti ile belirtiliyor.

Örneğin `number` tip tanımı yapmak istersek:

```ts
let counter: number;
```

Artık `counter` değişkenine sadece sayısal değerler atanabilir.

```ts
counter = 1;
```

Örneğin `string` tipinde bir değer atamaya kalkarsak compiler hata verecektir.

```ts
let counter: number;
counter = 'Hello'; // compile hatası 
```

Hata da şöyle görünecek:

```
Type '"Hello"' is not assignable to type 'number'.
```

Hem tip tanımı yapıp hem de başlangıç değeri ile değişken tanımlamak için:

```ts
let counter: number = 1;
```

Diğer primitive tip tanımları ise şöyle:

```ts
let name: string = 'John';
let age: number = 25;
let active: boolean = true;
```

Yukarıdaki örneklerde `name` değişkeni sadece `string`, `age` değişkeni sadece `number` ve `active` değişkeni sadece `boolean` tipinde değer kabul eder.

## Diziler

Bir dizinin tip tanımını yapmak için `: type[]` şeklinde, köşeli parantez kullanarak yapabilirsiniz. 

```ts
let arrayName: type[];
```

Örneğin `string` değerlerinden oluşan bir `array` oluştıralım.

```ts
let names: string[] = ['John', 'Jane', 'Peter', 'David', 'Mary'];
```

## Objeler

Obje tipi tanımlamak için objeye değer atamak gibi benzer bir tanım yapıyoruz. Örneğin:

```ts
let person: {
   name: string;
   age: number
};

person = {
   name: 'John',
   age: 25
}; // geçerli
```

Yukarıdaki örnekte `person` değişkeni bir obje ve 2 özelliği kabul ediyor. Bunlar `name` ve `age` değerleri, bunlarda `string` ve `number` tiplerinde olmalı. Aksi durumda compiler hata verecektir.

## Fonksiyon Parametre ve Geri Dönüş Tipi

Aşağıdaki örnekte değişkene bir fonksiyon tanımlanmalı, gönderilen parametre string olmalı ve geriye string dönmeli.

```ts
let greeting : (name: string) => string;
```

yani yukarıdaki tanıma uygun bir atama şöyle olabilirdi:

```ts
greeting = function (name: string) {
    return `Hi ${name}`;
};
```

Eğer aşağıdaki gibi bir atama yapsaydık compiler hata verecekti, çünkü bizim tip tanımımıza uymayacaktı.

```ts
greeting = function () {
    console.log('Hello');
};
```

Hata:

```
Type '() => void' is not assignable to type '(name: string) => string'. Type 'void' is not assignable to type 'string'.
```

## Özet

- Değişken, fonksiyon, nesne gibi tanımlayıcıların tiplerini açıkça belirtmek için `: type` syntax'ını kullanın.
