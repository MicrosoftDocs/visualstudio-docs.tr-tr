---
title: 'Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2351c048576d6cf0e93515df8bdce34eef09bfc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854669"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme
Bir yönetici veya Geliştirici yalıtılmış kabuk uzantısı, denetimleri, şablonlar ve araçlar Visual Studio Galerisi, Örnekler Galerisi veya özel galeriler erişimi denetleyebilirsiniz. Bir galeri kullanılabilir veya kullanılamaz hale getirmek için oluşturma bir *.pkgdef* değiştirilen kayıt defteri anahtarları ve değerlerini açıklayan dosyası.  
  
## <a name="manage-private-galleries"></a>Özel galeriler yönetme  
 Oluşturabileceğiniz bir *.pkgdef* galeriler birden çok bilgisayara erişimi denetlemek için dosya. Bu dosya aşağıdaki biçime sahip olmalıdır.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Anahtar etkin veya devre dışı bırakılacak Galerisine başvuruyor. Visual Studio Galerisi'ne ve Örnekler Galerisi GUID'lerini aşağıdaki depoyu kullanın:  
  
- Visual Studio Galerisi: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Örnekler Galerisi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled` Değeri, isteğe bağlıdır. Varsayılan olarak, bir galeri etkinleştirilir.  
  
  `Priority` Değeri içinde Galerilerde listelenir sırasını belirleyen **seçenekleri** iletişim kutusu. Visual Studio Galerisi 10 öncelikli ve öncelik 20 Örnekler Galerisi sahiptir. Özel galeriler 100 öncelikli olarak başlatın. Birkaç galeriler aynı öncelik değeri varsa, bunların yerelleştirilmiş değerini göründükleri sırayla belirlenir `DisplayName` öznitelikleri.  
  
  `Protocol` Atom veya SharePoint tabanlı galerileri değeri gereklidir.  
  
  Ya da `DisplayName`, veya her ikisini de `DisplayNameResourceID` ve `DisplayNamePackageGuid`, belirtilmesi gerekir. Tüm belirtilirse, ardından `DisplayNameResourceID` ve `DisplayNamePackageGuid` çifti kullanılır.  
  
## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Visual Studio Galerisi .pkgdef dosyası kullanarak devre dışı bırak  
 Galeride devre dışı bırakabilirsiniz bir *.pkgdef* dosya. Şu giriş, Visual Studio Galerisi devre dışı bırakır:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Şu girişi Örnekler Galerisi devre dışı bırakır:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özel galeriler](../extensibility/private-galleries.md)