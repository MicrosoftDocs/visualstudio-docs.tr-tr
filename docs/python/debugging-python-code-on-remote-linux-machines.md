---
title: Uzak Linux bilgisayarlarda Python kodunda hata ayıklama
description: Uzak Linux bilgisayarlarda çalışan, gerekli yapılandırma adımları, güvenlik ve sorun giderme Python kodunda hata ayıklamak için Visual Studio'yu kullanın.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c14fb14a8941895fab473952908e6aefa2e2f14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067952"
---
# <a name="remotely-debug-python-code-on-linux"></a>Linux'ta Python kodu uzaktan hata ayıklama

Visual Studio'yu başlatın ve Python uygulamaları bir Windows bilgisayarda yerel olarak ve uzaktan hata ayıklama (bkz [uzaktan hata ayıklama](../debugger/remote-debugging.md)). Bu da uzaktan farklı işletim sistemi, cihaz veya dışındaki CPython kullanarak Python uygulama hatalarını ayıklayabilir [ptvsd Kitaplığı](https://pypi.python.org/pypi/ptvsd).

Ptvsd kullanırken, ayıklanan Python kodu Visual Studio iliştirebilmek için hata ayıklama sunucusu barındırır. Bu barındırma içeri aktarın ve SQL Server, ağ gerektirir ve yapılandırmaları TCP bağlantılarına izin verecek şekilde uzak bilgisayarda güvenlik duvarı için kodunuzu için küçük bir değişiklik gerektirir.

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | Uzaktan hata ayıklama için bir giriş için bkz [yakından bakış: platformlar arası uzaktan hata ayıklama](https://youtu.be/y1Qq7BrV6Cc) (youtube.com, 6m22s), Visual Studio 2015 ve 2017 için geçerli olduğu. |

## <a name="set-up-a-linux-computer"></a>Bir Linux bilgisayarı ayarlama

Bu izlenecek yolda izlemek için aşağıdaki öğeler gerekir:

- Python Mac OSX veya Linux gibi işletim sistemi çalıştıran bir uzak bilgisayar.
- Bağlantı noktası 5678 (uzaktan hata ayıklama için varsayılan açılan o bilgisayarın güvenlik duvarında gelen).

Kolayca bir [azure'da Linux sanal makinesi](/azure/virtual-machines/linux/creation-choices) ve [Uzak Masaüstü kullanarak erişim](/azure/virtual-machines/linux/use-remote-desktop) Windows öğesinden. Ubuntu VM için kullanışlı çünkü Python varsayılan olarak yüklenir; Aksi takdirde, üzerinde listesine bakın [tercih ettiğiniz bir Python yorumlayıcısını yükleyerek](installing-python-interpreters.md) için konumları ek Python'ı indirin.

Bir Azure sanal makinesi için bir güvenlik duvarı kuralı oluşturma hakkında daha fazla bilgi edinmek için bkz: [Azure portalını kullanarak Azure'da bağlantı noktalarını VM'ye açma](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Betik hata ayıklama için hazırlama

1. Uzak bilgisayarda adlı bir Python dosyası oluşturun *tahmin game.py* aşağıdaki kod ile:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Yükleme `ptvsd` ortamı kullanarak paket `pip3 install ptvsd`. 
   >[!NOTE]
   >Sorun giderme için gerektiği durumlarda yüklediğiniz ptvsd sürümü kaydetmek iyi bir fikirdir; [ptvsd listeleme](https://pypi.python.org/pypi/ptvsd) kullanılabilir sürümleri de gösterir.

1. En erken olası noktada aşağıdaki kodu ekleyerek uzaktan hata ayıklamayı etkinleştirme *tahmin game.py*, diğer kod önce. (Katı bir gereksinim değil de, önce kökenli herhangi bir arka plan iş parçacığı hata ayıklama mümkün değildir `enable_attach` işlevi çağrılır.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Dosyayı kaydedin ve çalıştırın `python3 guessing-game.py`. Çağrı `enable_attach` arka planda çalışır ve aksi takdirde programla etkileşime geçtiğimiz sırada gelen bağlantılar için bekler. İsterseniz, `wait_for_attach` işlevi, sonra çağrılabilir `enable_attach` hata ayıklayıcı ekler kadar program engelleyecek.

> [!Tip]
> Ek olarak `enable_attach` ve `wait_for_attach`, ptvsd de yardımcı işlevini sağlar `break_into_debugger`, hata ayıklayıcıyı eklediyseniz programlı bir kesme noktası hizmet. Ayrıca bir `is_attached` döndüren işlev `True` hata ayıklayıcıyı eklediyseniz (diğer çağırmadan önce bu sonucunu denetle gerek olmadığını unutmayın `ptvsd` işlevler).

## <a name="attach-remotely-from-python-tools"></a>Python Araçları'ndan uzaktan ekleme

Bu adımlarda, uzak işlemini durdurmak için basit bir kesme noktası ayarladık.

1. Yerel bilgisayarda Uzak dosyanın bir kopyasını oluşturun ve Visual Studio'da açın. Burada dosya bulunur, ancak adı uzak bilgisayarda betiğin adı eşleşmelidir önemi yoktur.

1. (İsteğe bağlı) Yerel bilgisayarınızda ptvsd için IntelliSense sağlamak için Python ortamınıza ptvsd paketi yükleyin.

1. Seçin **hata ayıklama** > **işleme**.

1. İçinde **iliştirme** görüntülenen iletişim **bağlantı türü** için **Python uzaktan (ptvsd)**. (Bu komutlar Visual Studio'nun eski sürümlerini adlandırılır **aktarım** ve **Python uzaktan hata ayıklama**.)

1. İçinde **bağlantı hedefi** alan (**niteleyicisi** daha eski sürümlerindeki), girin `tcp://<ip_address>:5678` burada `<ip_address>` bu uzak bilgisayarın (olabilen bir açık adresi ya da adı gibi myvm.cloudapp.NET) ve `:5678` uzaktan hata ayıklama bağlantı noktası numarası.

1. Tuşuna **Enter** o bilgisayardaki kullanılabilir ptvsd işlemlerin listesini doldurmak için:

    ![Bağlantı hedefi girme ve işlemleri listeleme](media/remote-debugging-qualifier.png)

    Bu liste, seçme doldurulduktan sonra uzak bilgisayarda başka bir programı başlatmak için MSDN aboneliğine **Yenile** düğmesi.

1. Hata ayıklama işlemini seçin ve ardından **iliştirme**, veya işlemi çift tıklatın.

1. Visual Studio sonra geçiş betiği uzak bilgisayarda çalışmaya devam ederken hata ayıklama modu olarak tüm normal sağlama [hata ayıklama](debugging-python-in-visual-studio.md) özellikleri. Örneğin, üzerinde bir kesme noktası ayarlamak `if guess < number:` satır, ardından uzak bilgisayara geçebilir ve başka bir tahmin girin. Bunu, Visual Studio, kesme noktasını, yerel bilgisayar durur yaptıktan sonra yerel değişkenleri ve benzeri gösterir:

    ![Visual Studio, kesme noktasına gelindiğinde hata ayıklama duraklatır](media/remote-debugging-breakpoint-hit.png)

1. Hata ayıklamayı durdurduğunuzda Visual Studio uzak bilgisayar üzerinde çalışmaya devam eder ve programından ayırır. ptvsd hata ayıklayıcılar, istediğiniz zaman yeniden işleme iliştirebilirsiniz ekleseniz eklenmesi için dinleme devam eder.

### <a name="connection-troubleshooting"></a>Bağlantı sorunlarını giderme

1. Seçtiğinizden emin olun **Python uzaktan (ptvsd)** için **bağlantı türü** (**Python uzaktan hata ayıklama** için **aktarım** ile Eski sürümler.)
1. Kontrol gizli dizisinde **bağlantı hedefi** (veya **niteleyicisi**) gizli dizi uzak kodda tam olarak eşleşir.
1. IP adresi denetimi **bağlantı hedefi** (veya **niteleyicisi**), uzak bilgisayarın eşleşir.
1. Uzak bilgisayarda uzaktan hata ayıklama bağlantı noktası açık ve, bağlantı noktası son eki bağlantı hedefte gibi bulunduğundan emin olun `:5678`.
    - Farklı bir bağlantı noktası kullanmanız gerekiyorsa, içinde belirtebilirsiniz `enable_attach` çağrıda `address` bağımsız değişken, giriş olarak `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`. Bu durumda, belirli bir bağlantı noktasını Güvenlik Duvarı'nda açın.
1. Ptvsd sürümü tarafından döndürülen uzak bilgisayarda yüklü olup olmadığını kontrol edin `pip3 list` aşağıdaki tabloda Visual Studio'da kullanmakta olduğunuz Python tools sürümü tarafından kullanılan eşleşir. Gerekirse, uzak bilgisayardaki ptvsd güncelleştirin.

    | Visual Studio sürümü | Python araçları/ptvsd sürümü |
    | --- | --- |
    | 2017 15,8 | 4.1.1a9 (eski hata ayıklayıcı: 3.2.1.0) |
    | 2017 15.7 | 4.1.1a1 (eski hata ayıklayıcı: 3.2.1.0) |
    | 2017 15.4, 15.5, 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Ptvsd kullanarak 3.x

Aşağıdaki bilgiler, yalnızca uzaktan ptvsd ile hata ayıklama için geçerlidir ptvsd kaldırılan bazı özellikleri içeren 3.x 4.x.

1. Ptvsd ile 3.x `enable_attach` işlevi gerekli çalışan betiğe erişimi kısıtlayan ilk bağımsız değişken olarak "gizli dizisini" geçirin. Uzaktan hata ayıklayıcı eklerken bu gizli dizi girin. Önerilmez olsa da, bağlanmak, kullanan herkese izin verebilirsiniz `enable_attach(secret=None)`.

1. Bağlantı hedef URL `tcp://<secret>@<ip_address>:5678` burada `<secret>` geçirilen bir dize `enable_attach` Python kodunda.

Varsayılan olarak, sunucuya ptvsd 3.x uzaktan hata ayıklama yalnızca gizli dizi tarafından sağlanır ve tüm verileri, düz metin olarak geçirilir. Ptvsd daha güvenli bir bağlantı 3.x destekler SSL kullanarak `tcsp` Protokolü şu şekilde ayarlayın:

1. Uzak bilgisayarda ayrı otomatik olarak imzalanan sertifika ve openssl kullanarak anahtar dosyalarını oluşturur:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    İstendiğinde, ana bilgisayar adı veya IP adresi (hangisi bağlanmak için kullandığınız) kullanılmak **ortak ad** openssl tarafından istendiğinde.

    (Bkz [otomatik olarak imzalanan sertifikalar](https://docs.python.org/3/library/ssl.html#self-signed-certificates) python'da `ssl` modülü docs bakın. Bu docs komutta yalnızca tek bir birleştirilmiş dosya oluşturur unutmayın.)

1. Kod içinde çağrısını değiştirin `enable_attach` içerecek şekilde `certfile` ve `keyfile` dosya adlarını değerleri olarak kullanılarak bağımsız (Bu bağımsız değişkenler standart olduğu gibi aynı anlamları `ssl.wrap_socket` Python işlevi):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Yerel bilgisayarda kod dosyasında aynı değişikliği yapabilirsiniz, ancak bu kodu çalıştırdığı değildir çünkü kesinlikle gerekli değildir.

1. Uzak bilgisayarda hata ayıklama için hazır hale getirme Python programını yeniden başlatın.

1. Visual Studio ile Windows bilgisayarda güvenilen kök CA sertifikası ekleyerek güvenli kanal:

    1. Sertifika dosyasını yerel bilgisayarda Uzak bilgisayardan kopyalayın.
    1. Açık **Denetim Masası** gidin **Yönetimsel Araçlar** > **bilgisayar sertifikalarını yönetme**.
    1. Görüntülenen penceresinde genişletin **güvenilen kök sertifika yetkilileri** sağ tıklayın sol tarafta **sertifikaları**seçip **tüm görevler**  >  **Alma**.
    1. Bulun ve seçin *.cer* dosyasını kopyaladığınız uzak bilgisayardan, içeri aktarma işlemini tamamlamak için iletişim kutularını ' ye tıklayın.

1. Şimdi kullanarak daha önce açıklandığı gibi Visual Studio'da ekleme işlemi yineleyin `tcps://` protokolü için **bağlantı hedefi** (veya **niteleyicisi**).

    ![SSL ile uzaktan hata ayıklama taşıma seçme](media/remote-debugging-qualifier-ssl.png)

1. Visual Studio hakkında olası Sertifika sorunları, SSL üzerinden bağlanırken ister. Uyarılarını gözardı et ve devam, ancak kanal hala gizlice dinlemeye karşı şifrelenmiş olsa da adam-de-adam saldırılarına açık olabilir.

    1. Görürseniz **uzaktan sertifikası güvenilir değil** aşağıda uyarı, değil düzgün eklediğiniz sertifika için güvenilen kök CA'yı anlamına gelir. Bu adımlar denetleyin ve yeniden deneyin.

        ![SSL güvenilen bir sertifika Uyarısı](media/remote-debugging-ssl-warning.png)

    1. Görürseniz **uzak sertifika adı, ana bilgisayar adı eşleşmiyor** aşağıda uyarı, size kullanmayan uygun konak adı veya IP adresi olarak geldiğini **ortak ad** sertifikayı oluştururken.

        ![SSL sertifika ana bilgisayar adı Uyarısı](media/remote-debugging-ssl-warning2.png)
