# TypeScript Fonksiyon Türleri

**Özet:** Bu bölümde, fonksiyonlar için tipler tanımlamanıza olanak tanıyan TypeScript fonksiyon tipleri hakkında bilgi edineceksiniz.

Bir fonksiyon tipinin iki bölümü vardır: parametreler ve dönüş tipi. Bir fonksiyon tipini bildirirken, her iki kısmı da aşağıdaki sözdizimiyle belirtmeniz gerekir:

```ts
(parameter: type, parameter:type,...) => type
```

Aşağıdaki örnekte, iki sayı kabul eden ve bir sayı döndüren bir fonksiyon tipine sahip bir değişkenin nasıl tanımlanacağı gösterilmektedir:

```ts
let add: (x: number, y: number) => number;
```

Bu örnekte:

- Fonksiyon tipi iki parametre kabul eder: `x` ve `y`, `number` tipindedir.
- Dönüş değerinin tipi, parametreler ve dönüş tipi arasında beliren (=>) işaretini takip eden sayıdır.

> Parametre adlarının (`x` ve `y`) sadece okunabilirlik amaçlı olduğunu unutmayın. Parametrelerin tipleri eşleştiği sürece, fonksiyon için geçerli bir tipdir.

Bir değişkene bir fonksiyon tipiyle açıklama ekledikten sonra, fonksiyonu değişkene aynı tiple atayabilirsiniz.

TypeScript derleyicisi, parametrelerin sayısını tipleriyle ve dönüş tipiyle eşleştirecektir.

Aşağıdaki örnek, `add` değişkenine bir fonksiyonun nasıl atanacağını gösterir:

```ts
add = function (x: number, y: number) {
    return x + y;
};
```

Ayrıca, bir değişken tanımlayıp, değişkene aşağıdaki gibi bir fonksiyon da atayabilirsiniz:

```ts
let add: (a: number, b: number) => number =
    function (x: number, y: number) {
        return x + y;
    };
```

Türü `add` değişkeniyle eşleşmeyen başka fonksiyonlar atarsanız, TypeScript bir hata verir:

```ts
add = function (x: string, y: string): number {
    return x.concat(y).length;
};
```

Bu örnekte, tipi eşleşmeyen bir fonksiyonunu `add` değişkenine yeniden atadık.

## Fonksiyon tiplerini çıkarma

TypeScript derleyicisi, denklemin bir tarafında tip olduğunda fonksiyon tipini anlayabilir. Bu tip çıkarım biçimine bağlamsal tipleme denir. Örneğin:

![](https://www.typescripttutorial.net/wp-content/uploads/2020/06/TypeScript-Function-Type-Example.png)

Bu örnekte, `add` fonksiyonu `(x: number, y: number) => number` tipini alacaktır.

Tip çıkarımını kullanarak, ek açıklamalarla kod miktarını önemli ölçüde azaltabilirsiniz.
