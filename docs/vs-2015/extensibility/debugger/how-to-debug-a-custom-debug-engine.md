---
title: 'Nasıl yapılır: bir özel hata ayıklama altyapısında hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d293011a3865b4fb9c31349240c520e56f5a9e39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756771"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Nasıl Yapılır: Özel Hata Ayıklama Altyapısında Hata Ayıklama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir proje türü, gelen hata ayıklama altyapısı (DE) başlatır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> yöntemi. Yani DE örneğini denetiminde başlatılır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proje türü denetleme. Ancak, söz konusu örneğine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] DE hata ayıklaması yapılamıyor. Aşağıda, özel DE hata ayıklama için izin vermek için adımlar yer almaktadır.  
  
> [!NOTE]
>  : "Hata ayıklama bir özel hata ayıklama altyapısı" yordamda iliştirebilmek için önce başlatmak DE beklemelisiniz. Başlangıcına DE başlatıldığında görüntülenen sizin DE yakın bir ileti kutusu yerleştirin, bu noktada eklemek ve ardından devam etmek için ileti kutusunu temizleyin. Tümünü yakala bu şekilde DE olayları.  
  
> [!WARNING]
>  Aşağıdaki yordamlar denemeden önce yüklenmiş uzaktan hata ayıklama olması gerekir. Bkz: [uzaktan hata ayıklama](../../debugger/remote-debugging.md) Ayrıntılar için.  
  
### <a name="debugging-a-custom-debug-engine"></a>Özel hata ayıklama altyapısında hata ayıklama  
  
1.  Msvsmon.exe, uzaktan hata ayıklama İzleyicisi'ni başlatın.  
  
2.  Gelen **Araçları** msvsmon.exe, seçim menüsünde **seçenekleri** açmak için **seçenekleri** iletişim kutusu.  
  
3.  "Kimlik doğrulaması" seçeneğini ve tıklayın **Tamam**.  
  
4.  Bir örneği başlatın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve özel DE projenizi açın.  
  
5.  İkinci bir örneğini Başlat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve DE başlatan özel projenizi açın (geliştirme için genellikle VSIP yüklendiğinde, ayarlanmış Deneysel bir kayıt defteri kovanında budur).  
  
6.  Bu ikinci örneğini [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], projenize özel bir kaynak dosya yükleyin ve programı görüntüde hata ayıklamayı başlatın. Yük ya da bir kesme noktasına isabet beklemek DE izin vermek için birkaç dakika bekleyin.  
  
7.  İlk örneğinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] seçin (DE projenize) **iliştirme** gelen **hata ayıklama** menüsü.  
  
8.  İçinde **iliştirme** iletişim kutusunda, değişiklik **aktarım** için **uzaktan (kimlik doğrulama olmadan yalnızca yerel)**.  
  
9. Değişiklik **niteleyicisi** makinenizin adı (Not: Bu ad yalnızca bir kez yazın gerek girişlerini geçmişi olan).  
  
10. İçinde **kullanılabilir işlemler** listesinde, çalıştığını ve'a tıklayın, DE örneğini seçin **iliştirme** düğmesi.  
  
11. Sizin DE semboller sonra DE kodunuzda kesme noktaları yerleştirin.  
  
12. Durdur ve hata ayıklama işlemini yeniden her zaman, 6-10 arası adımları yineleyin.  
  
### <a name="debugging-a-custom-project-type"></a>Özel proje türünü hata ayıklama  
  
1.  Başlangıç [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeniz normal kayıt defteri kovanı ve yük (Bu, proje türünüzü proje türünüzü değil bir örneğinin kaynak) projesini yazın.  
  
2.  Proje özelliklerini açın ve gidin **hata ayıklama** sayfası. İçin **komut**, yolunu yazın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (varsayılan olarak, *[sürücü]* \Program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  İçin **komut satırı bağımsız değişkenlerini**, türü `/rootsuffix exp` (VSIP yüklendiğinde oluşturulan) Deneysel kayıt defteri kovanı için.  
  
4.  Değişiklikleri kabul etmek için **Tamam** 'ı tıklayın.  
  
5.  Proje türünüzü, F5 tuşuna basarak başlatın. Bu ikinci bir örneğini başlatır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
6.  Bu noktada, proje türü kaynak kodunuzda kesme noktaları yerleştirebilirsiniz.  
  
7.  İkinci örneğinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], yükleme veya proje türünüzü yeni bir örneğini oluşturun. Yük ya da oluşturma sırasında kesme noktalarınıza isabet ettirmek.  
  
8.  Hata ayıklama, proje türü.  
  
9. Bir DE başlatma işlemi hata ayıklama kullanmayı tercih ederseniz, başlatıldıktan sonra DE olarak eklemek için "Hata ayıklama bir özel hata ayıklama altyapısı" yordamdaki adımları gerçekleştirebilirsiniz. Bu üç örneklerini verir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çalıştıran: bir proje türü kaynağınız, örneklenmiş proje türü ve sizin DE olarak bağlı üçüncü bir saniye.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)

