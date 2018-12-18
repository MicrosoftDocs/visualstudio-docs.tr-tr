---
title: Kaynaklardan gelen bildirim | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 514135e5c6ba932d7b3b4319dd39c1df4e8cb212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134294"
---
# <a name="manifest-from-resources"></a>Kaynaklardan gelen bildirim
Bildirim kaynakları aracından görüntü kaynakları (.png veya .xaml dosyaları) bir listesini alır ve Visual Studio Görüntü hizmeti ile kullanılmak üzere bu görüntüleri izin veren bir .imagemanifest dosyası oluşturur bir konsol uygulamasıdır. Ayrıca, bu aracı için var olan bir .imagemanifest görüntüleri eklemek için kullanılabilir. Bu araç, bir Visual Studio uzantısı görüntülere yüksek DPI ve tema desteği eklemek için yararlıdır. Oluşturulan .imagemanifest dosya dahil ve Visual Studio Uzantısı (.vsix) bir parçası olarak dağıtılır.  
  
## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır  
 **Sözdizimi**  
  
 ManifestFromResources /resources:\<dizin1 >;\< Img1 > /assembly:\<AssemblyName > \<isteğe bağlı bağımsız değişken >  
  
 **Bağımsız Değişkenler**  
  
||||  
|-|-|-|  
|**Anahtar adı**|**Notlar**|**Gerekli veya isteğe bağlı**|  
|/Resources|Görüntüleri veya dizinleri noktalı virgülle ayrılmış listesi. Bu listede her zaman bildirimde olacaktır görüntüleri tam listesini içermelidir. Yalnızca kısmi bir liste verilirse dahil edilmeyen girdileri kaybolacak.<br /><br /> Belirtilen kaynak dosyası bir görüntü Şerit ise, aracı, ayrı görüntülere her subimage bildirime eklemeden önce bölecek.<br /><br /> Resim .png dosyası ise, böylece aracı görüntünün doğru özniteliklerini doldurabilirsiniz adı şöyle biçime önerilir: \<adı >.\< Genişlik >. \<Yükseklik > .png.|Gerekli|  
|/Assembly|(Uzantısı dahil değil) yönetilen derleme veya çalışma zamanı yolun kaynakları (göre bildirim çalışma zamanı konum) barındıran yerel derlemenin adı.|Gerekli|  
|/ bildirimi|Oluşturulan .imagemanifest dosyaya vermek için adı. Bu, farklı bir konumda dosya oluşturmak için mutlak veya göreli bir yol da içerebilir. Varsayılan derleme adı adıyla aynıdır.<br /><br /> Varsayılan: \<geçerli dizini >\\< derleme\>.imagemanifest|İsteğe Bağlı|  
|/guidName|Tüm görüntüleri oluşturulan bildiriminde GUID simgesi sağlamak için adı.<br /><br /> Varsayılan: AssetsGuid|İsteğe Bağlı|  
|/rootPath|Yönetilen kaynak URI oluşturmadan önce atılması gerektiğinde kök yolu. (Bu bayrak aracı göreli URI yolu kaynakları yüklemek başarısız olmasına neden yanlış alır burada talepleriyle yardımcı olmaktır.)<br /><br /> Varsayılan: \<geçerli dizin >|İsteğe Bağlı|  
|/ Recursive|Bu bayrak olarak ayarlandığında söyler yinelemeli olarak araç /resources değişkeninde herhangi bir dizin arayın. Bu bayrak atlama dizinleri top-düzey yalnızca aramada neden olur.|İsteğe Bağlı|  
|/isNative|Derleme bağımsız değişken bir yerel derleme için bir yol olduğunda bu bayrağını ayarlayın. Derleme bağımsız değişken bir yönetilen derlemenin adını olduğunda bu bayrağı yok sayın. (Bu bayrak hakkında ek bilgi için Notlar bölümüne bakın.)|İsteğe Bağlı|  
|/newGuids|Bu bayrak olarak ayarlandığında bildirimden varolan bir birleştirme yerine GUID simgesi görüntüler için yeni bir değer oluşturmak için aracı söyler.|İsteğe Bağlı|  
|/newIds|Bu bayrak olarak ayarlandığında değerleri varolan bildirimden birleştirme yerine her görüntü için yeni kimliği sembol değerleri oluşturmak için aracı söyler.|İsteğe Bağlı|  
|/ nologo|Bu bayrak olarak ayarlandığında, yazdırma ürün ve telif hakkı bilgileri durdurur.|İsteğe Bağlı|  
|/?|Yardım bilgileri yazdırın.|İsteğe Bağlı|  
|/help|Yardım bilgileri yazdırın.|İsteğe Bağlı|  
  
 **Örnekler**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Notlar  
  
-   Aracı yalnızca .png ve .xaml dosyalarını destekler. Diğer görüntü veya dosya türlerini yoksayılacak. Kaynakları ayrıştırılırken desteklenmeyen tüm türler için bir uyarı üretilir. Desteklenen Hayır ise görüntüleri aracı bittiği bulunan kaynaklar ayrıştırma, bir hata oluşturulur  
  
-   Resmin gerçek boyutundan farklı olsa bile .png görüntüleri için Önerilen biçimi izleyerek, aracı .png boyutu/boyut değeri biçimi tarafından belirtilen boyuta ayarlar.  
  
-   Genişliği/yüksekliğinin biçimi .png görüntüler için atlanabilir, ancak aracı görüntünün gerçek genişliği/yüksekliğinin okuyun ve bu görüntünün boyutu/boyut değeri için kullanın.  
  
-   Tek başına görüntülere görüntü Şerit bölme ve bu varolan bildirime eklemek aracın çalıştığı aynı görüntü Şerit birden çok kez aynı .imagemanifest için bu aracı çalışan yinelenen bildirim girdiler neden olur.  
  
-   (/NewGuids veya /newIds atlayarak) birleştirme yalnızca aracı tarafından oluşturulan bildirimleri için yapılması gerekir. Özelleştirilmiş veya başka yollarla oluşturulan bildirimleri doğru birleştirilebilir değil.  
  
-   Yerel derlemeler için oluşturulan bildirimleri kaynak kimlikleri yerel derlemenin .rc dosyasından eşleşen kimliği semboller yapmak için nesil sonra el ile düzenleyebilirsiniz olması gerekebilir.  
  
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
  
 **Bir görüntü Şerit için görüntü bildirimi**  
  
 Bir görüntü Şerit için bir resim bildirimi bu .xml dosyasına benzer olacaktır:  
  
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
  
 **Yerel derleme görüntü kaynakları için görüntü bildirimi**  
  
 Yerel görüntüler için bir resim bildirimi bu .xml dosyasına benzer olacaktır:  
  
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