---
title: Ana ve yerelleştirilmiş yardımcı derlemeler için sürüm numaraları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc74d746453c5d8e60161004a5b56a2c21915dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882612"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Ana ve yerelleştirilmiş yardımcı derlemeler için sürüm numaraları
<xref:System.Resources.SatelliteContractVersionAttribute> Sınıfını kullanan bir ana derlemeye yerelleştirilmiş kaynakları Resource Manager yoluyla sürüm oluşturma desteği sağlar. Uygulama <xref:System.Resources.SatelliteContractVersionAttribute> bir uygulamanın ana derlemeye güncelleştirin ve derlemenin uydu derlemelerini güncelleştirmeden yeniden olanak tanır. Örneğin, kullanabileceğiniz <xref:System.Resources.SatelliteContractVersionAttribute> yeni kaynakların yeniden oluşturulmasını ve uydu bütünleştirilmiş kodlarınızı yeniden dağıtmaya gerek olmadan tanıtan olmayan bir hizmet paketi sınıfı. Kullanılabilir olması, yerelleştirilmiş kaynaklar için ana derlemenin uydu sözleşme sürümü eşleşmelidir <xref:System.Reflection.AssemblyVersionAttribute> uydu bütünleştirilmiş kodlarınızı sınıfı. Bir tam sürüm numarası belirtin <xref:System.Resources.SatelliteContractVersionAttribute>; gibi joker karakterlere "*" izin verilmez. Daha fazla bilgi için [almak kaynakları](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).

## <a name="update-assemblies"></a>Güncelleştirme derlemeleri
 <xref:System.Resources.SatelliteContractVersionAttribute> Sınıfı, uydu derlemesi güncelleştirmek zorunda kalmadan bir ana derlemeye güncelleştirmenizi sağlar ya da tam tersi. Ana derleme güncelleştirildiğinde, derleme sürüm numarası değiştirilir. Varolan uydu derlemelerini kullanmaya devam etmek istiyorsanız, ana derlemenin sürüm numarasını değiştirebilirsiniz ancak uydu sözleşme sürüm numarası olduğu gibi bırakın. Örneğin, ilk ana derlemeye sürümünüzü 1.0.0.0 olabilir. Ayrıca uydu sözleşme sürümü ve uydu derlemesinin derleme sürümü 1.0.0.0 olacaktır. Ana derlemenizi için bir hizmet paketine güncelleştirmeniz gerekiyorsa, uydu sözleşme sürümü ve uydu derleme sürüm 1.0.0.0 olarak tutarken 1.0.0.1 için derleme sürümünü değiştirebilirsiniz.

 Uydu derlemesi ancak ana derlemenizi güncelleştirmeniz gerekirse, değiştirdiğiniz <xref:System.Reflection.AssemblyVersionAttribute> uydu bütünleştirilmiş kodun. Uydu derlemenizle birlikte sevk, yeni bir uydu derlemesini, eski bir uydu derlemesi ile uyumlu olduğunu belirten bir ilke derlemesi gerekir. İlkeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

 Aşağıdaki kod, uydu sözleşme sürümünün nasıl ayarlanacağını gösterir. Kod derleme betiği veya yerleştirilebilir *AssemblyInfo.vb* veya *AssemblyInfo.cs* dosya.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı derlemeleri nasıl bulur](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [Derleme özniteliklerini ayarlama](/dotnet/framework/app-domains/set-assembly-attributes)
- [Güvenlik ve yerelleştirilmiş yardımcı derlemeler](../ide/security-and-localized-satellite-assemblies.md)
- [Uygulamaları yerelleştirme](../ide/localizing-applications.md)
- [Globalize ve uygulamaları yerelleştirme](../ide/globalizing-and-localizing-applications.md)