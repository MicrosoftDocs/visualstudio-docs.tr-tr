---
title: Kod parçacıklarının sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fff2767c962cf6899840e54bff798bae1f9e202
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304817"
---
# <a name="troubleshooting-snippets"></a>Sorun Giderme Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense kod parçacıkları ile ilgili sorunlar genellikle iki sorunları neden: hatalı kod parçacığı dosyasının içeriğini ya da bozuk kod parçacığı dosyası.  
  
## <a name="common-problems"></a>Yaygın sorunlar  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Kod parçacığı bir Visual Studio kaynak dosyası için dosya Gezgini'nden sürüklenemez  
  
-   XML kod parçacığı dosyası bozulmuş olabilir. **XML Düzenleyicisi** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sorunları XML yapısı içinde bulabilirsiniz.  
  
-   Kod parçacığı dosyasını kod parçacığı şemaya uygun olmayabilir. **XML Düzenleyicisi** içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sorunları XML yapısı içinde bulabilirsiniz.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kodu değil vurgulanan derleyici hataları var  
  
-   Bir proje başvurusu eksik olabilir. Kod parçacığı hakkında belgeleri inceleyin. Referans bilgisayarda bulunmazsa yüklemeniz gerekir. Bir kod parçacığı eklemeden, gerekli tüm başvuruları projeye eklemeniz gerekir. Kod parçacığı başvuru bilgileri eksikse, hata olarak için kod parçacığı Oluşturucu bildirilebilir.  
  
-   Bir değişken tanımlanmamış olabilir. Tanımlanmamış bir kod parçacığı değişkenlerinde vurgulanmış olmalıdır. Aksi durumda, kod parçacığı oluşturan hata olarak bildirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod Parçacıkları](../ide/code-snippets.md)



