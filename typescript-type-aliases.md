# Tip Takma Adları

**Özet:** Bu bölümde, tip takma adlarını kullanarak tipler için yeni adları nasıl tanımlayacağınızı öğreneceksiniz.

Tip takma adları, mevcut bir tip için yeni bir ad oluşturmanıza olanak tanır. Aşağıda tip takma adının sözdizimi gösterilmektedir:

```ts
type alias = existingType;
```

`existingType`, geçerli herhangi bir TypeScript tipi olabilir.

Aşağıdaki örnekte, string tipi için takma ad olarak `chars` kullanılmaktadır:

```ts
type chars = string;
let messsage: chars; // string tipi ile aynı
```

Union tipleri için tip takma adları oluşturmak yararlıdır. Örneğin:

```ts
type alphanumeric = string | number;
let input: alphanumeric;
input = 100; // valid
input = 'Hi'; // valid
input = false; // Compiler error
```

## Özet

Mevcut tiplere yeni adlar tanımlamak için tip takma adlarını kullanın.
