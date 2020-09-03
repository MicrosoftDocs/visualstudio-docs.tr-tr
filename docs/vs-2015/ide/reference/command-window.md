---
title: Komut penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c3bcac9f320840faaed32d0622f30e4cbd288ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660840"
---
# <a name="command-window"></a>Komut Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Komut** penceresi, komutları veya diğer adları doğrudan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik GELIŞTIRME ortamında (IDE) yürütmek için kullanılır. Herhangi bir menüde görünmeyen menü komutlarını ve komutları çalıştırabilirsiniz. **Komut** penceresini görüntülemek Için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **komut penceresi**' ni seçin.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme
 Bir değişkenin değerini denetlemek için `varA` [Print komutunu](../../ide/reference/print-command.md)kullanın:

```
>Debug.Print varA
```

 Soru işareti (?) için bir diğer addır `Debug.Print` , bu nedenle bu komut de yazılabilir:

```
>? varA
```

 Bu komutun her iki sürümü de değişkenin değerini döndürür `varA` .

## <a name="entering-commands"></a>Komutları girme
 Büyüktür simgesi (), `>` yeni satırlar için istem olarak komut penceresi sol kenarında görüntülenir. Daha önce verilen komutlarda gezinmek için yukarı ok ve aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi bir soru işaretiyle () önyüz `?` .|`? myvar`|
|Anında pencereye geçiş yapın.|`immed`Büyüktür işareti olmadan pencereye girin (>)|`immed`|
|Hemen bir pencereden Komut penceresi geri dönün.|`cmd`Pencereye girin.|`>cmd`|

 Aşağıdaki kısayollar, komut modundayken gezinmenize yardımcı olur.

|Eylem|İmleç konumu|KeyBinding|
|------------|---------------------|----------------|
|Daha önce girilen komutların listesi boyunca ilerleyin.|Giriş çizgisi|YUKARı OK & AŞAĞı OK|
|Pencereyi yukarı kaydırın.|Komut penceresi içeriği|CTRL+YUKARI OK|
|Pencereyi aşağı kaydırın.|Komut penceresi içeriği|AŞAĞı ok veya CTRL + aşağı ok|

> [!TIP]
> Önceki bir komutun tümünü veya bir kısmını giriş satırına kaydırarak, bu bölümün tümünü veya bir kısmını vurgulayarak ENTER tuşuna basarak ekleyebilirsiniz.

## <a name="mark-mode"></a>İşaret modu
 **Komut** penceresinde önceki herhangi bir satıra tıkladığınızda, işaret moduna otomatik olarak kaydırma yapabilirsiniz. Bu, herhangi bir metin düzenleyicisinde yaptığınız gibi önceki komutların metnini seçmenizi, düzenlemenizi ve kopyalamanızı sağlar ve bunları geçerli satıra yapıştırabilirsiniz.

## <a name="the-equals--sign"></a>Eşittir (=) Işareti
 Komutun girilmesi için kullanılan pencere, `EvaluateStatement` bir eşittir işaretinin (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

 **Komut** penceresinde, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. **Komut** penceresinde atama işleçlerini kullanamazsınız. Bu nedenle, örneğin, değişkenlerin değerleri `varA` ve `varB` farklıysa, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 , bir değeri döndürür `False` .

 **Hemen** penceresinde, aksine, bir eşittir işareti (=) bir atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 değişkenin değeri değişkene atanır `varA` `varB` .

## <a name="parameters-switches-and-values"></a>Parametreler, anahtarlar ve değerler
 Bazı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutlarda gerekli ve isteğe bağlı bağımsız değişkenler, anahtarlar ve değerler vardır. Belirli kurallar söz konusu komutlarla ilgilenirken geçerlidir. Aşağıda, terminolojiyi açıklığa kavuşturmak için zengin bir komuta bir örnek verilmiştir.

```
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

 Bu örnekte

- `Edit.ReplaceInFiles` komut

- `/case` ve `/pattern:regex` anahtarlardır (eğik çizgi [/] karakteriyle önceden başlar)

- `regex``/pattern`anahtarın değeri; `/case` anahtarın değeri yok

- `var[1-3]+` ve `oldpar` parametreleri

  > [!NOTE]
  > Boşluk içeren herhangi bir komutun, parametrenin, anahtarın veya değerin her iki tarafta da çift tırnak işareti olmalıdır.

  Anahtar ve parametrelerin konumu, komut satırında, anahtar ve parametrelerini belirli bir sırada gerektiren [kabuk](../../ide/reference/shell-command.md) komutu hariç olmadan serbestçe değiştirilebilir.

  Bir komutun desteklediği neredeyse her anahtarın iki formu vardır: kısa (bir karakter) form ve uzun bir form. Birden çok kısa formlu anahtar, bir grup içinde birleştirilebilir. Örneğin, `/p /g /m` Alternatif olarak ifade edilebilir `/pgm` .

  Kısa biçimli anahtarlar bir grup içinde birleştirilirse ve bir değer verildiyse, bu değer her anahtar için geçerli olur. Örneğin, `/pgm:123` ile eşleledir `/p:123 /g:123 /m:123` . Gruptaki anahtarların herhangi biri bir değer kabul etmediğinde bir hata oluşur.

## <a name="escape-characters"></a>Kaçış karakterleri
 Komut satırında bir şapka işareti (^) karakteri, bir denetim karakteri olarak değil, bundan hemen sonra gelen karakterin bir şekilde yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini ("), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin,

```
>Edit.Find ^^t /regex
```

 Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır. Burada gösterilen örnekte, "^ t" deseninin nasıl aranacağı gösterilmektedir.

## <a name="use-quotes-for-path-names-with-spaces"></a>Boşluk içeren yol adları için tırnak Işaretleri kullanma
 Örneğin, boşluk içeren bir yolu olan bir dosyayı açmak isterseniz, boşluk içeren yolun veya yol segmentinin çevresine çift tırnak koymanız gerekir: **C: \\ "Program Files"** veya **"C:\Program Files"**.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
