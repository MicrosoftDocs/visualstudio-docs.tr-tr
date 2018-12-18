---
title: Komut Penceresi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27a9da182a2e4db76db0b5221178dfa6dc371723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943004"
---
# <a name="immediate-window"></a>Komut Penceresi
**Hemen** penceresi, hata ayıklama ve ifadelerini değerlendirme, deyimleri yürütme, değişken değerlerini yazdırma vb. için kullanılır. Değerlendirilen veya hata ayıklama sırasında geliştirme dili tarafından yürütülen ifadeleri girmenizi sağlar. Görüntülenecek **hemen** penceresinde düzenlemeye yönelik bir proje açın ve ardından **Windows** gelen **hata ayıklama** menü ve select **hemen**, veya CTRL + ALT + ı tuşlarına basın.

 Bu pencereyi sorunu kişiye kullanabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutları. Kullanılabilir komutlar içeren `EvaluateStatement`, değerleri değişkenlere atamak için kullanılabilir. **Hemen** penceresi de IntelliSense'i destekler.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme
 Bu pencereyi bir uygulamanın hatalarını ayıklama sırasında özellikle yararlı olabilir. Örneğin, bir değişkenin değerini denetlemek için `varA`, kullanabileceğiniz [Yazdır komutu](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

 Soru işareti (?) için bir diğer addır `Debug.Print`, bu komut ayrıca yazılabilir:

```cmd
>? varA
```

 Bu komutun her iki sürümü değişkenin değerini döndürecektir `varA`.

> [!NOTE]
> Sorun için bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutunu **hemen** penceresinde komutun önüne gerekir büyüktür işareti (>). Birden fazla komut girmek için geçin **komut** penceresi.


## <a name="design-time-expression-evaluation"></a>Tasarım zamanı ifade değerlendirmesi
 Kullanabileceğiniz **hemen** tasarım zamanında bir işlev veya alt yordamı yürütmek için pencere.

#### <a name="to-execute-a-function-at-design-time"></a>Tasarım zamanında bir işlevi yürütmek için

1. Aşağıdaki kodu kopyalayın bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] konsol uygulaması:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. Üzerinde **hata ayıklama** menüsünü tıklatın **Windows**ve ardından **hemen**.

3. Tür `?MyFunction(2)` içinde **hemen** penceresi ve Enter tuşuna basın.

    **Hemen** penceresi çalıştırılacağı `MyFunction` ve görüntüleme `4`.

İşlev veya alt yordam bir kesme noktası içeriyorsa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygun noktada yürütmeyi keser. Ardından, programınızın durumunu incelemek için hata ayıklayıcı penceresini kullanabilirsiniz. Daha fazla bilgi için [izlenecek yol: tasarım zamanında hata ayıklama](../../debugger/walkthrough-debugging-at-design-time.md).

Bir yürütme ortamı gerektiren proje türlerinde tasarım zamanı ifade değerlendirmesi kullanamazsınız dahil olmak üzere [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] projeleri, web projeleri, akıllı cihaz projeleri ve SQL projeleri.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çoklu proje çözümlerinde tasarım zamanı ifade değerlendirmesi
 Tasarım zamanı ifade değerlendirmesi için bağlamı oluşturulurken [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çözüm Gezgini'nde seçili olan projeye başvurur. Çözüm Gezgini'nde proje seçtiyseniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlangıç projesine karşı işlevi değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilemezse, bir hata iletisi alırsınız. Çözümün başlangıç projesi olmayan bir projede bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini'nde projeyi seçmeyi deneyin ve değerlendirmeyi yeniden deneyin.

## <a name="entering-commands"></a>Komutlar girme
 Büyüktür (>) verirken oturum girmelisiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutlarını **hemen** penceresi. Önceden yayınlanan komutlarda gezinmek için Yukarı Ok ve aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|İfadeyi değerlendirir.|İfade bir soru işareti (?) ile başlayın.|`? a+b`|
|Komut modu (tek bir komut çalıştırmak için) anlık modundayken geçici olarak girin.|Bunu koyarak komutu girin büyüktür işareti (>).|`>alias`|
|Komut penceresine geçiş yapın.|Girin `cmd` pencereye, önüne büyüktür işareti (>).|`>cmd`|
|Hemen penceresine geçin.|Girin `immed` pencereye büyüktür işareti (>) olmadan.|`immed`|

## <a name="mark-mode"></a>İşaret modu
 İçinde herhangi bir önceki satırdaki tıkladığınızda **hemen** penceresinde tıklattığınızda, otomatik olarak işaretleme moduna. Bu, seçin, düzenleme ve herhangi bir metin düzenleyicisinde yaptığınız ve bunları geçerli satıra yapıştırmanıza gibi önceki komutların metnini kopyalamak sağlar.

## <a name="the-equals--sign"></a>Eşittir (=) işareti
 Girmek için kullanılan pencere `EvaluateStatement` komut belirleyen bir eşittir işareti (=) karşılaştırma işleci veya bir atama işleci olarak yorumlanır.

 İçinde **hemen** penceresinde, eşittir işareti (=) bir atama işleci yorumlanır. Bunu, örneğin, komut

```cmd
>Debug.EvaluateStatement(varA=varB)
```

 atar `varA` değişkenin değerini `varB`.

 İçinde **komut** penceresinde, aksine, eşittir işareti (=) karşılaştırma işleci yorumlanır. Atama işlemlerini kullanamazsınız **komut** penceresi. Örneğin, bu nedenle, değişkenlerin değerleri `varA` ve `varB` farklı, sonra komutu

```cmd
>Debug.EvaluateStatement(varA=varB)
```

 bir değeri döndürür `False`.

## <a name="first-chance-exception-notifications"></a>İlk fırsat özel durum bildirimleri
 Bazı ayar yapılandırmalarında, ilk şans özel durum bildirimleri içinde görüntülenen **hemen** penceresi.

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>İlk fırsat özel durum bildirimleri hemen penceresinde geçiş yapmak için

1.  Üzerinde **görünümü** menüsünde tıklatın **diğer Windows**, tıklatıp **çıkış**.

2.  Metin alanına sağ **çıkış** penceresinde seçin veya seçimini **özel durum iletileri**.

## <a name="see-also"></a>Ayrıca Bkz.

- [Hata Ayıklayıcısı ile Kodlarda gezinme](../../debugger/navigating-through-code-with-the-debugger.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio’da hata ayıklama](../../debugger/debugging-in-visual-studio.md)
- [Hata Ayıklayıcısı Temel Bilgileri](../../debugger/getting-started-with-the-debugger.md)
- [İzlenecek Yol: Tasarım Zamanında Hata Ayıklama](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio'da Normal İfadeler Kullanma](../../ide/using-regular-expressions-in-visual-studio.md)