---
title: "Burpdock"
slug: "Burpdock"
date: 2019-06-02
summary: "How to setup Burp Suite inside a docker container"
draft: false
---

## How to setup Burp Suite inside a docker container

First we create a new directory - `burpdock`
Inside the directory, create the following `Dockerfile`

<div class="not-prose">
<script src="https://gist.github.com/1181d442b2a92067b5f3f111d5b3b69e.js?file=Dockerfile"></script>
</div>

Then we create a build script. You can directly give the command but I personally like using a script to avoid giving all the args whenever I want a build a new version.

<div class="not-prose">
<script src="https://gist.github.com/1181d442b2a92067b5f3f111d5b3b69e.js?file=build"></script>
</div>

Make the script executable and run it

```
chmod +x build
./build
```

Finally make the `start` script to run the container.

{{< alert cardColor="#e63946" iconColor="#1d3557" textColor="#f1faee">}} **NOTE:** This may overwrite your existing burp settings. Make a backup `mv ~/.java/.userPrefs/burp/prefs.xml ~/.java/.userPrefs/burp/prefs.xml.bkp`
{{< /alert >}}

<div class="not-prose mt-4">
<script src="https://gist.github.com/1181d442b2a92067b5f3f111d5b3b69e.js?file=start"></script>
</div>

Make the script executable and run it

```
chmod +x start
./start
```

After that simply run - `burpsuite` and you will see it open
