# ffmpeg file frome remote host

Scanario

You have you favorite TV-show (e.g. Babylon 5) on DVD and you want to transcode `.vob` -> `.mp4`

You probably want to use more than one computer to transcode those `.vob`'s

## vob's in remote host

### Use local ffmpeg to transcode remote file and save mp4 locally

We use Linux/Unix build-in STDIN to get the file from another host. And make so called Unix-glue with `ssh` and `ffmpeg`.

```
ssh <user@remote_host> 'cat <path_to_vob-file.OriginalDVD.vob>' | ffmpeg -i - -c:v libx264 -c:a ac3 output.mp4
```

`-` means that it get `STDIN` (input) from `ssh <user@remote_host> 'cat <path_to_vob-file.OriginalDVD.vob>'`

We save outputfile to current local host. In same computer, where ffmpeg is located.
