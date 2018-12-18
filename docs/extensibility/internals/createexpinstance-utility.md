---
title: Createexpınstance yardımcı programı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0f7f52f45023106d3e504258a538823c1c8fbb4
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500663"
---
# <a name="createexpinstance-utility"></a>Createexpınstance yardımcı programı
Kullanım **Createexpınstance** oluşturmak, sıfırlama veya Visual Studio'nun deneysel örneği silmek için yardımcı program. Deneysel örneğinde hata ayıklayın ve Visual Studio uzantıları temel ürünü değiştirmeden test etmek için kullanabilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>Parametreler  
 **/ Oluşturma** deneysel örneği oluşturur.  
  
 **/ Reset**  
 Deneysel örneği siler ve ardından yeni bir tane oluşturur.  
  
 **/ Temizle**  
 Deneysel örneği siler.  
  
 **/ VSInstance**  
 Kopyalamak için temel Visual Studio örneğini içeren dizinin adı.  
  
 **/ RootSuffix**  
 Deneysel örneği dizin adının sonuna eklenecek sonek.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio uzantısı üzerinde çalışırken, varsayılan deneysel örneğinde açın ve geçerli uzantıyı yüklemek için F5 tuşuna basabilirsiniz. Deneysel örnek varsa, varsayılan ayarlara sahip bir Visual Studio oluşturur.  
  
 Deneysel örneği varsayılan konumu, Visual Studio sürüm sayısına bağlıdır. Örneğin, Visual Studio 2015 için konumdur *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Tüm dosyaları dizin konumu, örnek bir parçası olarak kabul edilir. Dizin adı varsayılan konuma değiştirilmediği sürece, herhangi bir ek deneysel örneği Visual Studio tarafından yüklenmez.  
  
 Visual Studio deneysel örneği açıldığında, sistem kayıt defteri erişimi yoktur. Bu, kullanılan kayıt defteri kovanını Deneysel bir sürümü Visual Studio'nun önceki sürümlerden farklıdır.  
  
 **Createexpınstance** yardımcı programı değiştirir **VsRegEx** yardımcı programı.  
  
 Aşağıdaki örnek, Visual Studio varsayılan Deneysel örneğini sıfırlar:  
  
 **CreateExpInstance.exe Reset /VSInstance 14.0 = /RootSuffix Exp =**  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage’lar](../../extensibility/internals/vspackages.md)