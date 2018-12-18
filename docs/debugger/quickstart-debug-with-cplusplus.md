---
title: C++ hata ayıklama
description: Visual Studio hata ayıklayıcısını kullanarak yerel kodda hata ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 036774134f705d95fbc526a9e6a336ac43005820
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639782"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Hızlı Başlangıç: C++ ile Visual Studio hata ayıklayıcısını kullanarak hata ayıklama

Visual Studio hata ayıklayıcısını uygulamalarınızın hatalarını ayıklamanıza yardımcı olmak için çok sayıda güçlü özellikler sağlar. Bu konuda bazı temel özellikleri öğrenmek için hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma 

1. Visual Studio'da **Dosya > Yeni proje**.

2. Altında **Visual C++**, seçin **Windows Masaüstü**seçip Ortadaki bölmeden **Windows konsol uygulaması**.

    Görmüyorsanız **Windows konsol uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir**.

3. Gibi bir ad yazın **MyDbgApp** tıklatıp **Tamam**.

    Visual Studio projesi oluşturur.

4. Aşağıdaki kod MyDbgApp.cpp değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kod (kaldırmayın `#include "stdafx.h"`):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Bir kesme noktası ayarlayın

A *kesme noktası* olan Visual Studio çalışan burada askıya almanız gösteren bir işaretçi, değişkenlerin değerleri veya bellek veya isteyip istemediğinizi bir kod dalı çalıştırılır davranışını göz olabilmesi için kod. Hata ayıklama en temel özelliğidir.

1. Cilt payını solundaki kesme noktası ayarlamak için tıklayın `doWork` işlev çağrısı (veya kod tuşuna basın ve bir satırı seçin **F9**).

    ![Bir kesme noktası ayarlamak](../debugger/media/dbg-qs-set-breakpoint.png "bir kesme noktası ayarlayın")

2. Şimdi basın **F5** (veya tercih **hata ayıklama > hata ayıklamayı Başlat**).

    ![Bir kesme noktası isabet](../debugger/media/dbg-qs-hit-breakpoint.png "bir kesme noktası isabet")

    Hata ayıklayıcı, Kesme noktasının ayarlandığı duraklatır. Burada hata ayıklayıcı ve uygulamanın yürütülmesi duraklatıldı deyimi, sarı bir ok ile belirtilir. Satırla `doWork` işlev çağrısı henüz çalıştırılmadı.

    > [!TIP]
    > Bir döngüde veya özyinelemede bir kesme noktasına sahip ya da sık, adım adım çok sayıda kesme noktaları varsa, kullanmak istemiyorsanız bir [koşullu kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) yalnızca belirli koşullar karşılandığında kodunuzu askıya alındığından emin olmak için. Koşullu kesme noktası zaman tasarrufu sağlar ve ayrıca, yeniden oluşturulması zor olan sorunlarında hata ayıklama kolaylaştırabilir.

    C++'ta bellekle ilgili hataları ayıklanacak çalışırken, kesme noktaları (NULL arayın) adres değerlerini incelemek için kullanabilirsiniz ve başvuru sayısı. 

## <a name="navigate-code"></a>Kod gidin

Devam etmek için hata ayıklayıcı istemek için farklı komutlar vardır. Visual Studio 2017'de yeni bir faydalı kod Gezinti komut göstereceğiz.

Kesme noktasında duraklatıldığı sırada deyimi üzerinden gelin `c1.push_back(20)` yeşil kadar **Çalıştır'ı tıklatın** düğmesi ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png "RunToClick") görünür ve tuşuna basın **Çalıştır'ı tıklatın** düğmesi.

![Çalıştır'ı tıklatın](../debugger/media/dbg-qs-run-to-click.png "Çalıştır'a tıklayın")

Uygulama yürütülmeye çağırma `doWork`ve düğmeyi tıklattığınız kod satırında duraklatır.

Ortak klavye komutları için kullanılan kodu adımlayın dahil **F10** ve **F11**. Daha fazla ayrıntılı yönergeler için bkz: [Başlangıç Kılavuzu](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Bir datatip içinde değişkenleri denetleyin

1. Kod (sarı yürütme işaretçi işaretlenmiştir) geçerli satırda üzerine `c1` nesneyi farenizi bir datatip gösterilecek.

    ![Bir datatip görüntülemek](../debugger/media/dbg-qs-data-tip.png "bir datatip görüntüleyin")

    Datatip geçerli değerini gösteren `c1` değişkeni ve onun özelliklerini denetleme olanak tanır. Beklediğiniz olmayan bir değer görürseniz, hata ayıklama sırasında bir hata muhtemelen önceki veya çağıran kod satırıyla vardır. 

2. Geçerli özellik değerlerini aramak için datatip genişletin `c1` nesne.

3. Değerini görmek devam edebilmesi için datatip sabitlemek istiyorsanız `c1` kod çalıştırılırken, küçük bir Raptiye simgesine tıklayın. (Uygun bir konuma sabitlenmiş datatip taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Kodunuzda hata ayıklama oturumu sırasında ortasında test etmek istediğiniz bir değişiklik belirlerseniz, çok da yapabilirsiniz.

1. İkinci bir örneğini tıklatın `c2.front()` değiştirip `c2.front()` için `c2.back()`.

2. Tuşuna **F10** (veya **hata ayıklama > Step Over**) birkaç kez hata ayıklayıcı ilerleyin ve düzenlenen kod yürütmek için.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue.gif "Düzenle ve devam et")

    **F10** (atlayabilir kod hala çalışır) bunların Adımlama yerine işlevler üzerinde bir zaman alır, ancak adımları sırasında bir hata ayıklayıcı deyimi ilerler.

Düzenle ve devam et kullanma ve özellik kısıtlamaları hakkında daha fazla bilgi için bkz: [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)
