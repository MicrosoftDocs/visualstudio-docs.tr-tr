---
title: VSıX paketleri imzalanıyor | Microsoft Docs
description: Uzantı derlemeleri imzalama hakkında bilgi edinin. VSıX yükleyicisi, bir VSıX 'in imzalandığını ve imza hakkında bilgi görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d481c75754c7bc49369987d4bf6dc3aa33e96fdc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899166"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
Uzantı derlemelerinin Visual Studio 'da çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.

 Uzantınızı güvenli hale getirmek ve kurcalanmadığından emin olmak istiyorsanız VSıX paketine dijital imza ekleyebilirsiniz. Bir VSıX imzalandığı zaman VSıX yükleyicisi, imzalandığını belirten bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSıX içeriği değiştirilmişse ve VSıX yeniden imzalanmamışsa, VSıX yükleyicisi imza geçerli değil olarak gösterilir. Yükleme durdurulmaz, ancak Kullanıcı uyarıladır.

> [!IMPORTANT]
> Visual Studio 2015 ' den başlayarak, SHA256 şifrelemesi dışında bir şey kullanılarak imzalanmış VSıX paketleri geçersiz imzaya sahip olacak şekilde tanımlanır. VSıX yüklemesi engellenmiyor, ancak Kullanıcı uyarılacaktır.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Valtsigntool ile VSıX imzalama
 [Valtsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)'de NuGet.org üzerinde [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından kullanılabilen bir SHA256 şifreleme imzalama aracı vardır.

#### <a name="to-use-the-vsixsigntool"></a>Valtsigntool kullanmak için

1. VSıX 'i bir projeye ekleyin.

2. Çözüm Gezgini ' de proje düğümüne sağ tıklayın, &#124; Ekle ' yi seçin ve **NuGet Paketlerini Yönet**' i seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için bkz. [NuGet belge](/NuGet) ve [Paket Yöneticisi Kullanıcı arabirimi](/NuGet/Tools/Package-Manager-UI) konuları.

3. VisualStudioExtensibility adresinden Valtsigntool araması yapın ve NuGet paketini yükledikten sonra.

4. Şimdi de, projenin yerel paketler konumundan Valtsigntool öğesini çalıştırabilirsiniz. İmzalama senaryonuz (VSIXSignTool.exe/?) için araç komut satırı yardımına bakın.

   Örneğin, parola korumalı bir sertifika dosyası ile imzalamak için:

   VSIXSignTool.exe Sign/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
