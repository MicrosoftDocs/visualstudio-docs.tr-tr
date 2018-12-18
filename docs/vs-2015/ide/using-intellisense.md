---
title: IntelliSense kullanma | Microsoft Docs
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
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 586a0b31166f3b7696865e54f7d2df9c415315f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197203"
---
# <a name="using-intellisense"></a>IntelliSense Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense; Üyeleri Listeleme, Parametre Bilgisi, Hızlı Bilgi ve Tam Sözcük gibi bir dizi özellik için kullanılan genel bir terimdir. Bu özellikler, yalnızca birkaç tuş vuruşu ile kullandığınız kod hakkında daha fazla bilgi edinmenize, yazmakta olduğunuz parametreleri izlemenize ve özellik ve yöntem çağrıları eklemenize yardımcı olur.  
  
 IntelliSense'in birçok yönü dile özgüdür. Farklı dillere yönelik IntelliSense hakkında daha fazla bilgi için Ayrıca Bkz. altında listelenen konulara bakın.  
  
## <a name="list-members"></a>Üyeleri Listeleme  
 Bir tetikleyici karakteri yazdıktan sonra bir tür (veya ad alanı) geçerli üyelerin listesi görüntülenir (örneğin, bir süre (`.`) yönetilen kodda veya `::` C++'ta). Karakterleri yazmaya devam ederseniz, liste yalnızca bu karakterlerle başlayan üyeleri içerecek şekilde filtrelenir.  
  
 Bir öğeyi seçtikten sonra SEKME tuşuna basarak veya bir boşluk girerek öğeyi kodunuza ekleyebilirsiniz. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.  
  
 Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simgelerin bir listesi için bkz. [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Liste oldukça uzun olabilir; bu yüzden listede yukarı veya aşağı gitmek için PAGE UP ve PAGE DOWN tuşlarına basabilirsiniz.  
  
 ![Visual Studio üye listesi](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")  
  
 Çağırabilirsiniz **üyeleri Listele** CTRL + J tıklayarak yazarak el ile özellik **Düzenle/IntelliSense/liste üyelerini**, veya **üyeleri Listele** Düzenleyici düğmesi araç çubuğu. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.  
  
 Üyeleri listeleme (BT'nin özellikle görünmemesi için) varsayılan olarak devre dışı bırakmak için Git **Araçlar/Seçenekler/tüm diller** ve seçimini **otomatik üyeleri Listele**. Yalnızca belirli bir dil için liste üyelerini devre dışı bırakmak isterseniz, Git **genel** bu dil için ayarlar.  
  
 Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Örneğin, listede olmayan bir tanımlayıcı girip SEKME tuşuna basarsanız, tamamlama modunda bu giriş yazılan tanımlayıcının yerini alır. Tamamlama modu ile öneri modu arasında geçiş yapmak için CTRL + ALT + ARA ÇUBUĞU tuşlarına basın veya **Düzenle/IntelliSense/tamamlama modunu**.  
  
## <a name="parameter-info"></a>Parametre Bilgisi  
 Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.  
  
 Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklenmiş işlevler için, işlev aşırı yüklerine ilişkin alternatif parametre bilgilerini görüntülemek üzere YUKARI ve AŞAĞI ok tuşlarını kullanabilirsiniz.  
  
 ![Parametre bilgisi](../ide/media/vs2015-param-info.png "VS2015_param_Info")  
  
 XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için [XML kodu açıklamalarını sağlama](../ide/supplying-xml-code-comments.md).  
  
 Tıklayarak parametre bilgisini el ile çağırabilirsiniz **IntelliSense/parametre bilgilerini Düzenle**, CTRL + SHIFT + Ara çubuğu tuşlarına basarak veya tıklayarak **parametre bilgisi** Düzenleyici araç çubuğunda düğme.  
  
## <a name="quick-info"></a>Hızlı Bilgi  
 Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.  
  
 ![Visual Studio hızlı bilgi](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")  
  
 Bir üye seçtiğinizde **üyeleri Listele** kutusunda, hızlı bilgi de görünür.  
  
 ![Parametre bilgisi bir c&#35; kod dosyası](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")  
  
 Tıklayarak hızlı Bilgi'yi el ile çağırabilirsiniz **Düzenle/IntelliSense/hızlı bilgi**, CTRL + ı tuşlarına basarak veya tıklayarak **hızlı bilgi** Düzenleyici araç çubuğunda düğme.  
  
 Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.  
  
 Ayarlayarak C++ kapalı hızlı Bilgi'yi kapatabilirsiniz **Araçlar / Seçenekler / metin düzenleyici/C/C + +/ Gelişmiş/otomatik hızlı bilgi** için `false`.  
  
## <a name="complete-word"></a>Tam Sözcük  
 Tam Sözcük, terim belirsizliğini ortadan kaldıracak yeterli sayıda karakter girdikten sonra değişken, komut veya işlev adının kalanını tamamlar. Tıklayarak tam sözcük çağırabilirsiniz **Düzenle/IntelliSense/Sözcük tamamlama**, CTRL + boşluk tuşlarına basarak veya tıklayarak **tam sözcük** Düzenleyici araç çubuğunda düğme.  
  
## <a name="intellisense-options"></a>IntelliSense Seçenekleri  
 IntelliSense seçenekleri varsayılan olarak açıktır. Bunları devre dışı bırakmak için tıklayın **Araçlar/Seçenekler/metin düzenleyici** ve seçimini **parametre bilgileri** veya **otomatik üyeleri Listele** üyeleri listeleme özelliğini istemiyorsanız.  
  
## <a name="troubleshooting-intellisense"></a>IntelliSense Sorunlarını Giderme  
 IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.  
  
 **İmleç, kod bir hatadır.** Eksik bir işlev varsa IntelliSense'i kullanmanız mümkün olmayabilir veya IntelliSense kod öğelerini ayrıştıramayabileceğinden olmayabileceğinden imleç üzerindeki kodda başka bir hata bulunmaktadır. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.  
  
 **İmleç bir kod yorum var.** İmleç, kaynak dosyanızdaki bir açıklamada ise IntelliSense kullanamazsınız.  
  
 **İmleç bir dize sabit değeri var.** İmleç aşağıdaki örnekte olduğu gibi bir dize etrafında tırnak işaretlerinin içinde ise IntelliSense kullanamazsınız:  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Otomatik seçenekler kapalıdır.** Varsayılan olarak, IntelliSense otomatik çalışır, ancak bunu devre dışı bırakabilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'e özel IntelliSense](../ide/visual-basic-specific-intellisense.md)   
 [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md)   
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML Kodu Açıklamalarını Sağlama](../ide/supplying-xml-code-comments.md)



