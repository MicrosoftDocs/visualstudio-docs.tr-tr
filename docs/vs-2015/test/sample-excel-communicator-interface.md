---
title: Excel Communicator arabirimi örnekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1ffbfe7c8d69ecca2ff90dc1d01af2eb15d7d277
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194447"
---
# <a name="sample-excel-communicator-interface"></a>Excel Communicator Arabirimi Örnekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnek `IExcelUICommunication` arabirimi kullanılan `ExcelUICommunicator` nesnesine `ExcelAddIn` proje.  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication arabirimi  
 Bu arabirim, iletişim noktaları arasında tanımlar `CodedUIExtension`, kodlanmış UI testi işleminde çalışır ve `ExcelCodedUIAddIn`, çalışan [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] işlem.  
  
 `ExcelCodedUIAddinHelper` Derlemesi olan bir `ExcelUICommunicator` Excel nesne modeli yöntemleri işlemek için kullanır ve bu arabirimden türetilen sınıf.  
  
 Bazı yöntemler Excel'den istenen bilgileri alın ardından oluşturup gibi bilgileri birini nesnelerini döndürür `CellInformation` nesne.  
  
 Diğer yöntemleri sağlanan bilgi nesnesini kullanın, ilgili denetimin Excel'de bulun ve bazı işlem denetimi gerçekleştirin. Örneğin, `ScrollIntoView` yöntemi, belirtilen hücre görünür olması çalışma kaydırır.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample ve ExcelCodedUIAddinHelper iletişim  
 `ExcelCodedUIAddinHelper` Derleme Excel işlemi içinde çalıştırılan ve sahip `UICommunicator` uygulayan sınıf `IExcelUITestCommunication` arabirimini alır ve gerekli bilgileri doğrudan Excel Arabiriminden ayarlar.  
  
 `CodedUIExtensibilitySample` Derleme Visual Studio Kodlanmış UI testi işleminde çalışır. Bu bütünleştirilmiş kod sahip `Communicator` bir .NET uzaktan iletişim kanal açar ve sağlar sınıfını bir `Instance` kullanan özelliği `IExcelUICommunication` kullanılacak arabirimi `UICommunicator` nesnesine `ExcelCodedUIAddinHelper` istekleri ve bilgi geçirmek için derleme nesneleri gibi bir `CellInformation` iki derlemeler arasında sürekli bir nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodlanmış UI testlerini ve Eylem kayıtlarını Microsoft Excel'i desteklemek için genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Örnek Excel için kodlanmış UI Test Eklentisi](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Excel için Kodlanmış UI Testi Uzantısı Örneği](../test/sample-coded-ui-test-extension-for-excel.md)



