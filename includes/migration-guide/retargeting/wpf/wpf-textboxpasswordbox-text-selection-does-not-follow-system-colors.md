---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774000"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>WPF TextBox/PasswordBox 文本选择不遵循系统颜色

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.7.1 和更早版本中，WPF <code>System.Windows.Controls.TextBox</code> 和 <code>System.Windows.Controls.PasswordBox</code> 只能在装饰器层呈现文本选择。 在某些系统主题中，这会遮蔽文本，使其难以阅读。  在 .NET Framework 4.7.2 及更高版本中，开发人员可选择启用基于非装饰器的选择呈现方案，从而缓解此问题。|
|建议|开发人员若要利用此更改，必须正确设置以下 AppContext 标记。  若要利用此功能，已安装的 .NET Framework 必须是 4.7.2 或更高版本。若要启用基于非装饰器的选择，请使用以下 AppContext 标记。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|版本|4.7.2|
|类型|重定目标|
