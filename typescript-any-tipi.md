# TypeScript any Tipi

**Özet:** Bu bölümde `any` tipini ve bu tipi kodunuzda nasıl kullanacağınızı öğreneceksiniz.

Bazı durumlarda, bir değişkende tuttuğunuz değerin tipini o an bilmiyor olabilirsiniz. Örneğin bir API'dan gelen bilgiler gibi.

Bu durumda, compile aşamasında hata vermeden devam etmesini isteyebilirsiniz. 

Böyle bir senaryoda `any` tipini kullanabilirsiniz. Adından da anlaşılacağı üzere, atanan değer herhangi bir veri tipinde olabilir.

Örneğin:

```ts
const json = `{"latitude": 10.11, "longitude":12.12}`;

// Lokasyonu bulmak için JSON'ı parse edelim
const currentLocation = JSON.parse(json);
console.log(currentLocation);
```

Çıktı:

```ts
{ latitude: 10.11, longitude: 12.12 }
```

Bu örnekte `currentLocation` değişkenine `JSON.parse()` metodundan dönen bir nesne atandı. 

Yukarıdaki `currentLocation` değişkeni altında bir özelliğe erişmeye çalıştığınızda olmasa bile TypeScript hata vermeyecektir.

```ts
console.log(currentLocation.x);
```

Çıktı:

```ts
undefined
```

TypeScript compiler bir hata ya da sorun göstermeyecektir.

`any` tipi varolan JavaScript kod yapınızla çalışmanızı sağlar. Derleme sırasında tip kontroünü etkinleştirmenize ya da devre dışı bırakmanıza olanak sağlar. Yani anlayacağınız, bir JavaScript projesini TypeScript'e dönüştürürken `any` tipinden fazlaca yararlanabilirsiniz.

## Tip İması

Bir tip belirlemeden değişken oluşturursanız, TypeScript bunun bir `any` tipinde olduğunu varsayar. Bu özelliğe [tip çıkarımı](./typescript-tip-cikarimlari.md) deniyor. Temelde, TypeScript değişkenin tipiyle ilgili tahminde bulunuyor. Örneğin:

```ts
let result;
```

Bu örnekte, TypeScript tip çıkarımında bulunacaktır. Bu uygulamaya da tip iması deniyor. (adına çok takılmayın, yaptığı işi anlasanız yeter :))

## TypeScript any vs. object

Eğer bir değişkeni `object` tipiyle tanımlarsanız da buna istediğiniz değeri atayabilirsiniz.

Ancak, metod varolsa bile bir metodu çağıramazsınız. Örneğin:

```ts
let result: any;
result = 10.123;
console.log(result.toFixed());
result.willExist(); //
```

Bu örnekte, TypeScript `willExists()` metodu compile aşamasında olmasa bile runtie'da olabileceğinden hata yakalamayacaktır.

Ancak, tipi `object` olarak değiştirip şöyle denerseniz:

```ts
let result: object;
result = 10.123;
result.toFixed();
```

TypeScript şöyle bir hata fırlatacaktır:

```ts
error TS2339: Property 'toFixed' does not exist on type 'object'.
```

## Özet

- `any` tipi her tipten değer atanabilmesini sağlar ve compiler'ın tip kontrolünü atlamasını sağlar.
- `any` tipini compile-time'da tipi bilinmeyen durumlarda ya da varolan JavaScript kodlarınızı TypeScript'e geçirirken kullanın.
