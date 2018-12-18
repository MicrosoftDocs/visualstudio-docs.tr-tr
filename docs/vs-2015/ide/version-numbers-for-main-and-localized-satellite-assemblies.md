---
title: Ana ve yerelleştirilmiş yardımcı derlemeler için sürüm numaraları | Microsoft Docs
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
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5c6d5e16a77a8c04964beb38e21ebf82ede7f0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223047"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Ana ve Yerelleştirilmiş Yardımcı Derlemeler İçin Sürüm Numaraları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute> Sınıfını kullanan bir ana derlemeye yerelleştirilmiş kaynakları resource manager yoluyla sürüm oluşturma desteği sağlar. Uygulama <xref:System.Resources.SatelliteContractVersionAttribute> bir uygulamanın ana derlemeye güncelleştirip derleme, uydu derlemeleri güncelleştirmeden yeniden dağıtmanıza olanak tanır. Örneğin, kullanabileceğiniz <xref:System.Resources.SatelliteContractVersionAttribute> yeni kaynakların yeniden oluşturulmasını ve uydu bütünleştirilmiş kodlarınızı yeniden dağıtmaya gerek olmadan tanıtan olmayan bir hizmet paketi sınıfı. Kullanılabilir olması, yerelleştirilmiş kaynaklar için ana derlemenin uydu sözleşme sürümü eşleşmelidir <xref:System.Reflection.AssemblyVersionAttribute> uydu bütünleştirilmiş kodlarınızı sınıfı. Bir tam sürüm numarası belirtmelisiniz <xref:System.Resources.SatelliteContractVersionAttribute>; gibi joker karakterlere "*" izin verilmez. Daha fazla bilgi için [kaynakları alınıyor](http://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Derlemeleri güncelleştiriliyor  
 <xref:System.Resources.SatelliteContractVersionAttribute> Sınıfı, uydu derlemesi güncelleştirmek zorunda kalmadan bir ana derlemeye güncelleştirmenizi sağlar ya da tam tersi. Ana derleme güncelleştirildiğinde, derleme sürüm numarası değiştirilir. Varolan uydu derlemelerini kullanmaya devam etmek istiyorsanız, ana derlemenin sürüm numarasını değiştirebilirsiniz ancak uydu sözleşme sürüm numarası olduğu gibi bırakın. Örneğin, ilk ana derlemeye sürümünüzü 1.0.0.0 olabilir. Ayrıca uydu sözleşme sürümü ve uydu derlemesinin derleme sürümü 1.0.0.0 olacaktır. Ana derlemenizi için bir hizmet paketine güncelleştirmeniz gerekiyorsa, uydu sözleşme sürümü ve uydu derleme sürüm 1.0.0.0 olarak tutarken 1.0.0.1 için derleme sürümünü değiştirebilirsiniz.  
  
 Uydu derlemesi ancak ana derlemenizi güncelleştirmeniz gerekirse, değiştirdiğiniz <xref:System.Reflection.AssemblyVersionAttribute> uydu bütünleştirilmiş kodun. Uydu derlemenizle birlikte sevk, yeni bir uydu derlemesini, eski bir uydu derlemesi ile uyumlu olduğunu belirten bir ilke derlemesi gerekir. İlkeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 Aşağıdaki kod, uydu sözleşme sürümünün nasıl ayarlanacağını gösterir. Kod, derleme betiğindeki veya AssemblyInfo.vb veya AssemblyInfo.cs dosyasında yerleştirilebilir.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı derlemeleri nasıl bulur](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Derleme özniteliklerini ayarlama](http://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Güvenlik ve yerelleştirilmiş yardımcı derlemeler](../ide/security-and-localized-satellite-assemblies.md)   
 [Uygulamaları yerelleştirme](../ide/localizing-applications.md)   
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)

