# TypeScript Rest Parametresi

**Özet:** Bu bölümde belirsiz sayıda parametreyi bir dizi olarak temsil etmenize olanak tanıyan TypeScript `rest` parametresi hakkında bilgi edineceksiniz.

Rest parametresi, bir fonksiyonun belirtilen tipte sıfır veya daha fazla parametre kabul etmesini sağlar. TypeScript'te, `rest` parametresi şu kuralları izler:

- Fonksiyonun yalnızca tek bir `rest` parametresi vardır.
- Rest parametresi, parametre listesinde en sonda olmalıdır.
- Rest parametresinin tipi bir dizidir.

Bir rest parametresi tanımlamak için, parametre adının önüne üç nokta eklersiniz ve tip açıklaması olarak dizi tipini kullanırsınız:

```ts
function fn(...rest: type[]) {
   //...
}
```

Aşağıdaki örnekte rest parametresinin nasıl kullanılacağı gösterilmektedir:

```ts
function getTotal(...numbers: number[]): number {
    let total = 0;
    numbers.forEach((num) => total += num);
    return total;
}
```

Bu örnekte `getTotal()`, kendisine gönderile sayıların toplamını hesaplar.

`numbers` parametresi bir `rest` parametresi olduğundan, toplamı hesaplamak için bir veya daha fazla sayı gönderebilirsiniz:

```ts
console.log(getTotal()); // 0
console.log(getTotal(10, 20)); // 30
console.log(getTotal(10, 20, 30)); // 60
```

Bu bölümde, belirsiz sayıda parametreyi bir dizi olarak temsil etmenize olanak tanıyan TypeSript `rest` parametreleri hakkında bilgi edindiniz.
