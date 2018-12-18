---
title: İstek düzeyi eklentisi web performans testleri için oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 4b9408560eabf9a824f391625753b2ddd390a9d2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054080"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Nasıl yapılır: istek düzeyi eklentisi oluşturma

*İstekleri* web performans testleri oluşturan bildirim deyimleri. Web performans testi eklentileri yalıtmak ve ana bildirim deyimleri, web performans testinde dışındaki kod yeniden kullanımını etkinleştirin. Eklentileri oluşturun ve bunları tek bir istek de içeren web performans testi için farklı ekleyin. Özelleştirilmiş *istek eklentisi* belirli bir istek, bir web performans testi çalıştırırken kodu çağırmak için bir yol sunar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Her web performans test isteği eklentisi PreRequest yöntemi ve PostRequest yöntemi vardır. Belirli bir http isteği için bir istek eklentisi ekledikten sonra istek ve yanıt alındıktan sonra PostRequest harekete önce PreRequest olay harekete geçirilir.

Kendi sınıftan türetme tarafından özelleştirilmiş web performans test isteği eklentisi oluşturabilirsiniz <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> temel sınıfı.

Web performans testleri kaydettiğiniz özelleştirilmiş web performans testi isteği eklentileri kullanabilirsiniz. Özelleştirilmiş web performans testi isteği eklentileri en az miktarda bir büyük bir web performans testlerinizi üzerindeki denetim düzeyini elde etmek için kod yazmanıza olanak sağlar. Ancak, bunları kodlanmış web performans testleri ile de kullanabilirsiniz. Bkz: [oluştur ve Çalıştır kodlanmış web performans testi](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>İstek düzeyi eklentisi oluşturmak için

1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle** seçip **yeni proje**.

     **Yeni Proje Ekle** iletişim kutusu görüntülenir.

2.  Altında **yüklü şablonlar**seçin **Visual C#**.

3.  Şablonlar listesinde seçin **sınıf kitaplığı**.

4.  İçinde **adı** metin kutusuna sınıf ve seçin için bir ad yazın **Tamam**.

     Yeni sınıf kitaplığı projesi eklenir **Çözüm Gezgini** ve yeni bir sınıf görünür **Kod Düzenleyicisi**.

5.  İçinde **Çözüm Gezgini**, sağ **başvuruları** seçin ve yeni sınıf kitaplığı klasöründe **Başvuru Ekle**.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

6.  Seçin **.NET** sekmesinde, aşağı kaydırın, seçin **Microsoft.VisualStudio.QualityTools.WebTestFramework** seçip **Tamam**

     Başvuru **Microsoft.VisualStudio.QualityTools.WebTestFramework** eklenir **başvuru** klasöründe **Çözüm Gezgini**.

7.  İçinde **Çözüm Gezgini**web performansının üst düğümünü sağ tıklatın ve web performans testi isteği test eklentisini eklemek istediğiniz yük testini içeren test projesini yükleyin. Seçin **Başvurusu Ekle**.

     **Başvuru Ekle iletişim kutusu görüntülenir**.

8.  Seçin **projeleri** sekmesinde **sınıf kitaplığı projesi** seçip **Tamam** .

9. İçinde **Kod Düzenleyicisi**, eklentinizin kodunu yazın. İlk olarak, türetilen yeni bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

10. Uygulama içinde bir veya iki kod <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> olay işleyicileri. Örnek uygulama için aşağıdaki örnek bölümüne bakın.

11. Kodu yazdıktan sonra yeni projeyi derleyin.

12. İstek eklentisi eklemek istediğiniz web performans testi açın.

13. İstek eklentisi ve select eklemek istediğiniz isteğe sağ tıklatın **istek eklentisi Ekle**.

     **Web Test isteği Eklentisi Ekle** iletişim kutusu görüntülenir.

14. Altında **bir eklenti seçin**, yeni seçin eklenti.

15. İçinde **özelliklerini çili eklenti** bölmesinde, çalışma zamanında kullanmak eklenti için başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz sayıda özelliği getirebilir; bunları yalnızca genel, ayarlanabilir ve tam sayı, Boole veya dize gibi bir temel türden yapın. Özellikler penceresini kullanarak web başarım testi eklentisi özelliklerini daha sonra da değiştirebilirsiniz.

16. Seçin **Tamam**.

     Eklenti eklenir **istek eklentileri** HTTP isteğinin bir alt klasörü klasörü.

    > [!WARNING]
    > Bir web performans testi ya da eklentisini kullanan yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: özel durum \<eklenti > olay: dosyası veya bütünleştirilmiş kod yüklenemedi '\<"Eklenti adı".dll dosyası >, sürüm =\<n.n.n.n >, kültür neutral, PublicKeyToken = = null' veya bağımlılıklarından biri. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Eklentilerinizi birine kod değişikliği yapmanız ve yeni bir DLL sürümü oluşturursanız Bunun nedeni **(sürüm = 0.0.0.0)**, ancak eklenti hala özgün eklenti sürümüne başvuruyor. Bu sorunu gidermek için şu adımları izleyin:
    >
    > 1.  Web performansı ve yük testi projesi içinde başvurularda bir uyarı görürsünüz. Kaldırın ve Başvuruyu eklenti DLL'nizden yeniden ekleyin.
    > 2.  Test veya uygun konumdan eklentiyi kaldırın ve yeniden ekleyin.

## <a name="example"></a>Örnek

İki iletişim kutusu görüntüleyen bir özelleştirilmiş web performans testi eklentisi oluşturmak için aşağıdaki kodu kullanabilirsiniz. İstek Eklentisi Ekle istekle ilişkili URL bir iletişim kutusu görüntüler. İkinci iletişim kutusunda, aracı için bilgisayar adı görüntülenir.

> [!NOTE]
> Aşağıdaki kodu üzere System.Windows.Forms başvurusu eklemeniz gerekir.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kodu bir web performans testi için özel bir ayıklama kuralı](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodu bir web performans testi için özel doğrulama kuralı](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Oluşturma ve bir kodlanmış web performans testini çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)