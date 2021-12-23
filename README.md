Very simple Thunar Custom Action zenity-GUI for ffmpeg.
---
> For very simple media conversion 

* Selection-dialog for filetypes, error-dialog and system notification on completion   
* Supports multiple selected files.
* Applies ffmpeg default settings for output container (filetype).

This code is slghtly modified from one or more original codesnippets found around the web, but the research was conducted in a frenzy and the sources are lost in time, like tears in rain

---

### Requirements
* Zenity
* Parallel
* notify-send
* FFmpeg

---

### "Install"

> Copy paste into the "command"-field when creating or editing a Thunar custom action
<br/> > Replace the "FILETYPES" (e.g. "mp4" to "mp3") to change ouput format 

---

### Code

filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="An error occurred!\n\nSO SAD!"; } ; fi

---

```
filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="An error occurred!\n\nSO SAD!"; } ; fi
```

