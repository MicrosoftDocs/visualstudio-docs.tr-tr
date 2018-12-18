---
title: 'Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme | Microsoft Docs'
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
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fea42e1e59907c08d0a7e51a56875c1b73537
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744454"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir yönetici veya Geliştirici yalıtılmış kabuk uzantısı, denetimleri, şablonlar ve araçlar Visual Studio Galerisi, Örnekler Galerisi veya özel galeriler erişimi denetleyebilirsiniz. Bir galeri kullanılabilir veya kullanılamaz hale getirmek için değiştirilmiş kayıt defteri anahtarları ve değerlerini açıklayan .pkgdef dosyası oluşturun.  
  
## <a name="managing-private-galleries"></a>Özel galeriler yönetme  
 Galeriler birden çok bilgisayara erişimi denetlemek için .pkgdef dosyası oluşturabilirsiniz. Bu dosya aşağıdaki biçime sahip olmalıdır.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Anahtar etkin veya devre dışı bırakılacak Galerisine başvuruyor. Visual Studio Galerisi'ne ve Örnekler Galerisi GUID'lerini aşağıdaki depoyu kullanın:  
  
- Visual Studio Galerisi: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Örnekler Galerisi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled` Değeri, isteğe bağlıdır. Varsayılan olarak, bir galeri etkinleştirilir.  
  
  `Priority` Değeri galeriler Seçenekler iletişim kutusunda listelenen sırasını belirler. Visual Studio Galerisi 10 öncelikli ve öncelik 20 Örnekler Galerisi sahiptir. Özel galeriler 100 öncelikli olarak başlatın. Birkaç galeriler aynı öncelik değeri varsa, bunların yerelleştirilmiş değerini göründükleri sırayla belirlenir `DisplayName` öznitelikleri.  
  
  `Protocol` Atom veya SharePoint tabanlı galerileri değeri gereklidir.  
  
  Ya da `DisplayName`, veya her ikisini de `DisplayNameResourceID` ve `DisplayNamePackageGuid`, belirtilmesi gerekir. Tüm belirtilirse, ardından `DisplayNameResourceID` ve `DisplayNamePackageGuid` çifti kullanılır.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Visual Studio Galerisi .pkgdef dosyası kullanarak devre dışı bırakma  
 .Pkgdef dosyası bir galeride devre dışı bırakabilirsiniz. Şu giriş, Visual Studio Galerisi devre dışı bırakır:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Şu girişi Örnekler Galerisi devre dışı bırakır:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Galeriler](../extensibility/private-galleries.md)

