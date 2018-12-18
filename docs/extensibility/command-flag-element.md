---
title: Command Flag öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c963592fd286273e18a0bdf15905693f9f9cf1ce
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233184"
---
# <a name="command-flag-eelement"></a>Bayrağı Eelement komutu
Üst öğesi değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Aşağıdaki bölümde, geçerli öğe değerleri açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|AllowParams|Kullanıcı komut parametrelerinde girebilirsiniz gösterir **komut** penceresini, kurallı komut adını yazın.<br /><br /> Geçerlilik süresi: `Button`|  
|AlwaysCreate|Herhangi bir düğme veya grupları sahip olsa bile menü oluşturulur.<br /><br /> Geçerlilik süresi: `Menu`|  
|CaseSensitive|Kullanıcı girişleri büyük/küçük harfe duyarlıdır.<br /><br /> Geçerlilik süresi: `Combo`|  
|CommandWellOnly|Bu bayrak komutu üst düzey menüsünde görünmüyor ve klavye kısayolu bağlama için ek Kabuğu özelleştirme için kullanılabilir yapmak istiyorsanız geçerlidir. VSPackage'ı yükledikten sonra şu komutları açarak özelleştirebilirsiniz **seçenekleri** iletişim kutusunu ve ardından komut yerleştirme altında düzenleme **klavye ortam** kategorisi. Bu bayrak, yerleştirme kısayol menüleri, araç çubukları, menü denetleyicisi veya alt menüler etkilemez.<br /><br /> İçin geçerli: `Button`, `Combo`|  
|DefaultDisabled|Uyguladığı VSPackage'ı yüklü değilse, varsayılan olarak, komut devre dışı veya `QueryStatus` yöntemi çağrılmadı.<br /><br /> İçin geçerli: `Button`, `Combo`|  
|DefaultDocked|Varsayılan olarak panelin. Her zaman yerleşik olduğundan bu ayarı artık araç çubukları için geçerlidir.|  
|DefaultInvisible|Varsayılan olarak, komut uyguladığı VSPackage'ı yüklü değilse, görünmezdir veya `QueryStatus` yöntemi çağrılmadı.<br /><br /> Şununla Birleştir öneririz `DynamicVisibility` bayrağı.<br /><br /> İçin geçerli: `Button`, `Combo`, `Menu`|  
|DontCache|Geliştirme ortamını önbelleğe almaz `QueryStatus` bu komutun sonuçlarını yöntemi.<br /><br /> Bir menü için bu metin, menü öğelerinin önbelleğe menü denetleyicisi bildirir. Menü dinamik öğeleri veya dinamik metni olan öğeleri içerdiğinde bu bayrağı kullanın.<br /><br /> İçin geçerli: `Button`, `Menu`|  
|DynamicItemStart|Dinamik bir listesi başlangıcını gösterir. Bu sırayla çağırarak listesini oluşturmak bir ortam sunar `QueryStatus` OLECMDERR_E_UNSUPPORTED bayrağı döndürülünceye kadar liste öğelerini yöntemi. Bu, en son kullanılan (MRU) listeler ve pencere listeleri gibi öğeler için iyi çalışır.<br /><br /> Geçerlilik süresi: `Button`|  
|DynamicVisibility|Komut görünürlüğünü aracılığıyla değiştirilebilir `QueryStatus` yöntemi veya bir bağlam eklenmiştir GUID aracılığıyla `VisibilityConstraints` bölümü.<br /><br /> Menüleri ve araç penceresi araç çubukları, ancak ana pencerede görünen değil en üst düzey araç çubukları üzerinde görünmesini komutları için geçerlidir. Üst düzey araç çubuğu öğelerini devre dışı, ancak gelen OLECMDF_INVISIBLE bayrağı döndürüldüğünde, gizli olmayan `QueryStatus` yöntemi. Araç penceresi araç çubukları üzerinde görünmesini araç çubuğu komutlarını gizlenebilir.<br /><br /> Menüde, bu bayrak, tüm üyeleri gizli olduğunda bunu otomatik olarak gizlenmelidir de gösterir. Üst düzey menüler bu davranışı olduğundan bu bayrağı için alt menüler genellikle atanır.<br /><br /> Bu bayrak ile birleştirilmelidir `DefaultInvisible` bayrağı.<br /><br /> İçin geçerli: `Button`, `Combo`, `Menu`|  
|Süzme|Altında filtreleme anahtarları konusuna [Combos öğesi](../extensibility/combo-element.md).<br /><br /> Geçerlilik süresi: `Combo`|  
|FixMenuController|Bu komut, bir menü denetleyicisi üzerinde konumlandırılmış, her zaman varsayılan komuttur; diğer bir deyişle, menü denetleyicisi düğmesine kendisini seçildiğinde komutu seçilir. Menü denetleyicisi varsa `TextIsAnchorCommand` bayrağı ayarlanmış, menü denetleyicisi olan komut metnini kazanır `FixMenuController` bayrağı.<br /><br /> Yalnızca tek bir komutta menü denetleyicisi üzerinde olmalıdır `FixMenuController` bayrağı. Birden fazla komut şekilde işaretlenmişse, son komut menüsünde varsayılan komut haline gelir.<br /><br /> Geçerlilik süresi: `Button`|  
|IconAndText|Bir simge ve metin menü ve araç çubuğu üzerinde gösterir.<br /><br /> İçin geçerli: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Otomatik Tamamlama özelliği devre dışı bırakıldı.<br /><br /> Geçerlilik süresi: `Combo`|  
|NoButtonCustomize|Bu düğme özelleştirme kullanıcı izin vermez.<br /><br /> İçin geçerli: `Button`, `Combo`|  
|NoKeyCustomize|Klavye özelleştirme etkinleştirmeyin.<br /><br /> İçin geçerli: `Button`, `Combo`|  
|NoShowOnMenuController|Bu komut, bir menü denetleyicisi üzerinde konumlandırılmış, komut aşağı açılan listede görünmez.<br /><br /> Geçerlilik süresi: `Button`|  
|NotInTBList|Mevcut araç çubukları listesinde görünmüyor. Bu, yalnızca araç çubuğu menüsü türleri için geçerlidir.<br /><br /> Geçerlilik süresi: `Menu`|  
|NoToolbarClose|Kullanıcı araç çubuğunu kapatamazsınız. Bu, yalnızca araç çubuğu menüsü türleri için geçerlidir.<br /><br /> Geçerlilik süresi: `Menu`|  
|PICT|Bir simge yalnızca bir araç çubuğu, ancak yalnızca bir menü metni gösterir. Simge yok belirtilirse, tıklanabilir bir boşluk bir araç çubuğunda gösterilir.<br /><br /> Geçerlilik süresi: `Button`|  
|PostExec|Komut engelleyici olmayan hale getirir. Geliştirme ortamı, tüm ön işleme sorguları tamamlanana kadar yürütme erteler.<br /><br /> Geçerlilik süresi: `Button`|  
|RouteToDocs|Komut etkin belgeye yönlendirilir.<br /><br /> Geçerlilik süresi: `Button`|  
|StretchHorizontally|Bu bayrak ayarlandığında, minimum genişliğini birleşik giriş kutusu genişliği olur ve araç çubuğunda yer ise, birleşik giriş kutusu kullanılabilir alanı dolduracak şekilde uzatılır. Bu, yalnızca araç yatay olarak yerleştirilir ve araç çubuğunda tek bir birleşik giriş kutusunu (bayrağı ilk birleşik giriş kutusu hariç tüm sayılır) bayrağını kullanabilirsiniz oluşur.<br /><br /> Geçerlilik süresi: `Combo`|  
|TextMenuUseButton|Kullanım `ButtonText` menüleri için alan. Varsayılan alan `MenuText` belirtilmişse.<br /><br /> Geçerlilik süresi: `Button`|  
|TextChanges|Komut veya menü metni çalışma zamanında aracılığıyla genellikle değiştirilebilir `QueryStatus` yöntemi.<br /><br /> İçin geçerli: `Button`, `Menu`|  
|TextChangesButton|Geçerlilik süresi: `Button`|  
|TextIsAnchorCommand|Menü denetleyicisi için menü metnini varsayılan (bağlantı) komuttan alınır. Son komut seçilen ya da kilitli bir yer işareti komuttur. Bu bayrak ayarlanmazsa, menü denetleyicisi kendi kullanan `MenuText` alan. Ancak, menü denetleyicisi tıklayarak yine de söz konusu denetleyici son seçilen komuttan sağlar.<br /><br /> Bu bayrak ile birleştirerek öneririz `TextChanges` bayrağı.<br /><br /> Bu bayrak MenuController veya MenuControllerLatched yalnızca türü menüler için geçerlidir.<br /><br /> Geçerlilik süresi: `Menu`|  
|TextMenuCtrlUseMenu|Kullanım `MenuText` menü denetleyicisi ile sekmesindeki. Varsayılan alan `ButtonText`.<br /><br /> Geçerlilik süresi: `Button`|  
|TextMenuUseButton|Kullanım `ButtonText` menüleri için alan. Varsayılan alan `MenuText` belirtilmişse.<br /><br /> Geçerlilik süresi: `Button`|  
|TextOnly|Simge belirtilmiş olsa bile bir araç veya bir menü ancak herhangi bir simge yalnızca metin göstermek.<br /><br /> Geçerlilik süresi: `Button`|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Buttons öğesi](../extensibility/buttons-element.md)|Bir grubu için sağlar [Button öğesi](../extensibility/button-element.md) öğeleri.|  
|[Menus öğesi](../extensibility/menus-element.md)|VSPackage'ı uygulayan tüm menüleri tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)