# TypeScript Varsayılan Parametreler

Özet: Bu bölümde, TypeScript varsayılan parametreleri hakkında bilgi edineceksiniz.

JavaScript, ES2015'ten (veya ES6'dan) bu yana aşağıdaki sözdizimiyle varsayılan parametreleri desteklemektedir:

```js
function name(parameter1 = defaultValue1, ...) {
   // do something
}
```

Bu sözdiziminde, fonksiyonu çağırırken parametreleri göndermezseniz veya tanımlanmamış olanı gönderirseniz, fonksiyon atlanan parametreler için varsayılan ilk değerleri alacaktır. Örneğin:

```ts
function applyDiscount(price, discount = 0.05) {
    return price * (1 - discount);
}

console.log(applyDiscount(100)); // 95
```

Bu örnekte, `applyDiscount()` fonksiyonu varsayılan parametre olarak `discount` parametresine sahiptir.

`discount` parametresi `applyDiscount()` fonksiyonuna gönderdiğinizde, fonksiyon varsayılan değer olan `0.05` değerini kullanır.

JavaScript'e benzer şekilde, TypeScript'te de aynı sözdizimiyle varsayılan parametreleri kullanabilirsiniz.

```ts
function name(parameter1: type = defaultvalue1, parameter2: type = defaultvalue2, ...) {
   //
}
```

Aşağıdaki örnekte `applyDiscount()` fonksiyonu için varsayılan parametreler kullanılmaktadır:

```ts
function applyDiscount(price: number, discount: number = 0.05): number {
    return price * (1 - discount);
}

console.log(applyDiscount(100)); // 95
```

Fonksiyon tip tanımlarına varsayılan parametreleri dahil edemeyeceğinize dikkat edin. Aşağıdaki kod bir hatayla sonuçlanacaktır:

```ts
let promotion: (price: number, discount: number = 0.05) => number;
```

Hata:

```
error TS2371: A parameter initializer is only allowed in a function or constructor implementation.
```

## Varsayılan Parametreler ve İsteğe Bağlı Parametreler

İsteğe bağlı parametreler gibi, varsayılan parametreler de isteğe bağlıdır. Bu, fonksiyonu çağırırken varsayılan parametreleri atlayabileceğiniz anlamına gelir.

Ayrıca, hem varsayılan parametreler hem de sondaki varsayılan parametreler aynı türü paylaşır. Örneğin, aşağıdaki fonksiyon:

```ts
function applyDiscount(price: number, discount: number = 0.05): number {
  // ...
}
```

ve

```ts
function applyDiscount(price: number, discount?: number): number {
  // ...
}
```

aynı tipi paylaşır:

```ts
(price: number, discount?: number) => number
```

İsteğe bağlı parametreler gerekli parametrelerden sonra gelmelidir. Ancak, varsayılan parametrelerin gerekli parametrelerden sonra gelmesi gerekmez.

Varsayılan bir parametre gerekli bir parametreden önce olduğunda, varsayılan başlatılmış değeri almak için `undefined` değerini geçmeniz gerekir.

Aşağıdaki fonksiyon, belirtilen ay ve yıldaki gün sayısını döndürür:

```ts
function getDay(year: number = new Date().getFullYear(), month: number): number {
    let day = 0;
    switch (month) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            day = 31;
            break;
        case 4:
        case 6:
        case 9:
        case 11:
            day = 30;
            break;
        case 2:
            // leap year
            if (((year % 4 == 0) &&
                !(year % 100 == 0))
                || (year % 400 == 0))
                day = 29;
            else
                day = 28;
            break;
        default:
            throw Error('Invalid month');
    }
    return day;
}
```

Bu örnekte, bir parametre geçmezseniz veya tanımsız bir değer geçerseniz yılın varsayılan değeri geçerli yıldır.

Aşağıdaki örnek, Şubat 2019'daki gün sayısını almak için `getDay()` fonksiyonunu kullanır:

```ts
let day = getDay(2019, 2);
console.log(day); // 28
```

İçinde bulunduğunuz yılın Şubat ayındaki gün sayısını almak için, `year` parametresine aşağıdaki gibi `undefined` değerini göndermeniz gerekir:

```ts
let day = getDay(undefined, 2);
console.log(day);
```

## Özet
- Parametre için varsayılan değeri ayarlamak istiyorsanız varsayılan parametre sözdizimini yani `parameter:type = defaultValue` kullanmalısınız.
- Varsayılan parametreler isteğe bağlıdır.
- Bir parametrenin varsayılan değerini kullanmak için, fonksiyonu çağırırken parametreyi atlarsınız veya parametre olarak `undefined` değeri gönderebilirsiniz.
