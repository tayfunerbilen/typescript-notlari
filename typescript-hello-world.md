# Node.js'de TypeScript "Hello World" Programı

1. Çalışmak için bir klasör oluşturun. Örneğin: `helloworld`
2. VSCode'u başlatın ve ilgili klasörü açın.
3. `app.ts` adında bir typescript dosyası oluşturun.
4. Oluşturduğunuz dosyaya aşağıdaki kodları yazın:

```ts
let message: string = 'Hello, World!';
console.log(message);
```

5. Terminali başlatın. Bunun için `Terminal > Yeni Terminal` menüsünü kullanabilirsiniz.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/TypeScript-Hello-World-Launch-Terminal.png)

6. TypeScript'i JavaScript'e compile etmek için şu komutu çalıştırın:

```shell
tsc app.ts
```

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/TypeScript-Hello-World-compile-TS-file.png)

Eğer her şey yolunda gittiyse, TypeScript Compiler tarafından oluşturulmuş `app.js` adında yeni bir dosya göreceksiniz.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/TypeScript-Hello-World-Output-file.png)

Node.js'de `app.js` dosyasını çalıştırmak için:

```shell
node app.js
```

Bir önceki bölümde bahsedilen `ts-node` paketini yüklediyseniz, TypeScript'i compile eden ve çıktıyı çalıştıran komutu tek satıra indirebilirsiniz:

```shell
ts-node app.ts
```
