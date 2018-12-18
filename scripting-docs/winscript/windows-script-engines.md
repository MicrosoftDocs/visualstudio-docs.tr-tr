---
title: Windows komut dosyası motorları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16e699ee789ae10883152b5d8aa7d8ffee0ddffd
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572627"
---
# <a name="windows-script-engines"></a>Windows Komut Dosyası Motorları
Bir Microsoft Windows komut dosyası altyapısı uygulamak için aşağıdaki arabirimleri destekleyen bir OLE COM nesnesi oluşturun.  
  
|||  
|-|-|  
|Arabirim|Açıklama|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Temel betik yeteneği sağlar. Bu arabirim uygulaması gereklidir.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Betik metin eklemek, ifadeler değerlendirmek ve benzeri olanağı sağlar. Bu arabirim uygulaması isteğe bağlıdır; Bu kullanılırsa, ancak, betik altyapısı IPersist * arabirimlerinden biri, bir komut dosyası yüklemek için uygulanması gereken.|  
|IPersist *|Kalıcılık desteği sağlar. Aşağıdaki arabirimleri en az biri uygulamasıdır gerekli olmadığını [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) uygulanmadı.<br /><br /> IPersistStorage: verileri için destek sağlar = Nesne etiketinde {url} özniteliği.<br /><br /> IPersistStreamInit: aynı için destek sağlar `IPersistStorage` verilerin yanı sıra = "dize olarak kodlanmış bayt akışı" özniteliğini Nesne etiketinde.<br /><br /> IPersistPropertyBag: PARAM için destek sağlar = Nesne etiketinde özniteliği.|  
  
> [!NOTE]
>  Komut dosyası altyapısı asla sonra kaydetmek veya bir komut dosyası durumu aracılığıyla geri yüklemek için çağrılacağı mümkündür `IPersist*`. Bunun yerine, [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) çağırarak kullanılan [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) boş bir komut dosyası oluşturmak için ardından kod parçacıklarını eklenmiş ve olaylarla bağlı [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) ve genel kodu ile eklenir [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Öte yandan, bir komut dosyası motoru tam olarak en az bir uygulamalıdır `IPersist*` arabirimi (tercihen `IPersistStreamInit`), diğer ana bilgisayar uygulamaları yapmaya çünkü bunları kullanın.  
  
 Aşağıdaki bölümlerde daha ayrıntılı olarak bir Windows komut dosyası motoru uygulama açıklanmaktadır.  
  
 Bkz: [Windows komut dosyası arabirimleri başvurusu](../winscript/reference/windows-script-interfaces-reference.md) daha fazla bilgi için.  
  
## <a name="registry-standard"></a>Kayıt defteri standart  
 Bir Windows komut dosyası motoru kendisini kategori kimlikleri kullanarak tanımlayabilirsiniz. Windows komut dosyası şu anda iki kategorisi tanımlayıcı tanımlar.  
  
|||  
|-|-|  
|Kategori|Açıklama|  
|CATID_ActiveScript|Sınıf tanımlayıcıları (CLSID) desteği, en azından Windows komut dosyası motorları olduğunu gösterir [IActiveScript](../winscript/reference/iactivescript.md) arabirimi ve Kalıcılık mekanizması ( `IPersistStorage`, `IPersistStreamInit`, veya IPersistPropertyBag arabirimi).|  
|CATID_ActiveScriptParse|CLSID desteği, en azından Windows komut dosyası motorları olduğunu gösterir [IActiveScript](../winscript/reference/iactivescript.md) ve [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) arabirimleri.|  
  
 Ancak [Iactivescriptparse](../winscript/reference/iactivescriptparse.md) true Kalıcılık mekanizması değil destekliyor mu [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) işlevsel olarak eşdeğerdir yöntemi `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Komut dosyası altyapısı durumları  
 Belirli bir zamanda, bir Windows komut dosyası motoru birkaç durumlardan birinde olabilir.  
  
|||  
|-|-|  
|Durum|Açıklama|  
|başlatılmadı|Komut dosyası değiştirilmediğinden başlatılmamış veya IPersist * arabirim kullanılarak yüklenen veya sahip olmayan bir [Iactivescriptsite](../winscript/reference/iactivescriptsite.md) arabirim kümesi. Komut dosyası yüklenene kadar komut dosyası altyapısı genellikle bu durumdan kullanılabilir değil.|  
|başlatıldı|Komut dosyası ile başlatılmış bir `IPersist*` arabirim ve sahip bir [Iactivescriptsite](../winscript/reference/iactivescriptsite.md) arabirim kümesi, ancak ana bilgisayar nesneleri ve indirme olayları bağlı değil. Bu durum yalnızca, anlamına gelir `IPersist*::Load`, `IPersist*::InitNew`, veya [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) yöntemi tamamlanmış ve [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) yöntemi çağrılır. Kod altyapısı bu modda çalıştırılamaz. Alt yapısı ana bilgisayar üzerinden geçirir kod kuyruklar [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) yöntemi ve başlatıldı durumuna koddan sonra kodu yürütür.<br /><br /> Dilleri semantiği yaygın olarak değişebileceğinden altyapılarının bu durum geçişi desteklemek için gereken değil. Altyapıları destekleyen [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) yöntemi ancak desteklemelidir. Bu durum geçişi. Konaklar için bu geçişi hazırlamak ve uygun eylemi gerçekleştirin: geçerli komut dosyası altyapısı sürüm, yeni bir komut dosyası altyapısı ve çağrı `IPersist*::Load`, `IPersist*::InitNew`, veya [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (ve muhtemelen çağırıp [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). Bu geçiş kullanımını bir en iyi duruma getirme yukarıdaki adımları dikkate alınmalıdır. Herhangi bir bilgi komut dosyası altyapısı adlı öğe adları hakkında sağladığı ve adlı öğeleri açıklayan tür bilgisi geçerli kaldığı unutmayın.<br /><br /> Bu geçiş tam semantiği tanımlama dilleri büyük ölçüde farklılık nedeniyle zordur. En azından, komut dosyası altyapısı gerekir tüm olayları bağlantısını kesmek ve tüm çağırılarak alınır SCRIPTINFO_IUNKNOWN işaretçileri yayın [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemi. Komut dosyası yeniden çalıştırdıktan sonra altyapısı bu işaretçileri yeniden edinmeniz gerekir. Komut dosyası altyapısı ayrıca komut dosyası dili için uygun olan bir ilk duruma geri Sıfırla. VBScript, örneğin, tüm değişkenler sıfırlar ve dinamik olarak çağırarak eklenen herhangi bir kod korur [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) ile SCRIPTTEXT_ISPERSISTENT bayrağı ayarlanmış. Diğer diller geçerli değerleri (hiçbir kod/verilerin ayrılmasını olduğundan Lisp gibi) tutmak mı (statik olarak başlatılmış değişkenleri dillerle içerir) bilinen bir duruma sıfırlayın gerekebilir.<br /><br /> Başlama durumuna geçiş aynı semantiğine sahip olması gerektiğini unutmayın (diğer bir deyişle, bu komut dosyası altyapısı aynı durumda bırakın) arama olarak `IPersist*::Save` kaydetmek için komut dosyası altyapısı ve ardından arama `IPersist*::Load` yeni yüklemek için komut dosyası motoru; bunlar Eylemler aynı topluca olması gerektiğini [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Komut dosyası henüz desteklemeyen altyapılarındaki `IActiveScript::Clone` veya `IPersist*` böylece bu tür bir geçiş Yukarıdaki koşullar, ihlal değil dikkatle nasıl başlama durumuna geçiş hareket etmesi gerektiğini, göz önünde bulundurmalısınız `IActiveScript::Clone` veya `IPersist*` Daha sonra desteği eklendi.<br /><br /> Bu geçişi başlatıldı durumuna sırasında komut dosyası altyapısı olay havuzlarını sonra uygun Yıkıcılar bağlantısını keser ve benzeri komut dosyasında yürütülür. Yürütülen bu Yıkıcılar zorunda kalmamak için konak ilk komut dosyası bağlantısı kesilmiş bir duruma başlatılan bir duruma geçmeden önce taşıyabilirsiniz.<br /><br /> Kullanım [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) çalışan bir komut dosyası iş parçacığının geçerli olaylarını beklemeden iptal etmek ve benzeri için çalışmasının sonlanması.|  
|başlatıldı|Başlatılmış bir durumda geçiş Başlatıldı durumuna sıraya alınması ile başlatılmış durumda herhangi bir kod yürütmek alt neden olur. Altyapı başlatılan durumundayken kod yürütebilir karşın aracılığıyla eklenen olaylara bağlı [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) yöntemi. Altyapı alınan IDispatch arabirimi çağırarak kod yürütebilir [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) yöntemini veya çağırarak [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Daha fazla arka plan başlatmanın (aşamalı yükleme) hala devam eden mümkündür ve bu çağırma [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_CONNECTED bayrağı ayarlanmış yöntemi başlatma işlemi tamamlanana kadar engellemek komut dosyası neden olabilir.|  
|bağlı|Komut dosyası yüklenir ve ana bilgisayar nesnelerinden olayları indirme bağlı. Bu bir geçiş başlatılmış bir durumda ise, komut dosyası altyapısı aracılığıyla bağlantı durumu girerek ve olayları bağlama önce gerekli eylemleri gerçekleştirme başlama durumuna geçiş.|  
|bağlantısı kesilmiş|Komut dosyası yüklenir ve bir çalışma zamanı durumuna sahip, ancak geçici olarak ana bilgisayar nesneleri indirme olaylarından bağlantısı kesilmiş. Bu ya da mantıksal olarak yapılabilir (alınan olaylar yoksayar) ya da fiziksel olarak (uygun bir bağlantı noktalarında IConnectionPoint::Unadvise çağırma). Bu bir geçiş başlatılmış bir durumda ise, komut dosyası altyapısı aracılığıyla bağlantısı kesilmiş bir duruma girmeden önce gerekli eylemleri gerçekleştirme başlatılan durum geçiş. İşlenmekte olan olay havuzlarını önce durum değişiklikleri tamamlandı (kullanmak [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) çalışan bir komut dosyası iş parçacığının iptal etmek için). Bu durum, bu durum geçişi sıfırlamak komut dosyası neden olmaz, komut dosyası çalışma zamanı durumunu sıfırlanır ve bir komut dosyası başlatma yordamı yürütülmedi başlatılmış durumundan ayrılır.|  
|Kapalı|Komut dosyası kapatıldı. Komut dosyası altyapısı artık çalışır ve çoğu yöntemleri için hatalar döndürür.|  
  
 Aşağıdaki çizimde, çeşitli komut dosyası altyapısı durumlarını ilişkileri gösterir ve bir durumdan geçişleri neden yöntemleri gösterir.  
  
 Aşağıdaki çizimde, komut dosyası altyapısı çeşitli durumu geçişleri sırasında yaptığı eylemleri gösterir.  
  
## <a name="scripting-engine-threading"></a>Altyapısı komut dosyası iş parçacığı oluşturma  
 Bir Windows komut dosyası motoru birçok ortamlarda kullanılabildiğinden, yürütme modeli kadar esnek tutmak önemlidir. Örneğin, sunucu tabanlı bir ana bilgisayar, birden çok iş parçacıklı tasarım verimli bir şekilde Windows komut dosyası kullanırken korumak gerekebilir. Aynı zamanda, tipik bir uygulama gibi iş parçacığı oluşturma kullanmayan bir ana bilgisayar yönetimi iş parçacığı ile burdened değil. Windows komut dosyası ana bilgisayarlarını Bu yük boşaltma konağa ücretsiz iş parçacıklı bir komut dosyası altyapısı geri arama yöntemleri kısıtlayarak bu Bakiye erişir.  
  
 Komut dosyası motorları sunucularında kullanılan genellikle ücretsiz iş parçacıklı COM nesneleri olarak uygulanır. Bunun anlamı yöntemlere [IActiveScript](../winscript/reference/iactivescript.md) ve onun ilişkili arabirim çağrılabilir işleminde, herhangi bir iş hazırlama olmadan. (İşlemler arası ücretsiz iş parçacıklı nesnelerin hazırlama OLE şu anda desteklemediği için ne yazık ki, bu da bir işlem sunucusu komut dosyası altyapısı uygulanmalı anlamına gelir.) Eşitleme komut dosyası altyapısı sorumluluğundadır. Dahili olarak desteklemeyeceğini olmayan motorları komut dosyası için ya da birden çok iş parçacıklı olmayan dil modelleri için eşitleme bir mutex sahip komut dosyası motoru erişimi seri hale getirme olarak kadar basit olabilir. Elbette belirli yöntemlerini gibi [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), böylece takılmış bir komut dosyası başka bir iş parçacığından sonlandırılabilir bu şekilde seri hale getirilmemelidir.  
  
 Olgu, [IActiveScript](../winscript/reference/iactivescript.md) genellikle ücretsiz iş parçacıklı, genellikle gelir [Iactivescriptsite](../winscript/reference/iactivescriptsite.md) arabirimi ve ana bilgisayarın nesne modeli olmalıdır ücretsiz iş parçacıklı de. Bu uygulama konağının özellikle konak tek iş parçacıklı Windows tabanlı bir uygulama, nesne modelinde tek iş parçacıklı veya modeli ActiveX denetimleriyle olduğu ortak durumda oldukça zor hale. Bu nedenle, aşağıdaki kısıtlamalar üzerinde komut dosyası altyapısı kullanımını yerleştirilir [Iactivescriptsite](../winscript/reference/iactivescriptsite.md):  
  
 Komut dosyası site her zaman bir ana iş parçacığı bağlamında adı verilir. Diğer bir deyişle, komut dosyası altyapısını hiçbir zaman betik sitenin komut dosyası altyapısı oluşturulan bir iş parçacığı, ancak yalnızca içinden bağlamında bir komut dosyası ana bilgisayar üzerinden çağırıldığı yöntemi altyapısı çağrıları [IActiveScript](../winscript/reference/iactivescript.md) ve sunulan komut dosyası altyapısı gönderme nesnesi, bir Windows ileti yoluyla veya bir olay kaynağı ana bilgisayarın nesne modeli aracılığıyla türevleri.  
  
 Komut dosyası site hiçbir zaman bir basit iş parçacığı durumu denetim yöntemi bağlamında çağrılır (örneğin, [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi) veya [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Komut Dosyası Arabirimleri](../winscript/windows-script-interfaces.md)
