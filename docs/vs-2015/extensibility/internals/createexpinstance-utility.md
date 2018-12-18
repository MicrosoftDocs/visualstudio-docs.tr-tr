---
title: Createexpınstance yardımcı programı | Microsoft Docs
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
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a6761e844cee41c1a6f0df79f0d6529f4a8215
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768256"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance Yardımcı Programı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Createexpınstance yardımcı programı veya oluşturmak için sıfırlama, Visual Studio'nun deneysel örneği silin. Deneysel örneğinde hata ayıklayın ve Visual Studio uzantıları temel ürünü değiştirmeden test etmek için kullanabilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametreler  
 / Oluşturma  
 Deneysel örneği oluşturur.  
  
 / Reset  
 Deneysel örneği siler ve ardından yeni bir tane oluşturur.  
  
 /Clean  
 Deneysel örneği siler.  
  
 / VSInstance  
 Kopyalamak için temel Visual Studio örneğini içeren dizinin adı.  
  
 / RootSuffix  
 Deneysel örneği dizin adının sonuna eklenecek sonek.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio uzantısı üzerinde çalışırken, varsayılan deneysel örneğinde açın ve geçerli uzantıyı yüklemek için F5 tuşuna basabilirsiniz. Deneysel örnek varsa, varsayılan ayarlara sahip bir Visual Studio oluşturur.  
  
 Deneysel örneği varsayılan konumu, Visual Studio sürüm sayısına bağlıdır. Örneğin, Visual Studio 2015 için %localappdata%\Microsoft\VisualStudio\14.0Exp\ konumdur dizin konumunu tüm dosyaları bu örnek bir parçası olarak kabul edilir. Dizin adı varsayılan konuma değiştirilmediği sürece, herhangi bir ek deneysel örneği Visual Studio tarafından yüklenmez.  
  
 Visual Studio deneysel örneği açıldığında, sistem kayıt defteri erişimi yoktur. Bu, kullanılan kayıt defteri kovanını Deneysel bir sürümü Visual Studio'nun önceki sürümlerden farklıdır.  
  
 Createexpınstance yardımcı programı VsRegEx yardımcı programı değiştirir.  
  
 Aşağıdaki örnek, Visual Studio varsayılan Deneysel örneğini sıfırlar.  
  
 **CreateExpInstance.exe Reset /VSInstance 14.0 = /RootSuffix Exp =**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir ürün serbest bırakma](../../misc/releasing-a-visual-studio-integration-product.md)

