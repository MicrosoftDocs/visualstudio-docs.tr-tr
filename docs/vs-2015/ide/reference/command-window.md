---
title: Komut penceresi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83a9e86aea02e27242a0c1f02ca3f8459152214
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870191"
---
# <a name="command-window"></a>Komut Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Komut** penceresi komutları veya doğrudan diğer adlar yürütmek için kullanılan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE). Hiçbir araç çubuğunda hem menü komutları hem de görünmez komutları yürütebilir. Görüntülenecek **komut** penceresinde seçin **diğer Windows** gelen **görünümü** seçin ve menü **komut penceresi**.  
  
## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme  
 Bir değişkenin değerini denetlemek için `varA`, kullanın [Yazdır komutu](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Soru işareti (?) için bir diğer addır `Debug.Print`, bu komut ayrıca yazılabilir:  
  
```  
>? varA  
```  
  
 Bu komutun her iki sürümü değişkenin değerini döndürecektir `varA`.  
  
## <a name="entering-commands"></a>Komutlar girme  
 Sembol büyüktür (`>`) komut penceresinde sol ucuna yeni satırlar için bir istem görüntülenir. Önceden yayınlanan komutlarda gezinmek için Yukarı Ok ve aşağı ok tuşlarını kullanın.  
  
|Görev|Çözüm|Örnek|  
|----------|--------------|-------------|  
|İfadeyi değerlendirir.|İfade bir soru işareti ile yazdığınızdan (`?`).|`? myvar`|  
|Hemen bir penceresine geçin.|Girin `immed` pencereye büyüktür işareti (>) olmadan|`immed`|  
|Bir komut penceresi komut penceresine geçin.|Girin `cmd` penceresine.|`>cmd`|  
  
 Aşağıdaki kısayol tuşlarını komut modundayken gezinmenize yardımcı olur.  
  
|Eylem|İmleç konumu|Tuş|  
|------------|---------------------|----------------|  
|Daha önce girilen komutların listesini geçiş yapın.|Giriş satırı|YUKARI OK VE AŞAĞI OK|  
|Penceresini kaydırın.|Komut penceresi içeriği|CTRL + YUKARI OK|  
|Pencere aşağı kaydırın.|Komut penceresi içeriği|Aşağı Ok veya CTRL + AŞAĞI OK|  
  
> [!TIP]
>  İçin kaydırma, bir kısmını veya tamamını vurgulama ve ardından ENTER tuşuna basarak, giriş satırına önceki komutun bir kısmını veya tamamını kopyalayabilirsiniz.  
  
## <a name="mark-mode"></a>İşaret modu  
 İçinde herhangi bir önceki satırdaki tıkladığınızda **komut** penceresinde tıklattığınızda, otomatik olarak işaretleme moduna. Bu, seçin, düzenleme ve herhangi bir metin düzenleyicisinde yaptığınız ve bunları geçerli satıra yapıştırmanıza gibi önceki komutların metnini kopyalamak sağlar.  
  
## <a name="the-equals--sign"></a>Eşittir (=) işareti  
 Girmek için kullanılan pencere `EvaluateStatement` komut belirleyen bir eşittir işareti (=) karşılaştırma işleci veya bir atama işleci olarak yorumlanır.  
  
 İçinde **komut** penceresinde, eşittir işareti (=) karşılaştırma işleci yorumlanır. Atama İşleçleri kullanamazsınız **komut** penceresi. Örneğin, bu nedenle, değişkenlerin değerleri `varA` ve `varB` farklı, sonra komutu  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 bir değeri döndürür `False`.  
  
 İçinde **hemen** penceresinde, aksine, eşittir işareti (=) bir atama işleci yorumlanır. Bunu, örneğin, komut  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 atar `varA` değişkenin değerini `varB`.  
  
## <a name="parameters-switches-and-values"></a>Parametreler, anahtarlar ve değerler  
 Bazı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutları gerekli ve isteğe bağlı bağımsız değişkenler, anahtarları ve değerleri. Belirli kurallar gibi komutları ile ilgilenirken uygulanır. Aşağıdaki terimler açıklamak için zengin bir komutun bir örneğidir.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 Bu örnekte,  
  
- `Edit.ReplaceInFiles` Bu komut  
  
- `/case` ve `/pattern:regex` olan anahtarları (eğik çizgi [/] karakteriyle başlar)  
  
- `regex` değeri `/pattern` geçin; `/case` anahtar değere sahip değil  
  
- `var[1-3]+` ve `oldpar` parametreleri  
  
  > [!NOTE]
  >  Komutu, parametre, anahtar veya boşluk içeren değer iki tarafında çift tırnak işareti olmalıdır.  
  
  Anahtarlar ve parametreleri konumunu serbestçe dışında komut satırında deyimleri [Kabuk](../../ide/reference/shell-command.md) komutu, belirli bir sırayla parametreler ve anahtarlar gerektirir.  
  
  Neredeyse tüm anahtar komutu tarafından desteklenen iki biçimi vardır: bir kısa (bir karakter) formunu ve uzun biçimi. Bir gruba birden çok kısa biçimli anahtar birleştirilebilir. Örneğin, `/p /g /m` dönüşümlü olarak ifade edilebilir `/pgm`.  
  
  Kısa form anahtarları bir gruba birleştirilir ve verilen bir değer, bu değer her geçiş için geçerlidir. Örneğin, `/pgm:123` karşılık gelir `/p:123 /g:123 /m:123`. Herhangi bir grup anahtarları kabul etmiyor, değeri bir hata meydana gelir.  
  
## <a name="escape-characters"></a>Kaçış karakterleri  
 Aşağıdaki yerine birebir yorumlandığı bir denetim karakteri olarak yorumlanır hemen komut satırında bir şapka (^) karakter, karakter anlamına gelir. Bu anahtar adları dışında bir parametre veya anahtar değerine düz tırnak ("), boşluk, önde gelen eğik çizgiler, düzeltme işaretleri veya diğer bir hazır bilgi karakterleri katıştırmak için kullanılabilir. Örneğin,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 İç veya dış tırnak işaretleri olup olmadığını şapka işareti aynı şekilde çalışır. Şapka işareti satırdaki son karakterse, yoksayılır. Burada gösterilen örnek deseni araması yapmayı gösteren "^ t".  
  
## <a name="use-quotes-for-path-names-with-spaces"></a>Yol adları boşluk için tırnak işareti kullanın  
 Örneğin, boşluk içeren bir yola sahip bir dosyayı açmak istiyorsanız yolu veya boşluk içeren bir yol kesimi etrafına çift tırnak işareti yerleştirmeniz gerekir: **C:\\"Program Files"** veya **"C:\Program Files"**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)   
 [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)



