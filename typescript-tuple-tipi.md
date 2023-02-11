# TypeScript Tuple Tipi

  Tuple bazı farklılıkları dışında tıpkı `array` gibidir.
  
  - Tuple'daki eleman sayısı sabittir.
  - Tuple'daki tipler sabittir.

Bu sebeple Tuple, değerleri sabit ve iyi tanımlanmış diziler olarak tanımlanabilir.

Örneğin, `string` ve `number` tipleri içeren bir tuple örneği oluşturalım:

```ts
let skill: [string, number];
skill = ['Programming', 5];
```

Değerlerin sırası tuple'da önemlidir. Yukarıdaki örneğin değerlerini yer değiştirecek olursak hata alırız:

```ts
let skill: [string, number];
skill = [5, 'Programming'];
```

Hata:

```
error TS2322: Type 'string' is not assignable to type 'number'.
```

Bu yüzden, belirli bir sırası olan ve birbiriyle ilişkili değerler için tuple kullanmak doğru bir yaklaşım olacaktır.

Örneğin, RGB renk tanımı için tuple kullanabilirsiniz. Her zaman 3 sayıyı temsil eder ve tuple için mantıklıdır.

```
let color: [number, number, number] = [255, 0, 0];
```

`color[0]`, `color[1]` ve `color[2]` mantıken `Red`, `Green` ve `Blue` ya eşittir.

## Opsiyonel Tuple Öğeleri

TypeScript 3.0'dan sonra, öğelerin sonuna (?) koyarak opsiyonel yapabilirsiniz.

Örneğin, RGB yerine RGBA tanımlamak isteseydik, 4. parametre ALPHA değeri opsiyonel bir seçenek olacaktı.

```ts
let bgColor, headerColor: [number, number, number, number?];
bgColor = [0, 255, 255, 0.5];
headerColor = [0, 255, 255];
```
