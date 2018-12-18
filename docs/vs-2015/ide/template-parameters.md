---
title: Şablon parametreleri | Microsoft Docs
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
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef4e1a6e3c56df744ce5375a1cb3a1dbd53a6fad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238907"
---
# <a name="template-parameters"></a>Şablon Parametreleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablon örneği başlatıldığında şablonlarınızın parametreleri kullanarak, sınıf adları ve ad alanları gibi bir şablon anahtar bölümlerini değerlerini değiştirebilirsiniz. Bu parametreler, bir kullanıcı tıkladığında, arka planda çalışan Şablon Sihirbazı tarafından değiştirilir **Tamam** içinde **yeni proje** veya **Yeni Öğe Ekle** iletişim kutuları.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Bildirme ve şablon parametreleri etkinleştirme  
 Şablon parametreleri biçimi $ içinde bildirilen*parametre*$. Örneğin:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Parametre değiştirme şablonlarındaki etkinleştirmek için  
  
1.  Şablonun .vstemplate dosyasında bulun `ProjectItem` parametre değiştirme etkinleştirmek istediğiniz öğeye karşılık gelen öğe.  
  
2.  Ayarlama `ReplaceParameters` özniteliği `ProjectItem` öğesine `true`.  
  
3.  Proje öğesi için kod dosyasında, uygun yerlerde parametreleri içerir. Örneğin, aşağıdaki parametre dosyasındaki ad alanı için güvenli bir proje adı kullanılması belirtir:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri  
 Aşağıdaki tabloda, herhangi bir şablon kullanılabilecek ayırtılmış şablon parametreleri listeler.  
  
> [!NOTE]
>  Şablon parametreleri büyük/küçük harfe duyarlıdır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`clrversion`|Geçerli sürümü ortak dil çalışma zamanı (CLR).|  
|`GUID [1-10]`|' % S'projesi bir proje dosyasında GUID değiştirmek için kullanılan bir GUID. En fazla 10 benzersiz GUID'ler belirtebilirsiniz (örneğin, `guid1)`.|  
|`itemname`|Kullanıcı tarafından sağlanan adı **Yeni Öğe Ekle** iletişim kutusu.|  
|`machinename`|Geçerli bilgisayar adı (örneğin, Computer01).|  
|`projectname`|Kullanıcı tarafından sağlanan adı **yeni proje** iletişim kutusu.|  
|`registeredorganization`|Kayıt defteri anahtar değeri HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Geçerli projenin kök ad alanı. Bu parametre, yalnızca öğe şablonları için geçerlidir.|  
|`safeitemname`|Kullanıcı tarafından sağlanan adı **Yeni Öğe Ekle** olan tüm güvenli olmayan karakterleri ve boşlukları kaldırılmış bir iletişim kutusu.|  
|`safeprojectname`|Kullanıcı tarafından sağlanan adı **yeni proje** olan tüm güvenli olmayan karakterleri ve boşlukları kaldırılmış bir iletişim kutusu.|  
|`time`|GG/AA/YYYY biçiminde geçerli saati 00:00:00.|  
|`SpecificSolutionName`|Çözüm adı. "Çözüm dizini oluşturma" işaretlendiğinde `SpecificSolutionName` çözüm adına sahip. "Çözüm dizini oluşturma" işaretli olduğunda `SpecificSolutionName` boştur.|  
|`userdomain`|Geçerli kullanıcı etki alanı.|  
|`username`|Geçerli kullanıcı adı.|  
|`webnamespace`|Geçerli Web sitesinin adı. Bu parametre, Web formu şablonda benzersiz sınıf isimleri güvence altına almak için kullanılır. Web sitesi Web sunucusunun kök dizininde ise, bu şablon parametresi Web sunucusunun kök dizinine çözümler.|  
|`year`|YYYY biçiminde geçerli yıl.|  
  
## <a name="custom-template-parameters"></a>Özel şablon parametreleri  
 Kendi şablon parametreleri ve değerleri, ek parametre değiştirme sırasında kullanılan ayrılmış varsayılan şablon parametreleri olarak belirtebilirsiniz. Daha fazla bilgi için [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## <a name="example-replacing-files-names"></a>Örnek: Dosya adlarını değiştirme  
 Bir parametre ile kullanarak proje öğeleri için değişken dosya adlarını belirtebilirsiniz `TargetFileName` özniteliği. Örneğin, .exe dosyası tarafından belirtilen proje adı kullanmanızı belirtebilirsiniz `$projectname$`, dosya adı.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>Örnek: Namespace adı proje adı kullanma  
 Bir Visual C# sınıf dosyasında Class1.cs, ad alanı için proje adı kullanmak için aşağıdaki sözdizimini kullanın:  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 Class1.cs dosyasını başvurduğunuzda proje şablonu için .vstemplate dosyasında aşağıdaki XML'i şunlardır:  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şablonları Özelleştirme](../ide/customizing-project-and-item-templates.md)



