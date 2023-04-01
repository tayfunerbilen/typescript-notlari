# TypeScript Erişim Değiştiricileri

**Özet:** Bu bölümde, TypeScript'teki erişim değiştiricileri hakkında bilgi edineceksiniz.

Erişim değiştiricileri, bir sınıfın özelliklerinin ve yöntemlerinin görünürlüğünü değiştirir. TypeScript üç erişim değiştiricisi sağlar:

- private
- protected
- public

TypeScript'in erişimi çalışma zamanında (runtime) değil, derleme sırasında mantıksal olarak kontrol ettiğini unutmayın.

## `private` Değiştiricisi

`private` değiştiricisi, görünürlüğü yalnızca aynı sınıfla sınırlar. Bir özelliğe veya yönteme `private` değiştiricisini eklediğinizde, bu özelliğe veya yönteme aynı sınıf içinde erişebilirsiniz. Sınıf dışındaki özel özelliklere veya yöntemlere erişme girişimleri derleme zamanında bir hatayla sonuçlanır.

Aşağıdaki örnekte, `person` sınıfının `snn`, `firstName` ve `lastName` özelliklerinde `private` değiştiricisinin nasıl kullanılacağı gösterilmektedir:

```ts
class Person {
    private ssn: string;
    private firstName: string;
    private lastName: string;
    // ...
}
```

`private` eklendikten sonra, `Person` sınıfının yapıcısında veya yöntemlerinde `ssn` özelliğine erişebilirsiniz. Örneğin:

```ts
class Person {
    private ssn: string;
    private firstName: string;
    private lastName: string;

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

Aşağıda `ssn` özelliğine sınıf dışından erişilmeye çalışılmaktadır:

```ts
let person = new Person('153-07-3130', 'John', 'Doe');
console.log(person.ssn); // compile error
```

## `public` Değiştirici

`public` değiştiricisi, sınıf özelliklerinin ve yöntemlerinin tüm konumlardan erişilebilir olmasını sağlar. Özellikler ve yöntemler için herhangi bir erişim değiştiricisi belirtmezseniz, varsayılan olarak `public` değiştiricisini alırlar.

Örneğin, `Person` sınıfının `getFullName()` yöntemi `public` değiştiricisine sahiptir. Aşağıda, `getFullName()` yöntemine `public` değiştiricisi açıkça eklenmiştir:

```ts
class Person {
    // ...
    public getFullName(): string {
        return `${this.firstName} ${this.lastName}`; 
    }
    // ...
}
```

Bu, `public` anahtar sözcüğünün atlanmasıyla aynı etkiye sahiptir.

## `protected` Değiştirici

`protected` değiştiricisi, bir sınıfın özelliklerinin ve yöntemlerinin aynı sınıf içinde ve alt sınıflar içinde erişilebilir olmasını sağlar.

Bir sınıf (alt sınıf) başka bir sınıftan (üst sınıf) miras aldığında, üst sınıfın bir alt sınıfı olur.

`protected` özelliklere veya yöntemlere başka bir yerden erişmeye çalışırsanız TypeScript derleyicisi hata verir.

Bir özelliğe veya yönteme `protected` değiştiricisini eklemek için `protected` anahtar sözcüğünü kullanırsınız. Örneğin:

```ts
class Person {

    protected ssn: string;
    
    // other code
}
```

`ssn` özelliği artık korumalıdır. `Person`sınıfı içinde ve `Person` sınıfından miras alan herhangi bir sınıfta erişilebilir olacaktır. Burada kalıtım hakkında daha fazla bilgi edineceksiniz.

`Person` sınıfı iki `private` özellik ve bir `protected` özellik bildirir. Kurucusu bu özellikleri üç argümanla başlatır. 

Kodu daha kısa hale getirmek için TypeScript, özellikleri hem bildirmenize hem de constuctor'da şu şekilde başlatmanıza olanak tanır:

```ts
class Person {
    constructor(protected ssn: string, private firstName: string, private lastName: string) {
        this.ssn = ssn;
        this.firstName = firstName;
        this.lastName = lastName;
    }

    getFullName(): string {
        return `${this.firstName} ${this.lastName}`;
    }
}
```

Özelliklerin ve yöntemlerin görünürlüğünü değerlendirirken, en az görünür erişim değiştiricisi olan `private` ile başlamak iyi bir uygulamadır.

## Özet
- TypeScript, sınıf özellikleri ve yöntemleri için üç erişim değiştiricisi sağlar: `private`, `protected` ve `public`.
- `private` değiştiricisi, aynı sınıf içinde erişime izin verir.
- `protected` değiştiricisi, aynı sınıf ve alt sınıflar içinde erişime izin verir.
- `public` değiştiricisi, herhangi bir konumdan erişime izin verir.
