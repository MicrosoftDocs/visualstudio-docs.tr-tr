---
title: 'Test alanı 5: Kaynak denetimini Değiştir | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed7093d50290c4c0612faf6c7691f90e62a08267
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847363"
---
# <a name="test-area-5-change-source-control"></a>Test Alanı 5: Kaynak Denetimini Değiştirme
Bu kaynak denetimi eklentisi test alanını kapsayan aracılığıyla kaynak denetimi değiştirilmeden **kaynak denetimini Değiştir** komutu.  

 **Kaynak denetimini Değiştir** komut, kullanıcı için dört temel işlevleri sağlar:  

- **Bağlama:**  

   Kurmak veya bir kaynak denetimi bağlantısı çözüm/proje ve sürüm deposuna arasında yeniden açmasına olanak sağlar.  

- **Bağlamayı Kaldır:**  

   Bağlantı başına temelinde kaynak denetiminden bir proje/çözüm kaldırır.  

- **Bağlama/bağlantısını kes:**  

  Bağlı veya çevrimdışı durumunu değiştirir alanı 3'te bahsedilen denetimli çözüm. Daha fazla bilgi için [Test alanı 3: kullanıma / geri alma](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  

## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menüsü yolu test durumlarında kullanılır.  

 Kaynak denetimini Değiştir:**dosya**, **kaynak denetimi**, **değiştirmek kaynak denetimi**.  

## <a name="test-cases"></a>Test çalışmaları  
 Belirli test çalışmalarını şunlardır **kaynak denetimini Değiştir** test alanı komutu.  

### <a name="case-5a-bind"></a>Case 5a: bağlama  
 Bağlama seçili projeler ve çözümler için kaynak kodu denetim bilgisi eklemesine izin verir. Kullanıcı bir proje kaynak denetimine eklenecek bunlar tanımlamak için genellikle istenir. Kullanıcı yeni bir proje kaynak denetimi (kaynak denetimine Ekle karşıtlığını) bu işlemin bir parçası olarak oluşturamazsınız.  


| Eylem | Test adımları | Beklenen sonuçları doğrulamak için |
| - | - | - |
| Boş bir konuma bağlayın | 1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Açık **kaynak denetimini Değiştir** iletişim kutusu (**dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**).<br />4.  Tıklayın **Unbind**.<br />5.  Uyarı iletişim kutusu görüntülenirse, kabul edin.<br />6.  Tüm öğeleri seçin.<br />7.  Tıklayın **bağlama**.<br />8.  Boş bir kaynak denetim deposunda konumuna göz atın.<br />9. Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />10. Tıklayın **devam bu bağlamaları** onay iletişim kutusunda.<br />11. Tıklayın **Tamam** görünürse uyarı iletişim kutusunda.<br />12. Her şeyi denetleyin. Bu adım başarılı olursa, sonraki adıma geçin.<br />13. Çözümü kaynak denetiminden yeni bir konuma açın. | `Result from Step 12:`<br /><br /> Çözüm ve proje bağlı ve yeni hedef sürüm deposuna yazılır.<br /><br /> Çözüm ve proje dosyaları iade edilir.<br /><br /> Sürüm deposu proje hiyerarşisi klasör hiyerarşisi diskteki projenin eşleşir.<br /><br /> `Result from Step 13:`<br /><br /> Tüm proje öğeleri indirilir. |
| İstemci ile eşitlenmiş konuma bağlama | 1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Sürüm deposunda yinelenen proje ve çözüm oluşturma (paylaşın ve kullanıyorsanız dal [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Açık **kaynak denetimini Değiştir** iletişim kutusu (**dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**).<br />5.  Tüm bağlamayı Kaldır.<br />6.  Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />7.  Yeniden **kaynak denetimini Değiştir** iletişim kutusu.<br />8.  Tümünü seçin.<br />9. Tıklayın **bağlama**.<br />10. Çözüm ve proje dallı konumuna gözatın (adımdan, 3)<br />11. Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />12. Son yinelemeli olarak tüm öğeler için alın. | Aynı şekilde get önce get olduktan sonra dosya içeriği. |
| İstemci ile eşitlenmemiş konuma bağlama | 1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Sürüm deposunda yinelenen proje ve çözüm oluşturma (paylaşın ve kullanıyorsanız dal [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Dallı sürüm deposuna projede dosyaları değiştirin.<br />5.  Açık **kaynak denetimini Değiştir** iletişim kutusu (**dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**).<br />6.  Tüm bağlamayı Kaldır.<br />7.  Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />8.  Yeniden **kaynak denetimini Değiştir** iletişim kutusu.<br />9. Tümünü seçin.<br />10. Tıklayın **bağlama**.<br />11. Dallandırılmış için çözüm ve proje konuma göz atın.<br />12. Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />13. Uyarı iletişim kutusu görüntülenirse, kabul edin.<br />14. Son yinelemeli için tüm öğeleri alın. | Adım 4'te değiştirilmiş olan dosyaları da yerel olarak değiştirilir. |
| Hiç kaynak denetimi çözümü Bağla | 1.  Kaynak denetiminde bir boş klasör oluşturun.<br />2.  Bir istemci projesi oluşturun.<br />3.  Açık **kaynak denetimini Değiştir** iletişim kutusu (**dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**).<br />4.  Boş konumda kaynak denetimi çözümü bağlayın.<br />5.  Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />6.  Tıklayın **devam bu bağlamaları** onay iletişim kutusunda.<br />7.  Tıklayın **Tamam** görünürse uyarı iletişim kutusunda. | Çözüm kaynak denetimi eklenir.<br /><br /> Çözüm ve proje kullanıma. |
| Bağlama iptal et | 1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Kaynak denetimini Değiştir iletişim kutusunu açın.<br />4.  Tüm bağlamayı Kaldır.<br />5.  Tıklayın **Tamam** iletişim kutusunu kapatmak için düğme. Bu adım başarılı olursa, sonraki adıma geçin.<br />6.  Yeniden **kaynak denetimini Değiştir** iletişim kutusu.<br />7.  İlişkisiz bir konuma bağlayın.<br />8.  Tıklayın **iptal**. | `Result from Step 5:`<br /><br /> Çözüm, artık kaynak denetimi altında değil<br /><br /> `Result from Step 8:`<br /><br /> Çözümüdür altında hala olmayan kaynak denetimi. |

### <a name="case-5b-unbind"></a>Case 5b: Unbind  
 Proje ve çözüm kaldırır kaynak kodu denetim bilgisi bağlamayı Kaldır. Kullanıcı Seçimi ve nasıl öğeler kaynak denetimine eklenen bir karışımını etkilenen proje ve çözüm temel alır.  

|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Bir dosya sistemi veya yerel IIS Web projesi ve bir istemci projesini içeren çözüm unbind|1.  Bir dosya sistemi veya yerel IIS Web projesi oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Yeni bir istemci projesi çözüme ekleyin.<br />4.  Denetleyin / çözüm istenirse kabul edin.<br />5.  Açık **kaynak denetimini Değiştir** iletişim kutusu.<br />6.  Tıklayın **Unbind**.<br />7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.<br />8.  Çözüm, proje, çözüm öğeleri, proje öğeleri denetlemek çalışır.|Çözüm ve projeler kaynak denetimi altında değil.<br /><br /> Kaynak denetimi menüsü komutlarını görünmez.|  
|İptal Unbind|1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Açık **kaynak denetimini Değiştir** iletişim kutusu.<br />4.  Tıklayın **tüm bağlantısını**.<br />5.  Tıklayın **iptal**.|Kaynak denetimi altında bir çözümdür.|  

### <a name="case-5c-rebind"></a>Case 5c: yeniden bağlayın  
 Yeniden bağlamasını bağlamayı Kaldır ve bağlama yalnızca bir birleşimi olan — bir proje/daha önce kaynak denetimi altında olan ve bağlantısız çözüm yeniden bağlama işlemi.  

|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Çözüm ve projeler kapatmadan rebind **kaynak denetimini Değiştir** iletişim kutusu|1.  Bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Açık **kaynak denetimini Değiştir** iletişim kutusu.<br />4.  Tıklayın **Unbind**.<br />5.  Tüm satırları seçin.<br />6.  Tıklayın **bağlama**.<br />7.  Tıklayın **Tamam** kapatmak için **kaynak denetimini Değiştir** iletişim kutusu.<br />8.  Kullanıma alma istenirse kabul edin.|Çözüm ve proje kaynak denetimi altında olan.|  
|Yalnızca kapatmadan projeyi yeniden bağlamaya **kaynak denetimini Değiştir** iletişim kutusu|1.  Bir proje oluşturun.<br />2.  Sadece projeyi kullanarak kaynak denetimine Ekle (Dosya -> Kaynak Denetimi'ne seçili projeleri kaynak denetimine ekleyin.<br />3.  Kaynak denetimini Değiştir iletişim kutusunu açın.<br />4.  Sadece projeyi bağlamayı Kaldır.<br />5.  Sadece projeyi bağlayın.|Çözüm denetlenmeyen kalır.<br /><br /> Denetimli proje kalır.|  
|Çözüm yalnızca kapatmadan rebind **kaynak denetimini Değiştir** iletişim kutusu|1.  Bir proje oluşturun.<br />2.  Kullanarak kaynak denetimine Çözüm Ekle (**dosya**, **kaynak denetimi**, **seçili projeleri kaynak denetimine Ekle**.<br />3.  Açık **kaynak denetimini Değiştir** iletişim kutusu.<br />4.  Yalnızca çözüm bağlantısını (kapatmayın **kaynak denetimini Değiştir** iletişim kutusu.)<br />5.  Yalnızca çözüm bağlayın.<br />6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.<br />7.  Çözüm ve çözüm öğeleri çıkış (varsa) denetleyin|Çözüm, denetlenen kalır.<br /><br /> Proje denetlenmeyen kalır.|  
|Çözüm/proje yalnızca aynı dizinde, yeniden bağlayın|1.  Bir proje oluşturun.<br />2.  Sadece projeyi kullanarak kaynak denetimine Ekle (**dosya**, **kaynak denetimi**, **seçili projeleri kaynak denetimine Ekle**.<br />3.  Çözümü kapatın.<br />4.  Yeni bir çözüm ile en az iki proje oluşturun.<br />5.  Çözüm kaynak denetimine ekleyin.<br />6.  1. adımda oluşturduğunuz kaynak denetiminden proje ekleyin.<br />7.  Kullanıma alma çözümün istenirse kabul edin.<br />8.  Çözümün tamamını kontrol edin.<br />9. Açık **kaynak denetimini Değiştir** iletişim kutusu.<br />10. Eklenen projeden (6. adım) seçin ve tıklayın **bağlamayı Kaldır**.<br />11. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.<br />12. Kullanıma alma istenirse kabul edin.<br />13. Yeniden **kaynak denetimini Değiştir** iletişim kutusu.<br />14. Eklenen projeden (6. adım) seçin ve tıklayın **bağlama**.<br />15. Özgün konum seçin.|Çözüm ve projeler denetimli kalır.|  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)