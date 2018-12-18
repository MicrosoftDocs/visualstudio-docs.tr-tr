---
title: 'Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76be049c670fb91911be70132b459cad5e5183bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902470"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme
Yükleyebilirsiniz, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı ilk kez bir CD veya dosya paylaşımı, ancak uygulamanın Web üzerinde düzenli güncelleştirmeler için denetlemelisiniz. Böylece, uygulamanızın kendisini Web'den, ilk yüklemeden sonra güncelleştirebilirsiniz, dağıtım bildiriminde güncelleştirmeleri için alternatif bir konum belirtebilirsiniz.  
  
> [!NOTE]
>  Uygulamanızı yerel olarak bu özelliği kullanmak için yüklemek için yapılandırılmalıdır. Daha fazla bilgi için [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ayrıca yüklerseniz, bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ağdan farklı bir konuma nedenleri ayarlama uygulama [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ilk yükleme ve sonraki tüm güncelleştirmeler için bu konumu kullanmak üzere. Uygulamanızı yerel olarak (örneğin, bir CD) yüklerseniz, orijinal medya kullanarak ilk yüklemesi gerçekleştirilir ve sonraki tüm güncelleştirmeler alternatif konumu kullanır.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows Forms tabanlı yardımcı program) kullanarak güncelleştirmeleri için alternatif bir konum belirtme  
  
1.  Bir .NET Framework komut istemini açıp türü:  
  
     **mageui.exe**  
  
2.  Üzerinde **dosya** menüsünde seçin **açın** uygulamanızın dağıtım bildirimini açmak için.  
  
3.  Seçin **dağıtım seçenekleri** sekmesi.  
  
4.  Metin kutusuna adlı **başlatma konumu**, uygulama güncelleştirmeleri için dağıtım bildirimi içeren dizine URL'sini girin.  
  
5.  Dağıtım bildirimi kaydedin.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe kullanarak güncelleştirmeleri için alternatif bir konum belirtme  
  
1. .NET Framework komut istemini açın.  
  
2. Aşağıdaki komutu kullanarak güncelleştirme konumunu ayarlayın. Bu örnekte, *HelloWorld.exe.application* yoludur, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] her zaman .application uzantılı, uygulama bildiriminin ve *<http://adatum.com/Update/Path>* bu URL'dir[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama güncelleştirmelerini denetler.  
  
    **Görüntü-HelloWorld.exe.application - ProviderUrl güncelleştir http://adatum.com/Update/Path**  
  
3. Dosyayı kaydedin.  
  
   > [!NOTE]
   >  Şimdi dosya ile yeniden imzalamak gerekir *Mage.exe*. Daha fazla bilgi için [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızı bir CD gibi çevrimdışı bir orta yüklersiniz ve bilgisayar çevrimiçi alıyorsa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ilk tarafından belirtilen URL denetler `<deploymentProvider>` daha yeni bir sürümü güncelleştirme konumunu içerip içermediğini belirlemek için dağıtım bildirimi içinde etiketi uygulama. Aksi halde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ilk kurulum dizininden yerine doğrudan buradan uygulamayı yükler ve ortak dil çalışma zamanı (CLR), uygulamanızın güven belirler kullanarak düzey `<deploymentProvider>`. Bilgisayar çevrimdışı ise veya `<deploymentProvider>` erişilemiyor, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD ve CLR yükler yükleme noktasında dayalı güven verir; CD yükleme için bu, uygulama tam güven alır anlamına gelir. Sonraki tüm güncelleştirmeler, o güven düzeyi devralır.  
  
 Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanan uygulamaları `<deploymentProvider>` böylece uygulamanın farklı farklı bilgisayarlarda güven düzeyleri almaz açıkça uygulama bildiriminde, ihtiyaç duydukları izinleri bildirmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce güncelleştirme stratejisini seçin](../deployment/choosing-a-clickonce-update-strategy.md)