---
title: Bir Subversion deposu ayarlama
description: Subversion, Mac için Visual Studio kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 3995db4ef4609f68512dede454855da1f770141f
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295559"
---
# <a name="set-up-a-subversion-repository"></a>Bir Subversion deposu ayarlama

Subversion'dır Merkezi _sürüm denetimi sistemi_, tüm dosyaları ve düzeltmelerini içeren tek bir sunucu olduğu anlamına gelen, hangi kullanıcıların herhangi bir dosyayı herhangi bir sürümünü kontrol edebilirsiniz. Dosyalar uzak Subversion depodan kullanıma, kullanıcı o noktasında depo anlık görüntüsünü alır.

Sürüm denetimi için Subversion'ı kullanmak için makinenizde yüklü gerekir. Subversion olup olmadığını denetlemek için makinenizde yüklü, terminalde aşağıdaki komutu kullanın:

```bash
svn --version
```

Bu komut, sürüm numarasını döndürür.

Yükleyerek Subversion zaten yüklü değilse, bunu yapmanın en kolay yolu olan _Xcode komut satırı araçları_. Xcode komut satırı araçları ve Subversion'ı yüklemek için aşağıdaki komutu kullanın.

```bash
xcode-select --install
```

Subversion makinenizde yüklendikten sonra SVN projenizi yayımlamak için aşağıdaki adımları kullanın.

1. Bir ücretsiz SVN deposu oluşturun. Bu örnekte, [Assembla](https://app.assembla.com/) kullanıldı. Oluşturulduktan, bir URL sağlanacaktır, bu depoya bağlanmak için kullanılacak:

    ![SVN URL'yi kopyalayın](media/version-control-subversion1-sml.png)

2. Visual Studio için Mac projesi oluşturun veya açın.

3. Seçin ve proje üzerinde sağ tıklayın **sürüm denetimi > sürüm denetiminde Yayımla...** :

    ![Proje Yayımlama Başlat](media/version-control-subversion2.png)

4. İçinde **depo Bağlan** sekmesinde **Subversion** üst açılır.

5. Adım 1'den URL'sini girin. URL'sini girdikten sonra diğer alanları varsayılan olarak doldurulur:

    ![Depo seçin ve iletişim ayrıntılarını girin](media/version-control-subversion3.png)

7. Tıklayın **Tamam** tuşlarına basarak onaylayın **Yayımla**.

7. İstenirse, kimlik bilgilerinizi depo oluşturun site için aşağıda gösterildiği gibi girin:

    ![Subversion depo için kimlik bilgilerini girme](media/version-control-subversion5.png)

8.  Kullanılabilir tüm sürüm denetim komutlarını artık sürüm denetimi menüsünde görünür olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Subversion ile çalışma](working-with-subversion.md)