# TypeScript Getters ve Setters

**Özet:** Bu bölümde TypeScript getter ve setter'larını nasıl kullanacağınızı öğreneceksiniz.

Aşağıda üç özelliğe sahip basit bir `Person` sınıfı gösterilmektedir: `age`, `firstName` ve `lastName`:

```ts
class Person {
    public age: number;
    public firstName: string;
    public lastName: string;
}
```

`Person` sınıfının herhangi bir özelliğine erişmek için basitçe şu şekilde yapabilirsiniz:

```ts
let person = new Person();
person.age = 26;
```

Kullanıcı girdisinden gelen bir değeri `age` özelliğine atadığınızı varsayalım:

```ts
person.age = inputAge;
```

`inputAge` herhangi bir sayı olabilir. Yaşın geçerliliğini sağlamak için, atamadan önce aşağıdaki gibi bir kontrol gerçekleştirebilirsiniz:

```ts
if( inputAge > 0 && inputAge < 200 ) {
    person.age = inputAge;
}
```

Bu kontrolü her yerde kullanmak gereksiz ve sıkıcıdır.

Kontrolü tekrarlamaktan kaçınmak için setter ve getter kullanabilirsiniz. Getter ve setter'lar bir sınıfın özelliklerine erişimi kontrol etmenizi sağlar.

Her özellik için:

- Bir getter yöntemi özelliğin değerini döndürür. Getter aynı zamanda `accessor` olarak da adlandırılır.
- Bir setter yöntemi özelliğin değerini günceller. Bir setter aynı zamanda `mutator` olarak da bilinir.

Bir getter yöntemi `get` anahtar sözcüğü ile başlar ve bir setter yöntemi `set` anahtar sözcüğü ile başlar.

```ts
class Person {
    private _age: number;
    private _firstName: string;
    private _lastName: string;

 
    public get age() {
        return this._age;
    }

    public set age(theAge: number) {
        if (theAge <= 0 || theAge >= 200) {
            throw new Error('The age is invalid');
        }
        this._age = theAge;
    }

    public getFullName(): string {
        return `${this._firstName} ${this._lastName}`;
    }
}
```

Nasıl çalışır?

- İlk olarak, `age`, `firstName` ve `lastName` özelliklerinin erişim değiştiricilerini `public`'ten `private`'e değiştirin.
- İkinci olarak, `age` özelliğini `_age` olarak değiştirin.
- Üçüncü olarak, `_age` özelliği için getter ve setter yöntemleri oluşturun. Setter yönteminde, `_age` özelliğine atamadan önce giriş yaşının geçerliliğini kontrol edin.

Şimdi, `age` setter yöntemine aşağıdaki şekilde erişebilirsiniz:

```ts
let person = new Person();
person.age = 10;
```

Setter'a yapılan çağrının normal bir yöntem gibi parantez içermediğine dikkat edin. `person.age` öğesini çağırdığınızda, `age` setter yöntemi çağrılır. Geçersiz bir yaş değeri atarsanız, setter hata verir:

```ts
person.age = 0;
```

Hata:

```ts
Error: The age is invalid
```

`person.age` öğesine eriştiğinizde, `age` getter öğesi çağrılır.

```ts
console.log(person.age);
```

Aşağıda `firstName` ve `lastName` özelliklerine getter'lar ve setter'lar eklenmiştir.

```ts
class Person {
    private _age: number;
    private _firstName: string;
    private _lastName: string;

    public get age() {
        return this._age;
    }

    public set age(theAge: number) {
        if (theAge <= 0 || theAge >= 200) {
            throw new Error('The age is invalid');
        }
        this._age = theAge;
    }

    public get firstName() {
        return this._firstName;
    }

    public set firstName(theFirstName: string) {
        if (!theFirstName) {
            throw new Error('Invalid first name.');
        }
        this._firstName = theFirstName;
    }

    public get lastName() {
        return this._lastName;
    }

    public set lastName(theLastName: string) {
        if (!theLastName) {
            throw new Error('Invalid last name.');
        }
        this._lastName = theLastName;
    }

    public getFullName(): string {
        return `${this.firstName} ${this.lastName}`;
    }
}
```

## Daha Fazla TypeScript Getters/Setters Örneği

Koddan da görebileceğiniz gibi, setter'lar, verileri özelliklere atamadan önce doğrulamak istediğinizde kullanışlıdır. Ayrıca, karmaşık mantık gerçekleştirebilirsiniz.

Aşağıda `fullname` getter ve setter'ının nasıl oluşturulacağı gösterilmektedir.

```ts
class Person {
    // ... other code 
    public get fullName() {
        return `${this.firstName} ${this.lastName}`;
    }

    public set fullName(name: string) {
        let parts = name.split(' ');
        if (parts.length != 2) {
            throw new Error('Invalid name format: first last');
        }
        this.firstName = parts[0];
        this.lastName = parts[1];
    }
}
```

Nasıl çalışıyor?

- Getter yöntemi, `ad` ve `soyadın` birleştirilmesini döndürür.
- Setter metodu, `tam ad` olarak şu formatta bir string kabul eder: `first last` ve ilk kısmı `firstName` özelliğine, ikinci kısmı da `lastName` özelliğine atar.

Artık `fullname` setter ve getter'a normal bir sınıf özelliği gibi erişebilirsiniz:

```ts
 let person = new Person();
 person.fullname = 'John Doe';
 
 console.log(person.fullName);
```

## Özet
- Bir sınıfın erişim özelliklerini kontrol etmek için TypeScript getter/setter'larını kullanın.
- Getter/setter'lar, accessor/mutator olarak da bilinir.
