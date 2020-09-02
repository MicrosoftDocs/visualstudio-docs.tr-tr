---
title: Komut penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3177c92713f6fdeb9b9b8a47a0da38608714174d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651276"
---
# <a name="immediate-window"></a>Komut Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Komut** penceresi, ifadeleri hata ayıklamak ve değerlendirmek, deyimleri yürütmek, değişken değerlerini yazdırmak, vb. için kullanılır. Hata ayıklama sırasında geliştirme dili tarafından değerlendirilecek veya yürütülecek ifadeler girmenize olanak sağlar. **Hemen** penceresini göstermek için, bir projeyi düzenlemeniz için açın, ardından **Hata Ayıkla** menüsünde **Windows** ' u seçin ve **Hemen**' i seçin veya Ctrl + alt + ı tuşlarına basın.

 Bu pencereyi, tek tek komutlar vermek için kullanabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Kullanılabilir komutlar `EvaluateStatement` , değişkenlere değer atamak için kullanılabilecek içerir. **Komut** penceresi de IntelliSense 'i destekler.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme
 Bu pencere özellikle bir uygulamada hata ayıklarken yararlı olabilir. Örneğin, bir değişkenin değerini denetlemek için `varA` [Print komutunu](../../ide/reference/print-command.md)kullanabilirsiniz:

```
>Debug.Print varA
```

 Soru işareti (?) için bir diğer addır `Debug.Print` , bu nedenle bu komut de yazılabilir:

```
>? varA
```

 Bu komutun her iki sürümü de değişkenin değerini döndürür `varA` .

> [!NOTE]
> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Hemen** penceresinde bir komut vermek için, komutun işaretini büyüktür işareti (>) ile önceden başlatmalısınız. Birden çok komut girmek için, **komut** penceresine geçin.

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanında bir işlevi veya alt yordamı yürütmek için **hemen** penceresini kullanabilirsiniz.

#### <a name="to-execute-a-function-at-design-time"></a>Tasarım zamanında bir işlevi yürütmek için

1. Aşağıdaki kodu bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] konsol uygulamasına kopyalayın:

   ```
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. **Hata Ayıkla** menüsünde **Windows**' a ve ardından **hemen**' e tıklayın.

3. `?MyFunction(2)` **Hemen** penceresine yazın ve ENTER tuşuna basın.

    **Komut** penceresi çalışacaktır `MyFunction` ve görüntülenir `4` .

   İşlev veya alt yordam bir kesme noktası içeriyorsa, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uygun noktada yürütmeyi keser. Daha sonra program durumlarınızı incelemek için hata ayıklayıcı pencerelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında hata ayıklama](../../debugger/walkthrough-debugging-at-design-time.md).

   [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)]Projeler, Web projeleri, akıllı cihaz projeleri ve SQL projeleri dahil olmak üzere bir yürütme ortamının başlatılması gereken proje türlerinde tasarım zamanı ifade değerlendirmesi kullanamazsınız.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çoklu proje çözümlerinde tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanı ifade değerlendirmesi için bağlam oluştururken, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Çözüm Gezgini Şu anda seçili olan projeye başvurur. Çözüm Gezgini hiçbir proje seçilmezse, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] işlevi başlangıç projesine göre değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilemez, bir hata iletisi alırsınız. Çözüm için başlangıç projesi olmayan bir projedeki bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini ' de projeyi seçip değerlendirmeyi yeniden deneyin.

## <a name="entering-commands"></a>Komutları girme
 Komutları komut penceresinde verirken büyüktür işareti (>) girmelisiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . **Immediate** Daha önce verilen komutlarda gezinmek için yukarı ok ve aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi bir soru işaretiyle (?) önyüz.|`? a+b`|
|Komut modunu anında modda (tek bir komut yürütmek için) geçici olarak girin.|Komutu, işareti daha büyük (>) ile önceden girerek girin.|`>alias`|
|Komut penceresi geçin.|`cmd`Pencereye, daha büyüktür işareti (>) ile önceden girerek girin.|`>cmd`|
|Anında pencereye geri dönün.|`immed`Büyüktür işareti (>) olmadan pencereye girin.|`immed`|

## <a name="mark-mode"></a>İşaret modu
 **Hemen** penceredeki herhangi bir önceki satıra tıkladığınızda, işaret moduna otomatik olarak kaydırma yapabilirsiniz. Bu, herhangi bir metin düzenleyicisinde yaptığınız gibi önceki komutların metnini seçmenizi, düzenlemenizi ve kopyalamanızı sağlar ve bunları geçerli satıra yapıştırabilirsiniz.

## <a name="the-equals--sign"></a>Eşittir (=) Işareti
 Komutun girilmesi için kullanılan pencere, `EvaluateStatement` bir eşittir işaretinin (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

 **Hemen** penceresinde bir eşittir işareti (=) atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 değişkenin değeri değişkene atanır `varA` `varB` .

 **Komut** penceresinde, aksine, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. **Komut** penceresinde atama işlemlerini kullanamazsınız. Bu nedenle, örneğin, değişkenlerin değerleri `varA` ve `varB` farklıysa, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 , bir değeri döndürür `False` .

## <a name="first-chance-exception-notifications"></a>Birinci şans özel durum bildirimleri
 Bazı ayar yapılandırmalarında, ilk şans özel durum bildirimleri **komut** penceresinde görüntülenir.

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>İlk şans özel durum bildirimlerini hemen pencerede değiştirmek için

1. **Görünüm** menüsünde **diğer pencereler**' e tıklayın ve **Çıkış**' a tıklayın.

2. **Çıkış** penceresinin metin alanına sağ tıklayın ve **özel durum iletileri**' ni seçin veya seçimini kaldırın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da](../../debugger/debugging-in-visual-studio.md) hata ayıklayıcı [komut penceresi](../../ide/reference/command-window.md) hata ayıklaması [ile kod arasında gezinirken](../../debugger/navigating-through-code-with-the-debugger.md) , [Visual Studio](../../debugger/debugger-basics.md) ['da normal ifadeler kullanarak](../../ide/using-regular-expressions-in-visual-studio.md) Visual [Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md) hata [ayıklaması yapın.](../../debugger/walkthrough-debugging-at-design-time.md)
