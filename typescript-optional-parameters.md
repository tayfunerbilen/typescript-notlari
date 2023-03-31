# TypeScript İsteğe Bağlı Parametreler

**Özet:** Bu bölümde, fonksiyonlarda isteğe bağlı parametrelerini nasıl kullanacağınızı öğreneceksiniz.

JavaScript'te, fonksiyon parametreleri belirtilse bile herhangi bir parametre göndermeden bir fonksiyonu çağırabilirsiniz. Bu nedenle, JaveScript varsayılan olarak isteğe bağlı parametreleri destekler.

TypeScript'te, derleyici her fonksiyon çağrısını kontrol eder ve aşağıdaki durumlarda hata verir:

- Gönderilen parametre sayısı, fonksiyonda belirtilen parametre sayısından farklıysa
- Veya parametre değişken tipleri, fonksiyon parametrelerinin tipleriyle uyumlu değilse

Derleyici gönderilen parametreleri ayrıntılı olarak kontrol ettiğinden, parametreleri atladığınızda derleyiciye hata vermemesi talimatını vermek için isteğe bağlı parametrelere açıklama eklemeniz gerekir.

Bir fonksiyon parametresini isteğe bağlı yapmak için, parametre adından sonra `?` işaretini kullanırsınız. Örneğin:

```ts
function multiply(a: number, b: number, c?: number): number {

    if (typeof c !== 'undefined') {
        return a * b * c;
    }
    return a * b;
}
```

## Nasıl çalışıyor

- İlk olarak, `c` parametresinden sonra `?` kullanın.
- Daha sonra, `typeof c !== 'undefined'` ifadesini kullanarak parametrenin fonksiyona gönderilip gönderilmediğini kontrol edin.

> Bir parametrenin gönderilip gönderilmediğini kontrol etmek için `if(c)` ifadesini kullanırsanız, boş stringin veya sıfırın tanımsız olarak değerlendirileceğini unutmayın.

İsteğe bağlı parametreler, parametre listesinde gerekli parametrelerden sonra görünmelidir.

Örneğin, `b` parametresini isteğe bağlı ve `c` parametresini gerekli yaparsanız TypeScript derleyicisi bir hata verir:

```ts
function multiply(a: number, b?: number, c: number): number {

    if (typeof c !== 'undefined') {
        return a * b * c;
    }
    return a * b;
}
```

Hata:

```
error TS1016: A required parameter cannot follow an optional parameter.
```

## Özet

- Bir parametreyi isteğe bağlı yapmak için `parameter?: type` sözdizimini kullanın.
- Parametrenin gönderilip gönderilmediğini kontrol etmek için `typeof(parameter) !== 'undefined'` ifadesini kullanın.
