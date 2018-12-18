---
title: "İzlenecek yol: ClickOnce dağıtım API'si ile uydu derlemelerini indirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6e6de316fd0ff66e0815da7fa935d21e23a8285e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306338"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms uygulamaları için uydu derlemelerini kullanarak birden çok kültürde yapılandırılabilir. A *uydu derleme* uygulamanın varsayılan kültürünü dışındaki bir kültür için uygulama kaynaklarını içeren bir derlemedir.  
  
 Bölümünde açıklandığı gibi [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md), birden çok uydu derlemeleri aynı birden çok kültürde içerebilir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım. Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tek bir istemci, büyük olasılıkla yalnızca bir uydu derlemesine gereksinim duyacak olmanıza rağmen tüm uydu derlemeler, dağıtımınızdaki istemci makineye indirir.  
  
 Bu yönerge, uydu derlemeleri isteğe bağlı olarak işaretleme ve istemci makinesi, geçerli kültür ayarları için ihtiyaç duyduğu derlemeyi indirme nasıl gösterir. Aşağıdaki yordam kullanılabilen araçlar kullanır [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Bu görev ile de gerçekleştirebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  Ayrıca bkz: [izlenecek yol: ClickOnce dağıtım API'sini kullanarak tasarımcı ile isteğe bağlı uydu derlemelerini indirme](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) veya [izlenecek yol: ClickOnce dağıtım API'si ile isteğe bağlı uydu derlemelerini indirme Tasarımcı kullanarak](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Test amacıyla, aşağıdaki kod örneği programlı olarak kültürü ayarlar `ja-JP`. Bir üretim ortamı için bu kodu ayarlama konusunda bilgi için bu konunun ilerleyen bölümlerindeki "Sonraki adımlar" bölümüne bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, Visual Studio'yu kullanarak uygulamanıza yerelleştirilmiş kaynaklar ekleme bildiğiniz varsayılır. Ayrıntılı yönergeler için bkz. [izlenecek yol: Windows formlarını yerelleştirme](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Uydu derlemelerini yüklemek için  
  
1.  Uygulamanızı isteğe bağlı uydu derlemelerinin indirilmesini etkinleştirmek için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2.  Uygulamanız için uydu derlemeleri oluşturmak [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Bir uygulama bildirimi oluşturmak veya mevcut uygulama bildiriminizi MageUI.exe kullanarak açın. Bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4.  Tıklayın **dosyaları** sekmesi.  
  
5.  Tıklayın **üç nokta** düğmesine (**...** ) ve tüm uygulamanızın derlemeleri ve oluşturulan Resgen.exe'yi kullanmakla uydu derlemeleri dahil dosyaları içeren dizini seçin. (Bir uydu derlemesine biçiminde bir ada sahip olacaktır *isoCode*\ApplicationName.resources.dll, burada *isoCode* RFC 1766 biçiminde bir dil tanımlayıcısı.)  
  
6.  Tıklayın **Doldur** dosyaları dağıtıma eklenecek.  
  
7.  Seçin **isteğe bağlı** her bir uydu derleme için onay kutusu.  
  
8.  Her bir uydu derlemesi için ISO dil tanımlayıcısını grup alanını ayarlayın. Örneğin, Japonca uydu derlemesi için bir yükleme grubunun adını belirtirsiniz `ja-JP`. Bu, kullanıcının bağlı olarak uygun uydu derlemesini indirmek için 1. adımda eklediğiniz kodun olanak tanıyacak <xref:System.Threading.Thread.CurrentUICulture%2A> özellik ayarı.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bir üretim ortamında, büyük olasılıkla ayarlar aşağıdaki kod örneğinde şu satırı kaldırın gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> belirli bir değere istemci makinelere doğru değerine ayarlanmış olduğundan varsayılan olarak. Japonca istemci makine üzerinde örneğin, uygulamanız çalıştığında zaman <xref:System.Threading.Thread.CurrentUICulture%2A> olacaktır `ja-JP` varsayılan olarak. Bu değer programlı olarak ayarlama, uydu bütünleştirilmiş kodlarınızı Uygulamanızı dağıtmadan önce test etmek için iyi bir yoludur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarını Yerelleştirme](../deployment/localizing-clickonce-applications.md)



