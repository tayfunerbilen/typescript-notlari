# TypeScript Kalıtım

**Özet:** Bu bölümde, TypeScript kalıtım kavramını ve başka bir sınıfın işlevselliğini yeniden kullanmak için bu kavramı nasıl kullanacağınızı öğreneceksiniz.

Bir sınıf, başka bir sınıfın özelliklerini ve metodlarını yeniden kullanabilir. Buna TypeScript'te kalıtım (inheritance) denir.

Özellikleri ve metodları miras alan sınıfa alt sınıf denir. Özellikleri ve metodları miras alınan sınıf ise ana sınıf olarak bilinir. Bu isimler, çocukların ebeveynlerden genleri miras almasının doğasından gelir.

Kalıtım, mevcut bir sınıfın işlevselliğini yeniden yazmadan yeniden kullanmanıza olanak tanır.

JavaScript, Java veya C# gibi klasik kalıtımı değil, prototip kalıtımı kullanır. ES6, prototip kalıtımın sözdizimsel şekeri (syntactic sugar) olan sınıf sözdizimini sunar. TypeScript, ES6 gibi kalıtımı destekler.

> JavaScript sınıflarında "syntactic sugar", kodun okunabilirliğini ve yazılmasını kolaylaştırmak için kullanılan bir yapıdır. Yani, aslında yapılan şey aynı, ancak daha okunaklı bir yazım şekli kullanılarak daha anlaşılır hale getirilir.

Aşağıdaki `Person` sınıfına sahip olduğunuzu varsayalım:

```ts
class Person {
    constructor(private firstName: string, private lastName: string) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    getFullName(): string {
        return `${this.firstName} ${this.lastName}`;
    }
    describe(): string {
        return `This is ${this.firstName} ${this.lastName}.`;
    }
}
```

Bir sınıfı miras almak için `extends` anahtar sözcüğünü kullanırsınız. Örneğin aşağıdaki `Employee` sınıfı `Person` sınıfını miras alır:

```ts
class Employee extends Person {
    //..
}
```

Bu örnekte, `Employee` bir alt sınıf ve `Person` ise üst sınıftır.

## Constructor

`Person` sınıfının `firstName` ve `lastName` özelliklerini başlatan bir kurucusu olduğundan, `Employee` sınıfının kurucusunda üst sınıfın kurucusunu çağırarak bu özellikleri başlatmanız gerekir.

Üst sınıfın kurucusunu alt sınıfın kurucusunda çağırmak için `super()` sözdizimini kullanırsınız. Örneğin:

```ts
class Employee extends Person {
    constructor(
        firstName: string,
        lastName: string,
        private jobTitle: string) {
        
        // call the constructor of the Person class:
        super(firstName, lastName);
    }
}
```

Aşağıda `Employee` sınıfının bir örneği oluşturulmaktadır:

```ts
let employee = new Employee('John','Doe','Front-end Developer');
```

`Employee` sınıfı `Person` sınıfının özelliklerini ve yöntemlerini miras aldığından, `employee` nesnesinde `getFullName()` ve `describe()` metodlarını aşağıdaki gibi çağırabilirsiniz:

```ts
let employee = new Employee('John', 'Doe', 'Web Developer');

console.log(employee.getFullName());
console.log(employee.describe());
```

Çıktı:

```
John Doe
This is John Doe.
```

Metod Overriding (geçersiz kılma)
`employee` nesnesi üzerinde `employee.describe()` metodunu çağırdığınızda, mesajı gösteren `Person` sınıfının `describe()` metodu çalıştırılır: Bu John Doe'dur.

`Employee` sınıfının `describe()` metodunun kendi versiyonuna sahip olmasını istiyorsanız, bunu `Employee` sınıfında şu şekilde tanımlayabilirsiniz:

```ts
class Employee extends Person {
    constructor(
        firstName: string,
        lastName: string,
        private jobTitle: string) {

        super(firstName, lastName);
    }

    describe(): string {
        return super.describe() + `I'm a ${this.jobTitle}.`;
    }
}
```

`describe()` metodunda, `super.methodInParentClass()` sözdizimini kullanarak üst sınıfın `describe()` metodunu çağırdık.

`employee` nesnesi üzerinde `describe()` metodunu çağırırsanız, `Employee` sınıfındaki `describe()` metodu çağrılır:

```ts
let employee = new Employee('John', 'Doe', 'Web Developer');
console.log(employee.describe());
```

Çıktı:

```
This is John Doe.I'm a Web Developer.
```

## Özet
- Bir sınıfın başka bir sınıftan miras almasına izin vermek için `extends` anahtar sözcüğünü kullanın.
- Üst sınıfın kurucusunu çağırmak için alt sınıfın kurucusunda `super()` kullanın. Ayrıca, alt sınıfın metodunda `metodInParentClass()` çağırmak için `super.methodInParentClass()` sözdizimini kullanın.
