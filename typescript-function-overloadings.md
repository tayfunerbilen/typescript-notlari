# TypeScript Fonksiyon Aşırı Yüklemeleri

**Özet:** Bu bölümde, TypeScript'teki fonksiyon aşırı yüklemeleri hakkında bilgi edineceksiniz.

TypeScript'te, fonksiyon aşırı yüklemeleri, bir fonksiyonun parametre tipleri ve sonuç tipleri arasında ilişki kurmanıza olanak tanır.

> TypeScript fonksiyon aşırı yüklemelerinin, C# ve Java gibi diğer statik tipli diller tarafından desteklenen fonksiyon aşırı yüklemelerinden farklı olduğunu unutmayın.

Bazı basit fonksiyonlarla başlayalım:

```ts
function addNumbers(a: number, b: number): number {
    return a + b;
}

function addStrings(a: string, b: string): string {
    return a + b;
}
```

Bu örnekte:

- `addNumbers()` fonksiyonu iki sayının toplamını döndürür.
- `addStrings()` fonksiyonu iki stringin birleşimini döndürür.

Fonksiyon parametreleri ve sonuçları için bir tip aralığı tanımlamak üzere `union` tipi kullanmak mümkündür:

```ts
function add(a: number | string, b: number | string): number | string {
    if (typeof a === 'number' && typeof b === 'number')
        return a + b;

    if (typeof a === 'string' && typeof b === 'string')
        return a + b;
}
```

Ancak, `union` tipi parametre tipleri ve sonuçlar arasındaki ilişkiyi doğru bir şekilde ifade etmez.

`add()` fonksiyonu derleyiciye, sayıları veya stringleri kabul edeceğini ve bir sayı veya string döndüreceğini söyler. Fonksiyonun, parametreler sayı olduğunda bir sayı döndürdüğünü ve parametreler string olduğunda bir string döndürdüğünü açıklayamaz.

Bir fonksiyon tarafından kullanılan tipler arasındaki ilişkileri daha iyi tanımlamak için TypeScript, fonksiyon aşırı yüklemelerini destekler. Örneğin:

```ts
function add(a: number, b: number): number;
function add(a: string, b: string): string;
function add(a: any, b: any): any {
   return a + b;
}
```

Bu örnekte, `add()` fonksiyonuna iki aşırı yük ekledik. İlk aşırı yük derleyiciye, parametrelerin sayı olduğunda `add()` fonksiyonunun bir sayı döndürmesi gerektiğini söyler. İkinci aşırı yükleme de aynı şeyi yapar, ancak bir string için.

Her fonksiyon aşırı yükü, `add()` fonksiyonu tarafından desteklenen türlerin bir kombinasyonunu tanımlar. Parametreler ve döndürdükleri sonuç arasındaki eşlemeyi tanımlar.

Şimdi, `add()` fonksiyonunu çağırdığınızda, editör aşağıdaki resimde gösterildiği gibi bir aşırı yük fonksiyonunun mevcut olduğunu önerir:

![](https://www.typescripttutorial.net/wp-content/uploads/2020/06/typescript-function-overloadings.png)

## İsteğe Bağlı Parametrelerle Fonksiyon Aşırı Yükleme

Bir fonksiyonu aşırı yüklediğinizde, gerekli parametrelerin sayısı aynı olmalıdır. Bir aşırı yüklemenin diğerinden daha fazla parametresi varsa, ek parametreleri isteğe bağlı hale getirmeniz gerekir. Örneğin:

```ts
function sum(a: number, b: number): number;
function sum(a: number, b: number, c: number): number;
function sum(a: number, b: number, c?: number): number {
    if (c) return a + b + c;
    return a + b;
}
```

`sum()` fonksiyonu iki ya da üç sayı kabul eder. Üçüncü parametre isteğe bağlıdır. Bunu isteğe bağlı yapmazsanız hata alırsınız.

## Yöntem Aşırı Yükleme

Bir fonksiyon bir sınıfın özelliği olduğunda, buna yöntem (metod) denir. TypeScript ayrıca yöntem aşırı yüklemesini de destekler. Örneğin:

```ts
class Counter {
    private current: number = 0;
    count(): number;
    count(target: number): number[];
    count(target?: number): number | number[] {
        if (target) {
            let values = [];
            for (let start = this.current; start <= target; start++) {
                values.push(start);
            }
            this.current = target;
            return values;
        }
        return ++this.current;
    }
}
```

`count()` fonksiyonu, kendisine geçilen parameterelerin sayısına bağlı olarak bir sayı veya bir string döndürebilir:

```ts
let counter = new Counter();

console.log(counter.count()); // return a number
console.log(counter.count(20)); // return an array
```

Çıktı:

```js
1
[
   1,  2,  3,  4,  5,  6,  7,
   8,  9, 10, 11, 12, 13, 14,
  15, 16, 17, 18, 19, 20     
]
```

## Özet

TypeScript fonksiyon aşırı yüklemeleri, bir fonksiyonun parametre tipleri ve sonuçları arasındaki ilişkiyi tanımlamanıza olanak tanır.
