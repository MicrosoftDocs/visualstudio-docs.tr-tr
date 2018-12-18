---
title: "İzlenecek yol: ClickOnce dağıtım API'si ile uydu derlemelerini indirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 506495f8be0b552f35bed0610e9fb43a77efb151
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883035"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce dağıtım API'si ile uydu derlemelerini indirme
Windows Forms uygulamaları için uydu derlemelerini kullanarak birden çok kültürde yapılandırılabilir. A *uydu derleme* uygulamanın varsayılan kültürünü dışındaki bir kültür için uygulama kaynaklarını içeren bir derlemedir.  
  
 Bölümünde açıklandığı gibi [yerelleştirmek ClickOnce uygulamaları](../deployment/localizing-clickonce-applications.md), birden çok uydu derlemeleri aynı birden çok kültürde içerebilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tek bir istemci, büyük olasılıkla yalnızca bir uydu derlemesine gereksinim duyacak olmanıza rağmen tüm uydu derlemeler, dağıtımınızdaki istemci makineye indirir.  
  
 Bu yönerge, uydu derlemeleri isteğe bağlı olarak işaretleme ve istemci makinesi, geçerli kültür ayarları için ihtiyaç duyduğu derlemeyi indirme nasıl gösterir. Aşağıdaki yordam kullanılabilen araçlar kullanır [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Bu görev ile de gerçekleştirebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Ayrıca bkz: [izlenecek yol: ClickOnce dağıtım Tasarımcısı'nı kullanarak API'si ile uydu derlemelerini indirme](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) veya [izlenecek yol: isteğe bağlı olarak kullanarak ClickOnce dağıtım API'si ile uydu derlemelerini indirme Tasarımcı](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
> [!NOTE]
>  Test amacıyla, aşağıdaki kod örneği programlı olarak kültürü ayarlar `ja-JP`. Bir üretim ortamı için bu kodu ayarlama konusunda bilgi için bu konunun ilerleyen bölümlerindeki "Sonraki adımlar" bölümüne bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, Visual Studio'yu kullanarak uygulamanıza yerelleştirilmiş kaynaklar ekleme bildiğiniz varsayılır. Ayrıntılı yönergeler için bkz. [izlenecek yol: yerelleştirme Windows forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Uydu derlemelerini yüklemek için  
  
1. Uygulamanızı isteğe bağlı uydu derlemelerinin indirilmesini etkinleştirmek için aşağıdaki kodu ekleyin.  
  
    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2. Uygulamanız için uydu derlemeleri oluşturmak [Resgen.exe (kaynak dosya oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator) veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3. Bir uygulama bildirimi oluşturmak veya mevcut uygulama bildiriminizi kullanarak açmak *MageUI.exe*. Bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4. Tıklayın **dosyaları** sekmesi.  
  
5. Tıklayın **üç nokta** düğmesine (**...** ) ve tüm uygulamanızın derlemeleri ve oluşturulan kullanarak uydu derlemeleri dahil dosyaları içeren dizini seçin *Resgen.exe*. (Bir uydu derlemesine biçiminde bir ada sahip olacaktır  *\<isoCode > \ApplicationName.resources.dll*burada \<isoCode > RFC 1766 biçiminde bir dil tanımlayıcısı.)  
  
6. Tıklayın **Doldur** dosyaları dağıtıma eklenecek.  
  
7. Seçin **isteğe bağlı** her bir uydu derleme için onay kutusu.  
  
8. Her bir uydu derlemesi için ISO dil tanımlayıcısını grup alanını ayarlayın. Örneğin, Japonca uydu derlemesi için bir yükleme grubunun adını belirtirsiniz `ja-JP`. Bu, kullanıcının bağlı olarak uygun uydu derlemesini indirmek için 1. adımda eklediğiniz kodun olanak tanıyacak <xref:System.Threading.Thread.CurrentUICulture%2A> özellik ayarı.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bir üretim ortamında, büyük olasılıkla ayarlar aşağıdaki kod örneğinde şu satırı kaldırın gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> belirli bir değere istemci makinelere doğru değerine ayarlanmış olduğundan varsayılan olarak. Japonca istemci makine üzerinde örneğin, uygulamanız çalıştığında zaman <xref:System.Threading.Thread.CurrentUICulture%2A> olacaktır `ja-JP` varsayılan olarak. Bu değer programlı olarak ayarlama, uydu bütünleştirilmiş kodlarınızı Uygulamanızı dağıtmadan önce test etmek için iyi bir yoludur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)