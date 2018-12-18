---
title: '&lt;PackageFiles&gt; öğesi (Önyükleyici) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84451a90e316a98a9998e1a64e68a72668bd4781
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813771"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; öğesi (Önyükleyici)
`PackageFiles` Ögesinin `PackageFile` sonucu olarak çalıştırılan yükleme paketleri tanımlayan öğeleri `Command` öğesi.  

## <a name="syntax"></a>Sözdizimi  

```xml  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `PackageFiles` Öğesi aşağıdaki özniteliklere sahiptir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|İsteğe bağlı. Varsa kümesine `false`, yükleyici yalnızca öğesinden başvurulan dosyaları indirir `Command` öğesi. Varsa kümesine `true`, tüm dosyalar indirilir.<br /><br /> Varsa kümesine `IfNotHomesite`, yükleyici aynı davranış göstereceği gibi `False` varsa `ComponentsLocation` ayarlanır `HomeSite`ve aksi takdirde aynı davranış göstereceği gibi `True`. Bu ayar, kendileri paketleri HomeSite senaryosunda kendi davranışı önyükleyici vermesini sağlamak da yararlı olabilir.<br /><br /> Varsayılan, `true` değeridir.|  

## <a name="packagefile"></a>PackageFile  
 `PackageFile` Öğesi alt öğesi olan `PackageFiles` öğesi. A `PackageFiles` öğesi en az bir olmalı `PackageFile` öğesi.  

 `PackageFile` Aşağıdaki özniteliklere sahiptir.  


| Öznitelik | Açıklama |
|---------------| - |
| `Name` | Gerekli. Paket dosyasının adı. Bu addır, `Command` öğesi, bir paket yükleyen koşullarını tanımlayan olduğunda başvuracağı. Bu değer aynı zamanda bir anahtar olarak kullanılan `Strings` gibi araçlar yerelleştirilmiş adı almak için tablo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paketi tanımlamak için kullanır. |
| `HomeSite` | İsteğe bağlı. Uzak sunucuda yükleyiciyi dahil edilmezse paketinin konumu. |
| `CopyOnBuild` | İsteğe bağlı. Önyükleyici paket dosyası diske oluşturma zamanında kopyalama olup olmadığını belirtir. Varsayılan değer True'dur. |
| `PublicKey` | Paketin sertifikayı imzalayan şifrelenmiş ortak anahtarı. Gerekli if `HomeSite` kullanılan, isteğe bağlı; Aksi takdirde. |
| `Hash` | İsteğe bağlı. Paket dosyası bir SHA1 karması. Bu, yükleme sırasında dosya bütünlüğünü doğrulamak için kullanılır. Aynı karma paket dosyasından deltanın hesaplanamaması durumunda paketi yüklü değil. |

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için paketleri tanımlar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] yeniden dağıtılabilir paketi ve bağımlılıkları, Windows Installer gibi.  

```xml  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [\<Ürün > öğesi](../deployment/product-element-bootstrapper.md)   
 [\<Paket > öğesi](../deployment/package-element-bootstrapper.md)   
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)