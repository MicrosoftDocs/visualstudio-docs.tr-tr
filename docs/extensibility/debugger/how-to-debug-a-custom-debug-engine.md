---
title: 'Nasıl yapılır: bir özel hata ayıklama altyapısında hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdc01eec9982f7e3a03cd84424bc56b031846a7d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858868"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl yapılır: bir özel hata ayıklama altyapısında hata ayıklama
Bir proje türü, gelen hata ayıklama altyapısı (DE) başlatır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> yöntemi. Yani DE örneğini denetiminde başlatılır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje türü denetleme. Ancak, söz konusu örneğine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE hata ayıklaması yapılamıyor. Aşağıda, özel DE hata ayıklama olanak tanıyan adımlardır.  
  
> [!NOTE]
>  : "Bir özel hata ayıklama altyapısında hata ayıklama" yordamda iliştirebilmek için önce başlatmak DE beklemelisiniz. Başlangıcına DE başlatıldığında görüntülenen sizin DE yakın bir ileti kutusu yerleştirin, bu noktada eklemek ve ardından devam etmek için ileti kutusunu temizleyin. Tümünü yakala bu şekilde DE olayları.  
  
> [!WARNING]
>  Aşağıdaki yordamlar denemeden önce yüklenmiş uzaktan hata ayıklama olması gerekir. Bkz: [uzaktan hata ayıklama](../../debugger/remote-debugging.md) Ayrıntılar için.  
  
## <a name="debug-a-custom-debug-engine"></a>Özel hata ayıklama altyapısında hata ayıklama  
  
1. Başlangıç *msvsmon.exe*, uzaktan hata ayıklama İzleyicisi.  
  
2. Gelen **Araçları** menüde *msvsmon.exe*seçin **seçenekleri** açmak için **seçenekleri** iletişim kutusu.  
  
3. "Kimlik doğrulaması" seçeneğini ve tıklayın **Tamam**.  
  
4. Bir örneği başlatın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve özel DE projenizi açın.  
  
5. İkinci bir örneğini Başlat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve DE başlatan özel projenizi açın (geliştirme için genellikle VSIP yüklendiğinde, ayarlanmış Deneysel bir kayıt defteri kovanında budur).  
  
6. Bu ikinci örneğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], projenize özel bir kaynak dosya yükleyin ve programı görüntüde hata ayıklamayı başlatın. Yük ya da bir kesme noktasına isabet beklemek DE izin vermek için birkaç dakika bekleyin.  
  
7. İlk örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seçin (DE projenize) **iliştirme** gelen **hata ayıklama** menüsü.  
  
8. İçinde **iliştirme** iletişim kutusunda, değişiklik **aktarım** için **uzaktan (kimlik doğrulama olmadan yalnızca yerel)**.  
  
9. Değişiklik **niteleyicisi** makinenizin adı (Not: Bu ad yalnızca bir kere yazmanız gereken şekilde girişlerini geçmişi olan).  
  
10. İçinde **kullanılabilir işlemler** listesinde, çalıştığını ve'a tıklayın, DE örneğini seçin **iliştirme** düğmesi.  
  
11. Sizin DE semboller sonra DE kodunuzda kesme noktaları yerleştirin.  
  
12. Durdur ve hata ayıklama işlemini yeniden her zaman, 6-10 arası adımları yineleyin.  
  
## <a name="debug-a-custom-project-type"></a>Hata ayıklama özel Proje türü  
  
1. Başlangıç [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeniz normal kayıt defteri kovanı ve yük (Bu, proje türünüzü proje türünüzü değil bir örneğinin kaynak) projesini yazın.  
  
2. Proje özelliklerini açın ve gidin **hata ayıklama** sayfası. İçin **komut**, yolunu yazın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (varsayılan olarak, *[sürücü]* \Program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3. İçin **komut satırı bağımsız değişkenlerini**, türü `/rootsuffix exp` (VSIP yüklendiğinde oluşturulan) Deneysel kayıt defteri kovanı için.  
  
4. Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.  
  
5. Proje türünüzü basarak başlatın **F5**. Bu ikinci bir örneğini başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6. Bu noktada, proje türü kaynak kodunuzda kesme noktaları yerleştirebilirsiniz.  
  
7. İkinci örneğinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], yükleme veya proje türünüzü yeni bir örneğini oluşturun. Yük ya da oluşturma sırasında kesme noktalarınıza isabet ettirmek.  
  
8. Hata ayıklama, proje türü.  
  
9. Bir DE başlatma işlemi hata ayıklama kullanmayı tercih ederseniz, başlatıldıktan sonra DE olarak eklemek için "bir özel hata ayıklama altyapısında hata ayıklama" yordamdaki adımları gerçekleştirebilirsiniz. Bu üç örneklerini verir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalıştıran: bir proje türü kaynağınız, örneklenmiş proje türü ve sizin DE olarak bağlı üçüncü bir saniye.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)