## hugo-mod-mermaidjs

[mermaid-js/mermaid] packaged as a Hugo Module ([Hugo Modules]).

[mermaid-js/mermaid]: https://github.com/mermaid-js/mermaid
[Hugo Modules]: https://gohugo.io/hugo-modules


## Usage

To enable this module you must add the following parameters to your `config/_default/config.yaml`:

```yaml
module:
  imports:
    - path: github.com/peaceiris/hugo-mod-mermaidjs
```

If this is the first time you are using Hugo modules you need to prepare your setup by installing Go, initializing your modules and more. Please refer to the [official Hugo Documentation](https://gohugo.io/hugo-modules/use-modules/) to complete these steps.


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
