---
title: "İzlenecek yol: ClickOnce dağıtım Tasarımcısı'nı kullanarak API'si ile uydu derlemelerini indirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c5616a9233466c71ca036c4c0cb70d43649979
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154865"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>İzlenecek yol: ClickOnce dağıtım Tasarımcısı'nı kullanarak API'si ile uydu derlemelerini indirme
Windows Forms uygulamaları için uydu derlemelerini kullanarak birden çok kültürde yapılandırılabilir. A *uydu derleme* uygulamanın varsayılan kültürünü dışındaki bir kültür için uygulama kaynaklarını içeren bir derlemedir.  
  
 Bölümünde açıklandığı gibi [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md), birden çok uydu derlemeleri aynı birden çok kültürde içerebilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tek bir istemci, büyük olasılıkla yalnızca bir uydu derlemesine gereksinim duyacak olmanıza rağmen tüm uydu derlemeler, dağıtımınızdaki istemci makineye indirir.  
  
 Bu yönerge, uydu derlemeleri isteğe bağlı olarak işaretleme ve istemci makinesi, geçerli kültür ayarları için ihtiyaç duyduğu derlemeyi indirme nasıl gösterir.  
  
> [!NOTE]
>  Test amacıyla, aşağıdaki kod örnekleri programlı olarak kültürü kümesine `ja-JP`. Bir üretim ortamı için bu kodu ayarlama konusunda bilgi için bu konunun ilerleyen bölümlerindeki "Sonraki adımlar" bölümüne bakın.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>Uydu derlemeleri isteğe bağlı olarak işaretlemek için  
  
1.  Projenizi yapılandırın. Bu, tüm kültürler için yerelleştirme için uydu derlemeleri üretir.  
  
2.  Çözüm Gezgini'nde proje adına sağ tıklayın ve **özellikleri**.  
  
3.  Tıklayın **Yayımla** sekmesine ve ardından **uygulama dosyaları**.  
  
4.  Seçin **tüm dosyaları göster** uydu derlemelerini görüntülemek için onay kutusu. Varsayılan olarak tüm uydu derlemelerini, dağıtımınızdaki dahil edilir ve bu iletişim kutusunda görünmez.  
  
     Uydu derlemesi biçiminde bir ada sahip olacaktır  *\<isoCode > \ApplicationName.resources.dll*burada \<isoCode > RFC 1766 biçiminde bir dil tanımlayıcısı.  
  
5.  Tıklayın **yeni** içinde **indirme grubu** listesini her bir dil tanımlayıcısı. İndirme grubu adı için istendiğinde dil tanımlayıcısı girin. Örneğin, Japonca uydu derlemesi için indirme grubu adını belirtirsiniz `ja-JP`.  
  
6.  Kapat **uygulama dosyaları** iletişim kutusu.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>C# uydu derlemelerini yüklemek için 
  
1.  Açık *Program.cs* dosya. Bu dosya Çözüm Gezgini'nde, projenizi seçin görmüyorsanız ve üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.  
  
2.  Uygun bir uydu derlemesini indirmek ve uygulamanızı başlatmak için aşağıdaki kodu kullanın.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Visual Basic'te uydu derlemelerini yüklemek için  
  
1.  İçinde **özellikleri** uygulamanın pencereye tıklayın **uygulama** sekmesi.  
  
2.  Sekme sayfanın en altında tıklayın **uygulama olaylarını görüntüle**.  
  
3.  Başlangıcına aşağıdaki içeri aktarmaları ekleyin *ApplicationEvents.VB* dosya.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Aşağıdaki kodu ekleyin `MyApplication` sınıfı.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bir üretim ortamında, büyük olasılıkla kod örneklerinde ayarlar şu satırı kaldırın gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> belirli bir değere istemci makinelere doğru değerine ayarlanmış olduğundan varsayılan olarak. Japonca istemci makine üzerinde örneğin, uygulamanız çalıştığında zaman <xref:System.Threading.Thread.CurrentUICulture%2A> olacaktır `ja-JP` varsayılan olarak. Programlı olarak ayarlama, uydu bütünleştirilmiş kodlarınızı Uygulamanızı dağıtmadan önce test etmek için iyi bir yoludur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: ClickOnce dağıtım API'si ile uydu derlemelerini indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)
