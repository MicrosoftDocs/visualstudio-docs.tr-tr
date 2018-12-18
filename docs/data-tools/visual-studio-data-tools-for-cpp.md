---
title: C++ için veri araçları
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4c247d693da287581b8ab163880e9cecf4aeb17c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304934"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ için Visual Studio veri araçları

Veri kaynaklarına erişirken yerel C++ genellikle en hızlı performans sağlar. Ancak, veri Visual Studio'da C++ uygulamaları için Araçlar, .NET uygulamaları için olduğu gibi zengin değil. Örneğin, **veri kaynakları** penceresi, sürükle ve bırak C++ tasarım yüzeyine veri kaynakları için kullanılamaz. Bir nesne ilişkisel katmanı gerekiyorsa, kendi yazmak veya bir üçüncü taraf ürün kullanım gerekecektir. Microsoft Foundation Class kitaplığını kullanan uygulamaları bellekte veri depolamak ve kullanıcıya göstermek için belgeler ve görünümler, birlikte bazı veritabanı sınıfları kullanabilirsiniz, ancak aynı veri bağlama işlevselliği için geçerlidir. Daha fazla bilgi için [Visual C++'da veri erişimi](/cpp/data/data-access-in-cpp).

SQL veritabanlarına bağlanmak için yerel C++ uygulamaları, ODBC ve OLE DB sürücüleri ve Windows ile birlikte ADO sağlayıcıyı kullanabilirsiniz. Bunlar, bu arabirimleri destekleyen herhangi bir veritabanına bağlanabilirsiniz. ODBC sürücüsü standardıdır. OLE DB, geriye dönük uyumluluk için sağlanır. Bu veri teknolojileri hakkında daha fazla bilgi için bkz. [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

SQL Server 2005'te özel işlevsellikten yararlanmak ve daha sonra kullanmak üzere [SQL Server yerel istemcisi](/sql/relational-databases/native-client/sql-server-native-client). Yerel istemci ayrıca SQL Server ODBC sürücüsünü ve SQL Server OLE DB sağlayıcısı bir yerel dinamik bağlantı kitaplığı (DLL) içerir. Bu, Microsoft SQL Server için yerel kodlu API'ler (ODBC, OLE DB ve ADO) kullanan uygulamaları destekler. SQL Server veri araçları ile SQL Server Native Client yükler. Programlama Kılavuzu aşağıda verilmiştir: [programlama SQL Server yerel istemcisi](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Bir C++ uygulamasından localDB ODBC ve SQL Native Client aracılığıyla bağlanmak için

1. SQL Server veri Araçları'nı yükleyin.

2. Örnek SQL veritabanına bağlanmak için gerekiyorsa, Northwind veritabanı indirin ve yeni bir konuma sıkıştırmasını açın.

3. Sıkıştırması açılmış eklemek için SQL Server Management Studio'yu kullanın *Northwind.mdf* localDB dosyasına. SQL Server Management Studio başlatıldığında (localdb) \MSSQLLocalDB bağlanın.

   ![İletişim SSMS bağlanma](../data-tools/media/raddata-ssms-connect-dialog.png)

   Ardından localdb düğümü sol bölmede sağ tıklatın ve seçin **iliştirme**.

   ![Veritabanını SSMS ekleyin](../data-tools/media/raddata-ssms-attach-database.png)

4. ODBC Windows SDK örneği indirin ve yeni bir konuma sıkıştırmasını açın. Bu örnek, bir veritabanı ve çıkış sorguları ve komutları bağlanmak için kullanılan temel ODBC komutları gösterir. Bu işlevler hakkında daha fazla bilgi [Microsoft açık veritabanı bağlantısı (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). (Bu, C++ klasöründe bulunur) çözümü ilk kez yüklediğinizde, Visual Studio çözümü Visual Studio'nun geçerli sürümüne yükseltme olanağı sunar. **Evet**'i tıklayın.

5. Yerel istemci kullanmak için gerekir, *üstbilgi* dosya ve *LIB* dosya. Bu dosyalar, İşlevler ve sql.h içinde tanımlanan ODBC işlevleri ötesinde SQL Server'a özel tanımları içerir. İçinde **proje** > **özellikleri** > **VC ++ dizinleri**, aşağıdakileri içeren dizin ekleyin:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Ve bu kitaplık dizini:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Bu satırları ekleyin *odbcsql.cpp*. #Define ilgisiz OLE DB tanımları derlenen engeller.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Önceki adımlarda, derlemek ve çalıştırmak için gerekli değildir. Bu nedenle örnek gerçekten yerel istemci işlevleri kullanımda bulunmadığını unutmayın. Ancak, proje artık bu işlevselliği kullanmak için yapılandırılır. Daha fazla bilgi için [SQL Server Native Client programlama](/sql/relational-databases/native-client/sql-server-native-client).

7. ODBC alt sistemi kullanmak üzere hangi sürücüyü belirtin. Örnek sürücü bağlantı dizesi özniteliği, bir komut satırı bağımsız değişkeni geçirir. İçinde **proje** > **özellikleri** > **hata ayıklama**, bu komut bağımsız değişkeni ekleyin:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. Sürücüsünden bir veritabanı girmenizi isteyen bir iletişim kutusu görmeniz gerekir. Girin `(localdb)\MSSQLLocalDB`ve **güvenilir bağlantı kullan**. Tuşuna **Tamam**. Başarılı bir bağlantı iletileri konsoluyla görmeniz gerekir. Ayrıca SQL deyiminde girebileceğiniz bir komut istemini görmeniz gerekir. Aşağıdaki ekranda bir örnek sorgu ve sonuçları gösterir:

   ![ODBC örnek sorgu çıktısı](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)