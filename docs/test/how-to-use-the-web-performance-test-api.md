---
title: Web performans testi API'si
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: eacdcf65619909c052f786a8b22b61b4d48292d9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064504"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Nasıl yapılır: web başarım testi API'si kullanma

Web performans testleri için kod yazabilirsiniz. Web performans testi API'si, kodlanmış web performans testleri, web performans testi eklentileri, istek eklentileri, istekler, ayıklama kuralları ve doğrulama kurallarını oluşturmak için kullanılır. Bu türleri oluşturan sınıfları, bu API temel sınıflardır. Bu API diğer türleri oluşturulmasını desteklemek için kullanılan <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>, ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> nesneleri. Kullandığınız <xref:Microsoft.VisualStudio.TestTools.WebTesting> özelleştirilmiş oluşturmak için ad alanı web performans testleri.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Web performans testi API, program aracılığıyla oluşturma ve bildirim temelli web performans testlerini kaydetmek için de kullanabilirsiniz. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> sınıfları.

> [!TIP]
> İncelemek için Nesne Tarayıcısı kullanmanız <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanı. Visual C# ve Visual Basic düzenleyicileri ad alanındaki sınıflarla kodlamak için IntelliSense desteği sunar.

Yük testleri için eklentileri de oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: yük testi API'si kullanma](../test/how-to-use-the-load-test-api.md) ve [nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>WebTesting ad alanını kullanmak için

1.  Bir web performansı ve bir web performans testi içeren bir yük testi projesi açın.

2.  Visual C# veya Visual Basic kitaplık projesi sınama çözümünüze ekleyin.

3.  Bir başvuru, sınıf kitaplığı projesi için web performansı ve yük testi projesi ekleyin.

4.  Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL'ye bir başvuru ekleyin.

5.  Sınıf kitaplığı projesinde bulunan sınıf dosyası ekleyin bir `using` bildirimi <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanı.

6.  Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> arabirimi.

7.  Projeyi oluşturun.

8.  Web Performans Testi Düzenleyicisi'ni kullanarak yeni web performans testi eklentisi ekleyin:

    1.  Seçin **Web Testi Eklentisi Ekle** araç.

         **Web Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

    2.  Altında **bir eklenti seçin**seçin, web performans testi eklentisi sınıfı.

    3.  İçinde **özelliklerini çili eklenti** bölmesinde, çalışma zamanında kullanmak eklenti için başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz sayıda özelliği getirebilir; bunları yalnızca genel, ayarlanabilir ve tam sayı, Boole veya dize gibi bir temel türden yapın. Özellikler penceresini kullanarak web başarım testi eklentisi özelliklerini daha sonra da düzenleyebilirsiniz.

    4.  Seçin **Tamam**.

9. Web performans testinizi çalıştırın.

     Örnek uygulaması için <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, bkz: [nasıl yapılır: web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: yük testi API'si kullanma](../test/how-to-use-the-load-test-api.md)
- [Nasıl yapılır: web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)