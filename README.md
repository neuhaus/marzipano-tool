# Marzipano Tool

from https://www.marzipano.net/tool

Downloaded using the following commands:

```console
wget -w 1 -m https://www.marzipano.net/tool/ https://www.marzipano.net/tool/template/files.json -I /tool/
find . -name '*\?*' | while read -r file; do
  mv -v "$file" "${file%%\?*}"
done

cd www.marzipano.net/tool/template
jq -r '.[]' files.json | while read file; do
  mkdir -p "$(dirname "$file")"
  wget -O "$file" "https://www.marzipano.net/tool/template/$file"
  sleep 1
done
```
