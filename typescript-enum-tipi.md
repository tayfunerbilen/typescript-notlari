# TypeScript Enum Tipi

Enum, isimlendirilmiş sabit değerler grubu olarak tanımlanabilir. Enum'un açılımı `enumerated` dir.

Bir `enum` tanımlamak için:

- `enum` tanımından sonra ismi gelir.
- Sabit değerler `enum` içinde tanımlanır.

Aşağıdaki örnek yılın aylarını temsil eden bir `enum` örneğidir.

```ts
enum Month {
    Jan,
    Feb,
    Mar,
    Apr,
    May,
    Jun,
    Jul,
    Aug,
    Sep,
    Oct,
    Nov,
    Dec
};
```

Aşağıdaki fonksiyon parametre olarak `Month` enum tipini almaktadır.

```ts
function isItSummer(month: Month) {
    let isSummer: boolean;
    switch (month) {
        case Month.Jun:
        case Month.Jul:
        case Month.Aug:
            isSummer = true;
            break;
        default:
            isSummer = false;
            break;
    }
    return isSummer;
}
```

ve şu şekilde kullanılmaktadır:

```ts
console.log(isItSummer(Month.Jun)); // true
```

## TypeScript `enum` Nasıl Çalışıyor?

Yukarıdaki örnekte parametre olarak sabit değer olan `Jun` geçtiğimizi görebilirsiniz.

Ancak bunun yerine elbette sayı parametresi de geçebilirdik.

```ts
console.log(isItSummer(6)); // true
```

Örnekte `Jun` yerine `6` değerini geçtik. Ve bu da çalışmaktadır.

Gelin bir de JavaScript'de `enum` nasıl compile ediliyor ona bakalım.

```js
var Month;
(function (Month) {
    Month[Month["Jan"] = 0] = "Jan";
    Month[Month["Feb"] = 1] = "Feb";
    Month[Month["Mar"] = 2] = "Mar";
    Month[Month["Apr"] = 3] = "Apr";
    Month[Month["May"] = 4] = "May";
    Month[Month["Jun"] = 5] = "Jun";
    Month[Month["Jul"] = 6] = "Jul";
    Month[Month["Aug"] = 7] = "Aug";
    Month[Month["Sep"] = 8] = "Sep";
    Month[Month["Oct"] = 9] = "Oct";
    Month[Month["Nov"] = 10] = "Nov";
    Month[Month["Dec"] = 11] = "Dec";
})(Month || (Month = {}));
```

Ve `Month` değişkenini console'a bastığınızda şöyle bir sonuç göreceksiniz:

```js
{
  '0': 'Jan', 
  '1': 'Feb', 
  '2': 'Mar', 
  '3': 'Apr', 
  '4': 'May', 
  '5': 'Jun', 
  '6': 'Jul', 
  '7': 'Aug', 
  '8': 'Sep', 
  '9': 'Oct', 
  '10': 'Nov',
  '11': 'Dec',
  Jan: 0,     
  Feb: 1,     
  Mar: 2,     
  Apr: 3,     
  May: 4,
  Jun: 5,
  Jul: 6,
  Aug: 7,
  Sep: 8,
  Oct: 9,
  Nov: 10,
  Dec: 11
}
```

Çıktıdan da anlaşılacağı üzere, TypeScript enum aslında bir JavaScript objesidir. İsim ve değer, değer ve isim şeklinde bir objeyi temsil eder.

Bu örnekten de anlaşılacağı gibi, başlangıç sayısını değiştirmekte mümkündür. Yani ilk ay 0'dan değilde 1'den de başlayabilirdi.

## `enum` Başlangıç Sayısını Belirlemek

Bir enum tanımladığınızda öğe sayısı kadar 0'dan başlayarak numaralandırılır. Başlangıç sayısını 0 değilde başka bir değerden başlatmakta mümkündür.

```ts
enum Month {
    Jan = 1,
    Feb,
    Mar,
    Apr,
    May,
    Jun,
    Jul,
    Aug,
    Sep,
    Oct,
    Nov,
    Dec
};
```

## Ne Zaman `enum` Kullanılır

- Birbiriyle ilişkili az sayıda sabit değerleriniz varsa
- Ve bu değerler compile-time'da biliniyorsa.

Örneğin, enum'ı durumlar için tanımlayabilirdik:

```ts
enum ApprovalStatus {
    draft,
    submitted,
    approved,
    rejected
};
```

Ve şu şekilde erişip kullanabilirdik:

```ts
const request =  {
    id: 1,
    status: ApprovalStatus.approved,
    description: 'Please approve this request'
};

if(request.status === ApprovalStatus.approved) {
    // send an email
    console.log('Send email to the Applicant...');
}
```
