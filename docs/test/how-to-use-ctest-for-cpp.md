---
title: C++ için CTest kullanma
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7a4475cba023f792c2ff96895eb4dd7e0b4ebcf5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050220"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Visual Studio'da C++ için CTest kullanma

(Kod CTest içerir) CMake tümleşik Visual Studio IDE'ye varsayılan olarak **C++ ile masaüstü Develoment** iş yükü. Makinenizde yüklemeniz gerekiyorsa, Visual Studio yükleyicisi programını açın, **Değiştir** düğmesine ve ardından denetleyin [Visual C++ için CMake araçlarını](/cpp/ide/cmake-tools-for-visual-cpp) altında iş yükü bileşenlerin listesi.

## <a name="to-write-tests"></a>Testler yazmak için

Visual Studio'da CMake desteği, Visual Studio Proje sistemi kullanılmaz. Bu nedenle, yazma ve herhangi bir CMake ortamında olduğu gibi CTest testler yapılandırın. Visual Studio'da CMake kullanma hakkında daha fazla bilgi için bkz. [Visual C++ için CMake araçlarını](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>(Visual Studio 2017 sürüm 15.6) testleri çalıştırmak için

Visual Studio 2017 sürüm 15.6, CTest tam olarak tümleşiktir **Test Gezgini** ve aynı zamanda Google ve Boost birim testi çerçevelerini destekler. Bu çerçeveler bileşen olarak varsayılan olarak dahil **C++ ile masaüstü Develoment** iş yükü. Ancak, bir projeyi Visual Studio'nun eski bir sürümden yükseltiyorsanız, Visual Studio yükleyicisi programını kullanarak bu çerçeveleri yüklemeniz gerekebilir.

Aşağıdaki çizim bir CTest, Google Test çerçevesini kullanarak çalıştırma sonuçları gösterilmektedir:

![CTest vs2017 Google Test Framework 15,6](media/ctest-test-explorer.png)

CTest ancak değil Google veya Boost bağdaştırıcıları kullanıyorsanız, yöntem düzeyine test sonuçları yerine tek tek CTest düzeyinde bakın. Hata ayıklaması yapabilirsiniz ve adım adım yalnızca CTest yürütülebilir dosyaları, ancak yığın izlemelerini bireysel testler üzerinde desteklenmez.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>(Visual Studio 2017 sürüm 15.5) testleri çalıştırmak için

İçinde **Visual Studio 2017 sürüm 15.5**, CTest ile tümleşik olmayan **Test Gezgini**. Testlerinizi CMake ana menüden veya bağlam menüsünden çalıştırabileceğiniz bir *CMakeLists.txt* dosyası **Çözüm Gezgini**. Test sonuçları için Visual Studio yönlendirilmiş **çıkış penceresine**.

![VS2017 15.5 sürümünde CTest Testleri Çalıştır](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Ayrıca bkz.

[C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)