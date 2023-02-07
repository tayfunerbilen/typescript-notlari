# TypeScript Tip Çıkarımları

**Özet:** Bu bölümdee TypeScript'de bir tip tanımlanmaması durumunda, TypeScript'in nasıl çıkarım yaptığını öğreneceğiz.

## Basit Tip Çıkarımları

Bir değişken tanımladığınızda, tip tanımlarını kullanarak değişkenin tipini belirleyebilirsiniz.

```ts
let counter: number;
```

Eğer, `counter` değişkenini `0` değeriyle bir tip tanımı yapmadan oluştursanız TypeScript bunun `number` tipinde olduğunu bilecektir.

```ts
let counter = 0;
```

Aşağıdaki örnekle yukarıdaki örnek birbiriyle aynıdır:

```ts
let counter: number = 0;
```

Aynı şekilde, fonksiyonlarda varsayılan bir parametre değeri tanımımlarken tip belirlenmemişse, TypeScript bunun hangi tipte olduğunu bilecektir.

```ts
function setCounter(max=100) {
    // ...
}
```

Yukarıdaki örnekte TypeScript `max` parametresinin `number` tipinde olduğunu bilecektir.

Benzer şekilde, TypeScript dönen değerinde tip çıkarımını yapabilir.

```ts
function increment(counter: number) {
    return counter++;
}
```

Yukarıdaki kod aşağıdaki kod ile aynıdır:

```ts
function increment(counter: number) : number {
    return counter++;
}
```
