---
layout: post
title:  "JavaScript Callbacks"
date:   2017-02-10 15:41:58 +0000
categories: JavaScript
---
You already know about JavaScript functions. You can call them, they execute and optionally return a result. For example, this function returns all permutations of a string:

{% highlight html %}
<html>
<script>
<html>

<body>
<ul id="list">
</ul>

<script>
var s = prompt("Enter a word", "test");
var p = permutations(s.toLowerCase());
for (var i = 0; i < p.length; i++) {
  addListItem(p[i]);
}

function permutations(chars) {
  var result = [];
  var c = Array.from(new Set(chars));
  if (c.length <= 1) {
    return [chars];
  }
  for (var i = 0; i < c.length; i++) {
    var rest = [];
    for (var j = 0; j < chars.length; j++) {
      if (chars[j] == c[i]) {
        rest = chars.slice(0, j) + chars.slice(j + 1);
        break;
      }
    }
    var p = permutations(rest);
    for (var j = 0; j < p.length; j++) {
      p[j] = c[i] + p[j];
      result.splice(-1, 0, p[j]);
    }
  }
  return result;
}

function addListItem(text) {
  var item = document.createElement("LI");
  var t = document.createTextNode(text);
  item.appendChild(t);
  document.getElementById("list").appendChild(item);
}
</script>

</body>
</html>
{% endhighlight %}
