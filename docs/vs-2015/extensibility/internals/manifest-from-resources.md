---
title: Kaynaklardan bildirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d442686ab588932cac077a0b5fdc09a1a746c3d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771876"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bildirim kaynakları aracından görüntü kaynakları (.png veya .xaml dosyaları) bir listesini alır ve Visual Studio Görüntü hizmeti ile kullanılmak üzere bu görüntüleri izin veren bir .imagemanifest dosyası oluşturur bir konsol uygulamasıdır. Ayrıca, bu aracı için mevcut bir .imagemanifest görüntüleri eklemek için kullanılabilir. Bu araç, Visual Studio uzantısı görüntülere yüksek DPI ve Tema oluşturma desteği eklemek için yararlıdır. Oluşturulan .imagemanifest dosya dahil ve Visual Studio Uzantısı (.vsix) bir parçası olarak dağıtılabilir.  
  
## <a name="how-to-use-the-tool"></a>Aracı'nı kullanma  
 **Söz dizimi**  
  
 ManifestFromResources /resources:\<dizin1 >;\< Img1 >/Assembly:\<AssemblyName > \<isteğe bağlı bağımsız değişken >  
  
 **Bağımsız Değişkenler**  
  
||||  
|-|-|-|  
|**Anahtar adı**|**Notlar**|**Gerekli veya isteğe bağlı**|  
|/Resources|Görüntüleri veya dizinlerin noktalı virgülle ayrılmış listesi. Bu liste her zaman bildirimde olacak görüntü tam listesini içermelidir. Yalnızca kısmi bir liste verilirse, dahil edilmeyen girişleri kaybolur.<br /><br /> Belirtilen kaynak dosyasının bir görüntü şeridi ise, araç, ayrı görüntülere her subimage bildirime eklemeden önce bölecektir.<br /><br /> Resim .png dosyası ise, böylece aracı görüntünün doğru özniteliklerini doldurabilirsiniz adı gibi bu biçime önerilir: \<adı >.\< Genişlik >. \<Yükseklik > .png.|Gerekli|  
|/ Assembly|Yönetilen bütünleştirilmiş kod (uzantısı dahil değil) veya çalışma zamanı yolunu (göreli bildirim çalışma zamanının konumu) kaynakları barındıran yerel bütünleştirilmiş kodun adı.|Gerekli|  
|bildirim /|Oluşturulan .imagemanifest dosyaya vermek için adı. Ayrıca, farklı bir konumda dosya oluşturmak için mutlak veya göreli bir yol da içerebilir. Varsayılan adını derleme adı eşleşir.<br /><br /> Varsayılan: \<geçerli dizin >\\< derleme\>.imagemanifest|İsteğe Bağlı|  
|/guidName|Tüm görüntüleri oluşturulan bildirim için GUID sembol vermek için adı.<br /><br /> Varsayılan: AssetsGuid|İsteğe Bağlı|  
|/rootPath|Yönetilen Kaynak URI'leri oluşturmadan önce çıkarılır gereken kök yolu. (Bu bayrağı araç göreli URI yolu yanlış kaynakları yüklemek başarısız olmasına neden alır burada çalışmalarıyla yardımcı olmaya yöneliktir.)<br /><br /> Varsayılan: \<geçerli dizin >|İsteğe Bağlı|  
|/ Recursive|Bu bayrak ayarlandığında, yinelemeli olarak araç söyler /resources bağımsız değişkendeki herhangi bir dizin arayın. Bu bayrak atlama dizinleri top-düzey yalnızca Search'te neden olur.|İsteğe Bağlı|  
|/isNative|Derleme bağımsız değişken yerel bir derleme için bir yol olduğunda bu bayrağı ayarlayın. Derleme bağımsız değişken yönetilen derlemenin adını olduğunda bu bayrağı yoksayın. (Bu bayrağı hakkında ek bilgi için Notlar bölümüne bakın.)|İsteğe Bağlı|  
|/newGuids|Bu bayrak ayarlandığında, varolan bir bildirimi adresinden birleştirme yerine görüntüleri GUID sembol için yeni bir değer oluşturmak için aracı söyler.|İsteğe Bağlı|  
|/newIds|Bu bayrak ayarlandığında, varolan bir bildirimi değerlerinden birleştirme yerine her resim için yeni kod sembol değerleri oluşturmak için aracı söyler.|İsteğe Bağlı|  
|/ nologo|Bu bayrak ayarlandığında, ürün ve telif hakkı bilgileri yazdırmasının durdurur.|İsteğe Bağlı|  
|/?|Yardım bilgi yazdırır.|İsteğe Bağlı|  
|/help|Yardım bilgi yazdırır.|İsteğe Bağlı|  
  
 **Örnekler**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Notlar  
  
-   Araç yalnızca .png ve .xaml dosyalarını destekler. Diğer resim veya dosya türleri göz ardı edilir. Tüm desteklenmeyen türler kaynakları ayrıştırılırken bir uyarı oluşturulur. Desteklenen Hayır ise görüntüleri aracı tamamlandığında bulunan kaynakları ayrıştırma, bir hata oluşturulur  
  
-   Görüntünün gerçek boyutundan farklı olsa bile .png görüntüleri için önerdiğimiz biçimi takip ederek, aracı .png boyutu/boyut değeri biçimi belirtilen boyutuna ayarlanır.  
  
-   Genişliği/yüksekliğinin biçimi için .png görüntü atlanmış olabilir, ancak aracın görüntünün gerçek genişliği/yüksekliğinin okuyun ve bu görüntünün boyutu/boyut değeri için kullanın.  
  
-   Görüntü şeridi tek başına görüntülere bölmek ve bu varolan bir bildirimi eklemek aracın çalıştığı aynı görüntü şeridi birden çok kez aynı .imagemanifest için bu aracı üzerinde çalışan yinelenen bildirimi girişlerinde neden olur.  
  
-   (/NewGuids veya /newIds atlama) Birleştirme aracı tarafından oluşturulan bildirimleri yalnızca yapılmalıdır. Özelleştirilmiş veya başka yollarla oluşturulan bildirimleri doğru şekilde birleştirilebilir değil.  
  
-   Yerel derlemeler için oluşturulan bildirimleri kaynak kimliklerini yerel derlemenin .rc dosyasından eşleşen kimliği semboller yapmak için nesil sonra elle düzenlenerek olması gerekebilir.  
  
## <a name="sample-output"></a>Örnek Çıktı  
 **Basit görüntü bildirimi**  
  
 Bir görüntü bildirimi bu .xml dosyasına benzer olacaktır:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Görüntü şeridi için görüntü bildirimi**  
  
 Görüntü şeridi için bir görüntü bildirimi bu .xml dosyasına benzer olacaktır:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Yerel derleme resim kaynakları için görüntü bildirimi**  
  
 Yerel görüntüler için bir görüntü bildirimi bu .xml dosyasına benzer olacaktır:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```

