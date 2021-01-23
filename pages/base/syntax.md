#define:#slidedeck
Parents: #root
Styles: 
  - revealjs/dist/reveal.css
Scripts:
  - revealjs/dist/reveal.js
  
<div class="reveal">
<div class="slides">
{{.Content}}
</div></div>

#define:#slide
Parents: #slidedeck
Counter: slide
ResetCounters: subslide

<section{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{block "slide-start" .}}{{end}}
{{.Content}}
{{block "slide-end" .}}{{end}}
</section>

#define:#stack
Parents: #slidedeck
Counter: slide
ResetCounters: subslide

<section{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{.Content}}
</section>

#define:#subslide
Parents: #stack
Counter: subslide

<section{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{block "slide-start" .}}{{end}}
{{.Content}}
{{block "slide-end" .}}{{end}}
</section>

#define:#
Parents:
  - #slide
  - #subslide
FirstChild: true
Parenthood: indent

<div class="mates-head">
<h1{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{.Text}}
</h1>
{{.RemainingContent}}
</div>

#define:#title
Parents:
  - #slide
  - #subslide
FirstChild: true
Parenthood: indent

<div class="mates-title">
<h1{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{.Text}}
</h1>
{{.RemainingContent}}
</div>

#define:#author
Parents:
  - #slide
  - #subslide
Parenthood: root

<div class="mates-author">
<div{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>{{.Text}}</div>{{.RemainingContent}}</div>

#define:#multicol
Parents:
  - #slide
  - #subslide

<div class="mates-multicol">{{.Content}}</div>

#define:#column
Parents: #multicol
Parenthood: root

<div{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="mates-col {{.Class}}"{{else}} class="mates-col"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{.Content}}
</div>

#define:#main
Parents:
  - #slide
  - #subslide
Parenthood: default-root

<div {{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="mates-main {{.Class}}"{{else}} class="mates-main"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>
{{.Content}}
</div>

#define:#code
DefaultAttrib: class
Mode: code
Styles: revealjs/plugin/highlight/monokai.css
Scripts: revealjs/plugin/highlight/highlight.js
Parenthood: text

<pre><code data-trim data-noescape{{if .ID}} id="{{.ID}}"{{end}}{{if .Class}} class="{{.Class}}"{{end}}{{if .Style}} style="{{.Style}}"{{end}}>{{.Content}}</code></pre>