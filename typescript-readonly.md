# TypeScript readonly Erişim Değiştiricisi

**Özet:** Bu bölümde, sınıf özelliklerini değişmez (immutable) özellik olarak işaretlemek için TypeScript readonly erişim değiştiricisini nasıl kullanacağınızı öğreneceksiniz.

TypeScript, bir sınıfın özelliklerini değişmez (immutable) olarak işaretlemenize olanak tanıyan `readonly` değiştiricisini sağlar. Bir `readonly` özelliğine atama yalnızca iki yerden birinde gerçekleşebilir:

- Özellik bildiriminde.
- Aynı sınıfın kurucusunda.

Bir özelliği değişmez olarak işaretlemek için `readonly` anahtar sözcüğünü kullanırsınız. Aşağıda, `Person` sınıfında bir `readonly` özelliğinin nasıl bildirileceği gösterilmektedir:

```ts
class Person {
    readonly birthDate: Date;

    constructor(birthDate: Date) {
        this.birthDate = birthDate;
    }
}
```

Bu örnekte, `birthdate` özelliği `Person` sınıfının yapıcısında belirtilen ve sınıf içinde tanımlanan bir `readonly` özelliğidir.

Aşağıdaki `birthDate` özelliğini yeniden atama girişimleri bir hatayla sonuçlanır:

```ts
let person = new Person(new Date(1990, 12, 25));
person.birthDate = new Date(1991, 12, 25); // Compile error
```

Diğer [erişim değiştiricileri](./typescript-access-modifiers.md) gibi, `readonly` özelliğinin bildirimini yapıcıda ve sınıf içinde şu şekilde birleştirebilirsiniz:

```ts
class Person {
    constructor(readonly birthDate: Date) {
        this.birthDate = birthDate;
    }
}
```

## Readonly vs. const

Aşağıda `readonly` ve `const` arasındaki farklar gösterilmektedir:

|| readonly | const |
| ------------- | ------------- | ------------- |
| Kullanım | Sınıf özelliklerinde | Değişkenlerde |
| Başlatma | Aynı sınıfın bildiriminde veya kurucusunda	 | Tanımlamada |

## Özet
- Bir sınıf özelliğini değişmez olarak işaretlemek için `readonly` erişim değiştiricisini kullanın.
- Bir `readonly` özelliği, bildirimin bir parçası olarak veya aynı sınıfın kurucusu içinde başlatılmalıdır.
