---
title: 'CA2210: Derlemelerin geçerli tanımlayıcı adları olmalıdır | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1551cccb11fc33a21503e7030cfd671c953ee17d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865823"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Derlemelerin tanımlayıcı adı geçerli olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir derlemeyi tanımlayıcı bir ad ile imzalı değil, tanımlayıcı adı doğrulanamadı veya tanımlayıcı adı geçerli kayıt defteri ayarları bilgisayarın geçerli olmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, alır ve bir derlemenin tanımlayıcı adı doğrular. Aşağıdakilerden biri doğruysa bir ihlali oluşur:

- Derlemeyi tanımlayıcı bir ada sahip değil.

- Derleme imzalama sonra değiştirildi.

- Derleme gecikmeli imzalanmış.

- Derleme yanlış imzalı veya imzalama başarısız oldu.

- Derleme doğrulama geçirmek kayıt defteri ayarları gerektirir. Örneğin, tanımlayıcı ad Aracı (Sn.exe), derleme için doğrulama atlama için kullanıldı.

  Güçlü ad oynanmış derlemeyi bilmeden yükleyerek istemcileri korur. Güçlü adı olmayan derlemeler oldukça sınırlı sayıda senaryo dışında kullanılmamalıdır. Düzgün imzalanmamış derlemeleri paylaşırsanız veya dağıtırsanız, derleme aslı bozuabilir, ortak dil çalışma zamanı derlemeyi yükleyemeyebilir veya kullanıcı kendi bilgisayarındaki doğrulamayı devre dışı bırakabilir. Bir derlemeyi tanımlayıcı ad aşağıdaki dezavantajları vardır:

- Kendi kaynakları doğrulanamıyor.

- Ortak dil çalışma zamanı derlemenin içeriğini değiştirilmiş, kullanıcıları uyarın olamaz.

- Genel bütünleştirilmiş kod önbelleğine yüklenemiyor.

  Yüklenecek unutmayın ve gecikmeli imzalanmış bir bütünleştirilmiş kod çözümleme, derleme için doğrulama devre dışı bırakmanız gerekir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 **Bir anahtar dosyası oluşturmak için**

 Aşağıdaki yordamlardan birini kullanın:

- Tarafından sağlanan Assembly Linker (Al.exe) aracını [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- İçin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 veya v1.1, kullanın ya da <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> veya <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> özniteliği.

- İçin [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], hangisini `/keyfile` veya `/keycontainer` derleyici seçeneği [/keyfile (derlemeyi imzalamak için anahtar belirtin veya anahtar çiftini)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) veya  [ /keycontainer (derlemeyi imzalamak için bir anahtar kapsayıcısı belirtin)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) c++ bağlayıcı seçeneği).

  **Derlemenizi Visual Studio'da bir katı adla imzalamak için**

1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], çözümünüzü açın.

2. İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **özellikleri.**

3. Tıklayın **imzalama** sekmesine tıklayın ve **derlemeyi imzalamayı** onay kutusu.

4. Gelen **bir tanımlayıcı ad anahtar dosyası seç**seçin **yeni**.

    **Katı ad anahtarı oluştur** penceresinde gösterilir.

5. İçinde **anahtar dosya adını**, tanımlayıcı ad anahtarınız için bir ad yazın.

6. Anahtarı bir parolayla koruyun ve ardından isteyip istemediğinizi seçin **Tamam**.

7. İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **yapı**.

   **Derlemenizi Visual Studio dışında bir katı adla imzalamak için**

-   Tarafından sağlanan tanımlayıcı ad Aracı (Sn.exe) kullanan [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Derleme ortamında kullandıysanız yalnızca bu kuraldan bir uyarıyı bastırmak burada içeriğiyle oynama bir sorun değildir.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName><xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Nasıl yapılır: bir derlemeyi katı bir adla imzalamak](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (tanımlayıcı ad aracı)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)



