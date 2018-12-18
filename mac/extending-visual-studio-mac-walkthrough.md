---
title: Mac kılavuz için Visual Studio'yu genişletme
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: cbf0d99bd87b31484b6c74e9a6d67ac88dc5ba99
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294311"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Mac kılavuz için Visual Studio'yu genişletme

Bu konuda size yapı aracılığıyla [basit uzantı paketi](https://github.com/mjh4/AddIns/tree/master/DateInserter). Uzantı paketi, kullanıcının bir açık metin belgesine geçerli tarih ve saat eklemesine izin veren Mac Düzenle menüsü için Visual Studio'da yeni bir komut oluşturur.

Bu örnek, eklenti Oluşturucu kullanır. Eklenti Oluşturucu, yeni bir proje şablonu oluşturur ve bizim Özel uzantı paketi için gerekli dosyaları ile doldurur.

1. Zaten açık değilse, Mac için Visual Studio'yu başlatarak Başlangıç tarihi:

   ![Visual Studio için Mac ekran görüntüsü](media/extending-visual-studio-mac-addin3.png)

2. Yükleme _eklenti Oluşturucu uzantı paketi_ Uzantı Yöneticisi'ni kullanarak. Visual Studio menüsünden **uzantıları...** :

   ![Eklenti Yöneticisi sekmesi](media/extending-visual-studio-mac-addin4.png)

3. Galeri sekmesini türü gidip `Addin Maker` sağ üst kısmında arama çubuğuna. Eklenti Oluşturucu eklenti geliştirme kategori seçip tıklayın <kbd>yükleme</kbd>. Hiçbir şey gösterir, Yenile'ye tıklıyorum ve tekrar arama yapın:

   ![Eklenti Yöneticisi](media/extending-visual-studio-mac-addin5.png)

4. Eklenti Oluşturucu artık yüklendiğine göre bir uzantı paketi oluşturmaya başlayabilirsiniz. Yeni bir çözüm oluşturmaya başlayın.

5. Gelen **yeni çözümün iletişim kutusunu**, seçin **diğer > Diğer > Genel > Xamarin Studio eklentisi > C#** şablon ve aşağıdaki ekranda yeni çözümünü arlandırın `DateInserter`:

   ![Yeni bir çözüm oluşturma](media/extending-visual-studio-mac-addin7New.png)

6. Mac için Visual Studio, yeni bir çözüm doldurulur:

   ![Doldurulmuş bir çözüm](media/extending-visual-studio-mac-addin8.png)

7. Şablon Kodu Kaldır `Manifest.addin.xml` aşağıdakiyle değiştirin:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Şimdi tarih ve saati bir metin düzenleyiciye ekleme yönetilir dosyaları ayarlamanız gerekir. Proje düğümüne sağ tıklayın ve yeni bir dosya ekleyin. Seçin **genel > boş sınıf** ve yeni dosya adı *InsertDateHandler*:

   ![Tarih işleyicisi Ekle](media/extending-visual-studio-mac-addin9.png)

9. Şimdi şablonu koddan kaldırdığınızdan `InsertDateHandler.cs` aşağıdaki kodla değiştirin:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Biz bu yer tutucu yöntemlerden daha sonra genişletin.

10. Sağ **DateInserter** proje ve select **Ekle > yeni dosya**. Seçin **genel > boş bir sabit listesi**ve yeni dosya adı *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Ekleme `InsertDate` komut yeni bir numaralandırmada olarak `DateInserterCommands.cs` dosyası:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. Bu noktada, bir çalışma uzantı paketi gerekir. Teslim çalışmanızı kaydetme ve uygulama çalıştırarak test edebilirsiniz. IDE, yeni uzantı paketi yüklü Mac için Visual Studio'nun yeni bir örneğini başlatır. İçin giderseniz **Düzenle menüsü**, Mac için Visual Studio adlı yeni bir seçenek olduğunu göreceksiniz **tarih Ekle**ekran aşağıda gösterildiği gibi:

    ![Tarih komutu ekleme](media/extending-visual-studio-mac-addin11.png)

    Geçerli uygulama yalnızca yer tutucu yöntemleri olarak tarih Ekle menüden etkisi olduğuna dikkat edin.

13. Uzantı paketi için yerinde bir çerçeve olan ve güç katan tarihi ekleme kodu yazmak için zamanı. İlk olarak, şundan emin olun **Ekle tarih komutu** kullanıcının dosya değiştirerek açık bir metin olduğunda yalnızca etkin `Update` yönteminde `InsertDateHandler.cs` aşağıdaki kod ile:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Komut güncelleştirme `Run` yöntemi tarih ve saat ile aşağıdaki kodu ekleyin:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Son olarak, test etmek için sunduğumuz uzantı paketi çalıştıralım. Mac için Visual Studio yeni örneğini seçin **Düzenle > tarih Ekle**. Geçerli tarih ve saat ekran aşağıda gösterildiği gibi bizim giriş işareti eklenir:

    ![Tarih ekran görüntüsü Ekle](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İlk uzantınızı (Windows için Visual Studio) oluşturma](/visualstudio/extensibility/extensibility-hello-world)