---
title: Google Test için C++ kullanma
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 704d842aaf3ea5e3075939e4d52b042a4128b810
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060397"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio'da C++ için Google Test kullanma
İçinde **Visual Studio 2017 sürüm 15.5** ve daha sonra Visual Studio IDE'ye varsayılan bileşeni olarak Google Test tümleşiktir **C++ ile masaüstü geliştirme** iş yükü. Makinenizde yüklü olduğunu doğrulamak için Visual Studio Yükleyicisi'ni açın ve Google Test altında iş yükü bileşenlerin listesini bulun:

![Google Test yükle](media/cpp-google-component.png)

## <a name="add-a-google-test-project-to-the-solution"></a>Bir Google Test projesi çözüme ekleyin
1. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve seçin **Ekle** > **yeni proje**.
2. Sol bölmede seçin **Visual C++** > **Test** seçip **Google Test projesi** Orta bölmedeki.
3. Test projesi bir ad verin ve tıklayın **Tamam**.

![Yeni Google Test projesi](media/cpp-gtest-new-project.png)

## <a name="configure-the-test-project"></a>Test projesi yapılandırma
İçinde **Test proje yapılandırması** görüntülenen iletişim kutusunda, test etmek istediğiniz projeye seçebilirsiniz. Bir proje seçtiğinizde, Visual Studio Seçili projeye bir başvuru ekler. Hiçbir proje seçerseniz, test etmek istediğiniz projeleri başvuruları el ile eklemeniz gerekir. Statik ve dinamik Google Test ikili dosyalarına bağlanma arasında seçim yaparken, konuları herhangi bir C++ programı ile aynıdır. Daha fazla bilgi için [Visual C++'ta DLL'ler](/cpp/build/dlls-in-visual-cpp).

 ![Google Test projesi yapılandırma](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Ek seçeneklerini ayarlama
Ana menüden **Araçları** > **seçenekleri** > **Google Test için Test bağdaştırıcısı** ek seçeneklerini ayarlamak için. Bu ayarlar hakkında daha fazla bilgi için Google Test belgelerine bakın.

 ![Google Test projesi ayarları](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ekleme yönergelerinde
Testinizde *.cpp* dosya, gerekli ekleyin `#include` programınızın türleri ve işlevleri test kodu görünür yapmak için yönergeleri. Genellikle, bir düzey klasör hiyerarşisindeki bir programdır. Yazarsanız `#include "../"` IntelliSense penceresi görünür ve üstbilgi dosyasının tam yolunu seçin olanak sağlar.

![Ekle #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Yazma ve testleri çalıştırma
Artık yazmak ve Google testleri çalıştırmak hazır olursunuz. Bkz: [Google Test öncü](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) test makrolar hakkında daha fazla bilgi için. Bkz: [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) kullanarak testlerinizi gruplandırma bulma ve çalıştırma hakkında bilgi için **Test Gezgini**.

## <a name="see-also"></a>Ayrıca bkz.
[C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
