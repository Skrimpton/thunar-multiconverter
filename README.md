Very simple Thunar Custom Action zenity-GUI for ffmpeg - for very simple media conversion.
---
> Selection-dialog, error-dialog and system notification on completion   

* Supports multiple selected files.
* Applies ffmpeg default settings to selected files. 

### Requirements
* Zenity
* Parallel
* notify-send
* FFmpeg


### Code

> Copy paste into the "command"-field when creating or editing a Thunar custom action

```
filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="an error occurred!\n\nSO SAD!"; } ; fi

```
> _

filetype=$(zenity --list --height=300 --title="" --text="Convert film with ffmpeg:\n\nApplies standard settings\nfor selected filetype:"  --column="." "mp4" "mkv" "ogv" "mov" "flv" "avi" "wmv"); if [ "$filetype" != "" ]; then parallel -j 1 ffmpeg -i '{}' '{.}.'$filetype ::: %F && notify-send -t 9999999 "Convertion to $filetype is done!" || { zenity --error --text="an error occurred!\n\nSO SAD!"; } ; fi

