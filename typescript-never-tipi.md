# TypeScript never Tipi

**Özet:** Bu bölümde, hiçbir değer içermeyen TypeScript `never` türü hakkında bilgi edineceksiniz.

`never` türü, hiçbir değer içermeyen bir türdür. Bu nedenle, `never` türüne sahip bir değişkene herhangi bir değer atayamazsınız.

Genellikle, `never` türünü her zaman hata veren bir fonksiyonun dönüş türünü temsil etmek için kullanırsınız. Örneğin:

```ts
function raiseError(message: string): never {
    throw new Error(message);
}
```

Aşağıdaki fonksiyonun dönüş tipi never tipine çıkarım yapar:

```ts
function reject() { 
   return raiseError('Rejected');
}
```

Belirsiz bir döngü içeren bir işlev ifadeniz varsa, dönüş türü de `never` türüdür. Örneğin:

```ts
let loop = function forever() {
    while (true) {
        console.log('Hello');
    }
}
```

Bu örnekte, `forever()` fonksiyonunun geri dönüş türünün tipi never'dir.

Bir fonksiyonun geri dönüş türünün `never` olduğunu görürseniz, yapmak istediğiniz şeyin bu olmadığından emin olmalısınız.

Değişkenler, türünü asla doğru olamayacak bir tür korumasıyla daralttığınızda da `never` türünü alabilir.

Örneğin, never türü olmadan, aşağıdaki fonksiyon bir hataya neden olur çünkü tüm her koşulda bir değer döndürmez.

```ts
function fn(a: string | number): boolean {
  if (typeof a === "string") {
    return true;
  } else if (typeof a === "number") {
    return false;
  }   
}
```

Kodu geçerli kılmak için, dönüş türü `never` türü olan bir işlev döndürebilirsiniz.

```ts
function fn(a: string | number): boolean {
  if (typeof a === "string") {
    return true;
  } else if (typeof a === "number") {
    return false;
  }  
  // make the function valid
  return neverOccur();
}

let neverOccur = () => {
   throw new Error('Never!');
} 
```

## Özet
- `never` türü hiçbir değer içermez.
- `never` türü, her zaman hata atan bir işlevin veya belirsiz bir döngü içeren bir işlevin dönüş türünü temsil eder.
