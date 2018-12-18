---
ms.technology: vs-ai-tools
ms.openlocfilehash: 738ada7e72af6c6bfbb93b8c494fdec2aadf68c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895957"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio'da Python kodunun bir depoyu kopyalama

Kaydederler [yapay ZEKA için Visual Studio Araçları yüklü](installation.md), kolayca Python kodu bir depoyu kopyalamak ve bir proje oluşturun.

1. Visual Studio Yükleyicisi'ni çalıştırın, GitHub depoları için bağlanmayı seçin **Değiştir**seçip **tek tek bileşenler** sekmesi. Ekranı aşağı kaydırarak **kod Araçları** bölümünden **Visual Studio için GitHub uzantısı**seçip **Değiştir**.

    ![Visual Studio Yükleyicisi'nde GitHub uzantısı seçme](media/create-project-repo/installation-github-extension.png)

2. Visual Studio'yu başlatın.

3. Seçin **Görüntüle > Takım Gezgini...**  açmak için **Takım Gezgini** penceresi içinde GitHub veya Azure DevOps bağlanabilir, ya da bir depoyu kopyalayın.

    ![Azure DevOps, GitHub'ı gösteren ve bir depo kopyalama Takım Gezgini penceresi](media/create-project-repo/team-explorer.png)

4. Altında alanına **yerel Git depoları**, girin `https://github.com/Microsoft/samples-for-ai`, kopyalanan dosyalar için bir klasör girin ve seçin **kopya**.

    > [!Tip]
    > Takım Gezgini'nde belirttiğiniz klasör, kopyalanan dosyalar almak için belirli bir klasördür. Farklı `git clone` komutunu, Ekip Gezgini'nde bir kopya oluşturma otomatik olarak oluşturmaz bir alt klasör deponun adını.

5. Kopyalama tamamlandığında, Team Explorer'ı depo panosuna gitmek için sayfanın alt kısmında depo klasörü çift tıklatın. Altında **çözümleri**seçin **yeni...** .

    ![Takım Gezgini penceresinde, bir kopya yeni proje oluşturma](media/create-project-repo/team-explorer-new-project.png)

6. İçinde **yeni proje** görüntülenen iletişim seçin "**ilk mevcut Python kodu**", proje için bir ad belirtin, Ayarla **konumu** deposu olarak aynı klasöre ve seçin **Tamam**. Açılan sihirbazda seçin **son**.

7. Seçin **Görüntüle > Çözüm Gezgini** menüsünde.

8. Çözüm Gezgini'nde `TensorFlow Examples> MNIST` düğümünü sağ `convolutional.py`seçip **başlangıç dosyası olarak ayarla**. Bu adım, Visual Studio projeyi çalışırken kullanması gereken hangi dosya söyler.

9. Tuşuna **Ctrl**+**F5** veya **hata ayıklama > hata ayıklama olmadan Başlat** programı çalıştırmak için. Görürseniz bir ', önceki adımda ayarı çalışma dizini yeniden denetleyin.

10. Program başarıyla çalıştırıldığında, eğitim indirin ve veri kümesi, test sonra modeli eğitmek ve çıkış, hata oranı Başlat görürsünüz. İstediğiniz zaman içinde azaltmak için hata oranı

    ![İlk Python MNIST programının çıktısı](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda kullanıyorsanız ve eksik numpy hakkında bir hata iletisi, gerekebilir [Anaconda kullanmak için Python ortamınız değiştirme](../python/selecting-a-python-environment-for-a-project.md).

11. İlerleme durumunu TensorBoard görselleştirebilirsiniz. Projenize sağ tıklayın ve tıklayın **çalıştırma TensorBoard** TensorBoard günlükleri çıkış dizini'ı seçin.

   ![tensorboard çalıştırın](media/create-project-repo/run-tensorboard.png)

12. Kaliteyi artırma anlamına gelir, zaman içinde azalan hata dikkat edin.

   ![tensorboard çalıştırın](media/create-project-repo/tensorboard.png)
