---
title: Python projeleri için özel menü komutlarını tanımlama
description: Düzenleme proje ve MSBuild, Visual Studio yürütülebilir programlar, betikler, modüller, satır içi kod parçacıkları ve pip çağırmak için Python proje bağlam menüsüne özel komutlar ekleyebilirsiniz.
ms.date: 11/12/2018
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
ms.openlocfilehash: be8befcc549b76c8ac2b6435146c636b592b5494
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062877"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutlar tanımlayın

Python projelerinizi çalışma sürecinde kendinizi özel komut dosyaları veya modülleri pip komutları çalıştırmak veya başka bir rastgele aracını çalıştırın, çalıştırılacak bir komut penceresine geçiş bulabilirsiniz. İş akışınızı geliştirmek için özel komutları ekleyebilirsiniz **Python** alt menüde Python proje bağlam menüsü. Bir konsol penceresi veya Visual Studio komutları çalıştırabilirsiniz **çıkış** penceresi. Visual Studio hataları ve Uyarıları, komutun çıktısından ayrıştırmayı istemek için normal ifadeleri de kullanabilirsiniz.

Varsayılan olarak, bu menü yalnızca tek içeren **çalıştırma PyLint** komutu:

![Bir projenin bağlam menüsünden Python menüdeki varsayılan görünümünü](media/custom-commands-default-menu.png)

Özel komutlar bu aynı bağlam menüsünde görünür. Özel komutlar, bunlar burada tek tek proje için geçerli bir proje dosyasının doğrudan eklenir. Özel komutlar da tanımlayabilirsiniz bir *.targets* kolayca birden çok proje dosyalarına alınabilir dosya.

Belirli Visual Studio'da Python proje şablonları zaten kullanarak kendi özel komutlar ekleme, *.targets* dosya. Örneğin, iki komutu Bottle Webový projekt ve Flask Web projesi şablonları ekleyin **Spustit server** ve **başlangıç hata ayıklama sunucusunun**. Django Web projesi şablonu, bu aynı komutları yanı sıra çok sayıda videonuz daha ekler:

![Python alt bir Django projesinin bağlam menüsünde görünümü](media/custom-commands-django-menu.png)

Her özel komut bir Python dosyası, bir Python modülü, satır içi Python kodu, rastgele bir yürütülebilir dosya veya şu PIP komutunu başvurabilir. Ayrıca, nasıl ve nerede komutu çalıştırır belirtebilirsiniz.

> [!Tip]
> Bir proje dosyasını bir metin düzenleyicisinde değişiklik olduğunda, bu değişiklikleri uygulamak için Visual Studio projeyi tekrar yüklemek gereklidir. Örneğin, bir projeye özel komutu tanımları proje bağlam menüsünde görünmesini bu komutlara ekledikten sonra yeniden yüklemelisiniz.
>
> Sizin de bildiğiniz gibi Visual Studio Proje dosyasını doğrudan düzenlemeniz için bir yol sağlar. İlk proje dosyasını sağ tıklatın ve seçin **projeyi**, ardından tekrar sağ tıklayıp **Düzenle \<proje adı >** projeyi Visual Studio düzenleyicisinde açın. Ardından olun ve düzenlemeleri kaydedebilir, projeyi bir kez daha sağ tıklatın ve seçin **projeyi**, ayrıca ister Düzenleyicisi'nde proje dosyasını kapatmadan onaylayın.
>
> Ancak, özel komut geliştirirken, bu tıklama zahmetli hale gelebilir. Daha verimli bir iş akışı için Visual Studio'da projeye yüklemek ve açmak için ayrıca *.pyproj* ayrı bir düzenleyicide tamamen (başka bir örneği Visual Studio, Visual Studio Code, Not Defteri, vb. gibi.) dosyası. Düzenleyicide ve Visual Studio anahtara değişiklikleri kaydettiğinizde, Visual Studio değişiklikleri algılar ve projeyi yeniden yüklemeyi ister (**proje \<adı > ortam dışında değiştirilmiş.**). Seçin **yeniden** ve yaptığınız değişiklikleri tek bir adımda hemen uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>İzlenecek yol: bir komutu bir proje dosyasına ekleyin.

Özel komutları ile tanımak için bu bölümde doğrudan kullanarak bir projenin başlangıç dosyası çalışan basit bir örneği açıklanmaktadır *python.exe*. (Böyle bir komut etkili bir şekilde kullanarak aynıdır **hata ayıklama** > **hata ayıklama olmadan Başlat**.)

1. "Python-CustomCommands kullanarak" adlı yeni bir proje oluşturma **Python uygulaması** şablonu. (Bkz [hızlı başlangıç: bir şablondan bir Python projesi oluşturma](quickstart-02-python-in-visual-studio-project-from-template.md) , zaten işlemiyle ilgili bilgi sahibi değilseniz, yönergeler için.)

1. İçinde *Python_CustomCommands.py*, kod ekleme `print("Hello custom commands")`.

1. Projeye sağ **Çözüm Gezgini**seçin **Python**ve alt menüde görüntülenen yalnızca komut olduğuna dikkat edin **çalıştırma PyLint**. Özel komutlarınız bu aynı alt menüsünde görüntülenir.

1. Giriş olarak önerilen, açık *Python CustomCommands.pyproj* ayrı bir metin düzenleyicisinde. Ardından yalnızca kapatma içindeki dosyanın sonuna aşağıdaki satırları ekleyin `</Project>` ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Visual Studio'ya dönün ve seçin **yeniden** yaptığınızda, sizden dosya değişikliği hakkında. Denetleyin ardından **Python** yeniden görmek için menü **çalıştırma PyLint** olmasına rağmen yalnızca eklediğiniz satırları varsayılan çoğalttığı orada gösterilen tek öğe `<PythonCommands>` PyLint içeren özellik grubu komutu.

1. Proje dosyası ile Düzenleyicisi'ne geçin ve aşağıdaki `<Target>` tanımından sonra `<PropertyGroup>`. Bu makalenin sonraki bölümlerinde açıklandığı gibi bu `Target` öğe tanımlar başlangıç kullanarak ("StartupFile" özelliği tarafından tanımlanır) dosyasını çalıştırmak için özel bir komut *python.exe* konsol penceresinde. Öznitelik `ExecuteIn="consolepause"` kapatmadan önce bir tuşa basın bekler bir konsol kullanır.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Hedefin değeri Ekle `Name` özniteliğini `<PythonCommands>` özellik grubu öğesi aşağıdaki kod gibi görünür, böylece daha önce eklendi. Hedef adını bu listeye ekleme olduğundan bu gruba ekler **Python** menüsü.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Komutunuz içinde tanımlanan önce görünmesini istiyorsanız `$(PythonCommands)`, bunları önce bu belirteci yerleştirin.

1. Proje dosyasını kaydedin, Visual Studio'ya geçiş yapın ve istendiğinde projeyi yeniden yükleyin. Ardından sağ tıklayarak **Python CustomCommands** seçin ve proje **Python**. Görmelisiniz bir **başlangıç dosyası çalıştırmak** menüdeki öğe. Menü öğesi görmüyorsanız adına eklediğiniz denetleyin `<PythonCommands>` öğesi. Ayrıca bkz: [sorun giderme](#troubleshooting) bu makalenin ilerleyen bölümlerinde.

    ![Python bağlam alt menüde görünmesini özel komut](media/custom-commands-walkthrough-menu-item.png)

1. Seçin **başlangıç dosyası çalıştırmak** komut ve metinle görünür bir komut penceresi görmeniz **Hello özel komutlar** ardından **devam etmek için herhangi bir tuşa basın**.  Pencereyi kapatmak için bir tuşa basın.

    ![Özel komut çıktısında bir konsol penceresi](media/custom-commands-walkthrough-console.png)

1. Proje dosyası ile Düzenleyicisi'ne dönün ve değerini değiştirmek `ExecuteIn` özniteliğini `output`. Dosyayı kaydedin, Visual Studio'ya geçmek, projeyi yeniden yükleyin ve komutunu yeniden çağırın. Gördüğünüz program çıkış görünür Visual Studio'nun bu süre **çıkış** penceresi:

    ![Özel komut çıktısı çıktı penceresinde](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için uygun bir tanımla `<Target>` her komut için öğe ekleme hedef adını `<PythonCommands>` özellik grubu ve Visual Studio projeyi yeniden yükleyin.

>[!Tip]
> Kullandığı gibi özellikler, proje komut çağırma `($StartupFile)`ve belirteç tanımsız olduğundan komut başarısız olur, Visual Studio devre dışı bırakır komutu kadar projeyi yeniden yükleyin. Yine de bu gibi durumlarda projeyi yeniden gerek değişiklik projenin özellik tanımlarsınız, ancak bu komutları durumunu yenilemez.

## <a name="command-target-structure"></a>Komut hedef yapı

Genel formu `<Target>` öğesi aşağıdaki sözde kod gösterilir:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Proje özellikleri veya öznitelik değerleri içinde ortam değişkenlerini başvurmak için adını kullanın. bir `$()` gibi belirteci `$(StartupFile)` ve `$(MSBuildProjectDirectory)`. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Hedef öznitelik

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Ad | Evet | Visual Studio projesi içinde komut tanımlayıcısı. Bu ad eklenmeli `<PythonCommands>` özellik grubu komutun Python alt menüsünde görüntülenir. |
| Etiketle | Evet | Python alt menüde görüntülenen kullanıcı Arabiriminde görünen adı. |
| Döndürür | Evet | İçermelidir `@(Commands)`, hedef bir komut olarak tanımlar. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem öznitelikleri

Tüm öznitelik değerleri büyük/küçük harfe duyarsızdır.

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| TargetType | Evet | Hedef öznitelik ne içerdiğini ve bağımsız değişkenler özniteliği ile birlikte nasıl kullanıldığını belirtir:<ul><li>**yürütülebilir**: hedefte, doğrudan komut satırına girilen gibi bağımsız değişkenler, değer ekleme adlı yürütülebilir dosyayı çalıştırın. Değer bağımsız değişkenler olmadan yalnızca bir program adı içermelidir.</li><li>**betik**: çalıştırma *python.exe* ile hedef dosya adını, ardından bağımsız değişkenleri değere sahip.</li><li>**Modül**: çalıştırma `python -m` bağımsız değişken değeri ile izlenen hedefte, modül adı ardından.</li><li>**kod**: hedefte bulunan satır içi kodu çalıştırın. Bağımsız değişken değeri yok sayılır.</li><li>**pip**: çalıştırma `pip` ExecuteIn ", ancak pip varsayar çıktısını almak için" olarak ayarlanır; bağımsız değişken tarafından izlenen hedefte komutu olan `install` komut ve hedef olarak paket adını kullanır.</li></ul> |
| Hedef | Evet | Dosya adı, modül adı, kod veya, TargetType bağlı olarak kullanmak için pip komutu. |
| Arguments | İsteğe Bağlı | Bir dize bağımsız değişkenleri, hedef vermek için (varsa) belirtir. TargetType olduğunda dikkat `script`, bağımsız değişkenler Python programına verilmez *python.exe*. İçin göz ardı `code` TargetType. |
| ExecuteIn | Evet | Komutu çalıştırmak ortamı belirtir:<ul><li>**Konsol**: (varsayılan), hedef ve bağımsız değişkenler doğrudan komut satırında girilirse gibi çalışır. Hedef çalıştığından ve otomatik olarak kapatıldıktan bir komut penceresi görünür.</li><li>**consolepause**: konsol, aynı ancak beklediği için bir tuş basışı pencereyi kapatmadan önce.</li><li>**Çıkış**: çalıştırmaları hedef ve, hesaplamanın sonuçlarını görüntülediği **çıkış** Visual Studio'daki. TargetType "pip" ise, Visual Studio paket adını hedef kullanır ve bağımsız değişkenleri ekler.</li><li>**REPL**: çalıştırmaları hedefte [Python etkileşimli](python-interactive-repl-in-visual-studio.md) penceresi; isteğe bağlı görünen adı, pencere başlığı için kullanılır.</li><li>**Hiçbiri**: konsol gibi davranır.</li></ul>|
| Başlangıç | İsteğe Bağlı | Komut çalıştırmak için klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe Bağlı | Yalnızca ExecuteIn olduğunda kullanılan `output`. Her iki değer hangi Visual Studio ile ayrıştırır, hataları ve Uyarıları göstermek için çıktı komutu normal bir ifade belirtin, **hata listesi** penceresi. Belirtilmezse, komut etkilemez **hata listesi** penceresi. Bekliyor hangi Visual Studio hakkında daha fazla bilgi için bkz: [adlandırılmış yakalama grupları](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | İsteğe Bağlı | Paket gereksinimleri aynı biçimi kullanarak komut listesini [ *requirements.txt* ](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). **Çalıştırma PyLint** komutu, örneğin belirtir `pylint>=1.0.0`. Komutu çalıştırmadan önce Visual Studio listedeki tüm paketleri yüklü olduğunu denetler. Visual Studio tüm eksik paketleri yüklemek için pip kullanır. |
| Ortam | İsteğe Bağlı | Komutu çalıştırmadan önce tanımlamak için ortam değişkenlerini bir dize. Her bir değişken form kullanır \<adı > =\<değer > noktalı virgülle ayırarak birden fazla değişken ile. Birden çok değere sahip bir değişken olarak tek veya çift tırnak içinde bulunması gereken ' NAME = VALUE1; VALUE2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için adlandırılmış yakalama grupları

Visual Studio, hata ve uyarıların bir komutun çıktısından ayrıştırılırken bekliyor normal ifadelerde `ErrorRegex` ve `WarningRegex` adlandırılmış gruplar aşağıdaki değerleri kullanın:

- `(?<message>...)`: Hata metni
- `(?<code>...)`: Hata kodu
- `(?<filename>...)`: Bildirilen hata için dosyanın adı
- `(?<line>...)`: Kendisi için hata bildirdi dosya konumu satır sayısı.
- `(?<column>...)`: Kendisi için hata bildirdi dosya konumu sütun sayısı.

Örneğin, PyLint aşağıdaki biçimde uyarılar üretir:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Bu tür uyarılar doğru bilgileri ayıklamak ve bunları göstermek Visual Studio izin vermek için **hata listesi** penceresinde `WarningRegex` değerini **çalıştırma Pylint** komutu aşağıdaki gibidir:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Unutmayın `msg_id` değeri gerçekten olmalıdır `code`, bkz: [sorunu 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Bir .targets dosyasında özel komutları ile oluşturma

Bir proje dosyasında özel komutları tanımlayarak bunları yalnızca bu proje dosyası kullanılmasını sağlar. Birden çok proje dosyasında komutları kullanmak için bunun yerine tanımladığınız `<PythonCommands>` özellik grubunu ve tüm, `<Target>` öğelerinde bir *.targets* dosya. Ardından bu dosyayı her bir proje dosyalarına alın.

*.Targets* dosya şu şekilde biçimlendirilmiş:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Yüklenecek bir *.targets* yerleştirmek, dosya projeye bir `<Import Project="(path)">` öğesi içinde her yerden `<Project>` öğesi. Örneğin, adında bir dosya varsa *CustomCommands.targets* içinde bir *hedefleri* alt projenizde, aşağıdaki kodu kullanın:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Değiştirdiğiniz zaman *.targets* dosyayı yeniden yüklemek için ihtiyacınız *çözüm* içeren projenin kendisinin yalnızca bir proje.

## <a name="example-commands"></a>Örnek komutlar

### <a name="run-pylint-module-target"></a>Spustit pylint (modülü hedef)

Aşağıdaki kod görünen *Microsoft.PythonTools.targets* dosyası:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Belirli bir paket (pip hedef) ile pip yükleme çalıştırma

Aşağıdaki komutu çalıştırmaları `pip install my-package` içinde **çıkış** penceresi. Bir paket geliştirirken, böyle bir komut kullanabilirsiniz ve yükleme testi. Hedef paket adı içerdiğini unutmayın yerine `install` kullanırken varsayılır komutu `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Eski show pip paketleri (pip hedef)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Yürütülebilir bir dosya ile consolepause çalıştırın

Aşağıdaki komut yalnızca çalıştırmaları `where` proje klasöründe başlangıç Python dosyaları göstermek için:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Sunucu ve çalışma hata ayıklama server komutlarını çalıştırmak.

Araştırılacak nasıl **Spustit server** ve **başlangıç hata ayıklama sunucusunun** web projeleri tanımlanan için komutları inceleyin [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Geliştirme için paketini yükle

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Gelen [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) izniyle kullanılır.*

### <a name="generate-windows-installer"></a>Windows Installer'ı Oluştur

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Gelen [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) izniyle kullanılır.*

### <a name="generate-wheel-package"></a>Tekerlek paketi oluştur

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Gelen [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) izniyle kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "proje dosyası yüklenemedi"

Proje dosyasında sözdizimi hataları sahip olduğunu gösterir. Bir satır numarası ile özel hata iletisi içerir ve karakter konumu.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Konsol penceresi hemen komut çalıştırıldıktan sonra kapatır

Kullanım `ExecuteIn="consolepause"` yerine `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüsünde görünmüyor

Komut yer onay `<PythonCommands>` özellik grubu ve komut listesi adı belirtilen adla eşleşen `<Target>` öğesi.

Örneğin, aşağıdaki öğeler, ' % s'adı "ExampleCommand" hedef "Örnek" adı özellik grubundaki eşleşmiyor. Visual Studio, bir komut görünecek şekilde "Örnek" adlı bir komut bulmaz. Komut listesinde "ExampleCommand" kullanın veya "Örneği için" yalnızca hedef adını değiştirin.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>İleti: "çalıştırılırken bir hata oluştu \<komut adı >. Komut alınamadı \<hedef adı > projeden. "

Bildiren içeriğini `<Target>` veya `<CreatePythonCommandItem>` öğeleridir yanlış. Olası nedenler şunlardır:

- Gerekli `Target` özniteliktir boş.
- Gerekli `TargetType` öznitelik boş veya tanınmayan bir değer içeriyor.
- Gerekli `ExecuteIn` öznitelik boş veya tanınmayan bir değer içeriyor.
- `ErrorRegex` veya `WarningRegex` ayarlamadan belirtilen `ExecuteIn="output"`.
- Tanınmayan öznitelikleri öğesinde mevcut. Örneğin, kullanmış `Argumnets` (yazılmış) yerine `Arguments`.

Öznitelik değeri, tanımlanmayan bir özelliğe başvuruda bulunuyorsa boş olabilir. Örneğin, belirteç kullanırsanız `$(StartupFile)` ancak herhangi bir başlangıç dosyası projede tanımlanan ve ardından belirteci boş dize olarak çözer. Bu gibi durumlarda, varsayılan değer tanımlama isteyebilirsiniz. Örneğin, **Server'i** ve **Run hata ayıklama sunucusu** komutları Bottle, Flask, tanımlanan ve Django proje şablonları için varsayılan değer *manage.py* aksi yapmadıysanız Sunucu başlangıç dosyası, proje özelliklerinde belirtilmiş.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio yanıt vermemeye başlıyor ve bu komutu çalıştırırken kilitleniyor

Bir konsol komutu çalıştırmak büyük olasılıkla denediğiniz `ExecuteIn="output"`, bu durumda Visual Studio çıktı ayrıştırmaya çalışırken çökebilir. Bunun yerine `ExecuteIn="console"` kullanın. (Bkz [3682 sorun](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Yürütülebilir komut "iç ya da dış komut, çalıştırılabilir program ya da toplu iş dosyası tanınmıyor"

Kullanırken `TargetType="executable"`, değer `Target` olmalıdır *yalnızca* program adı herhangi bir bağımsız değişken gibi *python* veya *python.exe* yalnızca. Herhangi bir bağımsız değişken taşıma `Arguments` özniteliği.
