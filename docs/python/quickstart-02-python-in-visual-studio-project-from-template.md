---
title: Hızlı Başlangıç - şablon kullanarak bir Python projesi oluşturma
description: Bu hızlı başlangıçta basit bir Flask uygulaması için yerleşik bir şablon kullanarak Python için bir Visual Studio projesi oluşturun.
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
ms.openlocfilehash: c36fc6e10b196c3da4ba58ff047adab62345fa6f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066031"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Hızlı Başlangıç: Visual Studio'da bir şablondan bir Python projesi oluşturma

Kaydederler [Python desteği Visual Studio 2017'de yüklü](installing-python-support-in-visual-studio.md), çeşitli şablonları kullanarak yeni Python projesi oluşturmak daha kolaydır. Bu hızlı başlangıçta, bir şablon kullanarak basit bir Flask uygulaması oluşturun. El ile oluşturduğunuz proje için benzer bir sonuç projesi [hızlı başlangıç - Flask ile web uygulaması oluşturma](../ide/quickstart-python.md).

1. Visual Studio 2017'yi başlatın.

1. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**, ardından **yeni proje** iletişim arama "için boş flask", seçin **boş Flask Web projesi** ortadaki listeyi şablonunda projeye bir ad verin ve seçin **Tamam**:

    ![Boş bir Flask Web projesi şablonu ile yeni bir proje oluşturma](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio sizden bildiren bir iletişim kutusu ile **dış paketleri bu proje gerektirir.** Şablonun içerdiği için bu iletişim kutusu görünür bir *requirements.txt* Flask üzerinde bir bağımlılık belirten dosyasıdır. Visual Studio paketleri otomatik olarak yükleyebilir ve bunları yüklemek için seçeneği sunan bir *sanal ortam*. Bir sanal ortam kullanmak önerilir bir genel ortamına seçin yüklemenin önünde **sanal bir ortama yükleme** devam etmek için.

    ![Flask sanal bir ortama yükleme](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio görüntüler **sanal ortama ekleme** iletişim. Varsayılan değeri kabul edin ve seçin **Oluştur**, ardından tüm yükseltme isteklerinin için onay.

    > [!Tip]
    > Bir projeye başladığınızda, yapmak için çoğu Visual Studio şablonları çağırdığınız gibi yüksek oranda hemen bir sanal ortam oluşturmak için önerilir. Kitaplıkları ekleyip kaldırırken sanal ortamlar projenizin tam gereksinimleri zamanla korur. Ardından, kolayca oluşturabilirsiniz bir *requirements.txt* (ne zaman kullanarak kaynak denetimi gibi) diğer geliştirme bilgisayarlarda bu bağımlılıkların yeniden yüklemek için kullanacağınız dosya ve proje için bir üretim sunucusu dağıtılırken. Sanal ortamlar ve avantajları hakkında daha fazla bilgi için bkz. [sanal ortamları kullanma](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) ve [requirements.txt ile gerekli paketleri yönetme](../python/managing-required-packages-with-requirements-txt.md).

1. Visual Studio bu ortamı oluşturduktan sonra konum **Çözüm Gezgini** sahip olduğunuzu görmek için bir *app.py* ile birlikte dosya *requirements.txt*. Açık *app.py* şablon gibi içinde kod ayarının görmek için [hızlı başlangıç - Flask ile web uygulaması oluşturma](../ide/quickstart-python.md), birkaç ek bölüm ile. Aşağıda gösterilen tüm kodları oluşturulur şablon tarafından hiçbir yapıştırmak zorunda kalmazsınız *app.py* kendiniz.

    Kod gerekli içeri aktarmaları ile başlar:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Ardından bir web ana bilgisayarı için bir uygulama dağıtımı sırasında yardımcı olabilecek aşağıdaki satırı verilmiştir:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Ardından bir görünümü tanımlayan basit bir işlevi üzerinde rota dekoratör gelir:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Son olarak, aşağıdaki başlatma kodu bağlantı noktası üzerinden bunları kodlamak yerine ortam değişkenleri ve konak ayarlamanıza olanak sağlar. Bu kod, kodunu değiştirmeden hem geliştirme hem de üretim makinelerde yapılandırmayı kolayca denetlemenize olanak tanır:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Seçin **hata ayıklama** > **hata ayıklama olmadan Başlat** uygulamayı çalıştırın ve bir tarayıcıda `localhost:5555`.

**Soru: Hangi bir Python şablonları Visual Studio sunuluyor?**

**Yanıt**: Python iş yükü yüklenmiş, Visual Studio Proje şablonları için de dahil olmak üzere çeşitli sağlar [Flask, Bottle ve Django web çerçeveleri](../python/python-web-application-project-templates.md), Azure bulut Hizmetleri, farklı makine öğrenimi senaryolar ve hatta bir Python uygulaması içeren mevcut bir klasör yapısından bir proje oluşturmak için şablon. Bunlar üzerinden erişim **dosya** > **yeni** > **proje** iletişim kutusunu seçerek **Python** Dil düğümünü ve alt düğümleri.

Visual Studio ayrıca dosya çeşitli sağlar veya *öğe şablonları* Python sınıfı, bir Python paketi, bir test jednotky Pythonu, hızlı bir şekilde oluşturmak için *web.config* dosyaları ve daha fazlası. Açık bir Python projeniz varsa, öğe şablonları aracılığıyla erişim **proje** > **Yeni Öğe Ekle** menü komutu. Bkz: [öğe şablonları](python-item-templates.md) başvuru.

Şablonları kullanarak önemli zamandan tasarruf ne zaman bir projeye Başlarken veya bir dosya oluşturup ayrıca farklı uygulama türleri hakkında bilgi edinin ve kod yapıları için harika bir yol sağlar. Bunu sundukları teklifler ile tanımak için çeşitli şablonlardan projeler ve öğeler oluşturmak için birkaç dakikanızı ayırarak yardımcı olur.

**Soru: Ayrıca Cookiecutter şablonları kullanabilir miyim?**

**Yanıt**: Evet! Aslında, Visual Studio aracılığıyla hakkında bilgi edinebilirsiniz Cookiecutter ile doğrudan tümleştirme sağlayan [hızlı başlangıç: bir Cookiecutter şablonundan proje oluşturma](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [El ile var olan bir Python yorumlayıcısı tanımlayın](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015'te ve daha önce Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
