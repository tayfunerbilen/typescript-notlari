# TypeScript Array Tipi

TypeScript'te dizi, sıralı bir değerler listesidir. Belirli tipte değerleri tutan bir diziyi oluşturmak için şöyle bir syntax kullanılır:

```ts
let arrayName: type[];
```

Örneğin `string` değerleri tutan bir dizi tanımlamak için:

```ts
let skills: string[];
```

Bir ve ya birden fazla değeri şöyle ekleyebilirdik:

```ts
skills[0] = "Problem Solving";
skills[1] = "Programming";
```

ya da `push()` metodunu kullanabilirdik:

```ts
skills.push('Software Design');
```

Aşağıdaki örnekte `string` değerler tutan bir dizi tanımıdır:

```ts
let skills = ['Problem Sovling','Software Design','Programming'];
```

Bu örnekte TypeScript tip çıkarımı yapacak ve `string` bir dizi olduğuna karar verecektir. Aşağıdaki kod ile yukarıdaki birebir aynıdır:

```ts
let skills: string[];
skills = ['Problem Sovling','Software Design','Programming'];
```

Bir kere özel bir tip ile dizi tanımlarsanız, TypeScript başka türde ekleme yaparken hata fırlatacaktır.

Örneğin aşağıdaki gibi bir ekleme yapmak hataya sebep verir:

```ts
skills.push(100);
```

hata:

```
Argument of type 'number' is not assignable to parameter of type 'string'.
```

Diziden bir eleman çıkardığınızda, TypeScript bu elemanın tipini tahmin edecektir. Örneğin:

```ts
let skill = skills[0];
console.log(typeof(skill));
```

çıktı:

```
string
```

## TypeScript Dizi Özellikleri ve Metodları

TypeScript dizileri, JavaScript'deki tüm özellik ve metodlara erişebilir. Örneğin bir dizinin uzunluğunu almak isteseydik:

```ts
let series = [1, 2, 3];
console.log(series.length); // 3
```

Ayrıca `forEach()`, `map()`, `reduce()` ve `filter()` gibi metodların tamamını da kullanabilirsiniz:

```ts
let series = [1, 2, 3];
let doubleIt = series.map(e => e * 2);
console.log(doubleIt);
```

## Farklı Tiplerde Değer Depomalak

Aşağıdaki örnek `string` ve `number` tipinde değerlerin olduğu bir diziyi temsil eder:

```ts
let scores = ['Programming', 5, 'Software Design', 4]; 
```

Bu senaryoda TypeScript tip çıkarımı yaparak `scores` dizisinin tipini `string | number` olarak belirleyecektir.

Yani aşağıdaki kullanım yukarıdaki ile aynıdır:

```ts
let scores : (string | number)[];
scores = ['Programming', 5, 'Software Design', 4];
```

## Özet

- TypeScript'te dizi, sıralı bir değerler listesidir. Farklı tipte değerler depolanabilir.
- Belirli tipte bir dizi tanımlamak için `let arr: type[]` syntax'ı kullanılır.
