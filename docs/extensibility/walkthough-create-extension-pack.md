---
title: Uzantı paketi öğesi şablonuyla uzantı paketi oluştur | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 2e0215b22c66d6b555650e05985a674f2ad9aed4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943108"
---
# <a name="walkthrough-create-an-extension-pack"></a>İzlenecek yol: Uzantı Paketi Oluşturma

Birlikte yüklenebilir uzantıları kümesi bir uzantı paketidir. Uzantı paketleri kolayca sık kullandığınız uzantıların diğer kullanıcılarla paylaşmak ya da belirli bir senaryo için bir arada uzantıları kümesini paket olanak sağlar.
  
## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  

Uzantı paketi bu özellik, Visual Studio 15,8 önizleme 2'den itibaren kullanılabilir.
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Uzantı paketi öğesi şablonuyla uzantı oluşturma

Uzantı paketi öğe şablonu, bir uzantı paketi ile birlikte yüklenen uzantı kümesi oluşturur.
  
1. İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `Test Extension Pack`. **Tamam**'ı tıklatın.  
  
2. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **uzantı paketi**. Varsayılan dosya adı (ExtensionPack1.cs) bırakın.  
  
3. Aşağıdaki kodu içeren ExtensionPack1.vsext dosya eklendiğinde

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }  
   ```

4. Uzantının uzantısı paketinde içerecek şekilde vsixıd bulunabilir [Visual Studio Market](https://marketplace.visualstudio.com/). Uzantısına tıklayın ve eklemek istediğiniz bulma **kopya Kimliğini**. Var olan güncelleştirme **Vsixıd** yukarıdaki içinde dosya veya başka bir uzantı listeye ekleyin.

    ![Market'ten Vsixıd kopyalayın](media/vsixid-marketplace.png)

5. Projeyi oluşturmak ve Market'te uzantınızı yükleyin. Bkz: [Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). 
    
> [!NOTE]
> Uzantı paketi, kullanılabilir uzantıları yalnızca yükleyebilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/) veya [özel galeri](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).
 
## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Market'ten uzantı paketini yükle

Uzantı yayımlandıktan sonra Visual Studio'da yükleyin ve test etmek.

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler...** .

2. Tıklayın **çevrimiçi** bulun `Test Extension Pack`.

3. **İndir**'e tıklayın. Uzantı ve kendi uzantısı paketinde uzantılarının listesi için yükleme zamanlanacak.

4. Bir örnek uzantısı paketi yükleme görünümünü aşağıdadır **Uzantılar ve güncelleştirmeler** iletişim. Dahil edilen uzantılar yalnızca bazıları uzantısı paketinde yüklemeyi tercih ediyorsanız, uzantı listesinde değiştirebilirsiniz **için zamanlanmış yükleme**.

    ![Market'ten uzantı paketi indirin](media/vside-extensionpack.png)

5. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırın

Uzantıyı bilgisayarınızdan kaldırmak için:

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **uzantı ve güncelleştirmeler...** .

2. Seçin `Test Extension Pack` ve ardından **kaldırma**. Uzantı ve uzantısı paketinde uzantıları listesini kaldırma işlemi için zamanlanacak.

3. Kaldırma işlemini tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
