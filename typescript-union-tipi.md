# TypeScript Union Tipi

**Özet:** Bu bölümde, bir değişkende bir veya birkaç tipden değer saklamanıza olanak tanıyan `union` tipi hakkında bilgi edineceksiniz.

Bazen, bir sayı veya string olan bir parametre bekleyen bir fonksiyonla karşılaşırsınız. Örneğin:

```ts
function add(a: any, b: any) {
    if (typeof a === 'number' && typeof b === 'number') {
        return a + b;
    }
    if (typeof a === 'string' && typeof b === 'string') {
        return a.concat(b);
    }
    throw new Error('Parameters must be numbers or strings');
}
```

Bu örnekte, `add()` fonksiyonu, parametreleri sayı ise bunların toplamını hesaplayacaktır.

Parametrelerin string olması durumunda, `add()` fonksiyonu bunları tek bir string halinde birleştirir.

Parametreler ne sayı ne de string ise, `add()` işlevi hata verir.

`add()` fonksiyonunun parametreleriyle ilgili sorun, parametrelerinin herhangi bir tipe sahip olmasıdır. Bu, fonksiyonu ne sayı ne de string olan bağımsız değişkenlerle çağırabileceğiniz ve TypeScript'in bununla sorun yaşamayacağı anlamına gelir.

Bu kod başarıyla derlenecek ancak çalışma zamanında (runtime) bir hataya neden olacaktır:

```ts
add(true, false);
```

Bunu çözmek için TypeScript `union` tipini kullanabilirsiniz. Union tipi, birden fazla tipi tek bir tipde birleştirmenize olanak tanır.

Örneğin, aşağıdaki değişken sayı veya string tipindedir:

```ts
let result: number | string;
result = 10; // OK
result = 'Hi'; // also OK
result = false; // a boolean value, not OK
```

Union tipi, yalnızca iki değil birkaç tipden biri olabilen bir değeri tanımlar. Örneğin `number | string | boolean`, sayı, string veya boolean olabilen bir değerin tipidir.

`add()` fonksiyonu örneğine geri dönersek, parametrelerin tiplerini any'den union'a şu şekilde değiştirebilirsiniz:

```ts
function add(a: number | string, b: number | string) {
    if (typeof a === 'number' && typeof b === 'number') {
        return a + b;
    }
    if (typeof a === 'string' && typeof b === 'string') {
        return a.concat(b);
    }
    throw new Error('Parameters must be numbers or strings');
}
```

## Özet

- TypeScript union tipi, bir değişkende bir veya birden çok tipde değer saklamanıza olanak tanır.
