# TypeScript String Tipi

TypeScript'de de aynı javascript'de olduğu gibi string'ler için çift tırnak ve tek tırnak kullanılır.

```ts
let firstName: string = 'John';
let title: string = "Web Developer";
```

TypeScript aynı zamanda `template string` leri de destekler. Backtick karakteri ile oluşturulan string'leri.

`template string` ler çok satırlı string'ler oluşturmamızı ve interpolasyon uygulamamzı sağlıyor.

```ts
let description = `This TypeScript string can 
span multiple 
lines
`;

// ya da 

let firstName: string = `John`;
let title: string = `Web Developer`;
let profile: string = `I'm ${firstName}. 
I'm a ${title}`;

console.log(profile);
```
