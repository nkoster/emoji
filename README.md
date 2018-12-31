Simple emoji translation function, but with quite a complete, Slack-like formatted, conversion to unicode.

Please add missing stuff, and create a pull request!

The base line comes from https://gist.github.com/rxaviers/7360908 with this awkward bash script:

```
#!/bin/bash

curl -s https://gist.github.com/rxaviers/7360908 | \
grep g-emoji | \
awk -F '>' '{
    alias=substr($2, index($2, "alias=\"")+7)
    alias=substr(alias, 0, index(alias,"\"")-1)
    printf("     .replace(\":%s:\", \"%s\")\n",alias, substr($3,0,index($3, "<")-1))
}'
```
