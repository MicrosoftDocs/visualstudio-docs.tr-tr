---
title: 'Nasıl yapılır: izinleri ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6acd54a140d3281f4fd539cc12d07adb11cfd6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897390"
---
# <a name="how-to-set-permissions"></a>Nasıl yapılır: izinleri ayarlama

Bu makalede, bir bilgisayarın yönetici bir kullanıcı veya bu bilgisayar üzerinde yönetici izinlerine sahip olmayan bir grup için profil oluşturma için gereken güvenlik izinleri nasıl verir açıklanır.

Temel güvenlik ilkesine ihtiyaç duydukları izinleri en fazla uygulamaların çalışması gerektiğini belirtir. Bu ilke, kullanıcılar için de geçerlidir. Bunlar Yöneticiler grubu yerine Users grubunun üyesi olarak oturum açtığınızda kullanıcıların tam olarak etkili olması, bunlar yönetici izinleri verilmemelidir. "Kullanıcı izinlerine sahip bir kullanıcı hesabı oluşturmak için" İlk yordam, kullanıcılar grubunun bir üyesi için bir kullanıcı hesabı oluşturma işlemini açıklar.

Users grubunun üyeleri, diskteki diğer takım üyeleri ile paylaşılan dosyaları ve klasörleri erişimi gerekir. "Paylaşılan proje dosyalarına erişim vermek için" ikinci yordam o erişim açıklar.

Bir yöneticinin bunları profil oluşturma araçları için yazılım sürücü erişim verirse Users grubunun üyeleri profil oluşturma araçları çalıştırabilirsiniz. "Profil oluşturma sürücüsü, erişim vermek için" son yordamı Bu sürücü erişim açıklar.

> [!NOTE]
> Bu yordamlardaki adımları için yönetici izinlerine ihtiyacınız var.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Kullanıcı izinleri olan bir kullanıcı hesabı oluşturmak için

1. Sağ **Bilgisayarım** ve ardından **Yönet**.

     **Bilgisayar Yönetimi** penceresi açılır.

2. Genişletin **yerel kullanıcılar ve gruplar**.

3. Sağ **kullanıcılar** klasörünü ve ardından **yeni kullanıcı**.

     **Yeni kullanıcı** iletişim kutusu görüntülenir.

4. Bu iletişim kutusunda, oluşturduğunuz kullanıcı hesabı bilgilerle alanları doldurun. Bir parola belirtin. İsteğe bağlı olarak, sonraki oturum açışında parolasını kullanıcı değişikliği gerektiren bir onay kutusunu seçin.

5. Tıklayın **Oluştur** ve ardından **Kapat**.

     Yeni kullanıcı, bir Grup yönetici izinleri olmayan kullanıcılar kullanıcılar grubunda görünür.

## <a name="to-grant-access-to-shared-project-files"></a>Paylaşılan proje dosyalarına erişim vermek için

1. Windows Explorer (veya dosya Gezgini) içinde bu kullanıcı tarafından kullanılan ve proje ekibi tarafından paylaşılan proje dosyaları için klasör ağacının kökü bulun.

     Bu klasör yolu aşağıdaki gibi olabilir:

    ```cmd
    D:\ourProject
    ```

2. Klasörü sağ tıklatın ve ardından **özellikleri**.

     **\<Klasör adı > Özellikleri** iletişim kutusu görüntülenir.

3. Tıklayın **güvenlik** sekmesi.

4. Kullanıcı hesabı adına **grup veya kullanıcı adları** kutusu.

5. İçinde **izinlerini \<kullanıcı adı >** kutusunda, onay kutusunu seçin **tam denetim**.

6. **Tamam**'ı tıklatın.

     5. adımda seçtiğiniz klasör ile başlayan paylaşılan klasör ağacının kullanıcıya bu izinleri verir.

## <a name="to-grant-access-to-the-profiling-driver"></a>Profil oluşturma sürücü erişim vermek için

1. Yönetici olarak bir komut istemi açın.

2. Dizine değiştirin:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools
    ```

3. Şu komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Bu komut, yükler ve profil oluşturma araçlarından sürücüsünü başlatır.

     Bu komut, yönetici olmayan kullanıcılar, kendi kullanıcı işlem alanında kullanılabilir olan profil oluşturma özelliklerini kullanabilir, böylece profil oluşturma sürücü ve hizmeti başlatır. Yalnızca bir yönetici komut çalıştırabilirsiniz; ve yönetici olmayan kullanıcılar için başarısız olur.

     Bu adım etkilerini sonra geri bildirimi bilgisayarı yeniden başlatır, bu yordamda ayrıca son adım gerçekleştirmediğiniz sürece.

4. Sürücü işlevleri bir kullanıcı veya bilgisayarda yönetici erişimi yok grubu tarafından profil oluşturma için erişime izin vermek için komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Bu komut verir \<kullanıcı adı > veya \<grubu adı > Hesap profil oluşturma araçları için erişim. \<Doğru > seçeneğini belirler profil oluşturma işlevselliğini kullanıcı erişebilir. \<Doğru > seçeneği, bir veya daha fazla aşağıdaki değerlerden biri olabilir:

    - FullAccess - hizmetlerinden, performans verileri toplama dahil olmak üzere tüm profil oluşturma yöntemleri erişim örnekleme sağlar ve profil oluşturma oturumunu arası.

    - SampleProfiling - örnek profil oluşturma yöntemlerini erişim sağlar

    - CrossSession - çapraz oturum profil oluşturma hizmetleri için gerekli olan profil oluşturma erişim sağlar.

5. (İsteğe bağlı) Bilgisayar yeniden başlatıldıktan sonra önceki adımlardan herhangi birini sonuçlarını korumak için aşağıdaki komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Belirtilen kullanıcıların oturum açma sonra artık yönetici izinleri olmayan profil oluşturma araçlarını kullanmanız mümkün olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Profil Oluşturma ve Windows Vista Güvenliği](../profiling/profiling-and-windows-vista-security.md)