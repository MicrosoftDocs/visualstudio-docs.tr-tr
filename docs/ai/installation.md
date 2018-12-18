---
title: Yapay ZEKA araçları yükleme
description: Visual Studio için yapay ZEKA araçları yüklemeyi açıklar
keywords: yapay zeka, visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 465443211d1a3f1aff8bfa63fa6cb8068b55980b
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459770"
---
# <a name="installation"></a>Yükleme

AI için Visual Studio Araçları, Windows 64-bit işletim sistemlerine yüklenebilir.

## <a name="install-visual-studio-tools-for-ai"></a>Yapay ZEKA için Visual Studio Araçları yükleme

Bu uzantı, Visual Studio 2015 ve Visual Studio 2017 Community edition ile çalışır veya üzeri.

Araçları'ndan indirebileceğiniz [Visual Studio Market](http://aka.ms/vstoolsforai), veya Visual Studio içinde:

1. Seçin **Araçları** > **Uzantılar ve güncelleştirmeler**.

   ![Uzantılar ve güncelleştirmeler menüsünde Visual Studio](media/installation/extensions.png)

2. İçinde **Uzantılar ve güncelleştirmeler** iletişim kutusunda **çevrimiçi** sol taraftaki.
3. Sağ üst köşedeki arama kutusuna yazın veya "için yapay zeka Araçları" girin.
4. Seçin **yapay ZEKA için Visual Studio Araçları** sonuçlarından.
5. **İndir**'e tıklayın.

## <a name="prepare-your-local-machine"></a>Yerel makinenize hazırlama

Derin öğrenme modellerini yerel bilgisayarınızda eğitim önce uygun önkoşulların yüklü olduğundan emin olun. Bu, (varsa), en son sürücüleri ve kitaplıkları için NVIDIA GPU olmasını içerir. Ayrıca, emin olmalısınız Python ve Python'u yükledikten NumPy SciPy ve uygun derin öğrenme çerçeveleri Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch ve kullanılacağını düşündüğünüz bağlayıcı gibi gibi kitaplıkları projenizi.

> [!NOTE]
> Aşağıdaki alt bölümlerde yazılım giriş kendi giriş sayfaları ' alınmıştır.

### <a name="nvidia-gpu-driver"></a>NVIDIA GPU sürücüsünün

Derin öğrenme çerçeveleri doğruluk bir hızda öğrenin ve doğru true yapay zeka ölçeklendirme makineleri bildirmek için NVIDIA GPU yararlanın. Bilgisayarınızda NVIDIA GPU kartlarına varsa, lütfen [burada](http://www.nvidia.com/Download/index.aspx) veya en son sürücüsünü yüklenecek işletim sistemi güncelleştirme deneyin.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) olan paralel bilgi işlem platformu ve programlama modeli tarafından NVIDIA geliştirmiştir. Bu performans GPU gücünden yararlanılarak bilgi işlem önemli ölçüde artar sağlar. Şu anda, CUDA Araç Seti 8.0, derin öğrenme çerçeveleri tarafından gereklidir.

CUDA yüklemek için

- Bu ziyaret [site](https://developer.nvidia.com/cuda-80-ga2-download-archive)CUDA indirin ve yükleyin.
- CUDA çalışma zamanı kitaplıkları yüklediğinizden emin olun ve ardından CUDA ikili yolu % PATH % veya $Path ortam değişkenine ekleyin.
- Windows üzerinde bu yol "C:\Program Files\NVIDIA GPU bilgi işlem Toolkit\CUDA\v8.0\bin" varsayılan olarak açıktır.

![Windows üzerinde CUDA yükleyin](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA derin sinir ağı kitaplık) temel elemanlar için derin sinir ağı tarafından NVIDIA GPU hızlandırmalı bir kitaplık değil. en son derin öğrenme çerçeveleri tarafından cuDNN v6 gereklidir.

CuDNN yüklemek için:

- Ziyaret [NVIDIA Geliştirici](https://developer.nvidia.com/rdp/cudnn-download) en son paketini karşıdan yüklenip kurulacak.
- % PATH % veya $Path ortam değişkenine ikili cuDNN içeren dizine eklemek için emin olun.
- Windows üzerinde "C:\Program Files\NVIDIA GPU bilgi işlem Toolkit\CUDA\v8.0\bin için" cudnn64_6.dll kopyalayabilirsiniz.

> [!NOTE]
> CNTK 2.0 ve TensorFlow 1.2.1 gibi önceki derin öğrenme çerçeveleri cuDNN v5.1 gerekir. Ancak, birden çok cuDNN sürümü birlikte yükleyebilirsiniz.

### <a name="python"></a>Python

Python, derin öğrenme uygulamaları için birincil programlama dilini olmuştur. **64-bit** Python dağıtım gereklidir ve [Python 3.5.4](https://www.python.org/downloads/release/python-354/) en iyi uyumluluk için önerilir.

### <a name="to-install-python-on-windows"></a>Windows üzerinde Python yüklemek için

- Biz yalnızca kendiniz için Python Başlatıcısı'nı yükleme önermek ve Python % PATH % ortam değişkenine ekleyin.
- Instalovat modul pip yüklemek ve Python'da yazılmış yazılım paketlerini yönetmek için paket yönetim sistemi emin olun.

Derin öğrenme çerçeveleri, kendi yükleme için pip dayanır.

![Windows üzerinde Python'ı yükleyin](media/installation/install_python_win.png)

Ardından, Python 3.5 doğru yüklenip yüklenmediğini doğrulayın ve pip bir terminalde aşağıdaki komutları çalıştırarak en son sürüme yükseltmek için ihtiyacımız:

- **Windows**
    ```cmd
    C:\Users\test>python -V
    Python 3.5.4

    C:\Users\test>pip3.5 -V
    pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

    C:\Users\test>python -m pip install -U pip
    ```

- **macOS**
    ```bash
    MyMac:~ test$ python3.5 -V
    Python 3.5.4

    MyMac:~ test$ pip3.5 -V
    pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

    MyMac:~ test$ python3.5 -m pip install -U pip
    ```

### <a name="python-on-visual-studio"></a>Visual Studio'da Python

Python, uzantılar aracılığıyla Visual Studio'da tam olarak desteklenir.
Yükleme hakkında daha fazla bilgi [Visual Studio Araçları için Python](../python/installing-python-support-in-visual-studio.md) daha fazla ayrıntı için.

### <a name="numpy-and-scipy"></a>NumPy ve SciPy

- **NumPy** küçük çok boyutlu diziler için çok fazla hızdan ödün vermeden rastgele kayıtların büyük çok boyutlu diziler verimli bir şekilde yönetmek üzere tasarlanmış genel amaçlı bir dizi işlem paketidir.

- **SciPy** ("Sigh pasta" olarak okunur) matematik, Bilim ve mühendislik NumPy bağlı olarak, açık kaynaklı bir yazılımdır. Sürüm 1.0.0 ' başlayarak, SciPy artık resmi önceden oluşturulmuş Tekerlek paketi için Windows olarak sahiptir.

NumPy ve SciPy yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Varolan eski ya da terim ve kısaltmalarla yukarıdaki komutu yükseltmeleri (örn: üçüncü taraf paketleri http://www.lfd.uci.edu/~gohlke/pythonlibs/ Windows için) NumPy ve en son resmi olanlara SciPy.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Bilişsel Araç Seti (CNTK)

[Microsoft Bilişsel Araç Seti](https://cntk.ai) sinir ağları bir dizi aracılığıyla bir yönlü graf işlem adımları olarak tanımlayan bir birleşik derin öğrenme araç setidir. CNTK hem Python hem de BrainScript programlama dillerini destekler.

> [!NOTE]
> CNTK, macOS şu anda desteklemiyor.

CNTK Python paketini yüklemek için bkz: [CNTK yükleme](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) bir veri akış grafiklerini kullanarak sayısal hesaplama için açık kaynak yazılım kitaplığıdır. Başvurmak [burada](https://www.tensorflow.org/install/) ayrıntılı yükleme için.

> [!NOTE]
> 1.2 sürümü itibarıyla, TensorFlow, GPU desteğine artık macOS için sağlar.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) basit, modüler ve ölçeklenebilir derin öğrenme çerçevedir. Caffe2 özgün Caffe üzerinde oluşturma, ifade, hız ve modülerlik düşünülerek tasarlanmıştır.

Şu anda hiçbir önceden oluşturulmuş Caffe2 python Tekerlek paketi mevcut değildir.

Ziyaret [burada](https://caffe2.ai/docs/getting-started.html) kaynak koddan oluşturmak için.

### <a name="mxnet"></a>MXNet

[Apache (incubating) MXNet](https://mxnet.incubator.apache.org/) , verimlilik ve esneklik için tasarlanmış bir derin öğrenme altyapısıdır. Olanak tanır **karıştırmak** [sembolik ve zorunlu programlama](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) verimliliğini ve üretkenliğini en üst düzeye çıkarın.

MXNet yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- GPU ile
    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```
- GPU
    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) Python ve çalıştırma yeteneğine CNTK, TensorFlow veya Theano üstte yazılmış bir üst düzey sinir ağları API. Hızlı deneme etkinleştirme bir odak ile geliştirilmiştir. Idea olabildiğince az gecikme ile sonuçlanması gelen Git işaretleyebilmesine iyi araştırma yapmaya anahtardır.

Keras yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) tanımlayın, iyileştirin ve verimli bir şekilde çok boyutlu diziler içeren matematik nevyhodnocovat olanak tanıyan bir Python kitaplığıdır.

Theano yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) iki üst düzey özellikler sağlayan bir python paketi:

- Güçlü GPU hızlandırmalı tensor hesaplama (gibi numpy)
- Bant tabanlı autograd sistemde yerleşik derin sinir ağları

PyTorch yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- **Windows**
    - Henüz hiçbir resmi Tekerlek paketi yoktur. Bir üçüncü taraf indirebileceğiniz [Anaconda PyTorch paket](https://anaconda.org/pytorch/repo?type=all).
    - Örneğin giriş dizininize açılamadı "C:\Users\test\pytorch".
    - "C:\Users\test\pytorch\Lib\site-packages" % ise PYTHONPATH % ortam değişkenine ekleyin.

- **macOS**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```
    > [!NOTE]
    > macOS ikili dosyaları CUDA desteği yoktur, CUDA gerekirse kaynaktan yükleyin

- **Linux**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```
    > [!NOTE]
    > Bu tek bir pakette hem GPU ve CPU destekler.

Son olarak, Windows üzerinde olmayan torchvision yükleyin:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Bağlayıcı

[Bağlayıcı](https://chainer.org/) , esneklik amaçlayan bir Python tabanlı derin öğrenme altyapısıdır. Otomatik farklılaştırma dayalı API'leri sağlayan **tanımlayın-tarafından-Çalıştır yaklaşım** (yani) dinamik hesaplama grafikler) oluşturmak ve sinir ağları eğitmek için üst düzey API'ler nesne yönelimli yanı sıra.

CUDA desteğini etkinleştirmek için yükleme [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> Windows üzerinde bir 2015 sürümünü ihtiyacınız [Visual Studio](https://visualstudio.microsoft.com/) veya [Microsoft Visual C++ derleme Araçları](https://visualstudio.microsoft.com/visual-cpp-build-tools/) CuPy CUDA 8.0 ile derlemek için.

Bağlayıcı yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install chainer==3.0.0
```