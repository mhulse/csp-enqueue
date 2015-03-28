# Enqueue

### The `<custom:rg:enqueue>` [RULE](http://docs.intersystems.com/cache20091/csp/docbook/DocBook.UI.Page.cls?KEY=GCSP_customtags) inserts the content contained in the start and end tags into the `<head>` or `<body>` of the document.

Inspired by WordPress' [`wp_enqueue_script()`](http://codex.wordpress.org/Function_Reference/wp_enqueue_script).

---

#### FEATURES

* Prevents duplicate content from being inserted into a section.
* Ability to control the positioning of content using a numeric value.

---

#### USAGE

Insert `...CONTENT...` into `<head>` right before the closing `</head>` tag:

```html
<custom:rg:enqueue>...CONTENT...</custom:rg:enqueue>
```

Insert `...CONTENT...` into `<body>` right before the closing `</body>` tag:

```html
<custom:rg:enqueue body>...CONTENT...</custom:rg:enqueue>
```

Insert `...CONTENT...` into `<body>` right after the opening `<body>` tag:

```html
<custom:rg:enqueue body="-1">...CONTENT...</custom:rg:enqueue>
```

---

#### ATTRIBUTES

1. `head`: Insert content into the `<head>` of the document.
2. `body`: Insert content into the `<body>` of the document.
3. `uglify`: Trim leading/trailing spaces; remove horizontal tabs, line feeds and carriage returns.

If both `head` and `body` attributes aren't defined, then attribute `head` is used by default.

Both `head` and `body` attributes accept a numeric value which is used to relatively position the content within the [section](http://docs.intersystems.com/cache20091/csp/docbook/DocBook.UI.Page.cls?KEY=RCSP_CSP_SECTION); a negative number is the beginning of a section and a positive number is the end of a section. The default value is `1`.

**Note:** The `uglify` attribute doesn't (currently) take any arguments.

---

#### EXAMPLES

**Before:**

```html
<!doctype html>
<html>
<head>
</head>
<body>
<custom:rg:enqueue body uglify>
	<script type="text/javascript" src="http://rgweb.slideshowpro.com/m/embed.js"></script>
	<script type="text/javascript">
		SlideShowPro({
			attributes: {
				id: "album-363953",
				width: 550,
				height: 400
			},
			mobile: {
				auto: false
			},
			params: {
				bgcolor: "#000000",
				allowfullscreen: true
			},
			flashvars: {
				xmlFilePath: "http://rgweb.slideshowpro.com/images.php?album=363953"
			}
		});
	</script>
</custom:rg:enqueue>
<div id="album-363953"></div>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi lobortis elit dapibus eros ornare et venenatis turpis fermentum. Integer dictum, ipsum a dapibus gravida, arcu lorem blandit eros, sit amet commodo est sapien in velit. In hac habitasse platea dictumst. Sed lorem tortor, cursus accumsan iaculis sit amet, gravida eu nisl. Suspendisse potenti. Quisque in bibendum mauris. Pellentesque aliquet, velit eu congue placerat, metus nibh ornare neque, et lacinia libero odio at nunc. Curabitur lobortis consequat purus nec vulputate. Integer condimentum ullamcorper dictum. Nam eget nulla tortor. In eros nisl, lacinia ac ultrices ac, pulvinar vitae mi. Sed luctus, ipsum eu mollis venenatis, massa leo hendrerit elit, non dignissim lorem risus at quam. Curabitur cursus tincidunt nibh, at egestas nisl tempus ut. Cras condimentum dui a leo sodales vehicula.</p>
</body>
</html>
```

**After:**

```html
<!doctype html>
<html>
<head>
</head>
<body>
<div id="album-363953"></div>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi lobortis elit dapibus eros ornare et venenatis turpis fermentum. Integer dictum, ipsum a dapibus gravida, arcu lorem blandit eros, sit amet commodo est sapien in velit. In hac habitasse platea dictumst. Sed lorem tortor, cursus accumsan iaculis sit amet, gravida eu nisl. Suspendisse potenti. Quisque in bibendum mauris. Pellentesque aliquet, velit eu congue placerat, metus nibh ornare neque, et lacinia libero odio at nunc. Curabitur lobortis consequat purus nec vulputate. Integer condimentum ullamcorper dictum. Nam eget nulla tortor. In eros nisl, lacinia ac ultrices ac, pulvinar vitae mi. Sed luctus, ipsum eu mollis venenatis, massa leo hendrerit elit, non dignissim lorem risus at quam. Curabitur cursus tincidunt nibh, at egestas nisl tempus ut. Cras condimentum dui a leo sodales vehicula.</p>
<script type="text/javascript" src="http://rgweb.slideshowpro.com/m/embed.js"></script><script type="text/javascript">SlideShowPro({attributes: {id: "album-363953",width: 550,height: 400},mobile: {auto: false},params: {bgcolor: "#000000",allowfullscreen: true},flashvars: {xmlFilePath: "http://rgweb.slideshowpro.com/images.php?album=363953"}});</script>
</body>
</html>
```

**Before:**

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Testing enqueue</title>
<meta name="description" content="">
<meta name="keywords" content="">
</head>
<body>
<custom:rg:enqueue><script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script></custom:rg:enqueue>
<custom:rg:enqueue><script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script></custom:rg:enqueue>
<custom:rg:enqueue><script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script></custom:rg:enqueue>
<custom:rg:enqueue body><script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.9.0/jquery-ui.min.js"></script></custom:rg:enqueue>
<custom:rg:enqueue body><script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.9.0/jquery-ui.min.js"></script></custom:rg:enqueue>
<p>Ut a urna non lectus fermentum molestie id a sapien. Donec non dictum nulla. Aliquam gravida eleifend nisl sed consectetur. Pellentesque et varius neque. Aliquam eu eros est. Proin sed nibh nec neque adipiscing lacinia et eu ante. Suspendisse porta vehicula orci sit amet posuere. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Suspendisse euismod ipsum at eros fringilla elementum. Quisque eu leo arcu, tempus sodales tellus. Phasellus eleifend arcu ac est volutpat aliquam. Donec egestas, tortor eu mollis iaculis, est metus commodo mi, non semper enim metus dignissim augue. Sed auctor sollicitudin purus, id volutpat risus iaculis vitae. Suspendisse sodales tristique vestibulum. Nam purus turpis, convallis at consequat a, malesuada eu orci. Sed euismod posuere augue a scelerisque.</p>
</body>
</html>
```

**After:**

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Testing enqueue</title>
<meta name="description" content="">
<meta name="keywords" content="">
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
</head>
<body>
<p>Ut a urna non lectus fermentum molestie id a sapien. Donec non dictum nulla. Aliquam gravida eleifend nisl sed consectetur. Pellentesque et varius neque. Aliquam eu eros est. Proin sed nibh nec neque adipiscing lacinia et eu ante. Suspendisse porta vehicula orci sit amet posuere. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Suspendisse euismod ipsum at eros fringilla elementum. Quisque eu leo arcu, tempus sodales tellus. Phasellus eleifend arcu ac est volutpat aliquam. Donec egestas, tortor eu mollis iaculis, est metus commodo mi, non semper enim metus dignissim augue. Sed auctor sollicitudin purus, id volutpat risus iaculis vitae. Suspendisse sodales tristique vestibulum. Nam purus turpis, convallis at consequat a, malesuada eu orci. Sed euismod posuere augue a scelerisque.</p>
<script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.9.0/jquery-ui.min.js"></script>
</body>
</html>
```

**See also:** [`test.csp`](https://github.com/mhulse/csp-enqueue/blob/master/enqueue/test.csp).

---

#### INSTALLATION

For us DTI customers, there's a couple ways (that I can think of) to install this code:

### Copy/paste:

1. "File" >> "New..." and choose "Caché Server Page" from "CSP File" tab.
2. Copy/paste the **RAW** contents of `custom.rg.EnqueueRule.csr` into this new file.
9. Save this file as `custom.rg.EnqueueRule.csr` to the "CSP Files" >> `/csp/cms/customrules` package/folder/location.
10. Compile.

### Import local:

1. Download and unzip this repo to your local machine.
2. Open Studio.
3. Change to the `CMS` namespace.
4. "Tools" >> "Import Local...".
5. Import `custom.rg.EnqueueRule.csr` and check the compile box.

---

#### NOTES

Non-[DTI](http://www.dtint.com/) customers should emove these lines from `custom.rg.EnqueueRule.csr`:

```
<csr:class super="dt.common.page.Rule" />
```

```
<script language="cache" runat="compiler">
	do ##this.RenderDTStartTag()
</script>
```

```
<script language="cache" runat="compiler">
	do ##this.RenderDTEndTag()
</script>
```

---

#### DISCUSSION(S)

* [[RULE] How to track, and compare, previous RULE matches to the current RULE match?](https://groups.google.com/d/topic/intersystems-public-cache/kZ5CJdjSuQU/discussion)
* [In need of CSR rule advice](https://groups.google.com/d/topic/intersystems-public-cache/rhaOntJQWGA/discussion)

---

#### LEGAL

Copyright © 2012 [Micky Hulse](http://mky.io)/

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
