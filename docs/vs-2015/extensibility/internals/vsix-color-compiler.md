---
title: VSIX renk derleyicisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19ca749b3ddd2190fd667ddb6c96c2a88c557999
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788439"
---
# <a name="vsix-color-compiler"></a>VSIX Renk Derleyicisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio uzantısı renk derleyicisi bir .pkgdef için dosya Visual Studio'da bu renkleri kullanılabilir olacak şekilde dönüştürür ve mevcut Visual Studio Tema renkleri temsil eden bir .xml dosyasına götüren bir konsol uygulamasına bir araçtır. .Xml dosyaları arasındaki farkları karşılaştırmak kolay olduğundan, bu kaynak denetiminde özel renkler yönetmek için kullanışlı bir araçtır. Böylece yapı çıkışını geçerli .pkgdef dosyası derleme ortamlara da bağlanabilir.  
  
 **Temanın XML Şeması**  
  
 Tam tema .xml dosyası şöyle görünür:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 \<Tema > öğe tüm temayı tanımlar. Bir tema en az birini içermelidir \<Kategori > öğesi. Tema öğeleri şöyle tanımlanır:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Ad|[Gerekli] Temanın adı|  
|GUID|[Gerekli] Temanın GUID (GUID biçimlendirme eşleşmelidir)|  
  
 Özel renkler Visual Studio için oluştururken bu renkleri aşağıdaki temaları tanımlanması gerekir. Hiçbir renkleri belirli bir temaya varsa, Visual Studio, eksik renkleri açık tema yüklemeyi dener.  
  
|||  
|-|-|  
|**Tema adı**|**Tema GUID**|  
|Açık|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Koyu|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Mavi|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Yüksek Karşıtlık|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategori**  
  
 \<Kategori > öğesi bir Tema renkleri koleksiyonunu tanımlar. Kategori adları, mantıksal Gruplamalar sağlar ve mümkün olduğunca sayısı azalacağından'olarak tanımlanmamalıdır. Bir kategori en az birini içermelidir \<renk > öğesi. Kategori öğeleri şöyle tanımlanır:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Ad|[Gerekli] Kategori adı|  
|GUID|[Gerekli] Kategori GUID (GUID biçimlendirme eşleşmelidir)|  
  
 **Renk**  
  
 \<Renk > öğesi, bir bileşen ya da kullanıcı Arabirimi durumu için renk tanımlar. Bir renk için tercih edilen adlandırma şeması [UI türü] olan [durumu]. Yedekli olduğu gibi "renk" sözcüğünü kullanmayın. Bir renk, öğe türü ve durumlar veya "state" renk uygulanacak açıkça belirtmeniz gerekir. Bir renk boş olmamalı ve biri veya her ikisini de içermelidir bir \<arka plan > ve \<ön plan > öğesi. Renk öğeleri şöyle tanımlanır:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Ad|[Gerekli] Renk adı|  
  
 **Arka plan ve/veya ön plan**  
  
 \<Arka plan > ve \<ön plan > öğeler bir renk değeri ve türü için UI öğesinin ön plan veya arka plan tanımlayın. Bu öğeleri alt öğesi var.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Tür|[Gerekli] Renk türü. Aşağıdakilerden biri olabilir:<br /><br /> *CT_INVALID:* geçersiz ya da ayarlanmadığından rengi.<br /><br /> *CT_RAW:* bir ham ARGB değeri.<br /><br /> *CT_COLORINDEX:* KULLANMAYIN.<br /><br /> *CT_SYSCOLOR:* SysColor Windows sistem renk.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX Visual Studio renk.<br /><br /> *CT_AUTOMATIC:* otomatik rengi.<br /><br /> *CT_TRACK_FOREGROUND:* KULLANMAYIN.<br /><br /> *CT_TRACK_BACKGROUND:* KULLANMAYIN.|  
|Kaynak|[Gerekli] Rengin onaltılık olarak temsil edilen değeri|  
  
 Tür özniteliği yer alan şemada __VSCOLORTYPE numaralandırması tarafından desteklenen tüm değerleri desteklenir. Ancak, yalnızca CT_RAW ve CT_SYSCOLOR kullanmanızı öneririz.  
  
 **Hep birlikte**  
  
 Bu, geçerli tema .xml dosyasının basit bir örnektir:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Aracı'nı kullanma  
 **Söz dizimi**  
  
 VsixColorCompiler \<XML dosyası > \<PkgDef Dosya > \<isteğe bağlı bağımsız değişken >  
  
 **Bağımsız Değişkenler**  
  
||||  
|-|-|-|  
|**Anahtar adı**|**Notlar**|**Gerekli veya isteğe bağlı**|  
|Adlandırılmamış (.xml dosyası)|Bu ilk adlandırılmamış parametre ve dönüştürmek için XML dosyasının yolu.|Gerekli|  
|Adlandırılmamış (.pkgdef dosyası)|Bu ikinci adlandırılmamış parametreyi ve oluşturulan .pkgdef dosyası için çıkış yolu.<br /><br /> Varsayılan: \<XML dosya adı > .pkgdef|İsteğe Bağlı|  
|/ nologo|Bu bayrak ayarlandığında, ürün ve telif hakkı bilgileri yazdırmasının durdurur.|İsteğe Bağlı|  
|/?|Yardım bilgi yazdırır.|İsteğe Bağlı|  
|/help|Yardım bilgi yazdırır.|İsteğe Bağlı|  
  
 **Örnekler**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml/nologo  
  
## <a name="notes"></a>Notlar  
  
-   Bu araç, VC ++ Çalışma zamanı en son sürümü yüklü olmasını gerektirir.  
  
-   Yalnızca tek dosyalar desteklenir. Klasör yolları aracılığıyla toplu dönüştürme desteklenmiyor.  
  
## <a name="sample-output"></a>Örnek çıktı  
 Aracı tarafından oluşturulan .pkgdef dosyası şuna benzeyecektir anahtarları aşağıda:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```

