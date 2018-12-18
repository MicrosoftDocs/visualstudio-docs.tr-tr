---
title: Örnek Excel için kodlanmış UI Test Eklentisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 564669d5af3ea526ad8822d3aea7310095151c6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290686"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Kodlanmış UI Testi için Excel Eklenti Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu örnek için eklenti [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] özellikle kaydedilir ve Visual Studio Enterprise'da çalıştırma kodlanmış UI testleri Excel, çalışma sayfaları desteklemek için tasarlanmıştır. Eklenti Office için Visual Studio Araçları kullanılarak oluşturulur.  
  
 Bir Excel eklenti oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: Excel için oluşturma bilgisayarınızı ilk VSTO eklentisi](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) ya da "Excel eklentisi için" MSDN arayın.  
  
 Excel eklentisi Excel için kodlanmış UI testi uzantısı, bu belgenin birincil konu olmamasına karşın, birkaç faydalı olabilir.  
  
 Bu eklenti, önemli bölümleri:  
  
-   `ThisAddIn`  Sınıf - arasında .NET uzaktan iletişim kanalı yönetir `ExcelUICommunicator` ve [örnek kodlanmış UI testi uzantısı için Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  -Eklenti test etme bir güvenlik sertifikası.  
  
-   `ExcelUICommunicator`  Class - bu sınıfın uyguladığı `IExcelUICommunication` arabirimi.  
  
## <a name="thisaddin-class"></a>ThisAddIn sınıfı  
 Bu sınıfın çoğu Office için Visual Studio Araçları tarafından oluşturulan gerçekten `ThisAddIn.Designer.cs` dosya Excel eklenti projenizi oluşturduğunuzda.  
  
 Uygulamanız gereken üyeleri olay işleyicileridir: `ThisAddIn_Startup()` ve `ThisAddIn_Shutdown()`. Amaçları başlatmak veya tarafından kullanılan .NET uzaktan iletişim kanalı `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Bu dosya, Office için Visual Studio Araçları tarafından oluşturulan ve Excel eklenti ve uzantısını test etme işlemi çalışması eklenti derlemesi izni sağlayan geçici bir güvenlik sertifikası içerir. Bu sertifikayı silmeniz gerekir ve içinde yeni bir tane oluşturun **imzalama** proje için sekmesinde **özellikleri** penceresinde veya kendi test sertifikası ekleme.  
  
## <a name="exceluicommunicator-class"></a>ExcelUICommunicator sınıfı  
 Bu sınıfın uyguladığı `IExcelUITestCommunication` arabirim ve Excel nesne modelinden istenen UI bilgileri alır. Daha fazla bilgi için [Excel Communicator arabirimi örnekleme](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodlanmış UI testlerini ve Eylem kayıtlarını Microsoft Excel'i desteklemek için genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Office ve SharePoint geliştirme](http://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)



