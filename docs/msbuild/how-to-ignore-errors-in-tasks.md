---
title: 'Nasıl yapılır: görevlerdeki hataları yoksayma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild - "vs-ide-sdk"
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: 3df3a3b40dd67f12bac19f4e69f5293c85bb85f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940040"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıl yapılır: görevlerdeki hataları yoksayma
Bazen bir derleme hatalarının bazı görevler dayanıklı olmasını istersiniz. Kritik olmayan bu görev başarısız olursa yine de gerekli çıktı üretebilir çünkü devam etmek için yapı istediğinizde. Örneğin, bir proje kullanıyorsa bir `SendMail` her bileşenin oluşturulduktan sonra bir e-posta iletisi göndermek için görev posta sunucuları kullanılamaz ve durum iletilerinin gönderilemez bile tamamlanana kadar devam etmek derleme için kabul edilebilir düşünebilirsiniz. Veya Ara dosyaları derleme sırasında genellikle silinir, örneğin, bu dosyaları silinemez, tamamlanana kadar devam etmek derleme için kabul edilebilir düşünebilirsiniz.  
  
## <a name="use-the-continueonerror-attribute"></a>ContinueOnError özniteliği kullanın  
 `ContinueOnError` Özniteliği `Task` öğesi, bir derleme durdurur veya görev hatası oluştuğunda devam edip denetler. Bu öznitelik de derleme devam ettiğinde hatalarını hata veya uyarı kabul edilip edilmeyeceğini denetler.  
  
 `ContinueOnError` Öznitelik aşağıdaki değerlerden birini içerebilir:  
  
- **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, sonraki görevlerinde [hedef](../msbuild/target-element-msbuild.md) öğesi ile derleme devam yürütülecek ve görevin tüm hataları uyarı olarak kabul edilir.  
  
- **ErrorAndContinue**. Bir görev başarısız olduğunda, sonraki görevlerinde `Target` öğesi ile derleme devam yürütmek ve tüm hataları görev hata olarak kabul edilir.  
  
- **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, listesindeki kalan görevlere `Target` olmayan öğe ve derleme yürütülür ve tüm `Target` öğesi ve yapı başarısız olduğu değerlendirilir.  
  
  .NET Framework 4.5 yalnızca desteklenen önce sürümleri `true` ve `false` değerleri.  
  
  Varsayılan değer olan `ContinueOnError` olduğu `ErrorAndStop`. Öznitelik ayarlamanız `ErrorAndStop`, davranışı açık proje dosyasını okuyan herkese yapmanızı ister.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Bir görevdeki bir hatayı yok saymak için  
  
-   Kullanım `ContinueOnError` görevin özniteliği. Örneğin:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği gösterir `Build` hedef hala çalışır ve yapı değerlendirilir olsa bile, bir başarı `Delete` görev başarısız olur.  
  
```xml  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
[MSBuild](../msbuild/msbuild.md)  
[Görev başvurusu](../msbuild/msbuild-task-reference.md)   
[Görevler](../msbuild/msbuild-tasks.md)