---
title: 'Nasıl yapılır: bir kitaplıktaki sembolleri tanımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ff3f9ad93ddfb3b463d059fb2aba654ce48a501
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510535"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Nasıl yapılır: bir kitaplıktaki sembolleri tanımlama
Sembol tarama araçlarını hiyerarşik görünümleri simgeleri görüntüler. Simgeler, ad alanları, nesneler, sınıflar, sınıf üyeleri ve diğer dil öğelerini temsil eder.  
  
 Hiyerarşideki her bir simge için simge kitaplığı tarafından geçirilen Gezinti bilgileri belirlenebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aşağıdaki arabirimleri aracılığıyla Nesne Yöneticisi:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Hiyerarşideki simgenin konumunu sembol ayırır. Belirli bir simgeye gitmek sembol tarama araçlarını sağlar. Simgeyi benzersiz, tam yolunu konumunu belirler. Her öğe yolunda bir düğümdür. Yolu, üst düzey düğüm ile başlar ve belirli bir sembolün ile sona erer. Örneğin, M1 yöntemi C1 sınıfın bir üyesidir ve C1 N1 ad alanında ise, tam M1 yöntemin N1 yoludur. C1. M1. Bu yol üç düğüm içeriyor: N1, C1 ve M1.  
  
 Gezinti bilgileri sağlayan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nesne Yöneticisi'ni bulun, seçin ve simge hiyerarşisinde seçili tutabilir. Bir tarama aracını başka gezinme sağlar. Kullanırken **Nesne Tarayıcısı** sembolleri göz atmak için bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proje, bir yönteme sağ tıklayın ve başlangıç **çağrı tarayıcısı** yöntemi çağrısı grafikte görüntülenecek aracı.  
  
 İki tür simge konumu açıklar. Kurallı biçimi tam yolun simgenin temel alır. Bu hiyerarşi simgesinin benzersiz bir konumu temsil eder. Sembol tarama aracının bağımsızdır. Kurallı biçimi bilgi almak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nesnesi Yöneticisi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> yöntemi. Sunu formun içinde belirli bir sembol Tarama Aracı simgenin konumunu açıklar. Simgenin diğer simgeleri hiyerarşideki konumuna göre konumudur. Belirli bir sembol, kurallı tek yolu ancak birkaç sunu yolu olabilir. Örneğin, C1 sınıfı, C2 sınıfından devralınır ve N1 ad alanındaki sınıflar **Nesne Tarayıcısı** aşağıdaki hiyerarşik ağaç görüntüler:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Bu örnekte, C2 sınıfı kurallı yolunu, N1 + C2 şeklindedir. C2 sunu yolunu C1 ve "Tabanları ve arabirimleri" düğümleri içerir: N1 C1 + "Tabanları ve arabirimleri" + C2.  
  
 Nesne manager çağrılarını sunu form bilgi almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> yöntemi.  
  
  
## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kurallı edinme ve sunu forms bilgileri  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> yöntemi.  
  
     Nesne yöneticisine kurallı simge yolunda bulunan düğüm listesi elde etmek için bu yöntemi çağırır.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> yöntemi.  
  
     Nesne yöneticisine sembol sunu yolunda bulunan düğüm listesi elde etmek için bu yöntemi çağırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Sembol tarama araçlarını destekler](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Nasıl yapılır: nesne yöneticisine kitaplık kaydetme](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Nasıl yapılır: nesne yöneticisine kitaplık tarafından sağlanan sembollerin listelerini kullanıma sunma](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)