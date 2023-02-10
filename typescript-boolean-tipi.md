# TypeScript Boolean Tipi

TypeScript `boolean` tipi `true` ya da `false` olmak üzere iki değer içerebilir.

```ts
let pending: boolean;
pending = true;
// after a while
// ..
pending = false;
```

JavaScript'de bir de `Boolean` adında baş harfi büyük bir kullanım var. Bu `boolean` tipinden farklı olarak bir primitive bir tip yerine bir objedir.

Genelde de şu tarz kullanımlar için uygundur:

- Boolean tipi olduğu gibi geri döner.
- `undefined` tipi `false` olarak döner.
- `null` tipi `false` olarak döner.
- `0`, `-0` ve `NaN` tipleri `false` olarak döner, geri kalan bütün sayılar `true` döner.
- `0n` `false` döndürür. Diğer büyük sayılar `true` döndürür.
- Tüm objeler `true` döner.

```ts
Boolean(undefined) // false
Boolean(null) // false
Boolean(NaN) // false
```
