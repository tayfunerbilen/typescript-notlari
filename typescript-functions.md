# TypeScript Fonksiyonları

**Özet:** Bu bölümde, TypeScript fonksiyonları hakkında bilgi edinecek ve fonksiyonların tip denetimlerini uygulamak için tip ek açıklamalarını nasıl kullanacağınızı öğreneceksiniz.

## TypeScript fonksiyonlarına giriş

TypeScript fonksiyonları, okunabilir, bakımı yapılabilir ve yeniden kullanılabilir kod parçalarıdır.

JavaScript'te olduğu gibi, TypeScript'te de bir fonksiyon tanımlamak için `function` anahtar sözcüğünü kullanırsınız:

```ts
function name(parameter: type, parameter:type,...): returnType {
   // do something
}
```

JavaScript'in aksine TypeScript, bir fonksiyonun parametrelerinde ve dönüş değerinde tip ek açıklamalarını kullanmanıza izin verir.

Aşağıdaki `add()` fonksiyonu örneğini görelim:

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

Bu örnekte, `add()` fonksiyonu sayı tipinde iki parametre kabul eder.

`add()` fonksiyonunu çağırdığınızda, TypeScript derleyicisi, sayı olduklarından emin olmak için fonksiyona aktarılan her parametreyi kontrol eder.

`add()` fonksiyonu örneğinde, fonksiyona yalnızca sayıları parametre olarak geçebilirsiniz, diğer tiplerin değerlerini geçemezsiniz.

Aşağıdaki kod, `add()` fonksiyonuna iki sayı yerine iki string geçtiği için bir hatayla sonuçlanacaktır:

```ts
let sum = add('10', '20');
```

Hata:

```ts
error TS2345: Argument of type '"10"' is not assignable to parameter of type 'number'
```

Fonksiyon parametrelerinin tipleri de tip denetimi için fonksiyon gövdesi içinde mevcuttur.

Parantezlerden sonra gelen `: number` dönüş tipini gösterir. Bu durumda `add()` fonksiyonu `number` tipinde bir değer döndürür.

Bir fonksiyonun dönüş tipi olduğunda, TypeScript derleyicisi dönüş değerinin dönüş tipiyle uyumlu olduğundan emin olmak için her dönüş ifadesini dönüş tipine göre kontrol eder.

Bir fonksiyon bir değer döndürmüyorsa, dönüş tipi olarak `void` tipini kullanabilirsiniz. `void` anahtar sözcüğü, fonksiyonun herhangi bir değer döndürmediğini belirtir. Örneğin:

```ts
function echo(message: string): void {
    console.log(message.toUpperCase());
}
```

Void, fonksiyonun içindeki kodun bir değer döndürmesini engeller ve çağıran kodun fonksiyonun sonucunu bir değişkene atamasını durdurur.

Dönüş tipine açıklama eklemediğinizde, TypeScript uygun bir tip çıkarmaya çalışır. Örneğin:

```ts
function add(a: number, b: number) {
    return a + b;
}
```

Bu örnekte, TypeScript derleyicisi `add()` fonksiyonunun dönüş tipini beklenen sayı tipine çıkarmaya çalışır.

Ancak, bir fonksiyonun farklı tipler döndüren farklı dalları varsa, TypeScript derleyicisi union tipini veya herhangi bir tipi çıkarabilir.

Bu nedenle, bir fonksiyona mümkün olduğunca tip ek açıklamaları eklemek önemlidir.

## Özet

Çağıran kodu satır içinde tutmak ve fonksiyon gövdesi içinde tip denetimini sağlamak için fonksiyon parametreleri ve dönüş tipi için tip ek açıklamaları kullanabilirsiniz.
