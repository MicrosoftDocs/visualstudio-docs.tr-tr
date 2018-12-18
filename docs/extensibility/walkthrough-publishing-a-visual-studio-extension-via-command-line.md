---
title: 'İzlenecek yol: komut satırı aracılığıyla bir Visual Studio uzantısı yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 07/12/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d95e2fbe36a73074b97f47f6714f1fc4aa8228c
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050189"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>İzlenecek yol: komut satırı aracılığıyla bir Visual Studio uzantısı yayımlama

Bu kılavuzda komut satırını kullanarak Visual Studio Market'te Visual Studio uzantısı yayımlama gösterir. Market'te uzantınızı eklediğinizde, geliştiriciler kullanabilir [ **Uzantılar ve güncelleştirmeler** ](../ide/finding-and-using-visual-studio-extensions.md) iletişim için yeni ve güncelleştirilmiş uzantıları var gidin.

VsixPublisher.exe Market'te yayımlama Visual Studio uzantıları için komut satırı aracıdır. Erişilebileceğini ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Bu araç kullanılabilir komutlar: **yayımlama**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **oturum açma**, **oturum kapatma**.

## <a name="commands"></a>Komutlar

### <a name="publish"></a>Yayımlama

Bir uzantıyı Market'te yayımlar. Uzantı, bir VSIX, bir exe/MSI dosyası veya bir bağlantı olabilir. Uzantı ile aynı sürümü varsa, uzantı üzerine yazar. Uzantı zaten mevcut değilse yeni bir uzantı oluşturacaksınız.

|Komut seçenekleri |Açıklama |
|---------|---------|
|Yük (gerekli) | Ya da bir yolu veya yayımlamak için yükünü "Daha fazla bilgi URL" kullanmak için bir bağlantı. |
|publishManifest (gerekli) | Bildirim kullanılacak dosya yolu yayımlanır. |
|ignoreWarnings | Bir uzantı yayımlarken yok saymak için uyarıları listesi. Bu uyarı, bir uzantı yayımlarken komut satırı ileti olarak gösterilmez. (örneğin, "VSIXValidatorWarning01, VSIXValidatorWarning02")  
|personalAccessToken | Kişisel erişim belirteci (yayımcı kimliğini doğrulamak için kullanılan PAT). Sağlanmazsa, oturum açmış olan kullanıcılar PAT alınır. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Yayımcının Market'te oluşturur. Ayrıca yayımcı makinede gelecekteki Eylemler (örneğin bir uzantı siliniyor/yayımlama) günlüğe yazar.

|Komut seçenekleri |Açıklama |
|---------|---------|
|displayName (gerekli) | Yayımcı görünen adı. |
|publisherName (gerekli) | Yayımcı (örneğin, tanımlayıcı) adı. |
|personalAccessToken (gerekli) | Kişisel erişim yayımcı kimliğini doğrulamak için kullanılan belirteç. |
|shortDescription | Yayımcı (dosyası değil), kısa bir açıklaması. |
|longDescription | Yayımcı (dosyası değil) uzun açıklaması. |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Yayımcının Market'te siler.

|Komut seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcı (örneğin, tanımlayıcı) adı. |
|personalAccessToken (gerekli) | Kişisel erişim yayımcı kimliğini doğrulamak için kullanılan belirteç. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Market'ten bir uzantı siler.

|Komut seçenekleri |Açıklama |
|---------|---------|
|extensionName (gerekli) | Silmek için uzantı adı. |
|publisherName (gerekli) | Yayımcı (örneğin, tanımlayıcı) adı. |
|personalAccessToken | Kişisel erişim yayımcı kimliğini doğrulamak için kullanılan belirteç. Sağlanmazsa, oturum açmış olan kullanıcılar pat alınır. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>Oturum açma

Bir yayımcı makinesine kaydeder.

|Komut seçenekleri |Açıklama |
|---------|---------|
|(gerekli personalAccessToken | Kişisel erişim yayımcı kimliğini doğrulamak için kullanılan belirteç. |
|publisherName (gerekli) | Yayımcı (örneğin, tanımlayıcı) adı. |
|Üzerine yaz | Yeni bir kişisel erişim belirteci ile var olan bir yayımcı üzerine yazılması gerektiğini belirtir. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>oturum kapatma

Makine dışında bir yayımcı günlüğe kaydeder.

|Komut seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcı (örneğin, tanımlayıcı) adı. |
|ignoreMissingPublisher | Belirtilen yayımcı yok zaten oturum açmış durumdaysa aracı hata gerektiğini belirtir. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest dosyası

PublishManifest dosya tarafından kullanılan **yayımlama** komutu. Bu Market bilmesi gerekir. uzantıyı hakkındaki meta verileri temsil eder. Karşıya yüklenen uzantı bir VSIX uzantı ise, "kimlik" özelliği yalnızca "ayarlamak InternalName" olmalıdır. "Kimlik" özelliklerin geri kalanı vsixmanifest dosyasından oluşturulabilir olmasıdır. Uzantı bir MSI/exe veya bir bağlantı uzantısı ise, kullanıcı "kimlik" özelliği gerekli alanları sağlamanız gerekir. Market'te özgü bilgileri bildiriminin geri kalanını içerir (örneğin, kategoriler olup soru- cevap etkin, vb..).

VSIX uzantısı publishManifest dosyası örneği:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE veya bağlantı publishManifest dosyası örneği:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Varlık dosyaları

Varlık dosyaları readme dosyasında görüntüleri gibi şeyler eklemek için sağlanabilir. Örneğin, aşağıdaki "genel bakış" Markdown belgenin bir uzantısı varsa:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Önceki örnekteki "images/testlogo.png" çözmek için bir kullanıcı "assetFiles" sağlayabilir, yayımlama aşağıdaki gibi bildirim:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Yayımlama Kılavuzu

### <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturun

Bu durumda, varsayılan bir VSPackage uzantı kullanacağız, ancak aynı adımları her uzantı türü için geçerlidir.

1. C# ' "bir menü komutu içeren TestPublish" adlı bir VSPackage'ı oluşturun. Daha fazla bilgi için [ilk uzantınızı oluşturmaya: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Uzantınızı paketi

1. Uzantı vsixmanifest ürün adı, yazar ve sürüm doğru bilgilerle güncelleştirin.

   ![Uzantı vsixmanifest güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı yapı içinde **yayın** modu. Artık uzantınızı bir VSIX \bin\Release klasör olarak paketlenmiş.

3. Yüklemeyi doğrulamak için VSIX dosyasına çift tıklayabilirsiniz.

### <a name="test-the-extension"></a>Uzantıyı test etmek

 Uzantı dağıtmadan önce yapı ve Visual Studio'nun deneysel örneğinde doğru şekilde yüklendiğinden emin olmak için test.

1. Visual Studio'da hata ayıklama başlatılamıyor. Visual Studio deneysel örneği açılacak.

2. Deneysel örneğinde Git **Araçları** menüsüne ve ardından **Uzantılar ve güncelleştirmeler...** . TestPublish uzantısı, Orta bölmede görünür olmalıdır ve etkinleştirilmesi.

3. Üzerinde **Araçları** menüsünde, test komut gördüğünüzden emin olun.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Uzantı Marketi komut satırı aracılığıyla yayımlama

1. Uzantınızı sürümü oluşturulan ve güncel olduğundan emin olun.

2. Publishmanifest.json ve overview.md dosyaları oluşturduğunuz emin olun.

3. Komut satırı açın ve ${VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ dizine gidin.

4. Yeni yayımcı oluşturmak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Oluşturma başarılı publisher'ın, aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Oluşturduğunuz giderek yeni yayımcı doğrulayabilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/manage/publishers)

7. Yeni bir uzantı yayımlamak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Oluşturma başarılı publisher'ın, aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Yayımlanan giderek yeni uzantı doğrulayabilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Market'ten uzantı yükleme

Uzantı yayımlandıktan sonra Visual Studio'da yükleyin ve test etmek.

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler...** .

2. Tıklayın **çevrimiçi** ve sonra TestPublish için arama yapın.

3. **İndir**'e tıklayın. Uzantı ardından yükleme için zamanlanır.

4. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırın

Uzantı, Visual Studio Market'ten ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Komut satırı aracılığıyla marketten uzantıyı kaldırmak için

1. Bir uzantıyı kaldırmak istiyorsanız, aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Uzantı başarıyla silinmesini üzerinde aşağıdaki komut satırı iletiyi görürsünüz:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **uzantı ve güncelleştirmeler...** .

2. "MyVsixExtension" seçin ve ardından **kaldırma**. Uzantı ardından kaldırma işlemi için zamanlanacak.

3. Kaldırma işlemini tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
