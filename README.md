# My_Project_PNG 

[The-Ultimate-Markdown-Cheat-Sheet](https://github.com/lifeparticle/Markdown-Cheatsheet)

## 💡ONE GUI Tab-1:
![Description of the image](My_AHK_Project_Snaps/ONE_GUI.png "ONE_GUI.png")

## ONE GUI Templates Manager Tab-2 :
![Description of the image](My_AHK_Project_Snaps/ONE_GUI_Templates_Manager.png "ONE_GUI_Templates_Manager")


# AHK Volume Control and Window Management

<details>
<summary>Click to expand/collapse the code</summary>

```autohotkey
; ===== Volume Control =====
#HotIf MouseIsOver("ahk_class Shell_TrayWnd")
WheelUp::Send("{Volume_Up}")
WheelDown::Send("{Volume_Down}")
RButton::Send("{RButton}")
#HotIf WinActive("ahk_class CabinetWClass")
RButton::Send("{Shift Down}{RButton}{Shift Up}")
#HotIf
RAlt::AppsKey
MouseIsOver(WinTitle) {
    MouseGetPos(&x, &y, &win)
    return WinExist(WinTitle " ahk_id " win)
}
```

</details>

<br>

## Any Selected Window Resizer GUI:
![Description of the image](My_AHK_Project_Snaps/Window_Resizer_GUI.png "Window_Resizer_GUI")

## 💡Action Menu:
![Description of the image](My_AHK_Project_Snaps/Action_Menu.png "Action_Menu")

## 💡Password Generater:
![image](My_AHK_Project_Snaps/Password_Generator.png "Password_Generator")


[code sample You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com
