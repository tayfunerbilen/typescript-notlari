# TypeScript Object Tipi

TypeScript'de obje tipi primitive olmayan bütün tipleri temsil eder.

Primitive veri türleri şunlardı:

- number
- bigint
- string
- boolean
- null
- undefined
- symbol

Aşağıda örnek bir objenin nasıl tanımlanacağını göstermektedir:

```ts
let employee: object;

employee = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};

console.log(employee);
```

eğer `employee` değişkenine primitive bir değer atamaya çalışırsanız:

```ts
employee = "Jane";
```

şöyle bir hata alırsınız:

```
error TS2322: Type '"Jane"' is not assignable to type 'object'.
```

Eğer objede olmayan bir özelliğe erişmeye çalışırsanız:

```ts
console.log(employee.hireDate);
```

Yine şöyle bir hata alırsınız:

```
error TS2339: Property 'hireDate' does not exist on type 'object'.
```

> JavaScript'de yukarıdaki örneklerin hata vermeden çalıştığını ve `undefined` döndürdüğünü unutmayın :)

Bir objeye spesifik olarakda hangi değerlerin geleceğini belirleyebilirsiniz.

```ts
let employee: {
    firstName: string;
    lastName: string;
    age: number;
    jobTitle: string;
};
```

Ve şu şekilde değer atayabilirsiniz:

```ts
employee = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};
```

Ya da yukarıdaki iki ifadeyi şöyle de tanımlayabilirsiniz:

```ts
let employee: {
    firstName: string;
    lastName: string;
    age: number;
    jobTitle: string;
} = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    jobTitle: 'Web Developer'
};
```

## object vs. Object

TypeScript'de `Object` ya da `{}` adında başka bir tip daha mevcut. Baş harfi büyük, bunu `object` tipiyle karıştırmayın.

`object` tipi tüm primitive olmayan değerleri temsil eder. `Object` ise objelerin fonksiyonelliğini tanımlar.

- `{}` ya da `Object` en az spesifik olanıdır. Nesne, dizi ve primitive veri tiplerini atayabilirsiniz.

```ts
var p: {}; // or Object
p = { prop: 0 }; // OK
p = []; // OK
p = 42; // OK
p = "string"; // OK
p = false; // OK
p = null; // Error
p = undefined; // Error
```

- `object` biraz daha spesifik olanıdır. Nesne ve dizi hariç diğer tipleri tanımlayamazsınız.

```ts
var o: object;
o = { prop: 0 }; // OK
o = []; // OK
o = 42; // Error
o = "string"; // Error
o = false; // Error
o = null; // Error
o = undefined; // Error
```

## `{}` Boş Tip

TypeScript, boş tip olarak adlandırılan ve {} ile gösterilen, nesne tipine oldukça benzeyen başka bir tipe sahiptir.

Boş tip {}, kendi başına hiçbir özelliği olmayan bir nesneyi tanımlar. Böyle bir nesnedeki bir özelliğe erişmeye çalışırsanız, TypeScript compile hatası verir:

```ts
let vacant: {};
vacant.firstName = 'John';
```

hata:

```
error TS2339: Property 'firstName' does not exist on type '{}'.
```

## Özet

- TypeScript'de `object` tipi primitive olmayan tüm tipleri için geçerlidir.
- `Object` tipi tüm nesne metod ve özelliklerini kapsar.
- `{}` hiç özelliği olmayan bir nesneyi temsil eder.
