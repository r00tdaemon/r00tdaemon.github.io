---    
layout: post
title: "Recon tips by tomnomnom"
date: 2019-06-27
lead: "Notes from https://www.youtube.com/watch?v=l8iXMgk2nnY by STÖK"    
---

## Notes from [this video](https://www.youtube.com/watch?v=l8iXMgk2nnY) by STÖK

Enumerate subdomains -  
`assetfinder --subs-only <domain> > domains`

`httprobe` takes list of domains as input and outputs if http(s) server is listening. We pipe the output to tee command to see the output and write to file at the same time.  
`cat domains | httprobe | tee hosts`

Meg is used to fetch many paths for many hosts. [https://github.com/tomnomnom/meg](https://github.com/tomnomnom/meg)  
`meg -d 1000 -v /`

In the output dir of meg. `H` is for displaying file name in the output. `n` displays the line no. `r` recursive. `i` case-insensitive  
`grep -Hnri <host> * | vim -`

Sort and filter unique results  
`%! sort -u`

Remove unnecessary detail  
`%! grep -v Content-Sec`

Use gf to find common patterns like aws keys [https://github.com/tomnomnom/gf](https://github.com/tomnomnom/gf)   
`gf aws-keys`  
`gf base64 | vim -`  
`%!awk -F':' '{print $3}'`  
`:%s/<search>/<replace/`  
`:%!xargs -n1 -I{} sh -c 'echo {} | base64 -d'`  

Finding specific html tags/attribs using html-tool  
`find . -type f | html-tool attribs src`  

One liner to find `pattern` in all of the git repo  
`{ find .git/objects/pack/ -name "*.idx"|while read i;do git show-index < "$i"|awk '{print $2}';done;find .git/objects/ -type f|grep -v '/pack/'|awk -F'/' '{print $(NF-1)$NF}'; }|while read o;do git cat-file -p $o;done|grep -E 'pattern'`


