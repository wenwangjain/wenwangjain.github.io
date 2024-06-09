---
title: 1. 基础内容
weight: 111
#next: /step1
#prev: /docs
editURL: "https://example.com/edit/this/page"
toc: true
---



## good

\




测试


```python  {linenos=table   ,linenostart=1,filename="hello.py"}
import pandas as pd

class hugo:
    def alter_file(path, folder, file, content):
        import os

        path_folder = os.path.join(path, folder)
        path_file   = os.path.join(path, folder, file)

        if folder in os.listdir(path):
            with open(path_file, 'w', encoding='utf-8') as f:
                f.write(content)
        else:
            os.mkdir(path_folder)
            with open(path_file, 'w', encoding='utf-8') as f:
                f.write(content)
```
<br><br>




<br><br><br>



## 标题

Hugo 从 Hugo 网站根目录下的 hugo.yaml 读取配置。 在配置文件中，您可以配置站点的所有选项。 你可以在 exampleSite/hugo.yaml 中找到此站点的配置文件作为开始。<br>
Hugo 从 Hugo 网站根目录下的 hugo.yaml 读取配置。 在配置文件中，您可以配置站点的所有选项。 你可以在 exampleSite/hugo.yaml 中找到此站点的配置文件作为开始。



## 右侧边栏 
### 目录 
目录是根据内容文件中的标题自动生成的，可以在 front matter 设置 toc：false 来禁用它。




<br><br><br><br>




<div style="display: flex; justify-content: center;">

<div style="flex: 20%; padding: 10px; box-sizing: border-box; text-align: center;">
你的文本内容...<br><br>{{< hextra/hero-button text="教程" link="docs" >}}
</div>

<div style="flex: 20%; padding: 10px; box-sizing: border-box; text-align: center;">
你的文本内容...<br><br>{{< callout emoji="🎨" type="info" link="docs">}}
  请访问 GitHub 查看最新版本  
{{< /callout >}}
</div>

<div style="flex: 20%; padding: 10px; box-sizing: border-box; text-align: left;">
{{< card link="/docs/ai" title="Callout" subtitle="你的文本内容" icon="warning" >}}
</div>
<div style="flex: 20%; padding: 10px; box-sizing: border-box; text-align: left;">
{{< card link="/docs/ai" title="Callout" subtitle="你的文本内容" icon="warning" >}}
</div>
<div style="flex: 20%; padding: 10px; box-sizing: border-box; text-align: left;">
{{< card link="/docs/ai" title="Callout" subtitle="你的文本内容" icon="warning" >}}
</div>

</div>






{{< cards >}}
  {{< card link="../callout" title="Callout" icon="warning" >}}
  {{< card link="/" title="No Icon" >}}
{{< /cards >}}



{{< tabs items="JSON,YAML,TOML" >}}

  {{< tab >}}**JSON**: JavaScript Object Notation (JSON) is a standard text-based format for representing structured data based on JavaScript object syntax.{{< /tab >}}
  {{< tab >}}**YAML**: YAML is a human-readable data serialization language.{{< /tab >}}
  {{< tab >}}**TOML**: TOML aims to be a minimal configuration file format that's easy to read due to obvious semantics.{{< /tab >}}

{{< /tabs >}}







{{< callout emoji="⚠" >}}
  请访问 GitHub 查看最新版本
{{< /callout >}}


{{< callout  >}}
  请访问 GitHub 查看最新版本
{{< /callout >}}

{{< callout emoji="🎨" type="info" >}}
  请访问 GitHub 查看最新版本
{{< /callout >}}

{{< cards >}}
  {{< card link="../callout" title="Callout" subtitle="这里是一个测试" icon="warning" >}}
  {{< card link="/" title="No Icon" >}}
  {{< card link="/" title="No Icon" >}}
  {{< card link="/" title="No Icon" >}}
  {{< card link="/" title="No Icon" >}}
{{< /cards >}}

<br>



{{< hextra/hero-button text="教程" link="docs" >}}
{{< hextra/hero-button text="教程" link="docs" >}}
{{< hextra/hero-button text="教程" link="docs" >}}
{{< hextra/hero-button text="教程" link="docs" >}}
{{< hextra/hero-button text="教程" link="docs" >}}
