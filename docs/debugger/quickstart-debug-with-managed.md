---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
description: C# veya Visual Basic, Visual Studio hata ayıklayıcısını kullanarak hata ayıklama
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e35d102a30ffc7b80d39f359542bbdc4c00feff6
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257192"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Hızlı Başlangıç: ile hata ayıklama C# veya Visual Basic, Visual Studio hata ayıklayıcıyı kullanma

Visual Studio hata ayıklayıcısını uygulamalarınızın hatalarını ayıklamanıza yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma 

1. Visual Studio'da **Dosya > Yeni proje**.

2. Altında **Visual C#** veya **Visual Basic**, seçin **.NET Core**seçip Ortadaki bölmeden **konsol uygulaması (.NET Core)**.

     Görmüyorsanız **konsol uygulaması (.NET Core)** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** ve **.NET Core** iş yükü, ardından **Değiştir**.

3. Gibi bir ad yazın **MyDbgApp** tıklatıp **Tamam**.

    Visual Studio projesi oluşturur.

4. İçinde *Program.cs* veya *Module1.vb*, aşağıdaki kodu değiştirin

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    Bu kod ile:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic'te, Başlangıç nesnesi ayarlandığından emin olun `Sub Main` (**özellikleri > Uygulama > Başlangıç nesnesi**).

## <a name="set-a-breakpoint"></a>Bir kesme noktası ayarlayın

A *kesme noktası* olan Visual Studio çalışan burada askıya almanız gösteren bir işaretçi, değişkenlerin değerleri veya bellek veya isteyip istemediğinizi bir kod dalı çalıştırılır davranışını göz olabilmesi için kod. Hata ayıklama en temel özelliğidir.

1. Cilt payını solundaki kesme noktası ayarlamak için tıklayın `doWork` işlev çağrısı (veya kod tuşuna basın ve bir satırı seçin **F9**).

    ![Bir kesme noktası ayarlamak](../debugger/media/dbg-qs-set-breakpoint-csharp.png "bir kesme noktası ayarlayın")

2. Şimdi basın **F5** (veya tercih **hata ayıklama > hata ayıklamayı Başlat**).

    ![Bir kesme noktası isabet](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "bir kesme noktası isabet")

    Hata ayıklayıcı, Kesme noktasının ayarlandığı duraklatır. Burada hata ayıklayıcı ve uygulamanın yürütülmesi duraklatıldı deyimi, sarı bir ok ile belirtilir. Satırla `doWork` işlev çağrısı taşınmadığından henüz yürütülür.

    > [!TIP]
    > Bir döngüde veya özyinelemede bir kesme noktasına sahip ya da sık, adım adım çok sayıda kesme noktaları varsa, kullanmak istemiyorsanız bir [koşullu kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) yalnızca belirli koşullar karşılandığında kodunuzu askıya alındığından emin olmak için. Koşullu kesme noktası zamandan tasarruf edebilirsiniz ve bu da, yeniden oluşturulması zor olan sorunlarında hata ayıklama kolaylaştırabilir.

## <a name="navigate-code"></a>Kod gidin

Devam etmek için hata ayıklayıcı istemek için farklı komutlar vardır. Visual Studio 2017'de yeni bir faydalı kod Gezinti komut göstereceğiz.

Kesme noktasında duraklatıldığı sırada deyimi üzerinden gelin `c1.AddLast(20)` yeşil kadar **Çalıştır'ı tıklatın** düğmesi ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png "RunToClick") görünür ve tuşuna basın **Çalıştır'ı tıklatın** düğmesi.

![Çalıştır'ı tıklatın](../debugger/media/dbg-qs-run-to-click-csharp.png "Çalıştır'a tıklayın")

Uygulama yürütülmeye çağırma `doWork`ve düğmeyi tıklattığınız kod satırında duraklatır.

Ortak klavye komutları için kullanılan kodu adımlayın dahil **F10** ve **F11**. Daha fazla ayrıntılı yönergeler için bkz: [Başlangıç Kılavuzu](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Bir datatip içinde değişkenleri denetleyin

1. Kod (sarı yürütme işaretçi işaretlenmiştir) geçerli satırda üzerine `c1` nesneyi farenizi bir datatip gösterilecek.

    ![Bir datatip görüntülemek](../debugger/media/dbg-qs-data-tip-csharp.png "bir datatip görüntüleyin")

    Datatip geçerli değerini gösteren `c1` değişkeni ve onun özelliklerini denetleme olanak tanır. Beklediğiniz olmayan bir değer görürseniz, hata ayıklama sırasında bir hata muhtemelen önceki veya çağıran kod satırıyla vardır. 

2. Geçerli özellik değerlerini aramak için datatip genişletin `c1` nesne.

3. Değerini görmek devam edebilmesi için datatip sabitlemek istiyorsanız `c1` kod çalıştırılırken, küçük bir Raptiye simgesine tıklayın. (Uygun bir konuma sabitlenmiş datatip taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Kodunuzda hata ayıklama oturumu sırasında ortasında test etmek istediğiniz bir değişiklik belirlerseniz, çok da yapabilirsiniz.

1. İkinci bir örneğini tıklatın `c2.First.Value` değiştirip `c2.First.Value` için `c2.Last.Value`.

2. Tuşuna **F10** (veya **hata ayıklama > Step Over**) birkaç kez hata ayıklayıcı ilerleyin ve düzenlenen kod yürütmek için.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Düzenle ve devam et")

    **F10** (atlayabilir kod hala çalışır) bunların Adımlama yerine işlevler üzerinde bir zaman alır, ancak adımları sırasında bir hata ayıklayıcı deyimi ilerler.

Düzenle ve devam et kullanma ve özellik kısıtlamaları hakkında daha fazla bilgi için bkz: [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)
