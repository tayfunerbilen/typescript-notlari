# TypeScript Kurulumu

**Özet:** Bu bölümde TypeScript geliştirme ortamının nasıl kurulacağını öğreneceksiniz.

### Ders Videosu
[![Videolu Ders](https://i.ytimg.com/vi/w95wP6azdRU/maxresdefault.jpg)](https://www.youtube.com/watch?v=w95wP6azdRU)

TypeScript yazmaya başlamak için gerekli araçların kurulumu:

- Node.js - TypeScript compiler'ı çalıştırmak için gerekli program. Nodejs bilmenize gerek yok.
- TypeScript Compiler - TypeScript'den JavaScript'e compile etmek için gerekli modül. Eğer nodejs'de TypeScript kullanıyorsanız `ts-node` paketini kurabilirsiniz. 
- VSCode - TypeScript'i destekleyen bir kod editörü. Önerilir, ancak herhangi bri kod editörü de kullanabilirsiniz.

Eğer VSCode kullanıyorsanız, geliştirme sürecinizi hızlandırmak için aşağıdaki eklentiyi de yükleyebilirsiniz:

- Live Server - Değişiklikleri anında görebilmenizi sağlayan local bir server kurar.

## Node.js Kurulumu

Node.js'i yüklemek için şu adımları takip edin:
- Node.js indirme sayfasına [gidin](https://nodejs.org/en/download/)
- İşletim sisteminize uygun olan sürümünü indirin.
- İnen dosyayı çalıştırıp kurulumu gerçekleştirin.
- Kurulumu doğrulamak için terminalinizi açıp `node -v` komutunu çalıştırın, eğer bir sürüm bilgisi alıyorsanız başarıyla yüklenmiştir.

## TypeScript Compiler Kurulumu

TypeScript Compiler'ı kurmak için, terminalinizi açın ve aşağıdaki komutu çalıştırın.

```shell
npm install -g typescript
```

Yükleme bittikten sonra, yüklendiğini doğrulmak için versiyon kontrolü yapabilirsiniz.

```shell
tsc --v
```

`ts-node` paketini global olarak yüklemek için şu komutu çalıştırabilirsiniz:

```shell
npm install -g ts-node
```

## VSCode Kurulumu

VSCode'u yüklemek için şu adımları takip edin:
- VSCode indirme sayfasına [gidin](https://code.visualstudio.com/download)
- İşletim sisteminize uygun olan son sürümünü indirin.
- İndirdiğiniz programı çalıştırın ve kurulumu gerçekleştirin.
- VSCode'u başlatın.

Eğer her şey başarılıysa şöyle bir ekran göreceksiniz.

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/vs-code.png)

Live Server eklentisini yüklemek için şu adımları takip edin:

![](https://www.typescripttutorial.net/wp-content/uploads/2020/05/Live-Server.png)

- Eklentiler tabına basın.
- live server yazıp aratın.
- Yükleme butonuna basıp eklentiyi kurun.

Bu bölümde TypeScript çalıştırmak için gerekli ortamların kurulumunu öğrendiniz. Tebrikler :)

----

| 👈  Önceki Bölüm  | Sonraki Bölüm  👉 |
| ------------- | ------------- |
| [TypeScript Nedir?](./typescript-nedir.md) | [TypeScript, 'Hello, World!'](./typescript-hello-world.md) |
