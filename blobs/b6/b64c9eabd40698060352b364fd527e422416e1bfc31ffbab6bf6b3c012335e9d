#!/bin/bash
while IFS= read -r -d $'\0' f; do
        hash=$(sha256sum "$f" |awk '{print $1;}')
        echo $f: $hash $(du -b "$f" |awk '{print $1;}')
        if [ -n "$1" ]; then
                out="$1/blobs/${hash:0:2}/$hash"
                mkdir -p $(dirname "$out")
                cp "$f" "$out"
        fi
done < <(ag --search-binary -l -0)
read
