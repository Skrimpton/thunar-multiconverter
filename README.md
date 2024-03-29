Very simple Thunar Custom Action zenity-GUI for ffmpeg.
---

```
filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="An error occurred!\n\nSO SAD!"; } ; fi

```
---
> For very simple media conversion 

* *Uses the automatic FFMPEG flags, settings and such, so the quality of the outputted files may not be great, but most popular modern formats work well for personal use.*  
* Selection-dialog for filetypes, error-dialog and system notification on completion   
* Supports multiple selected files.

---

This code is slightly modified from one or more original codesnippets found around the web, but the research was conducted in a frenzy and the source(s) are lost in time, like tears in rain.
</br>
</br>
If someone recognizes this as their code, I apologize for not giving proper credit.

---

### Requirements
* Zenity
* Parallel
* notify-send
* FFmpeg

---

### "Install"

> Copy paste into the "command"-field when creating or editing a Thunar custom action
 
* Replace or add to the filetypes (e.g. "ogg", "mp3", "m4a", ) if you want to convert to other formats

---

### Code

filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="An error occurred!\n\nSO SAD!"; } ; fi
