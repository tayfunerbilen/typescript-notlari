# TypeScript Number Tipi

Büyük sayılar hariç bütün sayılar `number` tipindedir. Büyük sayılar ise `bigint` tipindedir.
  
Aşağıdaki şekilde bir `number` tipinde değişken tanımlayabilirsiniz.
  
```ts
let price: number;
```

Ya da varsayılan bir değerlede tipini zaten belirtmiş olursunuz:

```ts
let price = 9.95;
```

TypeScript ondalık, onaltılık, ikili ve sekizli tüm sayıları destekler.
  
Bunların her birine birer örnek vermek gerekirse:

```ts
// ondalık
let counter: number = 0;
let x: number = 100, 
    y: number = 200;

//  ikili
let bin = 0b100;
let anotherBin: number = 0B010;

// sekizli
let octal: number = 0o10;

// onaltılı
let hexadecimal: number = 0XA;
```

## Büyük Sayılar

Büyük sayılar 2 üssü 53 - 1'den büyük olan sayılar için geçerli veri tipidir. 
  
```ts
let big: bigint = 9007199254740991n;
```
