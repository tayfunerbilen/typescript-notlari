# TypeScript "Hello, World!"

**Özet:** Bu bölümde, en basit typescript uygulamasının nasıl geliştirildiğini öğreneceksiniz.

## Node.js'de TypeScript "Hello World" Programı

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

## Web Tarayıcı'da TypeScript "Hello World" Programı

1. `index.html` adında bir dosya oluşturun ve `app.js` dosyanızı sayfaya çağırın.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TypeScript: Hello, World!</title>
</head>
<body>
    <script src="app.js"></script>
</body>
</html>
```

2. Üstte oluşturduğunuz `app.ts` dosyanızı açın ve kodları şöyle değiştirin:

```ts
let message: string = 'Hello, World!';
// h1 etiketi oluşturuyoruz
let heading = document.createElement('h1');
heading.textContent = message;
// h1 etiketini dökümana ekliyoruz
document.body.appendChild(heading);
```

3. TypeScript dosyanızı JavaScript'e compile edin.

```shell
tsc app.ts
```

4. Html dosyanıza sağ tıklayıp "Open with Live Server" butonuna basarak local sunucunuzu başlatın.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/TypeScript-Hello-World-Live-Server.png)

Açılan tarayıcı aşağıdaki gibi bir çıktı verecek:

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/TypeScript-Hello-World-Web-Browser.png)

`app.ts` dosyanızıda bir değişiklik yaptığınızda ve bu değişiklikleri tarayıcıda görmek istediğinizde, ilk olarak `.ts` dosyasını compiler ile `.js` dosyasına çeviriyoruz yukarıda olduğu gibi. Ve `Live Server` eklentisi, dosyada bir değişiklik olduğunu anladığı anda sayfayı otomatik yeniliyor ve böylcee son halini ek bir şey yapmadan görebiliyorsunuz tarayıcı üzerinde. 

Unutmayın, `app.js` dosyası compiler tarafından üretiliyor, değişiklikleri bu dosya üzerinde doğrudan yaparsanız bir sonraki compile işleminde bu değişikliklerin üzerine yazılacaktır, bu yüzden her zaman `.ts` dosyasında geliştirmelerinizi yapın.

Bu bölüde node.js ve web tarayıcısında çalışan bir "hell world" yani en basit bir TypeScript örneğinin nasıl olabileceğini gördük.
