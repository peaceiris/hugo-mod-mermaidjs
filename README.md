## hugo-mod-mermaidjs

[mermaid-js/mermaid] packaged as a Hugo Module ([Hugo Modules]).

[mermaid-js/mermaid]: https://github.com/mermaid-js/mermaid
[Hugo Modules]: https://gohugo.io/hugo-modules


## Usage

`config/_default/config.yaml`

```yaml
module:
  imports:
    - path: github.com/peaceiris/hugo-mod-mermaidjs
```

In a Hugo template file.

```html
{{ $js := resources.Get "mod/mermaidjs/mermaid.min.js" }}
{{ $secureJS := $js | resources.Fingerprint "sha512" }}
<script src="{{ $secureJS.Permalink }}" integrity="{{ $secureJS.Data.Integrity }}"></script>
<script>
  var config = {
    startOnLoad: true,
    flowchart: {
      useMaxWidth: true,
      htmlLabels: true,
      curve: "cardinal",
    },
    theme: "neutral",
    securityLevel: "strict",
  };

  mermaid.initialize(config);
</script>
```
