---
title: launch.vs.jsüzerinde tasks.vs.jskullanarak derleme hata ayıklama görevlerini özelleştirin
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd0f7378893b52e93480272c73acc2aa413320d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533725"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Klasör aç" geliştirmesi için derleme ve hata ayıklama görevlerini özelleştirin

Visual Studio birçok farklı dili ve kod esaslarını nasıl çalıştıracağınızı bilir, ancak her şeyin nasıl çalıştırılacağını bilmez. Visual Studio 'da [bir kod klasörü açtıysanız](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) ve Visual Studio kodunuzun nasıl çalıştırılacağını biliyorsa, ek bir yapılandırma olmadan hemen çalıştırabilirsiniz.

Kod temeli, Visual Studio 'Nun tanımadığı özel yapı araçları kullanıyorsa, Visual Studio 'da kodun çalıştırılması ve hata ayıklaması için bazı yapılandırma ayrıntılarını sağlamanız gerekir. Visual Studio 'Nun *derleme görevlerini*tanımlayarak kodunuzun nasıl oluşturulacağını söyleyebilirsiniz. Bir dilin kodunu derlemek ve çalıştırmak için gereken tüm öğeleri belirtmek için bir veya daha fazla yapı görevi oluşturabilirsiniz. İstediğiniz neredeyse her şeyi yapabildiği rastgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listelemek veya bir dosyayı yeniden adlandırmak için bir görev oluşturabilirsiniz.

Aşağıdaki *. JSON* dosyalarını kullanarak proje-Less kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|* Üzerindetasks.vs.js*|Özel derleme komutları ve derleyici anahtarları ve rastgele (derleme olmayan ilişkili) görevleri belirtin.<br>**Çözüm Gezgini** sağ tıklama menü öğesi **görevleri Yapılandır**' ı kullanarak erişilir.|
|* Üzerindelaunch.vs.js*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>**Çözüm Gezgini** menü öğesi **hata ayıklama ve başlatma ayarları**' na sağ tıklayın.|

Bu *. JSON* dosyaları, kod tabanınızın kök klasöründe *vs. ile* adlı gizli bir klasörde bulunur. Dosyalarda *tasks.vs.js* ve *launch.vs.js* , **Çözüm Gezgini**bir dosya veya klasör üzerinde **görevleri yapılandırma** veya **hata ayıklama ve başlatma ayarları** ' nı seçtiğinizde, Visual Studio tarafından gerekli bir şekilde oluşturulur. Kullanıcılar genellikle kaynak denetimine denetlemek istemediğinden, bu *. JSON* dosyaları gizlidir. Ancak onları kaynak denetimine denetleyebilmek istiyorsanız, dosyaları görünür oldukları kod tabanınızın köküne sürükleyin.

> [!TIP]
> Visual Studio 'da gizli dosyaları görüntülemek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** düğmesini seçin.

## <a name="define-tasks-with-tasksvsjson"></a>tasks.vs.jsile görevleri tanımlama

Mevcut çalışma alanınızda bulunan dosyalar üzerinde, derleme betikleri veya diğer dış işlemleri otomatikleştirebilir ve bunları doğrudan IDE 'de görevler olarak çalıştırabilirsiniz. Bir dosya veya klasöre sağ tıklayıp **görevleri Yapılandır**' ı seçerek yeni bir görev yapılandırabilirsiniz.

![Görevler menüsünü Yapılandır](../ide/media/customize-configure-tasks-menu.png)

Bu, *. vs* klasöründeki dosyasında *tasks.vs.js* oluşturur (veya açar). Bu dosyada bir yapı görevi veya rastgele bir görev tanımlayabilir ve sonra **Çözüm Gezgini** sağ tıklama menüsünde bunu verdiğiniz adı kullanarak çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türdeki tüm dosyalara eklenebilir. Örneğin, NuGet paket dosyaları bir "paket geri yükleme" görevine sahip olacak şekilde yapılandırılabilir veya tüm kaynak dosyaları, tüm *. js* dosyaları için bir Kater gibi bir statik analiz görevine sahip olacak şekilde yapılandırılabilir.

### <a name="define-custom-build-tasks"></a>Özel derleme görevlerini tanımlama

Kod tabanınız Visual Studio 'Nun tanımadığı özel yapı araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar Visual Studio 'da kodu çalıştıramazsınız ve hata ayıklayamazsınız. Visual Studio, Visual Studio 'Nun kodunuzu nasıl derleyeceğini, yeniden derleyeceğini ve temizleyeceğini söyleyebileceğiniz *derleme görevleri* sağlar. Derleme görev dosyası *tasks.vs.js* , Visual Studio iç geliştirme döngüsünü kod tabanınızın kullandığı özel derleme araçlarına bağar.

*Hello.cs*adlı tek bir C# dosyasından oluşan bir kod temeli düşünün. Böyle bir kod temeli için *derleme görevleri dosyası* şöyle görünebilir:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Oluşturma, temizleme ve yeniden oluşturma hedeflerini içeren böyle bir *derleme görevleri* dosyası için, dosyasında aşağıdaki *tasks.vs.js* tanımlayabilirsiniz. Derleme aracı olarak NMAKE kullanarak kod temeli oluşturmaya, yeniden oluşturmaya ve temizlemeye yönelik üç derleme görevi içerir.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

*tasks.vs.jsüzerinde*yapı görevlerini tanımladıktan sonra, **Çözüm Gezgini**ilgili dosyalara sağ tıklama menüsü (bağlam menüsü) öğeleri eklenir. Bu örnek için, "derleme", "yeniden derleme" ve "Temizleme" seçenekleri, *derleme görevleri* dosyası dosyalarının bağlam menüsüne eklenir.

![derleme, yeniden oluşturma ve Temizleme ile derleme görevleri dosyası bağlam menüsü](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutlar, ayarları nedeniyle **görevleri Yapılandır** komutunun altındaki bağlam menüsünde görüntülenir `contextType` . "derleme", "yeniden derleme" ve "Temizleme" yapı komutlardır, bu nedenle bağlam menüsünün ortasındaki derleme bölümünde görünürler.

Bu seçeneklerden birini belirlediğinizde, görev yürütülür. Çıktı, **Çıkış** penceresinde görünür ve derleme hataları **hata listesi**görüntülenir.

### <a name="define-arbitrary-tasks"></a>Rastgele görevleri tanımlama

Yalnızca istediğiniz herhangi bir şeyi yapmak için dosyada *tasks.vs.js* rastgele görevler tanımlayabilirsiniz. Örneğin, seçili dosyanın adını **Çıkış** penceresinde göstermek veya belirtilen bir dizindeki dosyaları listelemek için bir görev tanımlayabilirsiniz.

Aşağıdaki örnekte, tek bir görevi tanımlayan bir dosya *tasks.vs.js* gösterilmektedir. Çağrıldığında, görev seçili olan *. js* dosyasının dosya adını görüntüler.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` sağ tıklama menüsünde görüntülenen adı belirtir.
- `appliesTo` komutun hangi dosyalara uygulanabilir olduğunu belirtir.
- `command`Özelliği çağrılacak komutu belirtir. Bu örnekte, `COMSPEC` ortam değişkeni, genellikle *cmd.exe*komut satırı yorumlayıcısını belirlemek için kullanılır.
- `args`Özelliği, çağrılan komuta geçirilecek bağımsız değişkenleri belirtir.
- `${file}`Makro seçili dosyayı **Çözüm Gezgini**alır.

*tasks.vs.js*kaydettikten sonra, klasördeki herhangi bir *. js* dosyasına sağ tıklayıp **yankı dosya adı**' nı seçebilirsiniz. Dosya adı **Çıkış** penceresinde görüntülenir.

> [!NOTE]
> Kod tabanınız dosya *tasks.vs.js* içermiyorsa, **Çözüm Gezgini**bir dosyanın sağ tıklama veya bağlam menüsünden **görevleri Yapılandır** ' ı seçerek bir tane oluşturabilirsiniz.

Sonraki örnek, *bin* dizininin dosyalarını ve alt klasörlerini listeleyen bir görevi tanımlar.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` , bloğundan önce ilk tanımlanan özel bir makrodur `tasks` . Daha sonra `args` özelliğinde çağırılır.

Bu görev tüm dosyalar için geçerlidir. **Çözüm Gezgini**bir dosya üzerinde bağlam menüsünü açtığınızda, görevin ad **listesi çıktıları** menünün alt kısmında görünür. **Liste çıktıları**' nı seçtiğinizde, *bin* dizininin Içeriği Visual Studio 'daki **Çıkış** penceresinde listelenir.

![Bağlam menüsünde rastgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Dosyalarda birden çok *tasks.vs.js* , bir kod temelinin kökünde ve alt dizinlerinde bulunabilir. Bu tasarım, kod temelinin farklı alt dizinlerinde farklı davranışa sahip olmak için esneklik sağlar. Visual Studio, dosyaları aşağıdaki sırada önceliklendirerek, kod temeli genelinde ayarları toplar veya geçersiz kılar:

- Kök klasörün *. vs* dizinindeki ayar dosyaları.
- Bir ayarın hesaplandığı dizin.
- Kök dizine kadar olan geçerli dizinin üst dizini.
- Kök dizindeki ayarlar dosyaları.

Bu toplama kuralları * üzerindetasks.vs.js*için geçerlidir. Diğer dosyadaki ayarların nasıl toplandığından ilgili bilgi için, bu makaledeki dosyanın ilgili bölümüne bakın.

### <a name="properties-for-tasksvsjson"></a>tasks.vs.jsiçin Özellikler

Bu bölümde, * üzerindetasks.vs.js*belirtebileceğiniz bazı özellikler açıklanmaktadır.

#### <a name="appliesto"></a>appliesTo

Alanında adını belirterek herhangi bir dosya veya klasör için görevler oluşturabilirsiniz `appliesTo` , örneğin `"appliesTo": "hello.js"` . Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|Dosya maskesi|Description|
|-|-|
|`"*"`| görev, çalışma alanındaki tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görev, çalışma alanındaki tüm klasörler için kullanılabilir|
|`"*.js"`| görev, çalışma alanında *. js* uzantısına sahip tüm dosyalar için kullanılabilir|
|`"/*.js"`| görev, çalışma alanının kökünde *. js* uzantısına sahip tüm dosyalar için kullanılabilir|
|`"src/*/"`| görev *src* klasörünün tüm alt klasörlerinde kullanılabilir|
|`"makefile"`| görev, çalışma alanındaki tüm *derleme görevleri* dosyası dosyaları için kullanılabilir|
|`"/makefile"`| görev yalnızca çalışma alanının kökündeki *derleme görevleri dosyası* tarafından kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>tasks.vs.jsmakrolar

|Makroya|Description|
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenini belirtir (örneğin, $ {env. Geliştirici komut istemi için ayarlanan PATH}, $ {env. COMSPEC} ve benzeri). Daha fazla bilgi için bkz. [Visual Studio Için Geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Çalışma alanı klasörünün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Bu görevi çalıştırmak için seçilen dosya veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolu (örneğin, *src\hello.js*)|
|`${fileBasename}`| Dosyanın yolu veya uzantısı olmayan adı (örneğin, *Merhaba*)|
|`${fileDirname}`| Dosya adı hariç dosyanın tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçilen dosyanın uzantısı (örneğin,  *. js*)|

## <a name="configure-debugging-with-launchvsjson"></a>launch.vs.jsile hata ayıklamayı yapılandırma

CMake projelerini hata ayıklama için yapılandırmak için bkz. [CMake hata ayıklama oturumlarını yapılandırma](/cpp/build/configure-cmake-debugging-sessions).

1. Kod tabanınızı hata ayıklama için yapılandırmak üzere **Çözüm Gezgini** öğesinde, çalıştırılabilir dosyanızın sağ tıklama veya bağlam menüsünden **hata ayıklama ve başlatma ayarları** menü öğesini seçin.

   ![Hata ayıklama ve başlatma ayarları bağlam menüsü](media/customize-debug-launch-menu.png)

1. **Hata ayıklayıcı Seç** iletişim kutusunda bir seçenek belirleyin ve ardından **Seç** düğmesini seçin.

   ![Bir hata ayıklayıcı iletişim kutusu seçin](media/customize-select-a-debugger.png)

   Dosyadaki *launch.vs.js* henüz yoksa, oluşturulur.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Sonra, **Çözüm Gezgini**' de çalıştırılabilir dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla**' yı seçin.

   Yürütülebilir dosya, kod tabanınız için başlangıç öğesi olarak atanır ve hata ayıklama **Başlangıç** düğmesinin başlığı, yürütülebilir dosyanızın adını yansıtacak şekilde değişir.

   ![Özelleştirilmiş Başlangıç düğmesi](media/customize-start-button.png)

   **F5**' i seçtiğinizde, hata ayıklayıcı önceden ayarlamış olduğunuz herhangi bir kesme noktasında başlatılır ve duraklar. Tüm tanıdık hata ayıklayıcı pencereleri kullanılabilir ve çalışır.

   > [!IMPORTANT]
   > C++ açık klasör projelerinde özel derleme ve hata ayıklama görevleriyle ilgili ek ayrıntılar için bkz. [Visual Studio 'Da c++ derleme sistemleri Için klasörü açma desteği](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenler belirtin

Dosyadaki *launch.vs.js* hata ayıklama için geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz. `args`Aşağıdaki örnekte gösterildiği gibi, dizideki bağımsız değişkenleri ekleyin:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Bu dosyayı kaydettiğinizde, yeni yapılandırmanın adı hata ayıklama hedefi açılır listesinde görünür ve hata ayıklayıcıyı başlatmak için bunu seçebilirsiniz. Dilediğiniz kadar çok hata ayıklama yapılandırması oluşturabilirsiniz.

![Hata ayıklama yapılandırması açılan listesi](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` *launch.vs.json* öğesinde dizi özelliği &mdash; , kod temeli ve *. vs* dizini için kök dizin olan iki dosya konumundan okunurdur. Bir çakışma varsa, *.vs\launch.vs.jsüzerindeki*değere öncelik verilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

Bu konuda açıklanan üç *. JSON* dosyasına ek olarak, Visual Studio kod tabanınızda varsa bazı ek dosyalardan de ayarları okur.

### <a name="vscodesettingsjson"></a>Üzerinde .vscode\settings.js

Visual Studio, *. vscode*adlı bir dizinde ise, *settings.jsüzerinde*adlı bir dosyadan sınırlı ayarları okur. Bu işlevsellik, daha önce Visual Studio Code daha önce geliştirilen codetabanlar için verilmiştir. Şu anda *.vscode\settings.json* ' dan okunan tek ayar, `files.exclude` Çözüm Gezgini ve bazı arama araçlarından dosyaları görsel olarak filtreleyerek.

Kod tabanınızdaki dosyalarda istediğiniz sayıda *.vscode\settings.js* olabilir. Bu dosyadan okunan ayarlar, *. vscode* üst dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>.gitignore

*. gitignore* dosyaları git 'e hangi dosyaların yoksayılacağını bildirmek için kullanılır; diğer bir deyişle, iade etmek istemediğiniz dosya ve dizinler. *. gitignore* dosyaları genellikle kod temelinin tüm geliştiricileriyle paylaşılabilmesi için bir kod temelinin parçası olarak dahil edilir. Visual Studio, öğeleri görsel olarak ve bazı arama araçlarından filtrelemek için *. gitignore* dosyalarındaki desenleri okur.

*. Gitignore* dosyasından okunan ayarlar, üst dizinine ve tüm alt dizinlere uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ için CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
