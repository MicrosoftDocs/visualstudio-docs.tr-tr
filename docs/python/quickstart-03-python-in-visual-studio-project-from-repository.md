---
title: Hızlı Başlangıç - Python kodu bir depoyu kopyalamak
description: Bu hızlı başlangıçta, Visual Studio Takım Gezgini kullanarak Python koans depoyu kopyalayarak Visual Studio'da Python projesi oluşturun.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 871a5f620cc90db5064562461336fdeac38ba757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068399"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Hızlı Başlangıç: Visual Studio'da Python kodu bir depoyu kopyalama

Kaydederler [Python desteği Visual Studio 2017'de yüklü](installing-python-support-in-visual-studio.md), Visual Studio için GitHub uzantısı ekleyebilirsiniz. Uzantı, kolayca Python kodu bir depoyu kopyalamak ve buradan gelen IDE içinde bir proje oluşturun olanak tanır. Her zaman de komut satırında depoları kopyalayın ve ardından Visual Studio'da çalışma.

## <a name="install-the-github-extension-for-visual-studio"></a>Visual Studio için GitHub uzantısı yükleme

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Visual Studio'da GitHub ile çalışma

1. Visual Studio'yu başlatın.

1. Seçin **görünümü** > **Takım Gezgini** açmak için **Takım Gezgini** penceresi içinde GitHub ya da Azure depoları bağlanabilir, ya da bir depoyu kopyalayın. (Görmüyorsanız **Connect** gösterilen sayfası aşağıda, bu sayfasına götürür üst araç çubuğunda Tak simgeyi seçin.)

    ![Takım Gezgini penceresini gösteren Azure depoları, GitHub ve bir depoyu kopyalama](media/team-explorer.png)

1. Altında **yerel Git depoları**seçin **kopya** komutunu ve ardından girin `https://github.com/gregmalcolm/python_koans` kopyalanan dosyalar için bir klasör URL alanına girin ve seçin **kopya** düğmesi.

    > [!Tip]
    > Belirttiğiniz klasör **Takım Gezgini** kopyalanan dosyalar almak için tam klasördür. Farklı `git clone` bir klonda oluşturma komutu, **Takım Gezgini** depo adı ile otomatik olarak bir alt klasör oluşturmaz.

1. Kopyalama tamamlandıktan sonra depo adı görünür **yerel Git depoları** listesi. Depo panoya gidin, adına çift tıklayarak **Takım Gezgini**.

1. Altında **çözümleri**seçin **yeni**.

    ![Takım Gezgini penceresinde, bir kopya yeni proje oluşturma](media/team-explorer-new-project.png)

1. İçinde **yeni proje** görüntülenen iletişim gidin **Python** dili (veya "Python" araması) seçin **ilk mevcut Python kodu**, proje için bir ad belirtin ayarlama **konumu** depo ve select aynı klasöre **Tamam**. Açılan sihirbazda seçin **son**.

1. Seçin **görünümü** > **Çözüm Gezgini** menüsünde.

1. İçinde **Çözüm Gezgini**, genişletin **python3** düğümünü sağ **contemplate_koans.py**seçip **başlangıç dosyası olarak ayarla**. Bu adım, Visual Studio projeyi çalışırken kullanması gereken hangi dosya söyler.

1. Seçin **proje** > **Koans özellikleri** menüden **genel** sekmesini tıklatıp ayarlamak **çalışma dizini** için " python3 ". Başlangıç dosyası konumu yerine Proje kök dizinini Visual Studio varsayılan olarak çalışma dizinini ayarlar nedeniyle bu adım gereklidir (*python3\contemplate_koans.py*, proje özelliklerinde de görebileceğiniz gibi). Program kodu için bir dosya arar *koans.txt* çalışma klasöründe, bu nedenle bu değer değiştirmeden gördüğünüz bir çalışma zamanı hatası.

    ![Python projesi için çalışma dizini ayarlama](media/projects-set-working-directory.png)

1. Tuşuna **Ctrl**+**F5** veya **hata ayıklama** > **hata ayıklama olmadan Başlat** programı çalıştırmak için. Görürseniz bir **FileNotFoundError** için *koans.txt*, önceki adımda açıklandığı gibi ayarlar çalışma dizini kontrol edin.

1. Program başarıyla çalıştırıldığında 17 satırında bir onaylama işlemi hatası görüntüler *python3/koans/about_asserts.py*. Bu kasıtlıdır: program öğretmeyi sorununuz tarafından Python kasıtlı tüm hataları düzeltin tasarlanmıştır. (Daha fazla ayrıntı bulunur [Ruby Koans](https://rubykoans.com/), Python Koans ilham.)

    ![İlk Python koans programının çıktısı](media/koans-output.png)

1. Açık *python3/koans/about_asserts.py* buna giderek **Çözüm Gezgini** ve dosyaya çift tıklayın. Satır numaraları, düzenleyicide varsayılan olarak görünmez dikkat edin. Bunu değiştirmek için seçin **Araçları** > **seçenekleri**seçin **tüm ayarları göster** iletişim kutusunun alt kısmında gidin **metin düzenleyicisi**   >  **Python** > **genel** seçip **satır numaraları**:

    ![Satır numarası Python dosyaları açma](media/options-general-line-numbers.png)

1. Değiştirerek bir hatayı düzeltmek `False` 17 satırında bağımsız değişken `True`. Satır şöyle:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Programı yeniden çalıştırın. Visual Studio, hataları hakkında sizi uyarır, yanıt **Evet** kod çalıştırmaya devam etmek için. Daha sonra ilk onay geçirir ve sonraki koan üzerinde programı durdurur bakın. Hataları ve program düzeltme devam etmek istediğiniz gibi yeniden.

> [!Important]
> Bu hızlı başlangıçta oluşturduğunuz doğrudan bir kopyasını *python_koans* github deposu. Böyle bir depo yazarı doğrudan değişikliklerden korunur, bu nedenle değişiklikleri depoya denemesi başarısız oluyor. Uygulamada, geliştiriciler bunun yerine kendi GitHub hesabına bir tür bir depo çatalını oluşturmanız, değişiklikleri yapın ve ardından bu değişiklikleri özgün depoya göndermek için çekme istekleri oluşturun. Kendi çatalınızı varsa, daha önce kullanılan özgün depo URL'si yerine URL'sini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [El ile var olan bir Python yorumlayıcısı tanımlayın](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015'te ve daha önce Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
