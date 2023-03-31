# TypeScript Sınıfı

**Özet:** Bu bölümde TypeScript'de Sınıflar hakkında bilgi edineceksiniz.

JavaScript, Java ve C# gibi diğer programlama dilleri gibi bir sınıf kavramına sahip değildir. ES5'te, bir "sınıf" oluşturmak için bir yapıcı fonksiyon ve [prototip kalıtımı](https://www.javascripttutorial.net/javascript-prototypal-inheritance/) kullanabilirsiniz.

Örneğin, ssn, ad ve soyad olmak üzere üç özelliği olan bir `Person` sınıfı oluşturmak için aşağıdaki yapıcı fonksiyonu kullanırsınız:

```ts
function Person(ssn, firstName, lastName) {
    this.ssn = ssn;
    this.firstName = firstName;
    this.lastName = lastName;
}
```

Ardından, ad ve soyadı aşağıdaki gibi birleştirerek kişinin tam adını almak için bir prototip yöntemi tanımlayabilirsiniz:

```ts
Person.prototype.getFullName = function () {
    return `${this.firstName} ${this.lastName}`;
}
```

Ardından, yeni bir nesne oluşturarak `Person` "sınıfını" kullanabilirsiniz:

```ts
let person = new Person('171-28-0926','John','Doe');
console.log(person.getFullName());
```

Konsola aşağıdaki çıktıyı verir:

```
John Doe
```

ES6, yapıcı metod ve prototip kalıtım oluşturmak için basitçe **sözdizimsel şeker (syntactic sugar)** olan bir sınıf tanımlamanıza izin verdi:

> JavaScript sınıflarında "syntactic sugar", kodun okunabilirliğini ve yazılmasını kolaylaştırmak için kullanılan bir yapıdır. Yani, aslında yapılan şey aynı, ancak daha okunaklı bir yazım şekli kullanılarak daha anlaşılır hale getirilir.

```js
class Person {
    ssn;
    firstName;
    lastName;

    constructor(ssn, firstName, lastName) {
        this.ssn = ssn;
        this.firstName = firstName;
        this.lastName = lastName;
    }
}
```

Sınıf sözdiziminde, kurucu (constructor) açıkça tanımlanır ve sınıfın içine yerleştirilir. Aşağıdakiler `getFullName()` yöntemini ekler:

```ts
class Person {
    ssn;
    firstName;
    lastName;

    constructor(ssn, firstName, lastName) {
        this.ssn = ssn;
        this.firstName = firstName;
        this.lastName = lastName;
    }

    getFullName() {
        return `${this.firstName} ${this.lastName}`;
    }
}
```

`Person` sınıfını kullanmak `Person` kurucu (constructor) metoduyla aynıdır:

```ts
let person = new Person('171-28-0926','John','Doe');
console.log(person.getFullName());
```

TypeScript sınıfı, sınıfın özelliklerine ve yöntemlerine [tip ek açıklamaları](./typescript-tip-tanimi.md) ekler. Aşağıda TypeScript'teki `Person` sınıfı gösterilmektedir:

```ts
class Person {
    ssn: string;
    firstName: string;
    lastName: string;

    constructor(ssn: string, firstName: string, lastName: string) {
        this.ssn = ssn;
        this.firstName = firstName;
        this.lastName = lastName;
    }

    getFullName(): string {
        return `${this.firstName} ${this.lastName}`;
    }
}
```

Özelliklere, yapıcıya (constructor) ve metoda tipler eklediğinizde, TypeScript derleyicisi ilgili tip denetimlerini gerçekleştirir.

Örneğin, `ssn` öğesini bir sayı ile başlatamazsınız. Aşağıdaki kod bir hatayla sonuçlanacaktır:

```ts
let person = new Person(171280926, 'John', 'Doe');
```

## Özet
- TypeScript'te bir sınıf tanımlamak için `class` anahtar sözcüğü kullanılır.
- TypeScript, ES6 sınıf sözdiziminden yararlanır ve sınıfı daha sağlam hale getirmek için tip ek açıklamaları ekler.
