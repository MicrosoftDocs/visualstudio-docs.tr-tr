---
title: VSIX renk derleyici | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144336"
---
# <a name="vsix-color-compiler"></a>VSIX renk derleyici
Visual Studio uzantısı renk derleyici mevcut Visual Studio Tema renkleri temsil eden bir .xml dosyasına götüren bir konsol uygulaması ve böylece bu renkleri Visual Studio'da kullanılabilir bir .pkgdef kendisine dosya öğesine dönüştürür aracıdır. .Xml dosyaları arasındaki farklar karşılaştırmak kolay olduğundan, bu kaynak denetiminde özel renkler yönetmek için yararlı bir araçtır. Böylece yapı çıktı geçerli .pkgdef dosya da yapı ortamlara bağlanabilir.  
  
 **Temanın XML Şeması**  
  
 Tam tema .xml dosyası şuna benzer:  
  
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
  
 \<Tema > öğesi tüm temayı tanımlar. Bir tema en az birini içermelidir \<Kategori > öğesi. Tema öğeleri şu şekilde tanımlanır:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Özniteliği**|**Tanım**|  
|Ad|[Gerekli] Temanın adı|  
|GUID|[Gerekli] Temanın GUID (GUID biçimlendirme eşleşmelidir)|  
  
 Özel renkler Visual Studio için oluştururken bu renkleri aşağıdaki temaları tanımlanması gerekir. Hiçbir renkleri belirli bir temaya yoksa, Visual Studio eksik renkleri hafif temayı yüklemeyi dener.  
  
|||  
|-|-|  
|**Tema adı**|**Tema GUID**|  
|Açık|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Koyu|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Mavi|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Yüksek Karşıtlık|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategori**  
  
 \<Kategori > öğesi bir Tema renkleri koleksiyonunu tanımlar. Kategori adları mantıksal gruplandırmaları sağlayın ve mümkün olduğunca dar olarak tanımlanması gerekir. Bir kategori en az birini içermelidir \<renk > öğesi. Kategori öğelerini şu şekilde tanımlanır:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Özniteliği**|**Tanım**|  
|Ad|[Gerekli] Kategori adı|  
|GUID|[Gerekli] Kategorinin GUID (GUID biçimlendirme eşleşmelidir)|  
  
 **Renk**  
  
 \<Renk > öğesi bir bileşeni ya da kullanıcı Arabirimi durumu için bir renk tanımlar. Bir renk için tercih edilen adlandırma şeması [UI] türüdür [State]. Yedek olduğu gibi "rengi," word kullanmayın. Bir renk öğe türü ve durumlar veya "Durum" rengi uygulanacak açıkça göstermelidir. Bir renk boş olmamalı ve bir ya da her ikisini de içermelidir bir \<arka plan > ve \<ön plan > öğesi. Renk öğelerini şu şekilde tanımlanır:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Özniteliği**|**Tanım**|  
|Ad|[Gerekli] Renk adı|  
  
 **Arka plan ve/veya ön plan**  
  
 \<Arka plan > ve \<ön plan > öğelerini tanımlama bir rengin değeri ve arka plan ya da bir kullanıcı Arabirimi öğesi ön plan için türü. Bu öğeler alt öğesi içerir.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Özniteliği**|**Tanım**|  
|Tür|[Gerekli] Renk türü. Aşağıdakilerden biri olabilir:<br /><br /> *CT_INVALID:* rengi ayarlanmadı veya geçersiz.<br /><br /> *CT_RAW:* ham ARGB değeri.<br /><br /> *CT_COLORINDEX:* KULLANMAYIN.<br /><br /> *CT_SYSCOLOR:* SysColor bir Windows Sistem rengi.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX bir Visual Studio rengi.<br /><br /> *CT_AUTOMATIC:* otomatik rengi.<br /><br /> *CT_TRACK_FOREGROUND:* KULLANMAYIN.<br /><br /> *CT_TRACK_BACKGROUND:* KULLANMAYIN.|  
|Kaynak|[Gerekli] Onaltılık temsil renk değeri|  
  
 __VSCOLORTYPE numaralandırması tarafından desteklenen tüm değerleri türü özniteliğinde şemayla tarafından desteklenir. Ancak, yalnızca CT_RAW ve CT_SYSCOLOR kullanmanızı öneririz.  
  
 **Hepsini bir araya**  
  
 Bu, geçerli tema .xml dosyası basit bir örneği verilmiştir:  
  
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
  
## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır  
 **Sözdizimi**  
  
 VsixColorCompiler \<XML dosyası > \<PkgDef Dosya > \<isteğe bağlı bağımsız değişken >  
  
 **Bağımsız Değişkenler**  
  
||||  
|-|-|-|  
|**Anahtar adı**|**Notlar**|**Gerekli veya isteğe bağlı**|  
|Adlandırılmamış (.xml dosyası)|Bu ilk adlandırılmamış parametre ve dönüştürmek için XML dosyasının yolu.|Gerekli|  
|Adlandırılmamış (.pkgdef dosyası)|Bu ikinci adlandırılmamış parametre ve oluşturulan .pkgdef dosyanın çıkış yolu.<br /><br /> Varsayılan: \<XML dosya adı > .pkgdef|İsteğe Bağlı|  
|/ nologo|Bu bayrak olarak ayarlandığında, yazdırma ürün ve telif hakkı bilgileri durdurur.|İsteğe Bağlı|  
|/?|Yardım bilgileri yazdırın.|İsteğe Bağlı|  
|/help|Yardım bilgileri yazdırın.|İsteğe Bağlı|  
  
 **Örnekler**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Notlar  
  
-   Bu araç, VC ++ Çalışma zamanı en son sürümü yüklü olmasını gerektirir.  
  
-   Yalnızca tek dosyalar desteklenir. Klasör yolları aracılığıyla toplu dönüştürme desteklenmiyor.  
  
## <a name="sample-output"></a>Örnek çıktı  
 Aracı tarafından oluşturulan .pkgdef dosyası şuna benzeyecektir anahtarları altında:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```