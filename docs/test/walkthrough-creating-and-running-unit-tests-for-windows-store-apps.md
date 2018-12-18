---
title: Oluşturma ve UWP uygulamaları için birim testleri çalıştırma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 66a107fbd738bc26fdf608223ff43f958754e3ae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065306"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

Visual Studio birim testi Evrensel Windows Platformu (UWP) uygulamaları için destek içerir. Visual C#, Visual Basic ve Visual C++ için birim test proje şablonlarını içerir.

> [!TIP]
> UWP uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [UWP uygulamaları kullanmaya başlama](/windows/uwp/get-started/).

Aşağıdaki yordamlar oluşturma, çalıştırma ve bir UWP uygulaması için birim testlerinin hatalarını ayıklama adımlarını açıklamaktadır.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Bir UWP uygulaması için birim test projesi oluşturma

1.  Gelen **dosya** menüsünde seçin **yeni proje**.

     **Yeni proje** iletişim kutusunu görüntüler.

2.  Şablonlar'ın altında birim testleri oluşturun ve sonra kitaplık ilişkili Windows Evrensel birim testi için kullanmak istediğiniz programlama dilini seçin. Örneğin, **Visual C#** , ardından **Windows Evrensel**ve ardından **birim testi kitaplığı (Evrensel Windows)**.

3.  (İsteğe bağlı) İçinde **adı** metin kutusuna proje için kullanmak istediğiniz adı girin.

4.  (İsteğe bağlı) Girerek projeyi oluşturmak istediğiniz yolu değiştirmek **konumu** metin veya seçerek **Gözat** düğmesi.

5.  (İsteğe bağlı) İçinde **çözüm** ad metin kutusunda, çözümünüz için kullanmak istediğiniz ismi girin.

6.  Bırakın **çözüm için dizin oluştur** seçeneği seçili ve seçin **Tamam** düğmesi.

     ![Özel olarak uyarlanmış bir birim testi kitaplığı](../test/media/unit_test_win8_1.png)

     **Çözüm Gezgini** doldurulur UWP birim testi projesi ve Kod Düzenleyicisi, UnitTest1 başlıklı varsayılan birim sınamasını görüntüler.

     ![Yeni özel olarak uyarlanmış bir birim test projesi](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Birim test projesinin UWP uygulama bildirim dosyasını Düzenle

1.  İçinde **Çözüm Gezgini**, sağ *Package.appxmanifest* seçin ve dosya **açık**.

     **Bildirim Tasarımcısı** düzenleme için görüntüler.

2.  İçinde **bildirim Tasarımcısı**, seçin **özellikleri** sekmesi.

3.  Listenin altında **özellikleri**, birim sınamanız ve kod gereken yetenekleri seçin sahip sınamanız. Örneğin, **Internet** birim testi ve test ettiği kodun onay kutusu İnternet'e erişme özelliği olması gerekir.

    > [!NOTE]
    > Seçtiğiniz yetenekler yalnızca birim testi düzgün çalışması gerekli olan yetenekleri içermelidir.

     ![Birim Test bildirimi](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Bir UWP uygulaması için birim testini kodlama

İçinde **Kod Düzenleyicisi**, birim sınamasını düzenleyin ve ekleyin onaylar ve sınama için gereken mantığı.

## <a name="run-unit-tests"></a>Birim testleri çalıştırma

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Çözümü derleyin ve Test Gezgini'ni kullanarak birim testini çalıştırmak için

1.  Üzerinde **Test** menüsünde seçin **Windows**ve ardından **Test Gezgini**.

     **Test Gezgini** listelenmesini test görüntüler.

2.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.

     Birim testiniz artık listelenir.

    > [!NOTE]
    > Test Gezgini'nde birim testleri listesini güncelleme çözümünü oluşturmanız gerekir.

3.  İçinde **Test Gezgini**, oluşturduğunuz birim sınamayı seçin.

    > [!TIP]
    > Test Gezgini kaynak koda bir bağlantı yanındaki sağlar **kaynak:**.

4.  Seçin **çalıştırması**.

     ![Birim Test Gezgini &#45; birim testi çalıştırma](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > Explorer'da listelenen bir veya daha fazla birim testleri seçebilir ve ardından sağ tıklatın ve seçin **seçili Testleri Çalıştır**.
    >
    > Ayrıca, seçebileceğiniz **seçilen Testlerde Hata Ayıkla**, **açık Test**ve **özellikleri** seçeneği.
    >
    > ![Birim Test Gezgini &#45; UNI test bağlam menüsü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

    Birim testi çalışır. Tamamlandıktan sonra **Test Gezgini** test durumunu, geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.

    ![Birim Test Gezgini &#45; test tamamlandı](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile UWP uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)
- [Yapı ve test bir UWP uygulaması](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
