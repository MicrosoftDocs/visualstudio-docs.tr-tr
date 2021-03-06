---
title: Devinit ile çalışmaya başlama
description: Devınit için Başlarken Kılavuzu.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 660bb5a2c3d235a347e478d55ae8176e87c5d626
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672483"
---
# <a name="getting-started-with-devinit"></a>Devinit ile çalışmaya başlama

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

devinit, basit bir komut çalıştırarak, herkesin koda almasını ve deponuzda üretken olmasını sağlamak için kullanabileceğiniz bir araçtır. Deponuzda SQL Server, Node.js, Docker veya IIS gibi bir şeyler için gereken tüm sistem genelinde bağımlılıkları tanımlamak için devinit kullanabilirsiniz. Devinit, deponuzu yüklemek için diğer araçları ve paket yöneticilerini çağırabilir. Bu bağımlılıkları [ üzerinde.devinit.js](devinit-json.md) ADLı bir JSON dosyasında tanımlarsınız ve sonra deponuzu kullanmak için bir sonraki kişinin yalnızca [`devinit init`](devinit-commands.md#init) Tüm bu bağımlılıkları yüklemek üzere çalıştırması gerekir. Bu nedenle, yeni bir depoya bir gün sonra ekleme yapmak yerine dakikalar içinde yapılabilir.

devinit, ve ' de bir paket yöneticisi veya bir sanal makine (VM) yapılandırma aracı değil. Bu, uygulamanızın ihtiyaç duyacağı sistem genelinde bağımlılıkları tanımlayan [.devinit.json](devinit-json.md)adlı bir bildirim dosyası için görev Çalıştırıcısı. Bu bağımlılıkları yüklemek için devinit, [Chocolatey](https://chocolatey.org)gibi zaten kullanmakta olabileceğiniz araçları kullanır. Kullanılabilen araçları [tam listede](devinit-tool-list.md)inceleyebilirsiniz. Devinit, yazılımın doğrudan dağıtılması yerine bu araçları kullanarak tercih ettiğiniz aracı kullanmanın rahatlığını sağlar ve var olan konfigürasyonları (örneğin, Chocolatey için bir [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) dosyası) kullanmanıza olanak tanır.  

## <a name="step-1-get-devinit"></a>1. Adım: devinit al

devinit Şu anda yalnızca Visual Studio kullanılırken GitHub Codespaces 'ın bir parçası olarak kullanılabilir ve Visual Studio 'daki tümleşik terminalden erişilebilir. Daha sonra devinit, Visual Studio 'nun bir parçası olarak kullanılabilir olacaktır.

## <a name="step-2-define-your-environment"></a>2. Adım: ortamınızı tanımlama

En önemli adım, ' geliştirme ' ortamınızı [ dosyadaki bir.devinit.js](devinit-json.md)tanımlamaktır. Bu dosya, çalıştırdığınızda ortamınızı oluşturmak için devinit tarafından kullanılacaktır `devinit init` .

Bu adım için, bir projeyi bir proje deposu ile çalışmaya ve çalıştırmaya verdiğiniz yönergeleri düşünün. Örneğin, SQL 'in yüklü olması gerekir mi? .NET Core 'un belirli bir sürümü mi? Etki alanları bu hiyerarşi sıralamasıyla devam eder. Ardından, bu bağımlılıkların her biri için, [Araçlar listesinde](devinit-tool-list.md) ilgili devinit aracına bakın ve bunu deponun `.devinit.json` dosyasına ekleyin.

Örnekler [belgelerinde](sample-readme.md)örnek seçimini de görebilir veya [öğreticiye](tutorial.md)göz atın.

## <a name="step-3-enjoy"></a>3. Adım: keyfini çıkarın!

Şimdi, deponuzu kopyaladıktan sonra tüm birisinin yapması gerekiyor `devinit init` .

```console
devinit init
```

[GitHub Codespaces](https://github.com/features/codespaces)kullanıyorsanız, `devinit init` codespace sağlandığında otomatik olarak çalışacak şekilde yapılandırabilirsiniz. Daha fazla bilgi edinmek için [devinit ve GitHub Codespaces belgelerine](devinit-and-codespaces.md)göz atın.
