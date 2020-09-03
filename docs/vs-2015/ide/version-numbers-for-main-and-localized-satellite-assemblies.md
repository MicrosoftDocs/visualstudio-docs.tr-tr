---
title: Ana ve yerelleştirilmiş uydu derlemeleri için sürüm numaraları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa064d875d5354ac4ae1fc5fdd8493c5efbbee01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663050"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Ana ve Yerelleştirilmiş Yardımcı Derlemeler İçin Sürüm Numaraları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute>Sınıfı, Resource Manager aracılığıyla yerelleştirilmiş kaynakları kullanan bir ana derleme için sürüm oluşturma desteği sağlar. <xref:System.Resources.SatelliteContractVersionAttribute>Uygulamasının ana derlemesine uygulanması, uydu derlemelerini güncelleştirmeden derlemeyi güncelleştirmenizi ve yeniden dağıtmanıza olanak tanır. Örneğin, <xref:System.Resources.SatelliteContractVersionAttribute> sınıfını, uydu derlemelerinizi yeniden derlemek ve yeniden dağıtmak zorunda kalmadan yeni kaynaklar bulunmayan bir hizmet paketiyle birlikte kullanabilirsiniz. Yerelleştirilmiş kaynaklarınızın kullanılabilmesi için, ana derlemenizin uydu sözleşmesi sürümünün <xref:System.Reflection.AssemblyVersionAttribute> uydu derlemelerinizin sınıfıyla eşleşmesi gerekir. İçinde tam sürüm numarasını belirtmeniz gerekir <xref:System.Resources.SatelliteContractVersionAttribute> ; "*" gibi joker karakterlere izin verilmez. Daha fazla bilgi için bkz. [kaynakları alma](https://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).

## <a name="updating-assemblies"></a>Derlemeler güncelleştiriliyor
 <xref:System.Resources.SatelliteContractVersionAttribute>Sınıfı, uydu derlemenizi güncelleştirmek zorunda kalmadan bir ana derlemeyi güncelleştirmenizi sağlar veya tam tersi de geçerlidir. Ana derleme güncelleştirilirken, derleme sürüm numarası değiştirilir. Mevcut uydu derlemelerini kullanmaya devam etmek istiyorsanız, ana derlemenin sürüm numarasını değiştirin, ancak uydu sözleşmesinin sürüm numarasını aynı şekilde bırakın. Örneğin, ilk sürümünüzde ana derleme sürümünüz 1.0.0.0 olabilir. Uydu sözleşmesi sürümü ve uydu derlemesinin derleme sürümü de 1.0.0.0 olacaktır. Bir hizmet paketi için ana derlemenizi güncelleştirmeniz gerekiyorsa, uydu sözleşmesi sürümünü ve uydu 'in derleme sürümünü 1.0.0.0 olarak tutarken derleme sürümünü 1.0.0.1 olarak değiştirebilirsiniz.

 Ana derlemeniz değil uydu derlemesini güncelleştirmeniz gerekiyorsa, <xref:System.Reflection.AssemblyVersionAttribute> uydu derlemesinin öğesini değiştirirsiniz. Uydu derlemelerinizi birlikte, yeni uydu derlemelerinizin eski uydu derlemeinizle uyumlu olduğunu belirten bir ilke derlemesi sunmaları gerekir. İlkeler hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

 Aşağıdaki kod, uydu sözleşmesi sürümünün nasıl ayarlanacağını gösterir. Kod, derleme betiğine veya AssemblyInfo. vb ya da AssemblyInfo.cs dosyasına yerleştirilebilir.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>

```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Çalışma zamanının derlemeleri](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34) [belirleme derleme öznitelikleri](https://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e) [güvenlik ve yerelleştirilmiş uydu bütünleştirilmiş kodları](../ide/security-and-localized-satellite-assemblies.md) [Yerelleştirme uygulamaları](../ide/localizing-applications.md) [, uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)
