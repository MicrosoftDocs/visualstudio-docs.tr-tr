---
title: ASP.NET hatalarını ayıklama
description: Visual Studio hata ayıklayıcısını kullanarak ASP.NET hatalarını ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636993"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Hızlı Başlangıç: Visual Studio hata ayıklayıcısı ile ASP.NET hatalarını ayıklama

Visual Studio hata ayıklayıcısını uygulamalarınızın hatalarını ayıklamanıza yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma 

1. Visual Studio'da **Dosya > Yeni proje**.

1. Altında **Visual C#**, seçin **Web**seçip Ortadaki bölmeden **ASP.NET Core Web uygulaması**.

1. Gibi bir ad yazın **MyDbgApp** tıklatıp **Tamam**.

1. Görünen iletişim kutusunda **Web uygulaması** orta bölmesinde ve ardından **Tamam**.

     Görmüyorsanız **Web uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **ASP.NET ve web geliştirme** iş yükü, ardından **Değiştir**.

    ![Bir Web uygulaması seçin](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio projesi oluşturur.

1. Çözüm Gezgini'nde About.cshtml.cs (altında Pages/About.cshtml) açın ve aşağıdaki kodu değiştirin

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    Bu kod ile:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Bir kesme noktası ayarlayın

A *kesme noktası* olan Visual Studio çalışan burada askıya almanız gösteren bir işaretçi, değişkenlerin değerleri veya bellek veya isteyip istemediğinizi bir kod dalı çalıştırılır davranışını göz olabilmesi için kod. Hata ayıklama en temel özelliğidir.

1. Cilt payını solundaki kesme noktası ayarlamak için tıklayın `doWork` işlevi (veya kod tuşuna basın ve bir satırı seçin **F9**).

    ![Bir kesme noktası ayarlayın](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Açılış ayracından solunda Kesme noktasının ayarlandığını (`{`).

1. Şimdi basın **F5** (veya tercih **hata ayıklama > hata ayıklamayı Başlat**).

1. Web sayfa yüklendiğinde tıklayın **hakkında** web sayfasının üstündeki bağlantısı.

    Hata ayıklayıcı, Kesme noktasının ayarlandığı duraklatır. Burada hata ayıklayıcı ve uygulamanın yürütülmesi duraklatıldı deyimi, sarı bir ok ile belirtilir. Açma küme ayracı ile satır (`{`) sonra `doWork` işlev bildirimi henüz çalıştırılmadı.

    ![Bir kesme noktası isabet](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Bir döngüde veya özyinelemede bir kesme noktasına sahip ya da sık, adım adım çok sayıda kesme noktaları varsa, kullanmak istemiyorsanız bir [koşullu kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) yalnızca belirli koşullar karşılandığında kodunuzu askıya alındığından emin olmak için. Bu, zaman tasarrufu sağlar ve ayrıca, yeniden oluşturulması zor olan sorunlarında hata ayıklama kolaylaştırabilir.

## <a name="navigate-code"></a>Kod gidin

Devam etmek için hata ayıklayıcı istemek için farklı komutlar vardır. Visual Studio 2017'de yeni bir faydalı kod Gezinti komut göstereceğiz.

Kesme noktasında duraklatıldığı sırada deyimi üzerinden gelin `return c2` yeşil kadar **Çalıştır'a tıklayın** düğmesi ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png) görünür ve tuşuna **Çalıştır'ı tıklatın** düğmesi.

![Çalıştır'a tıklayın](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Uygulama yürütme devam eder ve düğmeyi tıklattığınız kod satırında duraklatır.

Ortak klavye komutları için kullanılan kodu adımlayın dahil **F10** ve **F11**. Daha fazla ayrıntılı yönergeler için bkz: [Başlangıç Kılavuzu](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Bir datatip içinde değişkenleri denetleyin

1. Kod (sarı yürütme işaretçi işaretlenmiştir) geçerli satırda üzerine `c2` nesneyi farenizi bir datatip gösterilecek.

    ![Bir datatip görüntüleyin](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Datatip geçerli değerini gösteren `c2` değişkeni ve onun özelliklerini denetleme olanak tanır. Beklediğiniz olmayan bir değer görürseniz, hata ayıklama sırasında bir hata muhtemelen önceki veya çağıran kod satırıyla vardır. 

2. Geçerli özellik değerlerini aramak için datatip genişletin `c2` nesne.

3. Değerini görmek devam edebilmesi için datatip sabitlemek istiyorsanız `c2` kod çalıştırılırken, küçük bir Raptiye simgesine tıklayın. (Uygun bir konuma sabitlenmiş datatip taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Kodunuzda hata ayıklama oturumu sırasında ortasında test etmek istediğiniz bir değişiklik belirlerseniz, çok da yapabilirsiniz.

1. İçinde `OnGet` yöntemi, ikinci bir örneğini tıklatın `result.First.Value` değiştirip `result.First.Value` için `result.Last.Value`.

1. Tuşuna **F10** (veya **hata ayıklama > Step Over**) birkaç kez hata ayıklayıcı ilerleyin ve düzenlenen kod yürütmek için.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Düzenle ve devam et")

    **F10** (atlayabilir kod hala çalışır) bunların Adımlama yerine işlevler üzerinde bir zaman alır, ancak adımları sırasında bir hata ayıklayıcı deyimi ilerler.

Düzenle ve devam et kullanma ve özellik kısıtlamaları hakkında daha fazla bilgi için bkz: [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)
