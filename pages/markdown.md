---
title: Markdown
---

## Kramdown

### Block attributes (like classes)

```
[home](/)
{: .class1 #id2}
```
|
```
<p class="class1" id="id2"><a href="/">home</a></p>
```

### Manual line breaks

Add line breaks with two spaces or two backslashes at the end of a line.

Markdown (underscore for space):

```
Line__
break.
```

HTML:

```
<p>Line<br />
break.</p>
```

Markdown:

```
Line\\
break.
```

HTML:

```
<p>Line<br />
break.</p>
```

