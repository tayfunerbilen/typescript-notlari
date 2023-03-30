# TypeScript String Değişmez Tipleri

**Özet:** Bu bölümde, belirli bir string değişmezini kabul eden bir tip tanımlayan TypeScript string değişmez tipleri hakkında bilgi edineceksiniz.

String değişmezi tipleri, yalnızca belirtilen bir string değişmezini kabul eden bir tip tanımlamanıza olanak tanır.

Aşağıda, `'click'` değişmez stringini kabul eden bir değişmez string tipi tanımlanmaktadır:

```ts
let click: 'click';
```

`click`, yalnızca `'click'` string değişmezini kabul eden bir string değişmez tipidir. `click` değişkenine `click` stringini atarsanız, geçerli olacaktır:

```ts
click = 'click'; // valid
```

Ancak, `click` değişkenine başka bir string değişmezi atadığınızda, TypeScript derleyicisi bir hata verir. Örneğin:

```ts
click = 'dblclick'; // compiler error
```

Hata:

```ts
Type '"dblclick"' is not assignable to type '"click"'.
```

String değişmez tipi, bir değişkendeki olası bir string değerini sınırlamak için kullanışlıdır.

String değişmez tipleri, bir değişken için sonlu bir string değişmez değerleri kümesi tanımlamak üzere union tipleriyle güzel bir şekilde birleştirilebilir:

```ts
let mouseEvent: 'click' | 'dblclick' | 'mouseup' | 'mousedown';
mouseEvent = 'click'; // valid
mouseEvent = 'dblclick'; // valid
mouseEvent = 'mouseup'; // valid
mouseEvent = 'mousedown'; // valid
mouseEvent = 'mouseover'; // compiler error
```

Eğer string değişmez tiplerini birden fazla yerde kullanırsanız, çok ayrıntılı olacaklardır.

Bundan kaçınmak için tip takma adlarını kullanabilirsiniz. Örneğin:

```ts
type MouseEvent: 'click' | 'dblclick' | 'mouseup' | 'mousedown';
let mouseEvent: MouseEvent;
mouseEvent = 'click'; // valid
mouseEvent = 'dblclick'; // valid
mouseEvent = 'mouseup'; // valid
mouseEvent = 'mousedown'; // valid
mouseEvent = 'mouseover'; // compiler error

let anotherEvent: MouseEvent;
```

## Özet
- TypeScript string değişmez tipi, belirtilen string değişmezi kabul eden bir tip tanımlar.
- Sonlu bir string değişmezleri kümesini kabul eden tipleri tanımlamak için string değişmezi tiplerini union tipleri ve tip takma adlarıyla birlikte kullanabilirsiniz.
