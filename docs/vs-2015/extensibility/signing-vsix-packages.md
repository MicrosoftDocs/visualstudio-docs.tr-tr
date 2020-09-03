---
title: VSıX paketleri imzalanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4efaaa78ce593d8b97d1df454a9c30c2e62d9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918733"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantı derlemelerinin Visual Studio 'da çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.  
  
 Uzantınızı güvenli hale getirmek ve kurcalanmadığından emin olmak istiyorsanız VSıX paketine dijital imza ekleyebilirsiniz. Bir VSıX imzalandığı zaman VSıX yükleyicisi, imzalandığını belirten bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSıX içeriği değiştirilmişse ve VSıX yeniden imzalanmamışsa, VSıX yükleyicisi imza geçerli değil olarak gösterilir. Yükleme durdurulmaz, ancak Kullanıcı uyarıladır.  
  
> [!IMPORTANT]
> 2015 ' den başlayarak, SHA256 şifrelemesi dışında bir şey kullanılarak imzalanmış VSıX paketleri geçersiz imzaya sahip olacak şekilde tanımlanır. VSıX yüklemesi engellenmiyor, ancak Kullanıcı uyarılacaktır.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Valtsigntool ile VSıX imzalama  
 [Valtsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)'de NuGet.org üzerinde [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından kullanılabilen bir SHA256 şifreleme imzalama aracı vardır.  
  
#### <a name="to-use-the-vsixsigntool"></a>Valtsigntool kullanmak için  
  
1. VSıX 'i bir projeye ekleyin.  
  
2. Çözüm Gezgini ' de proje düğümüne sağ tıklayın, &#124; Ekle ' yi seçin ve **NuGet Paketlerini Yönet**' i seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için bkz. [NuGet 'e genel bakış](/nuget/) ve [Iletişim kutusunu kullanarak NuGet paketlerini yönetme](/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. VisualStudioExtensibility adresinden Valtsigntool araması yapın ve NuGet paketini yükledikten sonra.  
  
4. Şimdi de, projenin yerel paketler konumundan Valtsigntool öğesini çalıştırabilirsiniz. İmzalama senaryonuz (VSIXSignTool.exe/?) için araç komut satırı yardımına bakın.  
  
   Örneğin, parola korumalı bir sertifika dosyası ile imzalamak için:  
  
   VSIXSignTool.exe Sign/f \<certfile> /p \<password>\<VSIXfile>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
