---
title: Derleme hata ayıklama görevleri Tasks.vs.JSON launch.vs.json kullanarak özelleştirme
ms.date: 02/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
- vsworkspacesettings.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a5249c1b60c1a3a08e37386bcfbd3d06706bae8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063185"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Yapı özelleştirme ve hata ayıklama için "Klasör Aç" geliştirme görevleri

Visual Studio, birçok farklı dillerde çalıştırma bilir ve kod tabanlarında, ancak her şeyi çalıştırma bilmez. Varsa, [kod klasörü açılır](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) içinde Visual Studio ve Visual Studio kodunuzu çalıştırmak nasıl bilir, herhangi bir ek yapılandırma hemen çalıştırabilirsiniz.

Özel derleme araçları, Visual Studio tanımadığı bir kod temelinde kullanıyorsa, çalıştırmak ve Visual Studio kod hatalarını ayıklamak için bazı yapılandırma ayrıntılarını sağlamak gerekir. Visual Studio tanımlayarak, kodunuzu derlemek nasıl toplamasını *derleme görevleri*. Bir tane oluşturabilirsiniz veya daha fazla dil kendi kodunu derleme ve çalıştırma için gereken tüm öğeleri belirtmek için Görevler oluşturun. Hemen hemen istediğiniz her şeyi yapabilirsiniz, isteğe bağlı görevleri de oluşturabilirsiniz. Örneğin, bir görev bir klasörün içeriğini listelemek için veya bir dosyayı yeniden adlandırmak için oluşturabilirsiniz.

Özelleştirme aşağıdakileri kullanarak, proje daha az kod tabanı *.json* dosyaları:

|Dosya adı|Amaç|
|-|-|
|*tasks.vs.json*|Özel derleme komutları ve derleyici anahtarları rastgele (olmayan-ilgili derleme) belirtmek görevleri.<br>Aracılığıyla erişilen **Çözüm Gezgini** bağlam menüsü öğesi **yapılandırma görevleri**.|
|*launch.vs.json*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>Aracılığıyla erişilen **Çözüm Gezgini** bağlam menüsü öğesi **hata ayıklama ve başlatma ayarları**.|
|*VSWorkspaceSettings.json*|Genel görevleri etkileyebilir ve başlatma ayarları. Örneğin, tanımlama `envVars` içinde *VSWorkspaceSettings.json* dışarıdan komutlarını çalıştırmak için belirtilen ortam değişkenleri ekler.<br>Bu dosyayı el ile oluşturun.|

Bunlar *.json* dosyaları adlı gizli bir klasörde bulunan *.vs* temelinizin kök klasöründeki. *Tasks.vs.json* ve *launch.vs.json* dosyalarının oluşturulduğu Visual Studio tarafından bir gerektiği şekilde ya da seçtiğinizde **yapılandırma görevleri** veya **hata ayıklama ve başlatma ayarları** bir dosya veya klasör üzerinde **Çözüm Gezgini**. Bunlar *.json* dosyaları, kullanıcılar bunları kaynak denetimine kaydetmeye genellikle istemediğinden gizlidir. Ancak, kaynak denetimine denetlemek istiyorsanız, dosyaları burada görünür temelinizin, kök sürükleyin.

> [!TIP]
> Visual Studio'da gizli dosyaları görüntülemek için seçin **tüm dosyaları göster** düğmesini **Çözüm Gezgini** araç çubuğu.

## <a name="define-tasks-with-tasksvsjson"></a>Tasks.vs.json ile görevleri tanımlama

Derleme betikleri veya geçerli çalışma alanınızda doğrudan IDE'de görev olarak çalıştırarak olması dosyalarda dış diğer işlemleri otomatik hale getirebilirsiniz. Bir dosya veya klasörü sağ tıklatıp seçerek yeni bir görev yapılandırabileceğiniz **yapılandırma görevleri**.

![Görevler menüsü yapılandırın](../ide/media/customize-configure-tasks-menu.png)

Oluşturur (veya açılır) *tasks.vs.json* dosyası *.vs* klasör. Bir derleme görevi ya da isteğe bağlı görev bu dosyada tanımlayabilir ve ondan verdiğiniz ad kullanarak çağırma **Çözüm Gezgini** bağlam menüsü.

Özel görevleri, dosyalara veya belirli bir türdeki tüm dosyalar için eklenebilir. Örneğin, "Paketleri geri yükle" görev için NuGet paket dosyaları yapılandırılabilir veya tüm kaynak dosyaları, tüm bir lint gibi statik analiz yer alan bir görev için yapılandırılabilir *.js* dosyaları.

### <a name="define-custom-build-tasks"></a>Özel derleme görevleri tanımlama

Ardından kod temelinizde özel derleme araçları, Visual Studio tanımadığı kullanıyorsa, çalıştırın ve bazı yapılandırma adımları tamamlayana kadar Visual Studio code hata ayıklama yapılamıyor. Visual Studio sağlar *derleme görevleri* nasıl oluşturulacağını, Visual Studio söyleyebilirsiniz, yeniden oluşturun ve kodunuzu temiz. *Tasks.vs.json* görev dosyası Visual Studio iç geliştirme döngüsünü özel derleme araçlarını temelinizde tarafından kullanılan tüm çiftler oluşturun.

Bir tek oluşan bir kod temeli göz önünde bulundurun C# adlı dosya *hello.cs*. *Derleme görevleri dosyası* böyle bir kod temeli için şöyle görünebilir:

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

İçin böyle bir *derleme görevleri dosyası* temiz yapı içerir ve hedefleri yeniden, aşağıdaki tanımlayabilirsiniz *tasks.vs.json* dosya. Bu derleme, yeniden oluşturma ve NMAKE derleme aracı olarak kullanarak, kod tabanının Temizleme için üç derleme görevleri içerir.

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

Derleme görevleri tanımladıktan sonra *tasks.vs.json*, karşılık gelen dosyalar için de ek bağlam menüsü öğelerine eklenir **Çözüm Gezgini**. Bu örnekte, "derleme", "yeniden" ve "temiz" seçeneklerini herhangi bağlam menüsüne eklenen *derleme görevleri dosyası* dosyaları.

![derleme görevleri dosyası bağlam menüsü yapı ile yeniden oluşturun ve temizleme](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutlar bağlam menüsünden görünür **yapılandırma görevleri** nedeniyle komutunu kendi `contextType` ayarları. Bunlar yapı bölümünde bağlam menüsünü ortasında görünmesi için "derleme", "yeniden" ve "temiz" derleme komutlardır.

Bu seçeneklerden birini seçtiğinizde, görevi yürütür. Çıktı görünür **çıkış** penceresi ve derleme hatalarını görünür **hata listesi**.

### <a name="define-arbitrary-tasks"></a>İsteğe bağlı görevleri tanımlama

İsteğe bağlı görevleri tanımlayabilirsiniz *tasks.vs.json* hemen hemen istediğiniz her şeyi yapmak için dosya. Örneğin, şu anda seçili dosyanın adını görüntülemek için bir görev tanımlayabilirsiniz **çıkış** penceresinde veya belirtilen dizindeki dosyaların listesi.

Aşağıdaki örnekte gösterildiği bir *tasks.vs.json* tek bir görevi tanımlayan dosya. Çağrıldığında görev şu anda seçili dosya adını görüntüler *.js* dosya.

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

- `taskName` bağlam menüsünde görünen adını belirtir.
- `appliesTo` hangi dosyaların komutu gerçekleştirilebilir belirtir.
- `command` Özellik çağrılacak komutu belirtir. Bu örnekte, `COMSPEC` ortam değişkeni komut satırı Yorumlayıcı, genellikle tanımlamak için kullanılan *cmd.exe*.
- `args` Özelliği, çağrılan komutun geçirilecek bağımsız değişkenleri belirtir.
- `${file}` Makrosu alır seçili dosyasında **Çözüm Gezgini**.

Kaydettikten sonra *tasks.vs.json*, herhangi bir sağ tıklayabilirsiniz *.js* dosya klasöründe ve seçin **Yankı filename**. Dosya adı görüntülenen **çıkış** penceresi.

> [!NOTE]
> Kod temelinizde içermiyorsa, bir *tasks.vs.json* dosyası oluşturmak için kullanabileceğiniz bir seçerek **yapılandırma görevleri** bir dosyaya sağ tıklayın veya bağlam menüsünden **Çözüm Gezgini**.

Alt klasörleri ve dosyaları listeleyen bir görevi bir sonraki örnekte tanımlar *bin* dizin.

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

- `${outDir}` ilk özel bir makro önce tanımlanan `tasks` blok. Ardından çağrıldığı `args` özelliği.

Bu görev, tüm dosyalar için geçerlidir. Bağlam menüsünde herhangi bir dosyayı açtığınızda **Çözüm Gezgini**, görevin adı **listesi çıkışları** menüsünün altında görüntülenir. Seçeneğini belirlediğinizde **listesi çıkışları**, içeriğini *bin* dizin listelenir **çıkış** Visual Studio'daki.

![Rastgele görevde bağlam menüsü](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayar kapsamı

Birden çok *tasks.vs.json* dosyaları kök ve alt dizinleri bir kod temeli bulunabilir. Bu tasarım, kod tabanının farklı dizinlerde farklı bir davranış sahip olacak esneklik sağlar. Visual Studio toplar veya kod temeli, tüm dosyalarını aşağıdaki sırayla öncelik ayarları geçersiz kılar:

- Kök klasör ayarları dosyaları *.vs* dizin.
- Bir ayar hesaplanan burada dizin.
- Kadar tüm kök dizini geçerli dizinin üst dizini.
- Ayarlar dosyaları kök dizini.

Bu toplama kuralları için geçerli *tasks.vs.json* ve *VSWorkspaceSettings.json* dosyaları. Diğer dosyasındaki ayarları nasıl toplanır hakkında daha fazla bilgi için bu makalede söz konusu dosya için ilgili bölümüne bakın.

### <a name="properties-for-tasksvsjson"></a>Tasks.vs.json özellikleri

Bu bölümde bazı içinde belirtebileceğiniz özellikler açıklanmaktadır *tasks.vs.json*.

#### <a name="appliesto"></a>AppliesTo

Görevler için herhangi bir dosya veya klasör adını belirterek oluşturabileceğiniz `appliesTo` alan, örneğin `"appliesTo": "hello.js"`. Aşağıdaki dosya maskesi değerleri kullanılabilir:

|||
|-|-|
|`"*"`| Görev tüm dosyaları ve klasörleri çalışma alanında kullanılabilir|
|`"*/"`| Görev, çalışma alanındaki tüm klasörler için kullanılabilir|
|`"*.js"`| görevi, uzantılı tüm dosyaları kullanılabilir *.js* çalışma|
|`"/*.js"`| görevi, uzantılı tüm dosyaları kullanılabilir *.js* çalışma alanı kökünde|
|`"src/*/"`| tüm alt görevi kullanılabilir *src* klasörü|
|`"makefile"`| tüm görev *derleme görevleri dosyası* çalışma alanındaki dosyalara|
|`"/makefile"`| görevi, yalnızca kullanılabilir *derleme görevleri dosyası* çalışma alanı kökünde|

#### <a name="macros-for-tasksvsjson"></a>Tasks.vs.json makroları

|||
|-|-|
|`${env.<VARIABLE>}`| herhangi bir ortam değişkeni (örneğin, ${env. belirtir YOL}, ${env.COMSPEC} vb.) için geliştirici komut istemi ayarlayın. Daha fazla bilgi için [Visual Studio için geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Çalışma alanı klasörün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Dosya veya bu görevi karşı çalıştırmak için Seçili klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolunu (örneğin, *src\hello.js*)|
|`${fileBasename}`| Yol ve uzantı olmadan dosyasının adı (örneğin, *hello*)|
|`${fileDirname}`| Dosya adı hariç dosyasının tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçili dosya uzantısını (örneğin, *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Launch.vs.JSON ile hata ayıklamayı Yapılandır

1. Yapılandırmak için hata ayıklama için de codebase **Çözüm Gezgini** seçin **hata ayıklama ve başlatma ayarları** yürütülebilir dosyanızın sağ tıklayın veya bağlam menüsünde menü öğesi.

   ![Hata ayıklama ve başlatma ayarları bağlam menüsü](media/customize-debug-launch-menu.png)

1. İçinde **bir hata ayıklayıcı seçin** iletişim kutusu, bir seçenek belirleyin ve ardından **seçin** düğmesi.

   ![Hata ayıklayıcı iletişim kutusunu seçin](media/customize-select-a-debugger.png)

   Varsa *launch.vs.json* dosya önceden yoksa, oluşturulur.

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

1. Ardından, yürütülebilir dosyaya sağ tıklayarak **Çözüm Gezgini**ve **başlangıç öğesi olarak ayarla**.

   Yürütülebilir kod temelinizde ve hata ayıklama için başlangıç öğesi olarak tanımlanan **Başlat** yürütülebilir dosyanın adını yansıtacak şekilde düğmenin Başlıkta yapılan değişiklikleri.

   ![Özelleştirilmiş Başlat düğmesi](media/customize-start-button.png)

   Seçeneğini belirlediğinizde **F5**, hata ayıklayıcısını başlatan ve herhangi bir kesme noktasında durur zaten ayarlamadınız. Alıştığınız hata ayıklayıcı windows kullanılabilir ve çalışır.

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenlerini belirtme

Hata ayıklama için geçirmek için komut satırı bağımsız değişkenlerini belirtebilirsiniz *launch.vs.json* dosya. Bağımsız değişken Ekle `args` , aşağıdaki örnekte gösterildiği gibi dizi:

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

Bu dosyayı kaydettiğinizde, yeni yapılandırmayı adı hata ayıklama hedefi aşağı açılan listesinde görünür ve hata ayıklayıcıyı başlatmak için bunu seçebilirsiniz. İstediğiniz gibi birçok hata ayıklama yapılandırması oluşturabilirsiniz.

![Hata ayıklama yapılandırmaları aşağı açılan listesi](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` Dizi özelliğinde *launch.vs.json* iki dosya konumlarından okuma&mdash;codebase kök dizinini ve *.vs* dizin. Bir çakışma varsa, öncelik değeri verilir *.vs\launch.vs.json*.

## <a name="define-workspace-settings-in-vsworkspacesettingsjson"></a>Çalışma alanı ayarları içinde VSWorkspaceSettings.json tanımlayın

Etkileyen görevler ve içinde başlatma genel ayarları belirtebilirsiniz *VSWorkspaceSettings.json* dosya. Örneğin, tanımladığınız `envVars` içinde *VSWorkspaceSettings.json*, Visual Studio, harici olarak çalıştırılan komutları için belirtilen ortam değişkenleri ekler. Bu dosyayı kullanmak için el ile oluşturmanız gerekir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

Üç ek olarak *.json* bu konuda açıklanan dosyalarını, Visual Studio ayrıca okur ayarları bazı ek dosyalardan kod tabanınızdaki varsa.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio sınırlı ayarları adlı bir dosyadan okur *settings.json*, adlı bir dizinde ise *.vscode*. Bu işlev için sağlanır, kod tabanlarında daha önce Visual Studio Code'da geliştirilmiştir. Şu anda yalnızca ayarının okuma *.vscode\settings.json* olduğu `files.exclude`, dosyaları görsel olarak Çözüm Gezgini ve bazı arama Araçları'ndan filtreler.

Herhangi bir sayıda olabilir *.vscode\settings.json* temelinizde dosyaları. Bu dosyadan okunan ayarları üst dizini de uygulanır *.vscode* ve tüm alt dizinlerinde.

### <a name="gitignore"></a>.gitignore

*.gitignore* dosyaları yoksaymak için hangi dosyaların Git bildirmek için kullanılır; diğer bir deyişle, dosyaları ve dizinleri iade etmek istemediğiniz. *.gitignore* ayarları kod tabanının tüm geliştiricilere paylaşılabilir böylece dosyaları bir kod temeli genellikle birlikte parçası olarak. Visual Studio okur desenleri *.gitignore* dosyaları öğeleri filtrelemek için görsel olarak ve bazı arama araçları.

Ayarları okuma *.gitignore* dosya, kendi ana dizini ve tüm alt dizinleri için uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için klasör Proje Aç](/cpp/ide/non-msbuild-projects)
- [C++'da CMake projeleri](/cpp/ide/cmake-tools-for-visual-cpp)
- [NMAKE başvurusu](/cpp/build/nmake-reference)
- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)